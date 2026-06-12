---
title: "Missing mouse and keyboard controls in settings manager"
date: 2013-06-20
forum: General Help
---

### Post by ineuw on 2013-06-20
Using Xubuntu 12.04 and after installing Xfce4, the mouse (and keyboard) control applets are gone from the Settings manager. Also missing is the Xorg/Nvidia applet from the Accessories menu. Being new at this, I am not sure what I did exactly and don't know the terminal commands to check, but I do know that xfwm4 is running and it's one of the startup applications. Thanks in advance.

---

### Post by Toz on 2013-06-20
> Using Xubuntu 12.04 and after installing Xfce4
Xubuntu includes Xfce, so this is a little confusing. Did you install xfce on top of an Ubuntu installation?
>  the mouse (and keyboard) control applets are gone from the Settings manager. 
If you did install Xfce on top of Ubuntu, the keyboard and mouse applets are included in the xfce4-settings package. Was it installed as well?

---

### Post by ineuw on 2013-06-21
> **Toz said:**
> Xubuntu includes Xfce, so this is a little confusing. Did you install xfce on top of an Ubuntu installation?

If you did install Xfce on top of Ubuntu, the keyboard and mouse applets are included in the xfce4-settings package. Was it installed as well?

Thanks for asking the right questions, since I didn't know where to begin to get "the ball rolling". The installation is pure Xubuntu 12.04 from disk and not an upgrade from Ubuntu. As you pointed out, the above mentioned applets existed in the Settings Manager (and a couple of additional ones as well), in the original install. The applets appeared neatly laid out as opposed to currently being fewer applets which are divided into lined sections.

I tried to teach myself to make sense of all the various desktop environments and their components, and the differences between Xfce, Gnome, KDE, and installed some components from Gnome and KDE as well. Then, some time ago, I found this link [http://www.psychocats.net/ubuntu/purexubuntuprecise](http://www.psychocats.net/ubuntu/purexubuntuprecise) and ran the posted commands , as well as to be sure, I reinstalled Xfce 4.10, when the problem of the missing applets appeared.

---

### Post by Toz on 2013-06-21
>     I reinstalled Xfce 4.10, when the problem of the missing applets appeared. 
Xubuntu 12.04 included Xfce 4.8. If you've installed 4.10, have either upgraded Xubuntu to a newer release or are you using the 4.10 PPA?

To check your Xubuntu release, from a terminal window:
```
cat /etc/lsb-release
```

To check to see if you are using the Xfce 4.10 PPA:
```
apt-cache policy xfce4
```

---

### Post by ineuw on 2013-06-21
> **Toz said:**
> Xubuntu 12.04 included Xfce 4.8. If you've installed 4.10, have either upgraded Xubuntu to a newer release or are you using the 4.10 PPA?

To check your Xubuntu release, from a terminal window:
```
cat /etc/lsb-release
```

To check to see if you are using the Xfce 4.10 PPA:
```
apt-cache policy xfce4
```

Thanks for the commands. Here are the results:

ineuw@xubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

ineuw@xubuntu:~$ apt-cache policy xfce4
xfce4:
  Installed: (none)
  Candidate: 4.10.0~ppa1
  Version table:
     4.10.0~ppa1 0
        500 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/) precise/main i386 Packages
     4.8.0.3 0
        500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) precise/universe i386 Packages

 . . . . which means it's not installed :(

---

### Post by Toz on 2013-06-21
> ineuw@xubuntu:~$ apt-cache policy xfce4
xfce4:
Installed: (none)
Candidate: 4.10.0~ppa1
Version table:
4.10.0~ppa1 0
**[COLOR="#FF0000"]500 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/) precise/main i386 Packages[/COLOR]**
4.8.0.3 0
500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) precise/universe i386 Packages

You have the PPA referenced in your system so you must have had it installed at one time? I'm wondering whether it was installed at one time then removed (or components of it removed) by the commands entered earlier. 

What is the result of:
```
sudo apt-get update
```
...then
```
sudo apt-get --just-print upgrade
```

---

### Post by ineuw on 2013-06-21
> **Toz said:**
> You have the PPA referenced in your system so you must have had it installed at one time? I'm wondering whether it was installed at one time then removed (or components of it removed) by the commands entered earlier. 

What is the result of:
```
sudo apt-get update
```
...then
```
sudo apt-get --just-print upgrade
```

Prior to this post 'sudo apt-get update' didn't update xfxe4, although I tried several times. I also suspect that at an earlier attempt to restore xfce4, I only managed to re-install some selected features through Synaptic.

_But now - the following happened as I write this from Windows._

