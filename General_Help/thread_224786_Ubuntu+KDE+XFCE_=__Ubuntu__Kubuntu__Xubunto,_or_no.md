---
title: "Ubuntu+KDE+XFCE =  Ubuntu / Kubuntu / Xubunto, or not?"
date: 2006-07-28
forum: General Help
---

### Post by brjoon1021 on 2006-07-28
Hopefully that is clear from the Title. I want to play around with all of the major Linux desktops as I am still pretty new to Linux. Ubuntu has Gnome, Kubuntu has Kde and Xubuntu has XFCE. Well, I could multiboot all three easily enough. But... is adding KDE and XFCE to Ubuntu EXACTLY the same thing or would I be missing out on libraries, apps, and other niceties? I have tons of disk space so multibooting all three is just fine, but if adding the other two desktops to Ubuntu is the same thing, that would be even better.

Can Enlightenment be added (fairly easily for a newbie) to Ubuntu? If you have tried it, do you like it?

Thanks,

B.

---

### Post by ajgreeny on 2006-07-28
Go for it.  I added kubuntu-desktop (not xubuntu-desktop) to a standard ubuntu install and use Kubuntu KDE for preference all the time with no problems.  Some people even say that kubuntu installed that way is more stable than using the kubuntu iso to install it.  I don't know whether that is true, but I do know there are no likely problems with adding to the standard ubuntu.

If you do go ahead, install the xxxxx-desktop packages rather than straight KDE as it will contain more specifically (K X)ubuntu artwork etc and may be more easily compatible.

---

### Post by 5-HT on 2006-07-28
You can install the relevant metapackages (kubuntu-desktop & xubuntu-desktop) to get the default Kubuntu/Xubuntu installations installed along with Ubuntu -- there's no need to multi-boot unless you want to. Enlightenment is available in the repos as well. If you don't want a full blown Kubuntu/Xubuntu install alongside Ubuntu, you could just install the core KDE/XFCE packages (browse around the available packages in the repos).

GDM will display a list of the available DE/WMs to boot into.

I would suggest installing Kubuntu/Xubuntu/Enlightenment using Aptitude so that they would be easy to completely remove later on should you wish (there are many threads on Aptitude around the forums).

The default setting of Ubuntu's Aptitude is to treat recommended packages as dependencies. I would further suggest you change that setting, unless you are sure you would like to keep it, as it would result in the installation of *all*  of Kubuntu/Xubuntu/Enlightenment's recommended packages (which can be a lot).

e.g., to install Xubuntu without having Aptitude treat recommends as dependencies:

```
 sudo aptitude -R install xubuntu-desktop 
``` 
If you later wanted to completely remove xubuntu*:
```
 sudo aptitude purge xubuntu-desktop 
``` 
*residual configs for some packages may still reside on your system. They can be easily removed via Synaptic or Aptitude.

HTH

---

### Post by brjoon1021 on 2006-07-29
Thanks.

---

### Post by jimmygoon on 2006-07-29
GAH! don't use kubuntu-desktop! It changes your gdm/kdm , boot splash and all kidns of defaults! ITS EVIL!

Just do "sudo aptitude install kde" that way you can just choose it as an option! the same with xfce!

---

