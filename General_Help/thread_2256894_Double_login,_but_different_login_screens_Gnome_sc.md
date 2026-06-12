---
title: "Double login, but different login screens: Gnome screensaver and possibly LightDM?"
date: 2014-12-15
forum: General Help
---

### Post by deragon on 2014-12-15
I suffer from a double login, half the time.  The login screens are different.  The first one is Gnome screen saver (gnome-screensaver) and is the one I want to get ride of, as it does not allow anybody else to login as a different user.  The second one is the normal Ubuntu 14.04 login screen, which I want to continue to use.  I am not sure if it is the LightDM locker, as "light-locker" is not installed on my computer (but maybe it is integrated; not sure).

Before I report a bug, I want to make sure that my problem is not caused by some bizarre configuration in my environment.  Can anyone tell me why gnome-screensaver kicks in?  BTW, remember, it does not kick in all the time and I have not been able to reproduce it at will.

Running Ubuntu 14.04 LTS Trusty Thar.

---

### Post by ajgreeny on 2014-12-15
You should be able to change the settings of gnome-screensaver, if that is what is really causing your problem, and stop it asking for a password to stop it. then any key press or mouse movement will kill it straight away.

Are you using kubuntu as your forum info suggests, or unity/gnome, and therefore gnome-screensaver?

---

### Post by deragon on 2014-12-22
I figured out that there is something in Gnome screensaver's settings that is wrong, but I do not know how to change them.  In fact, why is Gnome screensaver running in the first place?  Why was it installed?  By what/whom?  What is its purpose, giving that there is already a locker provided by Unity?

Now regarding the settings, concretely, where can I change them?  What file and parameters should I look for?

I know that the following settings are not the one I must play with, because they affect Unity's screen locker.  I do not know what to change.
[INDENT][FONT=Fixedsys]
gsettings get org.gnome.desktop.screensaver lock-enabled
gsettings get org.gnome.desktop.lockdown     disable-lock-screen
[/FONT][/INDENT]

I am running Ubuntu 14.04 LTS Trusty Thar with Unity 7.  I corrected my profile to correct this.  Thank you.

---

### Post by CantankRus on 2014-12-22
Not too sure what you're referring to.
Do you mean by double login, that the login screen is different than the lock screen.
Other desktops like Xubuntu Ubuntustudio and Lubuntu will install **lightdm-gtk-greeter**
which will become your login screen.

Packages that will install lightdm-gtk-greeter...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **apt-cache rdepends lightdm-gtk-greeter**
lightdm-gtk-greeter
Reverse Depends:
  lightdm-gtk-greeter:i386
  xubuntu-default-settings
  lightdm-gtk-greeter:i386
  xubuntu-desktop
  xubuntu-default-settings
  ubuntustudio-lightdm-theme
  ubuntustudio-desktop
  ubuntustudio-default-settings
  mythbuntu-lightdm-theme
  lxgames-default-session
  lubuntu-nexus7-default-session
  lubuntu-default-session
  lubuntu-core
```
Ubuntu uses **unity-greeter**.

```
sudo apt-get purge lightdm-gtk-greeter
```
Reboot.

Can also check in synaptic for other greeter packages.
(There is also **ubuntustudio-lightdm-theme** and **mythbuntu-lightdm-theme**)

---

### Post by deragon on 2014-12-26
I should be more specific.  I have two lock screens to go through when I resume from suspend.  See the attachments associated with this reply   The first lock screen is from gnome-screensaver and this is the one I want eliminated.  I want to know how come this happens to me and how to fix it.  The second lock screen is from unity-greeter; that one I want to keep.

---

### Post by zuloch on 2015-03-10
Hi deragon, I have the same problem, did you find a solution?

Thanks

---

### Post by grayscale2 on 2016-01-24
Hi guys!
I just killed gnome-screesaver process and the problem disappeared.
kill -9 `pidof gnome-screensaver`

---