Successfully installed Xfce 4.10 as reported by 'apt-cache policy xfce4', but there was no change to the Settings Manager. So, I logged out, and the login screen provided the options of Xubuntu or Xfce sessions but neither option worked. Either selection keeps returning me to the login screen.  I rebooted, and using recovery mode, connected to the network and it downloaded additional files - but to no avail. It still won't get me in. Since this is a standalone desktop, I never logged in and on boot it went directly to the desktop.

---

### Post by Toz on 2013-06-21
From within recovery mode:

1. Delete the .Xauthority and .ICEauthority files from your home directory (if they exist):
```
rm /home/<USER>/.Xauthority
rm /home/<USER>/.ICEauthority
```
...replace <USER> with your actual userid.

2. Check that you haven't run out of disk space:
```
df -h
```

3. Delete your cached sessions:
```
cd /home/<USER>/.cache
rm -rf sessions
```

4. And finally, check the xsessions log file for any error messages that might help identify a cause for the automatic logout (if anything exists, it will be towards the end of the file)
```
cat /home/<USER>/.xsession-errors
```

Then reboot and see if you get to the desktop.

---

### Post by ineuw on 2013-06-21
> **Toz said:**
> From within recovery mode:

1. Delete the .Xauthority and .ICEauthority files from your home directory (if they exist):
```
rm /home/<USER>/.Xauthority
rm /home/<USER>/.ICEauthority
```
...replace <USER> with your actual userid.

2. Check that you haven't run out of disk space:
```
df -h
```

3. Delete your cached sessions:
```
cd /home/<USER>/.cache
rm -rf sessions
```

4. And finally, check the xsessions log file for any error messages that might help identify a cause for the automatic logout (if anything exists, it will be towards the end of the file)
```
cat /home/<USER>/.xsession-errors
```

Then reboot and see if you get to the desktop.

1. Deleted the .Xauthority and .ICEauthority files - they did exist.
2. All disks are less than 10% used - it's a new 500GB disk and most of my data is online at Wikipedia, Commons, or Wikisource.
3. Removed the sessions file.
4. .xsession-errors listed only one error regarding blutooth. The file was about 20 lines.

Many thanks. Did as instructed and logged in to the desktop directly, as it was before. I am still missing the keyboard mouse & the additional driver applets. While logged in as root from the recovery console, I managed to get an ugly  graphical interface as root. I checked the settings manager, the mouse, keyboard and other additional applets were there.

---

### Post by Toz on 2013-06-22
Log in normally again. Is there any chance you can send a screenshot of your Settings Manager?

Is xfce4-settings package installed?
```
apt-cache policy xfce4-settings
```

Which applets are installed:
```
ls /usr/share/applications/xfce-*
```

Note: Additional drivers are located at Software Centre -> Software Sources -> Additional Drivers or by running, from a terminal window:
```
software-properties-gtk
```

---

### Post by ineuw on 2013-06-22
Toz, I can't thank you enough for your patience and guidance. Seeing that we are from the same country - from cities with mayoral problems, I hereby offer you recently vacated mayoral positions in a Quebec city of your choice. That is, until your mayor also resigns.

_Here are the results_

[ATTACH=CONFIG]244033[/ATTACH]

[ATTACH=CONFIG]244038[/ATTACH]

_apt-cache policy xfce4-settings_

xfce4-settings:
  Installed: 4.10.1-1ubuntu1~ppa0.12.04.1
  Candidate: 4.10.1-1ubuntu1~ppa0.12.04.1
  Version table:
 *** 4.10.1-1ubuntu1~ppa0.12.04.1 0
        500 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
     4.8.3-1ubuntu3 0
        500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) precise/universe i386 Packages

_ls /usr/share/applications/xfce-*_

/usr/share/applications/xfce-backdrop-settings.desktop
/usr/share/applications/xfce-display-settings.desktop
/usr/share/applications/xfce-keyboard-settings.desktop
/usr/share/applications/xfce-mouse-settings.desktop
/usr/share/applications/xfce-session-settings.desktop
/usr/share/applications/xfce-settings-manager.desktop
/usr/share/applications/xfce-ui-settings.desktop
/usr/share/applications/xfce-wm-settings.desktop
/usr/share/applications/xfce-wmtweaks-settings.desktop
/usr/share/applications/xfce-workspaces-settings.desktop
/usr/share/applications/xfce-xfcalendar-settings.desktop

_software-properties-gtk_

gpg: /tmp/tmpDJ73DT/trustdb.gpg: trustdb created

ubuntu.mirror.iweb.ca

---

