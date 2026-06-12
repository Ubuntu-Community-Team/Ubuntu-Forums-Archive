---
title: "removed lightdm, thinking to use startx, 14.04 won't finish booting"
date: 2016-01-29
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2016-01-29
I thought I'd give starting x with startx a try on my main system. It worked ok when I logged in as another user on other ttys, so why shouldn't it work on my mains system? Duh, maybe because lightdm modified some config files when it was installed and didn't reverse the changes when I ```
sudo apt-get remove lightdm
```-ed it? I was expecting to get a login prompt when I rebooted, but instead, it never gets there.

I don't want to drag anyone into a long diagnostic discussion (unless you find that sort of thing interesting). I can reinstall easily enough and I intended to soon anyway (because I mistakenly believed this was a 32 bit comp when I installed the main system, so I'd like to go back and redo it anyway). So I'm not in big trouble, & I'm booting from a perfectly fine PClinuxOS partition on the same drive.

BUT, that said, if anyone sees a likely answer, like maybe some config file that tells the system to start x and lightdm automatically that I could edit, that would be nice.

Thanks.

14.04 32 bit plain openbox

---

### Post by v3.xx on 2016-01-29
Ctrl + Alt + F1

Will that get you to a login screen?

I use to run startx and I found Arch to be a good reference.  Seen this?

[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)

---

### Post by Dreamer Fithp Apprentice on 2016-01-29
Thank you, sir.

I'm such an idiot I should run for congress. I don't know why I didn't think to try that. Yes, I can log in on tty1. Furthermore I can update and dist-upgrade. And I can startx. Everything works there. So, presumably I could reinstall lightdm and be back where I was before I went adventuring.  

Thanks for the excellent link. I've barely dipped into it and I don't know yet if it will tell me RIGHT way to revert to a setup that boots to a non graphical system, a bare tty with a login prompt automatically, but even if it doesn't I can see it is going to repay study.

---

### Post by v3.xx on 2016-01-29
Welcome :)

A simpler way would be to add "text mode" to your boot.

[http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)

---

### Post by Dreamer Fithp Apprentice on 2016-01-29
LOL, thank you. A few minutes ago I'd found this:

[https://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode](https://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode)

which is similar. So the answer lies in grub, and I didn't even need to uninstall lightdm. Although I'll probably leave it off, at least for now. I suspect grub could be tinkered with more, so as to have this as an ADDITIONAL option, rather than a REPLACEMENT. That would beat editing the grub command line, or even worse, editing /etc/default/grub, updating, and rebooting every time you want to switch modes. If & when I reinstall lightdm, I'll try that. But for now I'm going to leave it off. I want to play with xinit commands and maybe put them in a menu. That arch link you posted is going to be EXTREMELY helpful.

Thanks for pointing me in the right directions.

---

