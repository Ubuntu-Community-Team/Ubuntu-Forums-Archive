---
title: "X cannot be installed on your computer type (i386)"
date: 2007-03-10
forum: General Help
---

### Post by balu123 on 2007-03-10
Hey,

I'm very new to Linux but I made it to install Ubuntu next to my XP prof, and using the mozilla suite for both OS and installing Beryl. It wasn't easy for me but in the last days I made it. Now after I'm thinking that I made all the tough parts, I just wanted to install the VLC player and I got this message in Add/Remove... :

VLC media player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type

This is strange!

Then I tried this:
sudo apt-get install vlc 

and got that:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it

Well. I'm not using any packet manager currently. I was also restarting and still get these messages. I cannot even install the flash plug-in in firefox. Nothing happens then.

And the file "lock" is empty

Also I'm in as Root. If I log-in in with another User is also not working.

These are my processes:

init&#9472;&#9516;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;beryl-manager&#9472;&#9516;&#9472;beryl
     &#9474;               &#9500;&#9472;emerald
     &#9474;               &#9492;&#9472;2*[{beryl-manager}]
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dd
     &#9500;&#9472;events/0
     &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;2*[{evolution-alarm}]
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;2*[{evolution-data-}]
     &#9500;&#9472;evolution-excha&#9472;&#9472;&#9472;{evolution-excha}
     &#9500;&#9472;firefox-bin&#9472;&#9472;&#9472;6*[{firefox-bin}]
     &#9500;&#9472;gaim
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9472;&#9472;ssh-agent
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-cups-icon
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-panel
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo
     &#9500;&#9472;gnome-volume-ma
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-keyb
     &#9474;                    &#9492;&#9472;5*[hald-addon-stor]
     &#9500;&#9472;hcid
     &#9500;&#9472;hpiod
     &#9500;&#9472;khelper
     &#9500;&#9472;klogd
     &#9500;&#9472;knodemgrd_0
     &#9500;&#9472;krfcommd
     &#9500;&#9472;ksoftirqd/0
     &#9500;&#9472;kswapd0
     &#9500;&#9472;kthread&#9472;&#9516;&#9472;aio/0
     &#9474;         &#9500;&#9472;kacpi_notify
     &#9474;         &#9500;&#9472;kacpid
     &#9474;         &#9500;&#9472;kblockd/0
     &#9474;         &#9500;&#9472;kgameportd
     &#9474;         &#9500;&#9472;khpsbpkt
     &#9474;         &#9500;&#9472;khubd
     &#9474;         &#9500;&#9472;kjournald
     &#9474;         &#9500;&#9472;kpsmoused
     &#9474;         &#9500;&#9472;kseriod
     &#9474;         &#9500;&#9472;2*[pdflush]
     &#9474;         &#9500;&#9472;scsi_eh_0
     &#9474;         &#9500;&#9472;scsi_eh_1
     &#9474;         &#9500;&#9472;scsi_eh_2
     &#9474;         &#9500;&#9472;shpchpd
     &#9474;         &#9492;&#9472;3*[usb-storage]
     &#9500;&#9472;logd
     &#9500;&#9472;mapping-daemon
     &#9500;&#9472;migration/0
     &#9500;&#9472;mixer_applet2
     &#9500;&#9472;nautilus
     &#9500;&#9472;perl
     &#9500;&#9472;python
     &#9500;&#9472;saa7134[0]
     &#9500;&#9472;sdpd
     &#9500;&#9472;sh&#9472;&#9472;&#9472;esd
     &#9500;&#9472;syslogd
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd
     &#9500;&#9472;update-notifier
     &#9492;&#9472;watchdog/0


I'm googleing for hours now without making any step forward. So it would be great if you have an idea.

Thanks
Balu

---

### Post by balu123 on 2007-03-11
Does nobody have an idea?

---

### Post by balu123 on 2007-03-11
I reinstalled ubuntu

---

### Post by sboots on 2008-01-05
See - 
[http://ubuntuforums.org/showthread.php?t=592031](http://ubuntuforums.org/showthread.php?t=592031)
particularly [http://ubuntuforums.org/showpost.php?p=3643304&postcount=7](http://ubuntuforums.org/showpost.php?p=3643304&postcount=7)

Seems to occur (still in 7.10) if your computer isn't connected to the net when installing ubuntu (there is a brief message about not being able to contact the ubuntu security servers, which results in commenting out the sources in the /etc/apt/sources.list file.  Going to "Preferences" in "Add/Remove Programs" and checking all the internet sources seems to do the trick.  (Or you can "sudo nano /etc/apt/sources.list" and uncomment the lines manually.)

Just for anyone else who had the same problem.  :)

---

