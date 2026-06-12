---
title: "GRUB Problems"
date: 2006-12-10
forum: General Help
---

### Post by gtkourounis on 2006-12-10
I installed 6.06 on my computer and i used the tool included to create two partitions, one for linux and one for windows..... and then, after the installation ended and the computer restarted grub doesnt give me the choice of booting form windows. In fact it automatically goes to linux, i have to press Esc for the Grub monitor to show up (and thats when i see that windows is missing). Also, i know that the windows partition has not been deleted because when i go to System > Administration > Disks i can see the two partitions and the correct sizes that i gave them. Now i know that i have to change someting in the /boot/grub/menu.lst but i am not sure what i have to add. If anyone knows PLEASE help, i dont want to install windows all over again, it takes a century!!!!!

anyhow, help will be much appreciated.

thanx in advance.
gtkourounis

---

### Post by dolphinholmer on 2006-12-12
can you post the text of your /boot/grub/menu.lst file?

---

### Post by indytim on 2006-12-12
Gtkourounis,

Don't take offense at this.... you said you made 2 partitions one for windows and one for linux.  Have you installed both operating systems in their correct partition?

IndyTim

---

### Post by Topsiho on 2006-12-12
I have had the same problem in the distant past, which amounts to the menu being hidden.

As root (sudo) edit /boot/grub/menu.lst and change the last line  

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

by putting a # in front it:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

This comments out this last line so that it is no longer active.

Hope this helps :)

Topsiho

---

### Post by gtkourounis on 2006-12-13
thanks for all the help, but i have to say that i completely removed windows after 2 days, got sick of it. Back to 100% linux, no more need for partitions.

thanx guys

---

### Post by Topsiho on 2006-12-16
Quite OK to throw MS away. But it's not necessary to do this right now. Probably you have some hardware (in my case a canon scanner) or some programs that you used for centuries, and built quite some data with them, in Windows, for which you would like to use windows until you moved the batch to Linux. I have some old WordPerfect material which can not be converted to OO.org without a lot of twiddling, so ...

But I agree: the sooner one can get rid of MS the better

:)

Topsiho

---