### Post by Toz on 2013-06-22
> **ineuw said:**
> Toz, I can't thank you enough for your patience and guidance. Seeing that we are from the same country - from cities with mayoral problems, I hereby offer you recently vacated mayoral positions in a Quebec city of your choice. That is, until your mayor also resigns.
lol. You are welcome to ours whenever you want him.

> _Here are the results_

[ATTACH=CONFIG]244033[/ATTACH]

[ATTACH=CONFIG]244038[/ATTACH]

_apt-cache policy xfce4-settings_

xfce4-settings:
  Installed: 4.10.1-1ubuntu1~ppa0.12.04.1
  Candidate: 4.10.1-1ubuntu1~ppa0.12.04.1
  Version table:
 *** 4.10.1-1ubuntu1~ppa0.12.04.1 0
        500 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
     4.8.3-1ubuntu3 0
        500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/) precise/universe i386 Packages

_ls /usr/share/applications/xfce-*_

/usr/share/applications/xfce-backdrop-settings.desktop
/usr/share/applications/xfce-display-settings.desktop
/usr/share/applications/xfce-keyboard-settings.desktop
/usr/share/applications/xfce-mouse-settings.desktop
/usr/share/applications/xfce-session-settings.desktop
/usr/share/applications/xfce-settings-manager.desktop
/usr/share/applications/xfce-ui-settings.desktop
/usr/share/applications/xfce-wm-settings.desktop
/usr/share/applications/xfce-wmtweaks-settings.desktop
/usr/share/applications/xfce-workspaces-settings.desktop
/usr/share/applications/xfce-xfcalendar-settings.desktop

_software-properties-gtk_

gpg: /tmp/tmpDJ73DT/trustdb.gpg: trustdb created

ubuntu.mirror.iweb.ca
Everything looks right, but I don't understand why the extra applets are not showing up in the Settings Manager. 

Can you try running the applet commands directly to see if the applets themselves work?
```
xfce4-mouse-settings
```
```
xfce4-keyboard-settings
```

Can you also post back the contents of your ~/.config/menus directory:
```
ls ~/.config/menus
```

Did you ever, by chance, edit the main applications menu?

---

### Post by ineuw on 2013-06-22
> **Toz said:**
> 

_xfce4-mouse-settings_ The panel comes up fine - but the settings were default, which is a clue since my original mouse was set to left hand use which is still functioning, but this showed right handed use. Thus these settings don't seem to be implemented. Is there another file which might hold my initial settings?

_xfce4-keyboard-settings _ also brings up the panel, and everything I use is default US English. I made no changes

_ineuw@xubuntu:~$ ls ~/.config/menus_
xfce-applications.menu          xfce-applications.menu.undo-21
xfce-applications.menu.undo-10  xfce-applications.menu.undo-22
xfce-applications.menu.undo-11  xfce-applications.menu.undo-23
xfce-applications.menu.undo-12  xfce-applications.menu.undo-24
xfce-applications.menu.undo-13  xfce-applications.menu.undo-25
xfce-applications.menu.undo-14  xfce-applications.menu.undo-26
xfce-applications.menu.undo-15  xfce-applications.menu.undo-27
xfce-applications.menu.undo-16  xfce-applications.menu.undo-28
xfce-applications.menu.undo-17  xfce-applications.menu.undo-29
xfce-applications.menu.undo-18  xfce-applications.menu.undo-30
xfce-applications.menu.undo-19  xfce-applications.menu.undo-31
xfce-applications.menu.undo-20  xfce-applications.menu.undo-32

[QUOTE]Did you ever, by chance, edit the main applications menu?

Yes. I moved items from one grouping to another, hid some, and even deleted a couple of duplicates. I also added a group named 'session'  which holds the three xfce session choices of Shutdown, Reboot and Logout. However, I didn't touch the Settings or the Configuration Editors. Just looked at them. I now just noticed that the Main Menu editor shows the xcfe panel manager as being displayed (checked) but it doesn't show up on the menu although, when xfce4-panel -p is pasted into the terminal, it works fine.

I use a single panel (Panel 0) placed at the bottom of a very simple desktop layout, somewhat emulating Windows XP  [ATTACH=CONFIG]244046[/ATTACH]

---

### Post by Toz on 2013-06-22
Lets try disabling your menu changes. We can do this by moving the menu directory (that way we can restore it later if required).
```
mv ~/.config/menus ~/.config/menus.BAK
```
Log out and back in again.

Also, can you post your ~/.xsession-errors file?
```
pastebinit ~/.xsession-errors
```
...and post back the link that is generated.

---

### Post by ineuw on 2013-06-22
> **Toz said:**
> Lets try disabling your menu changes. We can do this by moving the menu directory (that way we can restore it later if required).
```
mv ~/.config/menus ~/.config/menus.BAK
```
Log out and back in again.

