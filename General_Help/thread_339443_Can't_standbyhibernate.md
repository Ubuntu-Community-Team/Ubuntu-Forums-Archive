---
title: "Can't standby/hibernate"
date: 2007-01-15
forum: General Help
---

### Post by neoaddict on 2007-01-15
My swap is 1.1 GB, and I have 768 MB of RAM.

I tried to hibernate, but it just sends me back to my desktop and when standing by, I can't seem to load up anything - there's nothing on the monitor or anything.

Ideas?  Thanks.

---

### Post by Tristan9669 on 2007-01-16
same here but when press the hibernate button I get some error messages and my computer shuts down

---

### Post by vidak on 2007-01-17
Try adding a kernel option resume=/dev/hdaX where X is refers to your swap partition. Maybe this will solve your problem...

---

### Post by neoaddict on 2007-01-17
Sorry for sounding stupid, but how would you do that?

---

### Post by Tristan9669 on 2007-01-17
> **vidak said:**
> Try adding a kernel option resume=/dev/hdaX where X is refers to your swap partition. Maybe this will solve your problem...

how?

---

### Post by Rui Pais on 2007-01-17
do: 
```
gksudo gedit /boot/grub/menu.lst
```

search for the line that starts with the word kernel and contains the number of your kernel and add it at the end of it.

***Be careful with typing.*** No typo allowed or you system may even not boot!

edit: if you use kde or other, use kate, kedit, mousepad or whatever your text editor is...

---

### Post by vidak on 2007-01-18
You could try to enter the kernel options at boot time, I think you have to press 'E' or something like that... Its written on the lower part of the screen. So edit the kernel options, and boot the machine so. Try to hibernate the machine, power on, enter the according 'resume' option _again_, and see what happens... Hopefully it will work...

---

### Post by neoaddict on 2007-01-19
w00t!  I think that worked.  Thanks.

I just apt-get'd hibernate and used it along with your kernel option.

---

### Post by Tristan9669 on 2007-02-01
> **vidak said:**
> Try adding a kernel option resume=/dev/hdaX where X is refers to your swap partition. Maybe this will solve your problem...
I tried this but it still doesn't work. When I try to standby it goes to a black screen and shows 3 error messages talking about something failed then the computer shuts down. When I boot back up I get a little window asking for my password to unlock and log back in.
```
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash resume=/dev/hda8
``` hda8 is my swap

---

### Post by vidak on 2007-02-02
standby doesn't work at me, either. Try hibernating...

---

### Post by Tristan9669 on 2007-02-02
> **vidak said:**
> standby doesn't work at me, either. Try hibernating...
whats the difference, how can i standby

---

### Post by vidak on 2007-02-02
> **Tristan9669 said:**
> whats the difference, how can i standby

As I know standby is a low-power mode of the laptop, while hibernating saves the RAM to the swap partition, and after saving the laptop turns power off. When waking up from hibernation, the startup-sequence is the same until the grub-menu (note, that you should _always_ have that suspend part in the kernel options), and after grub, the computer skips the booting, and resumes your session from the swap partition.

---

### Post by galileon on 2007-02-07
for those standby and/or hibernate doesnt work, is anyone using nvidia cards and the nvidia driver?

---

