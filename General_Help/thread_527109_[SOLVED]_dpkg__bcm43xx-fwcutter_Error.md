---
title: "[SOLVED] dpkg / bcm43xx-fwcutter Error"
date: 2007-08-16
forum: General Help
---

### Post by dreamsR4living on 2007-08-16
Yesterday I have reinstalled bcm43xx-fwcutter. Since then I get the following error message when I try to install software with apt-get in terminal:

Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

When I try to install software with Synaptic I also get a bcm43xx-fwcutter error message.

Can anybody tell me how to solve this problem?

Tnx

---

### Post by heimo on 2007-08-16
I think I'm in middle of trying to solve a similar problem on another thread. Your package management database, or install scripts for that package are broken. Somewhere (and sorry for not checking if I remember this correctly) under /var/lib/dpkg/info are files beginning with that package name (bcm43xx-fwcutter). I'd try to move those to another directory and then forcing reinstall of that package (files you moved will be replaced with fresh ones from .deb package). That's the basic principle I've used several times to fix this kind of problems. Let us know if you need more specific advice.

---

### Post by dreamsR4living on 2007-08-17
I found the bcm43xx-fwcutter files in the directory which you mentioned. Which package should I reinstall? The bcm43xx-fwcutter? And how can I force the reinstall?

Tnx in advance.

---

### Post by heimo on 2007-08-17
> **dreamsR4living said:**
> I found the bcm43xx-fwcutter files in the directory which you mentioned. Which package should I reinstall? The bcm43xx-fwcutter? And how can I force the reinstall?

Tnx in advance.

Try something like
```
sudo apt-get --reinstall install bcm43xx-fwcutter
```

---

### Post by dreamsR4living on 2007-08-17
Tnx That worked, problem solved!

---

### Post by macaholic on 2007-08-17
If your problem is solved make sure you use the thread tools to mark it is [SOLVED] so if other people have the same problem they know that there is a possible answer in this thread.

---

### Post by dreamsR4living on 2007-09-05
My dpkg / bcm43xx-fwcutter error is coming up again.

Last time I have deleted my bcm43xx files in /var/lib/dpkg/info and reinstalled bcm43xx again. I didn't save those files because everything was working properly, but the error is back.

The error I get when using synaptic is;

E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1

The error I get when using dpkg in terminal is;

Setting up bcm43xx-fwcutter (006-1) ...
--16:05:31--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:05:31 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone advise me what to do to solve this problem?

---

### Post by dreamsR4living on 2007-09-07
Solved downloading wl_apsta.o from another website. (wget [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o) ) and extracting it with the following commands; 

> sudo bcm43xx-fwcutter -w /lib/firmware/ wl_apsta.o     

and     

> sudo bcm43xx-fwcutter -w /lib/firmware/2.6.XX wl_apsta.o

---

### Post by fakinfe on 2007-09-22
> **dreamsR4living said:**
> Solved downloading wl_apsta.o from another website. (wget [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o) ) and extracting it with the following commands; sudo bcm43xx-fwcutter -w /lib/firmware/ wl_apsta.o     and     sudo bcm43xx-fwcutter -w /lib/firmware/2.6.XX wl_apsta.o

Hi i am getting  error  extracting bcm43xx_microcode2.fw ...
/lib/firmware/2.6.XX/bcm43xx_microcode2.fw: No such file or directory.when i run your commands .Am new to this what should i do now

---

### Post by Junpei on 2008-05-05
Man, i can't move the files...

I'm having the same problem with bcm43xx-fwcutter... And I can't fix it...:(

Please tell me how i fix it...!!!

Thanks!

---

### Post by dreamsR4living on 2008-06-04
> Man, i can't move the files...

I'm having the same problem with bcm43xx-fwcutter... And I can't fix it...

Please tell me how i fix it...!!!

Thanks!

What Ubuntu version do you use? In Ubuntu Gutsy and Hardy installing bcm43xx wireless cards is pretty straight forward through the restricted drivers manager. Do you use Feisty?

---

