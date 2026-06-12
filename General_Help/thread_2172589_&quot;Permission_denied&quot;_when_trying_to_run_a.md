---
title: "&quot;Permission denied&quot; when trying to run application from terminal"
date: 2013-09-05
forum: General Help
---

### Post by dubious5 on 2013-09-05
I have created a stand alone application using matlab, and everything seems to work fine until actually trying to run it, as shown below.

[HR][/HR]
ck@R4:~$ sudo ./run_test1.sh /usr/local/MATLAB/MATLAB_Compiler_Runtime/v717
[sudo] password for ck: 
------------------------------------------
Setting up environment variables
---
LD_LIBRARY_PATH is .:/usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/runtime/glnx86:/usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/bin/glnx86:/usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/sys/os/glnx86:/usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/sys/java/jre/glnx86/jre/lib/i386/native_threads:/usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/sys/java/jre/glnx86/jre/lib/i386/server:/usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/sys/java/jre/glnx86/jre/lib/i386/client:/usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/sys/java/jre/glnx86/jre/lib/i386
./run_test1.sh: 1: eval: ./test1: Permission denied
ck@R4:~$ 
[HR][/HR]
I have tried the usual permission modifications with no luck. I am the owner of "test1" and it is marked as "allow executable."

Does anyone have any suggestions?

Thanks in advance!

Running Ubuntu 12.04 32-bit

---

### Post by steeldriver on 2013-09-05
Does *root *have permission to execute ./test1? Why do you need to run the script with sudo anyway?

---

### Post by dubious5 on 2013-09-05
root has permission, but It does the same thing without using sudo. I was just trying different things because I had run out of ideas.

---

### Post by steeldriver on 2013-09-05
can you share (at least the top few lines of) your run_test1.sh script? are you explicitly using eval or is that something the shell is doing implicitly?

---

