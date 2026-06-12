---
title: "Recent Updates - now three kernels in grub"
date: 2008-06-03
forum: General Help
---

### Post by jimmy the saint on 2008-06-03
I have been using Ubuntu for around a year now and I am still a little green apparently.  I installed todays updates (Jun 3, 2008 ) and now grub lists three linux kernels. I ran Fiesty, Gutsy and now Hardy and have never had more than one show up.  Is this something new?  Do these new kernels include critical updates?  Is it normal for the old kernels not to be removed when new ones are added through Udate Manager, or was this simply an oversight?
I know it is a lot of questions, but like I said, I am still learning here.  should I remove these old ones or keep them around in case of application incompatibility?

Thanks for any input!

JTS

---

### Post by edm1 on 2008-06-03
It's completely normal. Many people dont like having multiple kernels in menu.lst but really, what difference does it make?

---

### Post by bingoUV on 2008-06-03
Unless you boot from the older kernels, you don't have any security or other risk. Only harm is
1. They clutter your grub menu, and
2. Take about 3 MB of hard disk space. 

If you do not like either of these, remove them. A sample advantage of keeping them : 
       You feel after some days that suspend does not resume always, but just 99% of the times. Earlier it used to resume 100% times, so you could boot from an older kernel.

---

### Post by jimmy the saint on 2008-06-03
Gottcha.

I appreciate the responses.  I use a thinkpad so suspend and resume have always been a pain.  I doubt the kernel version is going to make that better or worse!!  I will go ahead and hold onto them for a while and then remove them if all goes well.

Thanks guys!

---

### Post by Mikecore on 2008-06-03
I now have 4 old kernels. I am one that doesn't like having a lot of wasted space and will be manually removing them. I understand a back up kernel however snice hardy is a LTS release which I would guess will have many more kernel updates there needs to be a process in which after one or two backup kernels the rest are automatically removed. I say this because not all Ubuntu users or even most are not linux guru's to the point that they may not even know where to find the older kernels or how to correctly edit grub.<- which as you know could lead to not booting at all. Point is this is something that should be addressed on LTS releases.

---

### Post by louieb on 2008-06-03
Did a fresh install of Hardy Beta. Now I have 4 kernels listed also. Doesn't bother me. The easy way to get rid of them is to open Synaptic - click on the status tab - choose **installed (local or obsolete)** you'll find them listed there. Just right click a choose remove. 

Also the Debian update-grub script looks for an option in the auto magic setction of menu.lst  **# howmany= **that lets you choose the number of kernels to list in the menu. (Ubuntu  uses this script come kernel update time). 

:guitar:

---

### Post by chex_m8 on 2008-06-04
a simple way to not have them show up in the grub menu is to comment them out. 

sudo gedit /boot/grub/menu.lst

navigate to the old kernel title and put a # in front, now it won't show up.

---

### Post by robert shearer on 2008-06-04
I have 2 instances of Hardy on the same machine and 1 of Debian Etch.

When I apply updates the new kernel version appears in grub, only for the last Hardy install (presumably as the grub bootloader is for that install) and no new kernels are shown if I update the other o/s'.

The kernels are installed as I've checked with Synaptic in each instance.They just don't appear in grub.

How can I add them to grub so I can boot each o/s with its newest kernel??.

---

### Post by drs305 on 2008-06-04
I just wrote a guide on this today. The bytes are still wet!

If anything is unclear I can edit it.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by robert shearer on 2008-06-05
I tried startupmanager but it has no ability to modify other o/s boot options so unable to change the preferred kernel on my other Ubuntu and Debian installs on this drive.

However, by using gedit to cut and paste in grub menu.list I was able to manually add the options to boot the newest kernels (that were installed but not available thru grub).

Now I know how to do this it will just be a matter of editing grub each time the 2nd Hardy o/s or the debian Etch is updated with a new kernel.

Many thanks for your how-to.

---

