---
title: "Lubuntu 13.10 autostart issues"
date: 2013-10-23
forum: General Help
---

### Post by fpD7n6W on 2013-10-23
Hi,

I did a clean install of Lubuntu 13.10 recently, but at the moment I have problems with autostarting  applications.

Here's what I have done so far:

1. I want to autostart Dropbox after Login. Therefore, I copied the .desktop file into ~/.config/autostart/ . -> Doesn't work.
2. Then, I checked ~/.config/lxsession/Lubuntu/desktop.conf . I changed disable_autostart from "disable-config" to "no".
3. Reboot, and now the strange thing: Dropbox autostarts, but the network manager autostarts **twice **now.
4. Then I checked lxsession-default-apps Autostart tab, the app seems to suffer from a bug:

At first, the menu for disable-autostart is set to "no", but the field for "known applications" is empty. 
After changing disable-autostart to another setting and back to "no", some applications show up. However, the columns are copied 4 times, placed one after another. Repeating that process will cause more columns to appear, extending the window's size horizontally. Still, after playing around with this a bit, I'm unable to prevent the network manager from starting up twice.

I don't know if this bug is known, or where to report it. Can someone help me?

PS: I'd provide screenshots,but I don't know where I should upload them/link them from.

---

### Post by ajgreeny on 2013-10-23
Autostart of apps in lubuntu is not so straightforward as it is in Ubuntu or Xubuntu buty here are some pointers which may help you sort out the difficulty you are having.

Include command to start apps in list in:-
/home/username/.config/lxsession/Lubuntu/autostart
    eg,
    
parcellite            normal command
gmail-notify-delay        shell script copied to /usr/bin
bash -c "sleep 10; conky"    compound command to give 10 second delay

Other items go in either
    /etc/xdg/autostart    as the .desktop configuration file, ie the launcher copied /usr/share/applications
or
    /etc/xdg/lxsession/Lubuntu/autostart    in form
    
@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@notap  (this is a shell script I wrote to stop trackpad tap-to-click which I then copied to/usr/bin)

---

### Post by vasa1 on 2013-10-23
You [aren't alone in being confused]("http://askubuntu.com/questions/362263/what-is-default-applications-for-lxsession-in-lubuntu-13-10") about lxsession-default-apps.

---

### Post by infectedorganism on 2013-10-23
I'm not sure how helpful this post will be, but I have been suffering from the same issues. I too got most things set up correctly, but nm-applet was always spawning two processes and dropbox isn't autostarting. 

Ultimately, I restored a desktop.conf file that I had backed up from 13.04 and that seemed to fix most of my problems; everything is working properly except for dropbox.

  For now, I would suggest not using lxsession-default-apps, restoring an old or editing the desktop.conf file and then trying to get your autostart issues resolved.

Here is my /.config/lxsession/lubuntu/desktop.conf. You will need to edit for your particular install; theme, font, etc. 

```

[Session]
window_manager=openbox-lubuntu
disable_autostart=config-only

[GTK]
sNet/ThemeName=Lubuntu-default
sNet/IconThemeName=Faenza-Dark
sGtk/FontName=Ubuntu 11
iGtk/ToolbarStyle=3
iGtk/ButtonImages=1
iGtk/MenuImages=1
iGtk/CursorThemeSize=18
iXft/Antialias=1
iXft/Hinting=1
sXft/HintStyle=hintslight
sXft/RGBA=rgb
sGtk/CursorThemeName=DMZ-White
sGtk/ColorScheme=
iGtk/ToolbarIconSize=3
iNet/EnableEventSounds=1
iNet/EnableInputFeedbackSounds=1

[Mouse]
AccFactor=20
AccThreshold=10
LeftHanded=0

[Keyboard]
Delay=500
Interval=30

```

Here is my /.config/lxsession/lubuntu/autostart. Again, edit for your install:

```

@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@xscreensaver -no-splash
@xfce4-power-manager
@xcompmgr
@tint2
@volumeicon
@nm-applet
@clipit -n
@yeahconsole

```

Lastly, I too have dropbox installed and have a dropbox.desktop file in /.config/autostart, but that fails to start at boot. Because my desktop.conf is set to config-only, I may have to add '@dropbox start' to my /.config/lxsession/lubuntu/autostart config file, but I have yet to test that out.

**** Edit:** adding '@dropbox start' to my /.config/lxsession/lubuntu/autostart file works correctly. After adding that, dropbox successfully starts at boot.
Also, it seems as though lxsession ignores any files in the /.config/autostart folder. I can't say that with 100% confidence, but any .desktop file placed in that folder fails to autostart. Again, that may be because my desktop.conf file is set to config-only.

Hopefully you find something useful within this post.

---

### Post by vasa1 on 2013-10-23
My autostart (/home/vasa1/.config/lxsession/Lubuntu/autostart) is this:
```

/home/vasa1/.dropbox-dist/dropbox
/home/vasa1/bin/cpu-usage-alert.sh

```
Note the lack of "@" at the start of each line. The second line is irrelevant but the first is what I used to get Dropbox 2.4.3 going on startup.

---

### Post by sepbot on 2013-10-29
You can stop the the additional instance of the network manager from starting by removing the following line from your ~/.config/lxsession/Lubuntu/desktop.conf file:

```
 network_gui/command=nm-applet 
```

---

### Post by afc888ny on 2013-12-22
In case anyone who uses earlier versions of Lubuntu were redirected here, a procedure that worked for me was:
1) Go to /etc/xdg/lxsession/Lubuntu folder; 2) sudo nano autostart; 3) Add programs wanted, save and exit; **(Directly putting cli commands in autostart file causes lxsession user preferences to not load, thus I added bash filename.sh into autostart (no /bin/ pathname necessary) and achieved my purpose)

