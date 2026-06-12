---
title: "[SOLVED] getting libc"
date: 2006-12-22
forum: General Help
---

### Post by nga911 on 2006-12-22
hi 
how can i install libc from command line (my ubuntu crashed ,x actually ) and am trying to compile a Linux modules for my nvidia driver](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

edit: using apt get stuff

---

### Post by po0f on 2006-12-22
nga911,

libc6 is already installed; without it, I highly doubt you'd get far running Linux.  ;)

Now, if you are talking about compiling stuff, you'll need libc6**-dev**.  Along with this package, [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) (as the name implies) contains packages essential to building software on Ubuntu:
```
[FONT="Courier New"]$ sudo aptitude update && sudo aptitude install build-essential[/FONT]
```

---

### Post by nga911 on 2006-12-22
thx i will try that.:KS

---

### Post by nga911 on 2006-12-22
sorry didnt work keeps telling me that you must tell destination ](*,) :confused: ](*,)

---

### Post by po0f on 2006-12-22
nga911,

Please copy and paste the exact error, and a couple of lines above the error as well.

---

### Post by nga911 on 2006-12-22
yeah i would like to but i don't know how:confused: dose the print screen puton work :confused: or any other way

---

### Post by po0f on 2006-12-22
nga911,

Open a terminal.  Try to install the above application.  When it errors out, come here and reply to this thread.  Go back to the terminal and highlight the error with the mouse.  Come back here and middle-click to paste the error.  Hit submit.

---

### Post by nga911 on 2006-12-22
hi 
am not using X it crashed every time i boot ( was trying to install @#$% nvidia stuff and it damged my x conf file )](*,) so now am using a live CD ](*,)

---

### Post by po0f on 2006-12-22
nga911,

Which HOWTO are you following to get the drivers installed?  Are you following the directions step by step?

---

### Post by nga911 on 2006-12-22
:D i was using easyubuntu but it didnt do the job .. to i used a HOW-TO in [ubuntu.com]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") but i think i unstalled nvidia-xgl :twisted: ....... i got the .bin from nvidia web site but ween it wants to compile the kernel header it stopes ( no libc );)

---

### Post by po0f on 2006-12-22
nga911,

Can you boot into recovery mode?

---

### Post by nga911 on 2006-12-22
virtually am on recovery mode as after startup the X server crashes and am left with the command line :(  so say on.

---

### Post by po0f on 2006-12-22
nga911,

[ How to install Beta Graphics Driver (NVIDIA)](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29).

---

### Post by nga911 on 2006-12-22
one more thing is that i used ```
# sudo nvidia-config
``` and ofcurse it backed up my xconfig

---

