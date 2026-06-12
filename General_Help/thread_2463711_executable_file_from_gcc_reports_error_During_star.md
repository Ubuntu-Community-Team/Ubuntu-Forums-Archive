---
title: "executable file from gcc reports error: During startup program terminated with signal"
date: 2021-06-16
forum: General Help
---

### Post by smgandhi on 2021-06-16
Hello,

I am using Ubuntu 18.04 LTS on VMWare on Windows host.

I have been trying to run a c code using the Ubuntu terminal command line:
[I][B]gcc -mcmodel=large xxx.c -o xxx
./xxx 
[list of input files][/B]
[/I]It then reports segmentation fault. To further investigate it, I use the gdb.
[I]
[B]gdb --args ./xxx 
[list of input files]
(gdb) run[/B]
[/I]It reports an error: [I]During startup program terminated with signal SIGSEGV, Segmentation fault.

[/I]I found that some explanation for this error that states:  [COLOR=#0000cd]the shell or the wrapper specified with ' exec-wrapper ' crashed, not your program. Most often, this is caused by something odd in your shell's non-interactive mode initialization file.

[/COLOR]Can someone please help me how to work around this issue?

Thanks,

---