I had originally tried the above to try to 1) reactivate LibreOffice Quickstarter (a]Make bash file with &#8220;libreoffice --quickstart --nologo &#8211;nodefault&#8221;; b] place bash filename.sh in /etc/xdg/lxsession/Lubuntu/Autostart file); and 2) have pcmanfm to autostart up to my most commonly used directory (pcmanfm pcmanfm /media/a/LG/AC/Learn/).  The method I have provided works for older versions.

Again, hope everyone can learn from my mistake.  Definitely do not put regular cli commands directly into Autostart and expect them to execute normally, neither my desktop background, pcmanfm preferences(specifically the folder would open in icon view rather than my preference which is "detailed" view), nor my symbolic links loaded each time after bootup, and I was left with a desolate gray screen.

(I'm using Lubuntu 13.04 on a Samsung NC110 netbook, 2GB RAM)

---

### Post by peysun1 on 2014-01-01
> **fpD7n6W said:**
> Hi,

I did a clean install of Lubuntu 13.10 recently, but at the moment I have problems with autostarting  applications.

Here's what I have done so far:

1. I want to autostart Dropbox after Login. Therefore, I copied the .desktop file into ~/.config/autostart/ . -> Doesn't work.


I had the same issue with dropbox. This one worked for me:
Menu --> Preferences --> Default applications for LXSession --> Autostart 
Under **Manual autostarted application** type "dropbox start" (without quotes) and hit add.

---

### Post by Tacuabe on 2014-01-20
> **peysun1 said:**
> I had the same issue with dropbox. This one worked for me:
Menu --> Preferences --> Default applications for LXSession --> Autostart 
Under **Manual autostarted application** type "dropbox start" (without quotes) and hit add.

Yes, I can confirm this really works. The new GUI may require some tidying, but is a welcome addition which appears in Lubuntu 13.10.

I may add, that any application you may want to concot must be placed in /usr/bin to work in autostart. For example, I detest touchpads, so I wrote a simple application:

#!/bin/sh 

synclient TouchpadOff=1

Named it TouchpadOff.sh, enabled execution, placed it (as root) in /usr/bin and added it with the above method suggested by peysun. Now my touchpad is off from the very start.

---

### Post by xerostomus on 2014-03-21
I also faced strange not working of .config/autostart. I found out finally that all programs must be in a form .desktop file. 
So if I put there two files, say 
     autokey.desktop
     tappingoff.sh
then none of them were executed, to I had to write
     tappingoff.desktop
with following text:

[Desktop Entry]
Name=tapping off
GenericName=vyckvik mysi
Comment=aby neprudila
Exec=/home/USERNAME/bash/tapping_off.sh
Terminal=false
Type=Application
Icon=default
Categories=Utility;

Suprisingly now  both files run correctly... :-)
May be this can be of some help.

---

### Post by sini2 on 2014-03-23
I'm also having the same problem, and I might have figured out why changing the Autostart settings in lxconfig doesn't do anything.

Usually, the window should look like that:

[http://media.cdn.ubuntu-de.org/wiki/attachments/23/43/Einstellungen-Sitzungseinstellungen.jpg](http://media.cdn.ubuntu-de.org/wiki/attachments/23/43/Einstellungen-Sitzungseinstellungen.jpg)

But the netbook resolution of 1024x600 prevents the "OK" button from appearing !!!

Are there any keyboard shurtcuts to reach that damn button? :)

---

### Post by sini2 on 2014-03-25
Also, I tried hooking the Netbook (It's a Samsung NC10) up to a Full HD screen - max VGA out resolution is 1024x768, and the OK button was still not appearing.
Weird thing is: I could not set it any higher, although the VGA chip of the NC10 support a resolution up to 2048 x 1536 .... is there any driver problem, or how can I solve this?

---

### Post by sini2 on 2014-03-28
Hm.. anyone care to help here? :/ Please?

---

### Post by vasa1 on 2014-03-28
> **sini2 said:**
> Hm.. anyone care to help here? :/ Please?

You can sign up and ask here also: [https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)

---

### Post by vasa1 on 2014-03-28
> **sini2 said:**
> Hm.. anyone care to help here? :/ Please?

Please read [http://ubuntuforums.org/showthread.php?t=2190191](http://ubuntuforums.org/showthread.php?t=2190191) for a **workaround**.

---

### Post by sini2 on 2014-03-29
Hello vasa1,
Thanks for your reply! Unfortunately, the OK button is not rendered at all and does not show up on the bottom of the window even if I drag (or resize) it :/

---

### Post by danny28 on 2014-04-04
> **peysun1 said:**
> I had the same issue with dropbox. This one worked for me:
Menu --> Preferences --> Default applications for LXSession --> Autostart 
Under **Manual autostarted application** type "dropbox start" (without quotes) and hit add.

Great ! Worked for me ! :guitar: 
I tried manual edit of autostart with vi before, which doesn't work.

Thanks for the hint!

---

