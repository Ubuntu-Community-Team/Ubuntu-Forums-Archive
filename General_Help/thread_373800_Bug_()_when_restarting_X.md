---
title: "Bug (?) when restarting X"
date: 2007-03-01
forum: General Help
---

### Post by raul_ on 2007-03-01
When I restart X with ctrl+alt+backspace and try do log back in Gnome, i can hear the drums, but nothing happens. I can move the mouse, restart X again, etc etc, but Gnome won't fully load. I can log in E17 though. Is anyone having this problem? 

This started happening a couple of days ago, just magically. I made some modifications to my xorg.conf but i tried turning them off and the problem persists

---

### Post by zvacet on 2007-03-02
You are not first one with this problem.Type ctrl+alt+F1 and you will find yourself in the terminal.
```
  sudo dpkg-reconfigure xserver-xorg
```
If you want to disable ctrl+alt+backspace 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
that edit ```
sudo gedit /etc/X11/xorg.conf
```
and add this on the end of the file 
```
Section	"ServerFlags"
Option	"DontZap"	"yes"
EndSection
```
You can restart with ```
sudo /etc/init.d/gdm restart
```

---

### Post by Ramses de Norre on 2007-03-02
What does the unzap option do? Turn off the ctrl-alt-backspace function?
Sometimes gnome refuses to load here after an X restart too, the splash screen never comes up than. The only solution I've found already is going to a tty, change to runlevel 1 and change back to 2.

---

### Post by raul_ on 2007-03-02
Well as I said, the problem isn't the xorg.conf. Anyway i tried a reconfigure again, and nothing happened, so, that option doesn't work. I really didn't want to remove the shortcut.

Ramses de Norre, can you tell me how you do that so I can try and see if it works? Maybe i'll fill a bug report.
I wanted to dump Gnome for good but I can't [Get the darn XFCE transparency to work!]("http://www.ubuntuforums.org/showthread.php?p=2236476")

---

### Post by tcrroadie on 2007-03-02
> **raul_ said:**
> When I restart X with ctrl+alt+backspace and try do log back in Gnome, i can hear the drums, but nothing happens. I can move the mouse, restart X again, etc etc, but Gnome won't fully load. I can log in E17 though. Is anyone having this problem? 

This started happening a couple of days ago, just magically. I made some modifications to my xorg.conf but i tried turning them off and the problem persists

Have you tried deleting your Gnome session file.  

```
rm ~/.gnome2/session 
```

2 days ago Gnome was also acting crazy on me.  It was only auto mounting it's / directory and another ext3 partition I have, and none of my windows partitions.  I deleted my gnome session file in my home directory and it fixed it.  I still have no idea what originally caused the problem.  

Also, Is there a log file for Gnome that can be analyzed?  Or any other log that may give some information.  Xorg.log?

Just a thought.

---

### Post by raul_ on 2007-03-03
I don't know. I dumped Gnome for Xfce so maybe i'll try that later :)

There are xorg log files in /var/log/

I think it's smoething like Xorg.0.log or Xorg.anynumberhere.log. I don't know about gnome though

---

### Post by Ramses de Norre on 2007-03-04
> **raul_ said:**
> Ramses de Norre, can you tell me how you do that so I can try and see if it works? Maybe i'll fill a bug report.
I wanted to dump Gnome for good but I can't [Get the darn XFCE transparency to work!]("http://www.ubuntuforums.org/showthread.php?p=2236476")

I press ctrl-alt-F1, log in, sudo init 1, sudo init 2. Then gdm works again.
It's a temporary fix though.. you need to do it every time gdm refuses to load gnome...

For xfce: enable compositing in xorg.conf and edit ~/.config/xfce4/mcs_settings/wmtweaks.xml, search the line reading ```
<option name="Xfwm/UseCompositing" type="int" value="0"/>
``` and change '0' to '1', I needed to log off and on for it to persist. If you then open the window manager tweaks dialog you can alter the transparency settings.
Btw: xfce didn't work at all with that composite manager here, but it does work for most people.

---

