---
title: "moved /lib - now missing most bash commands"
date: 2013-02-22
forum: General Help
---

### Post by themullet on 2013-02-22
Hi there, wondered if anyone could help me, 

so I moved /lib 

mv /lib /home/lib

had lib64 -> /lib

was clearing space on my root partition. 

now none of the commands seem to work. 

i.e.

mv
-bash: /bin/mv: No such file or directory

still logged into the server as root and can cd around, though that's about it. 

any ideas?

---

### Post by steeldriver on 2013-02-22
boot a live CD / USB and move it back maybe?

---

### Post by dino99 on 2013-02-22
its an easy way for breaking  the system  :p
dont be surprised it cant find its children  ;)

where do you think updates/upgrades will go now ?

maybe copying back the moved stuff will be enough (if silly softlinks have not been created/broken), otherwise you are ready for a new fresh clean install   

):P):P):P

---

### Post by Impavidus on 2013-02-22
If you still know exactly what you have done you can move everything back. With commands unavailable you'll have to use a live session. If you actually deleted things it will be more complicated.

If I'm not mistaken /lib, /bin, /sbin, /etc have to be in the root partition, as they are needed before mounting other partitions. /usr should be safe to move somewhere else, if you really need.

---

### Post by themullet on 2013-02-22
> **steeldriver said:**
> boot a live CD / USB and move it back maybe?

server is a remote server :( 

> **dino99 said:**
> its an easy way for breaking  the system  :p
dont be surprised it cant find its children  ;)

where do you think updates/upgrades will go now ?

maybe copying back the moved stuff will be enough (if silly softlinks have not been created/broken), otherwise you are ready for a new fresh clean install   

):P):P):P
think it's looking like a clean install :( 

mmmm rip server

---

### Post by zhaozhou on 2013-02-22
```

/bin/busybox mv /home/lib /lib

```

---

### Post by themullet on 2013-02-22
> **zhaozhou said:**
> ```

/bin/busybox mv /home/lib /lib

```

nice idea

```
root@oxim:/bin# /bin/busybox mv /home/lib /lib
-bash: /bin/busybox: No such file or directory
root@oxim:/bin# busybox mv /home/lib /lib
-bash: /usr/bin/python: No such file or directory
-bash: busybox: command not found

```

---

### Post by themullet on 2013-02-22
so here's what thinking of trying, following zhaozhou idea of different shell, I've got phpmyadmin on there, upload a shell into one of the content areas of my site and then try editing using that ...hhmm permission might be a bit off, though it's worth a shot

---

### Post by steeldriver on 2013-02-22
Hmm... I'm thinking there shouldn't be too much in /lib (as compared to, say /usr/lib) that is essential for running basic commands - maybe just the .so files in /lib itself and /lib/i386-linux-gnu/ ?

So maybe something like

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/lib:/home/lib/i386-linux-gnu/
```would get your basic commands back?

Obviously change the i386- to the appropriate x64 directory if it's a 64-bit installation

---

### Post by themullet on 2013-02-22
> **steeldriver said:**
> Hmm... I'm thinking there shouldn't be too much in /lib (as compared to, say /usr/lib) that is essential for running basic commands - maybe just the .so files in /lib itself and /lib/i386-linux-gnu/ ?

So maybe something like

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/lib:/home/lib/i386-linux-gnu/
```would get your basic commands back?

Obviously change the i386- to the appropriate x64 directory if it's a 64-bit installation
nice idea, gave that a try with i386-linux-gnu/ and x86_64-linux-gnu/ without any luck

---

### Post by themullet on 2013-02-22
just as a heads up this is running ubuntu 8 lts, if that's of any useful information!

---

### Post by schragge on 2013-02-22
> **themullet said:**
> so here's what thinking of trying, following zhaozhou idea of different shell, I've got phpmyadmin on there, upload a shell into one of the content areas of my site and then try editing using that ...hhmm permission might be a bit off, though it's worth a shotYou probably need a standalone, statically linked shell that doesn't depend on libc6. Try *busybox-static* or *sash*.

---

### Post by schragge on 2013-02-22
Another thought. You can try to reboot into rescue (initramfs) shell. It's BusyBox.

---

### Post by themullet on 2013-02-22
> **schragge said:**
> You probably need a standalone, statically linked shell that doesn't depend on libc6. Try *busybox-static* or *sash*.
any idea how to get it on there though? 

--- 

just got pointed to the recovery tool by my server provider ... looks like can do the usb stick method remotely ... righty time to get this moved and hopefully should be back up and running again soon. 

thanks all for the help. Lesson here, when moving important files / folders copy em and then link up the copy rather than moving :)

cheers all, hopefully can move this to solved in a bit

---

### Post by rnerwein on 2013-02-22
> **themullet said:**
> Hi there, wondered if anyone could help me, 

so I moved /lib 

mv /lib /home/lib

had lib64 -> /lib

was clearing space on my root partition. 

now none of the commands seem to work. 

i.e.

mv
-bash: /bin/mv: No such file or directory

still logged into the server as root and can cd around, though that's about it. 

any ideas?
hi
you got of answers and i will tell you now what the problem is.
in a terminal type e.g.: ldd /bin/bash  and have a look to the output.
richi@tschang:~ 16:41-> ldd /bin/bash
    linux-vdso.so.1 =>  (0x00007fff4f948000)
    libtinfo.so.5 => /lib/x86_64-linux-gnu/libtinfo.so.5 (0x00007fd81e975000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fd81e771000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fd81e3b1000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fd81ebb9000)

all the commands (wich i know on the system now) are dynamic linked (see the pointer to the library-path). that's the same in windoz there is it called DLL..
good old time - the system always got some static linked commands (the /sbin/sh for sure !). 
ciao

---

