---
title: "EDD information not avaiable"
date: 2013-10-10
forum: General Help
---

### Post by jagjit_singh on 2013-10-10
I guess this question has already been asked couple of times before but I still can't find a significant solution to the following problem:

When I try to install Ubuntu on a PC which is currently having Red Hat Linux, in the boot, I am getting a message

BIOS EDD facility ..... 0 devices found
EDD information not available

Any help would be highly appreciated !

---

### Post by j-r-blake on 2014-04-05
So I've just had this problem too.

12.04.4, Mac Mini from late 2009, previously running fine. On boot, I got a black screen, nothing else, no USB working---indicated by no light on the optical mouse and Num Lock on the keyboard not working.

After turning on the verbose boot, I got the exact same error about EDD 0.16 not found, with a kernel timestamp of 1.xxx seconds.

This thread contained the solution:

[http://ubuntuforums.org/showthread.php?t=1464751](http://ubuntuforums.org/showthread.php?t=1464751)

So I worked round it by adding 

```

edd=on 

```

and 

```

nolapic

```

to the kernel boot line. (You get there by pressing 'e' when presented by the boot option in Grub.)

I've added this just in case anyone else can't find this solution.

J

---

