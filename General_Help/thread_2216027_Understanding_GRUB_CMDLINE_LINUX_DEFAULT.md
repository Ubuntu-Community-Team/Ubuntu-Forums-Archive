---
title: "Understanding GRUB_CMDLINE_LINUX_DEFAULT"
date: 2014-04-09
forum: General Help
---

### Post by jackkk2 on 2014-04-09
Hello, 

I am quite a beginner with Ubuntu which I like very much but does give me severall troubles. I actually use Xubuntu 13.10 and I am running it on a Sony Vaio with a ATI radeon graphic card. The processor is a little old, I am talking about a Intel Core Duo 2. 

I need some clarification on the GRUB_CMDLINE_LINUX_DEFAULT line which can be found in the grub file. Basically a few days ago I had the problem that every time I would close the lid of my laptop or the PC would go to suspend when I then would turn the PC on again it would actually reboot and not simply allow me to re-enter in the OS. 
To fix this I found that changing 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"

would solve this. 

Later I had another problem, no audio came out from my TV speakers when I would connect my PC to it via HDMI. 

To fix this I found that changing: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

would solve it. 

Now, of course I seems I need to choose, either having the PC not rebooting everytime it suspends OR having HDMI audio and this is annoying. 

 So my question is, what exavtly is the GRUB_CMDLINE_LINUX_DEFAULT and how can I keep both lines working together? 

Thanks a lot for your help!
Jack

P.S: of course after each grub file editing I always updated the grub via sudo update-grub.

---

### Post by Toz on 2014-04-09
Hello and welcome to the forums. I'm going to move this thread to General Help - it really isn't an Absolute Beginner's type question.

> So my question is, what exavtly is the GRUB_CMDLINE_LINUX_DEFAULT and how can I keep both lines working together? GRUB_CMDLINE_LINUX_DEFAULT contains command line arguments to the linux kernel. You can put as many as you want there provided they are separated by a space. In your case, you could use:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs radeon.audio=1"
```
...and they will all be passed to the kernel.

---

### Post by Bashing-om on 2014-04-09
jackkk2; Hi !

Might try these edits also, and see what results: {always make a backup prior to editing any file}
"GRUB_DEFAULT=0" -> GRUB_DEFAULT=saved
"GRUB_HIDDEN_TIMEOUT=0" -> #GRUB_HIDDEN_TIMEOUT=0  (add a 'comment' character to comment out the line)
"GRUB_HIDDEN_TIMEOUT_QUIET=true -> GRUB_HIDDEN_TIMEOUT_QUIET=false

For full documentation see:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
as a great place to start learning grub.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by jackkk2 on 2014-04-09
Hello! Thank you both for your help and very fast feedback! 
I was pretty sure I had tried what you advised Toz but maybe I didn't wrong earlier, I tried again and it seems to work! At least the PC doesn't reboot after it suspens. I still need to check the HDMI audio on the TV but I am confident.

---

### Post by Cavsfan on 2014-04-09
That is odd. All I have ever had for that line is **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**.

I wonder if the fact that you have a radeon video card has anything to do with it. I have an nvidia card.

From Ubuntu 9.04 (Jaunty Jackalope) to Ubuntu 14.04 LTS (Trusty Tahr) and every single version in between all I have ever used is the above command.

---

### Post by zemega on 2014-04-09
I have to edit that line as well on my laptop. It was a problem with keyboard and touchpad not being used in Ubuntu. It has AMD GPU though.

---

