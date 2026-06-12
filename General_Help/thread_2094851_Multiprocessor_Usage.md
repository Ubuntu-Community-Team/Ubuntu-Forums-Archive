---
title: "Multiprocessor Usage"
date: 2012-12-15
forum: General Help
---

### Post by ashkot on 2012-12-15
Hi all,
I have a situation wherein I have a 8 core computer and when I run a command from the terminal it uses one processor. Then if I want to run another command then I open another terminal.
 
the command is as follows:
samtools sort myfile.txt
 
What I want to do is run several commands in parallel, for e.g.
samtools sort myfile1.txt
samtools sort myfile2.txt 
 
both the commands should run in parallel.
 
what would be the best way to accomplish this?
 
thanks,
a

---

### Post by Doug S on 2012-12-15
If you do not want to run one command per terminal, then you could detach the command from the terminal. You will get your terminal prompt back and be able to continue. Meanwhile the first command will continue to run in the background. You would enter:```
samtools sort myfile1.txt &
samtools sort myfile2.txt &
samtools sort myfile3.txt &
samtools sort myfile4.txt &
samtools sort myfile5.txt &
```

---

### Post by ashkot on 2012-12-15
Could each of the command instead be a shell script?
 
 
> **Doug S said:**
> If you do not want to run one command per terminal, then you could detach the command from the terminal. You will get your terminal prompt back and be able to continue. Meanwhile the first command will continue to run in the background. You would enter:```
samtools sort myfile1.txt &
samtools sort myfile2.txt &
samtools sort myfile3.txt &
samtools sort myfile4.txt &
samtools sort myfile5.txt &
```

---

### Post by rnerwein on 2012-12-15
> **ashkot said:**
> Could each of the command instead be a shell script?
hi
hypothetical you can run everything in the background ( but i think it makes no sense to try e.g. firefox in the bg. ).
but - if your background process (e.g. a shell script) want's to have a terminal input it will be stoped by the shells job control !!!! you can those jobs by typeing in the same ! terminal: jobs
the shell will show you the stoped jobs.
you can get them back to the interactiv status by typing: fg
or: fg nr (number of the desired jobs)
even you kann kill them with: kill %jobnumber
but i think it makes no sense to send jobs wich are want some terminal input to the background
cheers

---

### Post by ashkot on 2012-12-16
I really want to run taks in parallel and wanted to know if there was a way to run several shell scripts on each core.

---

### Post by rnerwein on 2012-12-17
> **ashkot said:**
> I really want to run taks in parallel and wanted to know if there was a way to run several shell scripts on each core.
hi
you can bind a process to a special cpu using the command: [COLOR=Blue]taskset[/COLOR]   
eg. the command:[COLOR=Red] taskset -p 0x00000002 1780[/COLOR]  will bind the running process with PID 1780 on cpu1
for more information see: man taskset

have fun

---

### Post by 3rdalbum on 2012-12-17
> **ashkot said:**
> Could each of the command instead be a shell script?

It certainly can.

That's how my program Blacklight (a video converter) used to work. Blacklight would first look to see how many cores you have. Let's say you have four cores and six files to encode. It would start the FFMPEG transcoder four times simultaneously, once for each file.

Blacklight didn't need to manage the allocation of cores. It simply made sure that the number of files simultaneously being processed was the same as the number of cores in your computer, or the same as the number of files yet to encode - whichever was lower. The Linux kernel itself knew to allocate these different tasks to different cores.

---

### Post by rnerwein on 2012-12-17
> **3rdalbum said:**
> It certainly can.

That's how my program Blacklight (a video converter) used to work. Blacklight would first look to see how many cores you have. Let's say you have four cores and six files to encode. It would start the FFMPEG transcoder four times simultaneously, once for each file.

Blacklight didn't need to manage the allocation of cores. It simply made sure that the number of files simultaneously being processed was the same as the number of cores in your computer, or the same as the number of files yet to encode - whichever was lower. The Linux kernel itself knew to allocate these different tasks to different cores.
hi
there is a little (big) difference of binding a process to a core or let the system do it.
what i know a long time ago as a sys V developer is cp0 a special (intrerrupts and so on)
on the other side you will avoid cache faults because the program is fix bound on one
cpu and the corresponding cache. for special computing it makes sense to bind a task onto a cpu.
the kernel is quite clever. you can see this if you got a simple c-program eg.
main(){ while(1) }
you can see in a monitor that mostely this process will start at cpu0 and migrate step by step to your last cpu (eg. from cpu0 to cpu3 and if there is not other load on the system it will stay there)
cheers

---

### Post by ashkot on 2012-12-17
> **3rdalbum said:**
> It certainly can.

That's how my program Blacklight (a video converter) used to work. Blacklight would first look to see how many cores you have. Let's say you have four cores and six files to encode. It would start the FFMPEG transcoder four times simultaneously, once for each file.

Blacklight didn't need to manage the allocation of cores. It simply made sure that the number of files simultaneously being processed was the same as the number of cores in your computer, or the same as the number of files yet to encode - whichever was lower. The Linux kernel itself knew to allocate these different tasks to different cores.

I am certainly with you on some of it. Although it's still not clear if i could have a list of shell scripts, pass it to a program which could run each script separately or in parallel. When one script get's done the next one is loaded.

---

