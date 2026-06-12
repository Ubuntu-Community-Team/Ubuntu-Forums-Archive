---
title: "KDM corrupted ! Cannot login. Help Please !"
date: 2005-11-02
forum: General Help
---

### Post by TomG on 2005-11-02
Hi

I installed a KDM theme (from KDE-Look.org and installed with relevant application) and now (after logout/reboot) I get an error box that indicate the theme is corrupted !
I'm not able to get the login panel, I only have an endless hourglass on a black screen...

My questions :
1. How to get the console on boot instead of hanging hourglass/black screen ?
2. How to change the KDM theme to default from command line ?

Heeelllppp ! :( 

Tx
TomG

---

### Post by niko_ on 2005-11-02
personaly i use gdm and it has its themes in /usr/share/gdm/themes,
well try looking at /usr/share/kdm/themes and if its right then just remove the theme.
you can also find the theme probably by: locate kdm | grep -i theme, or something

---

### Post by TomG on 2005-11-02
Thanks for your reply.
Do you also know how I could get command line on boot ?
Tom

---

### Post by niko_ on 2005-11-02
just press ctrl+alt+f1 (could also f2,f3.. instead f1)
and it prompts you for your login and password, after that you will get into command line (console).

---

### Post by TomG on 2005-11-02
Tx a lot. Will try asap.
Tom :)

---

### Post by Thorsten on 2005-11-02
[quote=TomG]
I installed a KDM theme (from KDE-Look.org and installed with relevant application) and now (after logout/reboot) I get an error box that indicate the theme is corrupted !
I'm not able to get the login panel, I only have an endless hourglass on a black screen...
[/quote] 
Kdm theses are configured thru /etc/kde3/kdm/kdmrc
To get the original theme back, change the appropriate line back to
```
Theme=/usr/share/apps/kdm/themes/kubuntu
``` Alternatively, you can disable kdm themes altogether by changing
```
UseTheme=true
``` to
```
UseTheme=false
``` 
To change this file when you can't log in using kdm, change to a virtual console by pressing Ctrl-Alt-F1 (hold down both Ctrl and Alt and press F1), log in and do sth like
```
sudo nano /etc/kde3/kdm/kdmrc
``` 
I don't know if nano is installed on your syste. If not, you'll have to use another text editor. If you don't have any non-graphical editor, you can also start KDE from a virtual console. Log in and execute ```
startkde
```, e.g.

If that doesn't work because the default graphical terminal is taken up by the (broken) kdm, use sth like ```
startkde -- :1
```.

HTH,
Thorsten

---

### Post by TomG on 2005-11-02
Thanks for your help ! I solved the problem.

I installed KDE with Ubuntu (and not Kubuntu directly).
I don't know why but I had to edit /etc/gdm/gdm.conf and change the # to :
             # GraphicalTheme=Krystal
             GraphicalThemes=circles/:happygnome
Do you know why when we switch to KDE as default window manager gdm is still ran on boot ?

Thanks anyway !
Tom

---

### Post by Thorsten on 2005-11-03
[quote=TomG]Thanks for your help ! I solved the problem.

I installed KDE with Ubuntu (and not Kubuntu directly).
I don't know why but I had to edit /etc/gdm/gdm.conf and change the # to :
             # GraphicalTheme=Krystal
             GraphicalThemes=circles/:happygnome
[/quote] 
I'm not quite sure I understand your problem. You had a problem with kdm, which was solved, but you are still running gdm?

[quote=TomG]
Do you know why when we switch to KDE as default window manager gdm is still ran on boot ?
 [/quote] 
Sure. Installing kubuntu-desktop or KDE packages in general doesn't necesssarily mean that the display manager gets switched by the installation routine. As part of the boot process, [K]ubuntu runs the scripts to start kdm **and** gdm (if they are installed, see /etc/init.d/kdm and /etc/init.d/gdm.) Since it does not make sense to actually run both gdm and kdm, each script checks the contents of /etc/X11/default-display-manager and aborts if it isn't mentioned there. Therefore, you could set which display manager is run by changing /etc/X11/default-display-manager. There is a more convenient way though, simply run 
```
sudo dpkg-reconfigure kdm
``` and select kdm in the menu that will appear.

If you can't login from kdm, you may want to check out this issue:
[http://ubuntuforums.org/showthread.php?t=81431]("http://ubuntuforums.org/showthread.php?t=81431")

HTH,
Thorsten

---

### Post by TomG on 2005-11-03
Excellent. Thanks for this tip !
Tom

---

