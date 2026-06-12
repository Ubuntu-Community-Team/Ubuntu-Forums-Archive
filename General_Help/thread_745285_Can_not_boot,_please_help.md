---
title: "Can not boot, please help"
date: 2008-04-04
forum: General Help
---

### Post by mordi05 on 2008-04-04
Suddenly I am not able to boot my Ubuntu gutsy normally.
My OS hung previously when surfing the web. So I tried rebooting, only I am not able to.

The boot menu is displaying like it should (I dual boot with Win XP).
After I choose Ubuntu, I get the splash screen. Then there is the sequence of which all the boot text is supposed to display on screen, only I have always had this turned off, so there is just a blinking "_" in the top left corner of the screen. This is normal.

But then the login screen should display, and it doesn't. I am stuck with the blinking "_" for eternity.
So, what could have happend?

My system has been working fine for months, then this suddenly happens. 
From the boot menu I tried choosing (recovering mode), and this gives me a CLI as root. So I am free to enter commands, however I do not know what I could try to fix the problem.

Also, booting Windows still works.

Please don't let me stay in Windows longer than I have to.

---

### Post by banewman on 2008-04-04
From the recovery kernel open /boot/grub/menu.lst for editing and scroll down to the "end default options" The third line down starts with kernel - at the end of that line is the options for what is shown during boot - normally it is "quiet splash" but from what you said it will be different. You need to add "verbose" as the option there to see where/why the system is hanging.
While in the recovery kernel cd to /etc/rc2.d and ls the contents to see if gdm is listed.
:)

---

### Post by mordi05 on 2008-04-04
That certainly was the kind of help I was looking for.
But I can not seem to save the menu.lst file after I modify it.
This is really strange to me as I am logged in as root. (it says so right in the command line, root@computername:#).

It gives me this error: read-only filesystem.
when I try to save it.

What obvious thing am I missing?


EDIT:
By the way, gdm is listed as S30gdm in rc2.d.
And my menu.lst option reads: "...splash vga=792 quiet" This is part of a custom login theme I think. But as I said, I can save any changes.

---

