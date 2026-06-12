---
title: "How about  ubuntu using  my  CPU&#65311;"
date: 2015-04-14
forum: General Help
---

### Post by zhou380491943 on 2015-04-14
Thanks  anyone  for  his/her  helping&#65281;At first,  apologise  for  my  less  computer  knowledge.
My CPU   information  through  'cpuinfo‘ is &#65306;
Intel(R) Core(TM) i3-2330M
Packages(sockets) : 1
Cores             : 2
Processors(CPUs)  : 4
Cores per package : 2
Threads per core  : 2
with using ’top’ command  in  terminal&#65292;I could  get four  processors  information,just  like  %cpu0~3.However,the column  'CPU%'  giving the information about processes is not divided  into  four  parts,just list  ,for example,  cpu% of  process  'firefox'   is  
Why  not   show us   repective   processor of  four,does  ubuntu   think   there  is  only  one  cpu??

Thank you  again!:p[ATTACH=CONFIG]261282[/ATTACH]

---

### Post by J_Me on 2015-04-14
Try using htop instead
```
sudo apt-get install htop
```
Or if you want to use the GUI goto the system monitor > system load

---

### Post by Holger_Gehrke on 2015-04-14
CPU-affinity of processes is weak; a process might run on a different CPU several times per second. 'top' can be set to show which cpu a process ran on at the time of observation by hitting 'f' to select fields, 'j' to choose the field "Last Used CPU" and 'enter'. You can also change the overview at the top to show the load per core by hitting '1'.

'top' is **very** configurable. Read the manual page ('man top') to find out more.

---

### Post by dino99 on 2015-04-14
nothing is wrong, except the terminology:

you have 1 phisical cpu, having itself 2 cores, each one is able to run 2 threads (multithreading): so 1 cpu with 4 threads

---

### Post by Impavidus on 2015-04-14
The %CPU column adds the CPUs together. You may occasionally see that a multithreaded application (like firefox) uses more than 100% of the CPU. When this happens, it runs on multiple cores simultaneously.

---

### Post by zhou380491943 on 2015-04-18
Thank you for replies posted above&#65281;What's more,may I have more questions about the relationship between the CPU and process&#65311;If I could&#65292;now the questions is“
Could a process use four threads  in the two cores when it run simultaneously on two cores&#65311;”
Is there any articles about this issue&#65311;
Sincere gratitudes to anyone help&#65281;
Have a nice day

---

### Post by dino99 on 2015-04-18
you still can search/read about multithreading. But you need to understand that multithreading can only be used by apps written for it: systemd is an example of apps to run multiple processes at once in parallel mode, cuda is an other example. That mean that usual queued big processes have to be splitted into smaller sub-processes to run on the found multi-cores. So the user cant do tweakings to change how the app have been designed and written.

---

