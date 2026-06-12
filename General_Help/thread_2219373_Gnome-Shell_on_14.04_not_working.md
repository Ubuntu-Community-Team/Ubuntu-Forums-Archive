---
title: "Gnome-Shell on 14.04 not working"
date: 2014-04-23
forum: General Help
---

### Post by ryankrizan on 2014-04-23
Hello,

I installed 14.04 fresh this afternoon. Immediately after I updated the installation, and installed gnome-shell. However, ligthdm does not have the typical selector wheel to select Gnome over "Ubuntu" (Unity). So I switch to GDM, and I was given the selector wheel with 2 options. "Ubuntu" and "System Default" -- the "Default" selection gives me my desktop without any real environment. Logging into "Ubuntu" of course gives me Unity.

I installed gnome-shell the way I've done for some time now, via terminal "sudo apt-get install gnome-shell" and letting it do it's thing. 

Any help would be greatly appreciated. 

Thank you,

 Ryan

---

### Post by Frankiewizard on 2014-04-24
I had a problem like that so I installed the official >Ubuntu Gnome 14.04< and it functions well. I am not sure why the Gnome shell does not fire up when you install ubuntu unity. May be a Ubuntu Gnome jedi may be able to tell us?

---

### Post by tea for one on 2014-04-24
I have had the same problem. It seems that gnome-shell does not register itself in the desktop switcher software so there isn't a choice of desktop environments when you log in.

I have also separately installed Ubuntu Gnome 14.04, which does not contain Unity as a default. I then installed the Unity package via synaptic and, again, there was not a choice to choose Gnome-shell or Unity at log in. Only Gnome-shell was available.

I am still searching for a tutorial to allow the log in to recognise both desktop environments...........fingers crossed.

---

### Post by Frogs Hair on 2014-04-24
I have installed ,tried, and removed the Gnome Shell (3.10) but used the light gdm option during installation . I don't know if that makes a difference or not because I have never selected the gdm option.

---

### Post by tea for one on 2014-04-24
> **Frogs Hair said:**
> I have installed ,tried, and removed the Gnome Shell (3.10) but used the light gdm option during installation . I don't know if that makes a difference or not because I have never selected the gdm option.

Unfortunately, I could not get the desktop selector to work with either LDM or GDM.

Your installation of Trusty 14.04 is it new or upgraded from a previous version?

The reason I ask is that the desktop switcher functioned OK when I had a quick trial of the 14.04 beta during January 2014.

---

### Post by malspa on 2014-04-24
> **tea for one said:**
> Your installation of Trusty 14.04 is it new or upgraded from a previous version?

I was wondering about this, too. I have 12.04, with GNOME Shell added to it. Wondering if I'll have a problem logging into either Unity or GNOME Shell if I upgrade to 14.04.

---

### Post by Frogs Hair on 2014-04-24
> **tea for one said:**
> Unfortunately, I could not get the desktop selector to work with either LDM or GDM.

Your installation of Trusty 14.04 is it new or upgraded from a previous version?

The reason I ask is that the desktop switcher functioned OK when I had a quick trial of the 14.04 beta during January 2014.



I preformed a clean installation of the rc a week or so  before the final .

The final freeze was in place when I installed . [https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

---

### Post by tea for one on 2014-04-24
> **Frogs Hair said:**
> I preformed a clean installation of the rc a week or so  before the final .

The final freeze was in place when I installed . [https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

Thanks for the info.

It's a bit baffling that your release candiidate installation gives you a working desktop switcher at log-in, yet my installation of the official release does not allow me to switch to Gnome-shell.

Nevertheless, I'll keep trying to find a fix because I quite like to alternate between Unity and Gnome-shell.

---

### Post by Frankiewizard on 2014-04-25
The story continues > stay tuned >

---

### Post by tea for one on 2014-04-25
> **Frankiewizard said:**
> The story continues > stay tuned >

Hello Frankiewizard

I hope that you are still tuned..................

This worked for me.

I have logged in and out a few times between Unity and Gnome-shell and it looks like a solution.

```
sudo apt-get install gnome-session
```

I found it on the ask ubuntu site with a fuller explanation [http://askubuntu.com/questions/452385/lightdm-is-missing-gnome-shell-icon](http://askubuntu.com/questions/452385/lightdm-is-missing-gnome-shell-icon)

---

### Post by malspa on 2014-04-29
Excellent. Also, if you install the gnome-shell-extensions package, it brings in gnome-session.

---

### Post by Frogs Hair on 2014-04-29
I had installed the Tweak Tool and extensions at the same time as the shell .

---

### Post by Frankiewizard on 2014-04-29
Cheers >tea for one< sounds groovy. But my ubuntu Gnome 14.04 Lts is giving me a few problems at the moment and stopped booting. I may re-install Ubuntu and use your code   > sudo apt-get install gnome-session

---

### Post by tea for one on 2014-04-30
> **Frogs Hair said:**
> I had installed the Tweak Tool and extensions at the same time as the shell .

Now I understand why your desktop switcher appeared and mine was missing. You already had gnome-session installed together with other packages.

Now I am less baffled than a week ago.............

Best wishes

---

