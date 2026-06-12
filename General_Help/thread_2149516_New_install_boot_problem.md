---
title: "New install boot problem"
date: 2013-05-29
forum: General Help
---

### Post by benjamin3878 on 2013-05-29
Hi, I'm new to Ubuntu and having a little trouble with with a dual boot system I'm setting up. I have 2 ssd, one with windows 7 and the other Ubuntu 12.04. After installing Ubuntu and booting into the OS successfully once, it had many updates to install. Once the installs were done, a restart was performed and   is now were I'm having some problems.  

 

 The boot-loader opens correctly I believe but once I select Ubuntu it boots to a command line inner face. The command line asks for user name and then password. Once those are entered the “startx” command can be used to load the desktop but there is nothing there but the background image. I right clicked and added a folder so the OS can be assessed and programs can be run but I'm not sure why the menu bars are missing?

 

 I have figured out that the fully working OS can be assessed by clicking the second option of the boot-loader, “recovery mode” then selecting the first option again which is “resume normal boot”. Then everything works great... boots to the gui login screen and everything works.

From some of the things i have read, it seems like it could be a problem with the graphics card drive but im not having much luck getting it updated..

Any help would be very kind!
Thanks

---

### Post by carl4926 on 2013-05-29
Ubuntu gives you the option to boot older kernels
It does sound like something went wrong with the update to the newer kernel.
Use the Advanced options to access those and see which works
Boot it and check your updates again

What graphics device do you have

---

### Post by HiImTye on 2013-05-29
if you're using proprietary drivers, post the output of
```
apt-cache policy linux-headers*
```
(or for a cleaner output)
```
sudo apt-get install aptitude
aptitude search linux-headers~i
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by benjamin3878 on 2013-05-29
thanks for the quick responce.. I have a Gigabyte HD5770 which is the ATI Radeon HD 5770, just over clocked i think. Its also 1 GB GDDR5/ 128 bit, if that makes any difference.
I'm working on trying to boot the old kernel now.

as for the proprietary driers, im not sure? Heres a link to the first code after running..[https://docs.google.com/file/d/0B1le7hwsnsc_SGw3ODdUM1FIOEk/edit?usp=sharing](https://docs.google.com/file/d/0B1le7hwsnsc_SGw3ODdUM1FIOEk/edit?usp=sharing)

The set set of code was much shorter, so here it is..
benjamin@benjamin-System-Product-Name:~$ aptitude search linux-headers~i
i A linux-headers-3.5.0-23          - Header files related to Linux kernel versi
i A linux-headers-3.5.0-23-generic  - Linux kernel headers for version 3.5.0 on 
i   linux-headers-3.5.0-31          - Header files related to Linux kernel versi
i   linux-headers-3.5.0-31-generic  - Linux kernel headers for version 3.5.0 on 
i   linux-headers-generic-lts-quant - Generic Linux kernel headers

---

### Post by HiImTye on 2013-05-29
are you using the default Ubuntu interface? if so, try to open a terminal (ctrl+alt+t or alt+f2 then enter 'gnome-terminal') and try
```
sudo apt-get install dconf-tools
dconf reset -f /org/compiz/
setsid unity
```
and if you still don't have unity, use
```
unity --replace
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by benjamin3878 on 2013-05-30
hey guys, thanks for the help. I ran that code and got all kinds of errors. I can post the results if you would like but I ended up downloading and installing one of the beta drivers for my graphics card which seems to have fixed the problem.  
thanks again for the help.

---

