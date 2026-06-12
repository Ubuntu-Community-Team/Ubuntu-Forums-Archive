---
title: "Problems with MPI"
date: 2013-09-13
forum: General Help
---

### Post by s_a2 on 2013-09-13
I am somewhere between a beginner and whatever is the next level. 

2 years ago, my collaborator wrote a C code that computes a certain physical quantity. This quantity is made up of a sum of many integer modes. Since each mode is independent of another mode, it can be thought of as something like a loop, where each individual loop element (labelled by an integer mode) is computed by a different core then sent to the MPI counter core.

On my own machine (Ubuntu 11, dual-quad cores), I executed

>> mpd&

once then ran the code with

>> mpiexec -n $number_of_cores    ./output_code     $parameter1       $parameter2

The code ran fine on my machine for a long time. then at some point, I must've typed in the wrong thing like 

                  mpiexec -2 instead of mpiexec -n 2 

or something like  mpd -n, I am not sure. I then went away for over a year and did not touch anything. Now I am working on the same code and I get the following error messages:

>> mpiexec mpiexec -n $number_of_cores   ./output_code   $param1    $param2
    ssh: connect to host user-desktop port 22: Connection timed out

If I try

>> mpd &
   An mpd is already running with console at /tmp/mpd2.console_user on user-desktop. 
   Start mpd with the -n option for a second mpd on same host.

I couldn't make much of this either, and google-ing the error messages didn't help me fix the problem because I am pretty incompetent.
It seems to me like some sort of a communication problem between the cores since it comes from "ssh" and mentions port22.
I was hoping that someone could point out a fix for this in a way an ignorant fool like myself can understand.

Thanks all

S

---

