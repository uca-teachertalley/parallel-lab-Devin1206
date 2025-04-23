Prime number count parallelism exercise

- This code counts the number of primes in an array without parallelism
- Your goal is to add parallelism with OpenMP!
- The project should be configured properly, but you can add OpenMP to 
  Visual Studio project by going to Project Properties-C/C++-Language.
  Set the Open MP Support option to "Yes"

  1. What is the average time for ten runs of the serial version of the code? (You may run this 
10 times and manually calculate the average or you may write a loop to do it for you.)  37.44 seconds
	
	
2. What is the average time for ten runs of the parallel version of the code? (You may run 
this 10 times and manually calculate the average or you may write a loop to do it for 
you.)    34.38 seconds


3. Calculate the speedup of the parallel version. Is the parallel code significantly faster?  See 
how to calculate speed up below: 
• First: work out the difference (increase) between the two numbers you are 
comparing. 
• Increase = Original Number – New Number. 
• Then: divide the increase by the original number and multiply the answer by 100. 
• % increase = Increase ÷ Original Number × 100. 
 16.7468496

4. The Methodology section above described how you decompose the summation routine to 
parallelize it.  Obviously, OpenMP did all the work for you.  How many elements of the 
array do you think OpenMP assigned to each processor? Hint: have your code print 
the number of threads in the computation (the function omp_get_num_threads() 
returns the number of threads, the function omp_get_thread_num()returns the 
thread number for the current thread.  See an example of how you need to structure your 
code so you that you don’t print the values inside of your for loop. 
int count = 0; 
#pragma omp parallel 
{ 
cout << “Thread number” << omp_get_thread_num() << endl; 
#pragma omp for reduction(+:count) 
for (int i = 0; i < n; ++i) { 
// do work here 
} 
} 
You may see that the output looks strange and that is because the threads are not 
synchronizing output.   


5. If you have time, try to parallelize the gen_numbers() function and compare the timing. 
Was it faster?  If it wasn’t faster, what do you think happened?