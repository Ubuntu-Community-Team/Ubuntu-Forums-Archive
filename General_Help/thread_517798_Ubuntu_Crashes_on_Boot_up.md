---
title: "Ubuntu Crashes on Boot up"
date: 2007-08-05
forum: General Help
---

### Post by ADloser on 2007-08-05
About once every week my Ubuntu freezes at boot up and continues to freeze until I fix it. 

When it freezes it displays a blank screen. So far I have been pushing random button combinations, Alt+Ctrl+ F1 through F12, escape, tilda, and so forth, until a bunch of text appears on the screen. Unfortuneately I can't read the entire text because about 3/4 of it runs off the screen. I can however see that it is asking for my password to perform maintenence. After I enter my password it complains about not being able to  use apt-get and tells me to install apt-get with the apt function (lol). 

I also see "fsck" in there somewhere so I usually just type fsck and then proceed to hold down "yes" for all the prompt (usually about inode values or sizes or something). This will usually fix the problem and I can boot up on the next reboot.  

My question can someone tell me what the hell is going on with my Ubuntu? I'm sure this is not normal and that I am not fixing this correctly. How can I solve this problem or at least what button combinations will let me exit out of the freeze and into a prompt.

 Thanks!!

---

### Post by nitro_n2o on 2007-08-05
you should have a look at the syslog and bootstrap in /var/log you might get some hints

---

### Post by ADloser on 2007-08-05
bootstrap is blank

syslog has only the most recent good entry:

```
Aug  5 09:27:33 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Aug  5 09:27:34 ubuntu anacron[5713]: Job `cron.daily' terminated
Aug  5 09:27:34 ubuntu anacron[5713]: Normal exit (1 job run)
```

---

### Post by ADloser on 2007-08-09
up

---

### Post by ADloser on 2007-09-03
up

---

### Post by fumduck on 2007-09-03
How many partions do you have on your harddrive (s)?? what i found before (and this may not find your problem) was that I had reinstalled a partion and never updated my fstab.  So my boot would halt when it was doing a filesystem check, because it could not find partion and give some  press  ctrl d to ignore and continue boot...?

---

### Post by family on 2007-09-03
I have a similar problem, except this happens to me every time I boot. For me  though, pressing random key combinations does not help. My HP boots, hits the Ubuntu load screen, and freezes right before the login screen. Then I have to manually shut it down, boot again, goto the Boot Menu, select Hard Drive, and then there is a 3/4 chance it will make it all the way to GNOME.
I use a wireless USB mouse, and my brother suggested that my computer tries to boot from the USB stick. How does this explain the Ubuntu load screen coming up every time though? :confused:

---

### Post by family on 2007-09-03
rrgh, somebody reply before this problem sinks into the deep mud-pits of unanswered posts.

---

### Post by ADloser on 2007-09-05
> **fumduck said:**
> How many partions do you have on your harddrive (s)?? what i found before (and this may not find your problem) was that I had reinstalled a partion and never updated my fstab.  So my boot would halt when it was doing a filesystem check, because it could not find partion and give some  press  ctrl d to ignore and continue boot...?

I have 3 partitions. 1 windows 1 Ubuntu and 1 storage
How do I update my fstab?

---

