---
title: "GUI to manage Plymouth themes Ubuntu 14.04"
date: 2014-11-25
forum: General Help
---

### Post by Gordonbp531 on 2014-11-25
Can anyone help with this?
I've tried installing Super-boot-manager - added the ppa, but I then get "some packages were ignored or old ones used" and then "can't find package super-boot-manager"

I've used the CLI process [here]("http://www.enqlu.com/2014/04/how-to-install-and-change-boot-splash-screen-themes-on-ubuntu-14-04-lts-or-linux-mint-17.html"), but the command "sudo update-alternatives &#8211;config default.plymouth" gives "update-alternatives: error: unknown argument `&#8211;config'. I looked at the man pages for update-alternatives and it says to use -- before the config argument, but that still produces the same error.

What's currently happening is that on boot up I get the edubuntu splash screen. I've changed the config file default.plymouth in /lib/plymouth/ to Ubuntu rather than edubuntu, but I'm still getting the edubuntu splash screen.

What I'm looking to do is to change the splash screen at boot, and the sign on screen backgrounds to something other than the plain colour, but I don't want the edubuntu screen!

At the very least, I'd like to get back to the original Ubuntu theme!

---

### Post by Dennis N on 2014-11-25
Maybe you are forgetting a step:

After using the command **[FONT=Courier New]sudo update-alternatives --config default.plymouth[/FONT]**  to select a new theme,
you need to run the command **[FONT=Courier New]sudo update-initramfs -u[/FONT]** and then reboot.

---

### Post by CantankRus on 2014-11-25
Copy **Dennis N's** command because the one you posted was using a single long dash before config ...ie  [COLOR="#FF0000"]**[FONT=Courier New]&#8211;config[/FONT]**[/COLOR]
Whereas it should be a double dash ...ie  [COLOR="#FF0000"]**[FONT=Courier New]--config[/FONT]**[/COLOR]

---

### Post by Gordonbp531 on 2014-11-26
Hi, sorry I've not been back, been a bit busy!
If you look at my OP, you'll see I used the "--" before the config argument, and got the same error message.

---

### Post by CantankRus on 2014-11-26
> **Gordonbp531 said:**
> Hi, sorry I've not been back, been a bit busy!
If you look at my OP, you'll see I used the "--" before the config argument, and got the same error message.
Can you run it again and copy and paste your terminal output.
eg
```
glen@Trusty:~$ **sudo update-alternatives --config default.plymouth**
[sudo] password for glen: 
There are 4 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                               Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/moka-logo/moka-logo.plymouth                   150       auto mode
  1            /lib/plymouth/themes/moka-logo/moka-logo.plymouth                   150       manual mode
  2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo-scale-2.plymouth       99        manual mode
* 3            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth               100       manual mode
  4            /lib/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth   150       manual mode

Press enter to keep the current choice[*], or type selection number:
```

---

### Post by Gordonbp531 on 2014-11-26
For some inexplicable reason, the command has now decided to work, with no error message, and I've been able to select the theme, which I wasn't able to do before.
I'm hoping it's now fixed!

Thanks for the input.
Cheers

---

