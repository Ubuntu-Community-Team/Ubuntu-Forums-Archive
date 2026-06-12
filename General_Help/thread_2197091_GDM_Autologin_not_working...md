---
title: "GDM Autologin not working.."
date: 2014-01-02
forum: General Help
---

### Post by krishna.988 on 2014-01-02
Hi All,

I removed lightdm since I was not able to login as it was booting to a blank screen. Hence I installed GDM and everything was fine. Now when I try to use the Autologin option through GUI interface and also by editing the 

[SIZE=4][FONT=FontinRegular] /etc/gdm/custom.conf[/FONT][/SIZE]

AutomaticLoginEnable=[COLOR=#008000]**[COLOR=#000080][B]true**[/COLOR][/B][/COLOR]
AutomaticLogin=[COLOR=#008000][B] <My User name>
[/B][/COLOR]
Autologin fails in GDM also. It goes into a black screen.


Can anyone help me out on how to reset lightdm to ubuntu defaults..and autologin?

Btw I tried

sudo *dpkg*-reconfigure lightdm etc...commands

---

### Post by krishna.988 on 2014-01-03
Do I need to reinstall ubuntu for Autologin to work again?

---

### Post by krishna.988 on 2014-01-03
Should I post in any other section? Why no one is replying?

---

### Post by krishna.988 on 2014-01-05
Nevermind..I reinstalled Ubuntu it was fine..But later on I realized this might be the reason..which might help others facing the same issue

[COLOR=#333333][FONT=UbuntuRegular]Although normal software updates will bring your system up to 12.04.3, the Hardware Enablement Stack (HWE; the *-lts-raring packages) is not part of those updates ([by policy]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#A12.04.3_.2B-_13.04_Hardware_Enablement_Stack_Policies_and_Procedures")).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]You can install the HWE packages manually, but there are some caveats.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]To upgrade use this command line only:[/FONT][/COLOR]
sudo apt-get install --install-recommends xserver-xorg-lts-raring
[COLOR=#333333][FONT=UbuntuRegular]**The --install-recommends is important:** it makes sure that the xserver will install completely. Without it, xserver will only install partly, and apt will remove most of your system. You do not need to add linux-generic-lts-raring, as it is already recommended by the xserver package, and the 3.8 kernel will install too.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]When you upgrade like this you may notice that there are configurations left over, among others those of the original xserver-xorg. You can purge them (I always do), but beware: this will remove the symlink /etc/X11/X that is used to start the XServer, so on next boot it won't start. To prevent this, after purging left over configurations, do the following **before the next boot**:[/FONT][/COLOR]
sudo dpkg-reconfigure xserver-xorg-lts-raring
[COLOR=#333333][FONT=UbuntuRegular]This will recreate the necessary symlink and everything is fine again.[/FONT][/COLOR]

---

