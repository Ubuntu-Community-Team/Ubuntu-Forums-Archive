---
title: "Terminal and Files won't open / launch?"
date: 2018-08-09
forum: General Help
---

### Post by alka5eltzer on 2018-08-09
Hi all.

Running 18.04.1 LTS

Just booted up my system there. Can't open Terminal, nor can I open Files to browse my home folder etc. Is there a fix or anything I can do for this?

Thanks in advance

---

### Post by TheFu on 2018-08-09
It isn't normal for things to happen as you describe. Definitely unusual.
To know the issue, we need to know what you've done or may have done. I have a guess, but it is a permissions problem, if I'm correct.   I've seen it happen when someone used **sudo** with a GUI program.  Might you have done that?

The hard part is that troubleshooting is best performed using a terminal. There are a few different programs that are "terminals", so an lxterm, lxterminal, xterm or gnome-terminal are each options you can try. 

If you can't get one of those (or some other terminal) working, then we have to go the hard way, but realistically, if you are really new, it might be easier just to reinstall the OS again.  Normally, with the 18.04.1 distro, installations take under 15 minutes.  On a fast machine, they are 7-8minutes.  Just backup or copy off any files to some portable storage, if you can, first.

If you can get a terminal running, we can look around a little to see what might be the problem.  Looking at system log files is where I always begin. Those are under /var/log/.
You can also check permissions for personal settings, which are normally stored in ~/.config/ - so **ls -la ~/.config/ **will show the permissions we need to see.

---

### Post by alka5eltzer on 2018-08-09
Thank you for your reply.

Basically...it did a couple of updates yesterday and also this morning.. it updated Chrome?

When I launched Chrome, I had to basically start log back in again. As if it was a fresh install of chrome?
So I'm not sure if it was the chrome update or the update yesterday (Ubuntu base).

In my in my digging around.. I'm reading it could be something to do with my profile being corrupted?

Also... I can get to a terminal by hitting alt+f6 as far as I remember.

Thanks again &#128077;

---

### Post by alka5eltzer on 2018-08-09
Just to add... When I try to launch files.. it gets.. it has the whirly thing lol.

Also... I'm able to open Draftsight, but when I click on the window nothing happens.. I can't drag or move it or interact with the window.

---

### Post by QIII on 2018-08-09
Hello!

TheFu asked several questions that will provide some diagnostic information.  It would be helpful if you would answer those.

Cheers!

---

### Post by TheFu on 2018-08-09
The easy way to check if there is a personal setting as the issue is to create a new userid and login to that account.  Then try to run the same program.  If it works as expected, then you know the issue is in the other userid's ~/.config/ somewhere.

---

### Post by alka5eltzer on 2018-08-09
Will do.. I'll answer those.. not in my office at the moment. Thanks guys for your help &#128077;

---

### Post by cmcouto-silva on 2019-05-20
A friend of mine just faced a similar problem, and I was able to help him in the following way:

- First I download the [lxterminal]("https://pkgs.org/download/lxterminal") (.deb);
- Then I downloaded and opened it so that I was able to install the lightdm package through terminal: `$ sudo apt install lightdm -y` 
- Finally I did logout/login again. Done, solved! At least for him.

When I installed the lightdm display manager, it was automatically set as the default  display manager at the login session (Ubuntu 18.04 has the Wayland as default, though it will be there yet!).
I think there is some hardware incompatibility with Wayland display manager in a couple of PCs. I don't know, and I am far away from being an expert, but I hope it helps!

Best regards

---

### Post by pratham2003 on 2019-06-26
I had this issue today.
Turns out it was caused by Google Remote Desktop
Source: [https://askubuntu.com/questions/1050761/ubuntu-18-04-cant-start-nautilus-or-terminal/](https://askubuntu.com/questions/1050761/ubuntu-18-04-cant-start-nautilus-or-terminal/)
Be sure to log off and then re-login after uninstalling google remote desktop.

---

### Post by jjherriott3535 on 2019-10-03
I have this issue, too.

---

### Post by coffeecat on 2019-10-03
Old thread closed.

If anyone needs help with a similar issue, please start your own new thread. You are much more likely to get help that way.

---