Also, can you post your ~/.xsession-errors file?
```
pastebinit ~/.xsession-errors
```
...and post back the link that is generated.

The reset menu looks interesting, but there is no change in the settings manager. If it's of any importance to you, after logging out, my screen went crazy and flickered.

[http://paste.ubuntu.com/5791509/](http://paste.ubuntu.com/5791509/)

---

### Post by Toz on 2013-06-23
IHmmm.

If you want to reset your menus to the way they were, simpy rename the folder back:
```
mv ~/.config/menus.BAK ~/.config/menus
```

Can you login as the guest account and see if the items show up in the Settings Manager properly. If they do, then there is something wrong with your profile. Otherwise it is a system problem. At least help us identify where the issue is.

---

### Post by ineuw on 2013-06-23
> **Toz said:**
> IHmmm.

If you want to reset your menus to the way they were, simpy rename the folder back:
```
mv ~/.config/menus.BAK ~/.config/menus
```

Can you login as the guest account and see if the items show up in the Settings Manager properly. If they do, then there is something wrong with your profile. Otherwise it is a system problem. At least help us identify where the issue is.

Sorry for the delay. I created a Guest account as there was none before. The settings manager is fine and the missing icons are there. 

Is it worth repairing the account, or create a new account with the root privileges, remove & purge the broken account, then recreate it under the same name? I don't mind learning. This whole excercise is about being completely familiar with Linux.

As for the menu, I don't need to restore because all the menu items are there - they were just moved to "Other".  Besides I kept notes which I saved on an NTFS drive.

I also ran saved the results of "dpkg --get-selections" and it seems strange. The results are in the attached zip file.

---

### Post by Toz on 2013-06-23
> **ineuw said:**
> Sorry for the delay. I created a Guest account as there was none before. The settings manager is fine and the missing icons are there.
Then its defintely something wrong with your profile. You could create another account, or could just reset your Xfce. To reset your Xfce settings:

1. Logout, go to the first tty (Ctrl+Alt+F1) and log in to the text session.
2. Rename the config directories:
```
mv ~/.config/xfce4 ~/.config/xfce4.BAK
mv ~/.config/autostart ~/.config/autostart.BAK
mv ~/.config/menus ~/.config/menus.BAK
mv ~/.config/Thunar ~/.config/Thunar.BAK
mv ~/.cache ~/.cache.BAK
mv ~/.local/share ~/.local/share.BAK
```
3. Restart lightdm (should auto-login you in again):
```
sudo service lightdm restart
```

Hopefully I got them all with those commands.

---

### Post by ineuw on 2013-06-24
> **Toz said:**
> Then its defintely something wrong with your profile. You could create another account, or could just reset your Xfce. To reset your Xfce settings:

1. Logout, go to the first tty (Ctrl+Alt+F1) and log in to the text session.
2. Rename the config directories:
```
mv ~/.config/xfce4 ~/.config/xfce4.BAK
mv ~/.config/autostart ~/.config/autostart.BAK
mv ~/.config/menus ~/.config/menus.BAK
mv ~/.config/Thunar ~/.config/Thunar.BAK
mv ~/.cache ~/.cache.BAK
mv ~/.local/share ~/.local/share.BAK
```
3. Restart lightdm (should auto-login you in again):
```
sudo service lightdm restart
```

Hopefully I got them all with those commands.

I will begin with the end to save you the trouble of reading this whole post to find out what happened. I will list events in reverse . . . . 

Everything is working fine, now that I did a complete and fresh reinstall of Xubuntu 12.04.2. :-)

I couldn't execute sudo tasks because, while I created a new user and assigned Admin rights, I forgot to assign sudo to the new user before deleting the old Admin sudo account.

I had to go with the new user option because the account was so messed up that I couldn't repair it with the above instructions.

Again, many many thanks for your patience, and I hope this thread will be a good example to others as what NOT to do. :-)

---

### Post by Toz on 2013-06-24
Sorry that you had to do a full re-install. But, on the bright side, you've got a clean system now.

---

### Post by ineuw on 2013-06-24
> **Toz said:**
> Sorry that you had to do a full re-install. But, on the bright side, you've got a clean system now.

I _always look at the bright side,_ and again many thanks. I have a slow learning curve but finally learned what I needed from this last experience - which is an overall picture starting from ISO issues, installation and disk space usage, security, Grub, applications and utility softwares and finally, the relationships between Xfce, Gnome, and KDE. (This wasn't the first time I had to re-install).

Have a nice summer.

---

