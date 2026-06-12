---
title: "Want different Grub boot order"
date: 2007-10-20
forum: General Help
---

### Post by CD Baric on 2007-10-20
I am dual booting into WinXP Pro and Ubunto 7.10 and want the Windows boot option to be first.

I just know my client will complain bitterly if his precious XP doesn't automatically boot first.

I know how to set it up BUT I also know that a kernel upgrade will lop off the Windows boot selection if it is at the top.

Any recomendations?

Thanks,

CD Baric

---

### Post by p_quarles on 2007-10-20
You should be able to cut-and-paste the Windows option so that it comes before the Automagic Kernels List in /boot/grub/menu.lst

Leave the "default" value at zero, and it will boot to Windows after the timeout duration.

Please note that I haven't tested this, so try this at your own risk. Based upon the directions in the menu.lst file, though, this should work. And, of course, it's easy to reinstall GRUB if this borks something.

---

### Post by rsambuca on 2007-10-20
Yes, that method works.  Just put your Windows entry before the line that says:

### BEGIN AUTOMAGIC KERNELS LIST

Keep the default at 0, and set the timeout at 2 seconds (which gives you enough time to hit at arrow key to stop the timer and select ubuntu).  Then the other Computer users don't have to press anything, and only have to wait 2 seconds.  You can also uncomment the '#hiddenmenu' line, and then they won't even know that grub is installed.  You can press ESC to get to the grub menu, since you know about it.

---

### Post by CD Baric on 2007-10-22
Thank you both, your recommendations worked perfectly.

Now client is happy and I am happy.

Best regards,

CD Baric

---

