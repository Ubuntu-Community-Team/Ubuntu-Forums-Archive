---
title: "update install hang with errors"
date: 2017-08-21
forum: General Help
---

### Post by Gnusboy on 2017-08-21
Hello

I had a large update today that had several system hangs. They resolved quickly, but I've never had that happen before.
Another part of that update also showed there were segments that would only install partially. It offered to continue without installing that part of the upgrade, and a button to look at the part that couldn't be upgraded.
When I clicked on that, it just continued with the remaining install. 
I wasn't able to save these notices. I looked through syslog and found several entries with warnings and and over 150 continuous lines of "ignored relative path"
I estimate that all the entries in the syslog that appeared relevant totaled about 1000 lines. Didn't count them all.
I don't check my syslog often, and I certainly don't understand it.

What does this stuff mean?

I also have been dealing with many system hangs for several weeks. I usually do a "force quit" and go on top my work, but before this, the hangs didn't happen with regularity as it does now.

There are also other things goofy with my system lately, but I'll save that for a different post.

Any help is appreciated. Thanks

---

### Post by Futant on 2017-08-21
Hi, what hardware are you using and which version of Ubuntu? What exactly do you mean by 'system hangs'? How long have you been experiencing them and can you think of anything you did before they started that might be causing problems? Do they happen when you're using particular programs or seemingly at random? Could your hard drive be failing? A number of things could be causing lagging, freezing etc (low memory, high CPU load, driver issues, disk failure...), without more details it's hard to help.

Your update issue could be unrelated, try updating in a terminal:```
 sudo apt update && sudo apt upgrade
``` If you see any error messages or anything that seems odd, post them here using code tags. 

[This]("https://askubuntu.com/questions/749224/92-of-syslog-is-filled-with-message-regarding-ureadahead-ignoring-relative-pa") might shed some light on your syslog 'ignored relative path' messages. Couldn't tell you if it's related to you issue though...

Just out of interest what other issues have you been experiencing? As you say you might want to start new threads for them, but it's possible they could point to something that might help.

---

### Post by Gnusboy on 2017-08-21
Hey, thanks

If you need more than this let me know.

I'm on a an AMD Phenom desktop with 4 gigs of ram and a 650 HDD on board and I'm running Ubuntu 16.04. I am also running Ubuntu 14.04 in parallel. When I installed the HD I initially partitioned it into
*I initially  *partitioned the 650 GB into relatively equal  2 partitions. 

BUT - when I did that, it actually split into 3 parts, with a 156 GB partition which unusable. I am locked out of it. I didn't worry too much cause I don't need the space.
Then another weird thing happened (don't know what) and the drive split into 4 partitions or 93 GB 113 GB  113 GB and the 156GB part. When I ran 14.04 I did not have trouble at first, but later it started getting fluky. Nothing regular, and not repeating
But It would not run deja-dup for a backup until I attached a 1 TB USB.

That's the background. Then later, I split one partition to make room to install Ubuntu 16.04
It worked very well. I'm able to boot into either one. It's only recently, that the system started freezing. Only for a few seconds or so.
I don't know if any of this applies to the problem I had today with the update.
Here are a few excerpts from my syslog right after the update finished.

Forgive me, but I am not experienced with code tags. I'll try to add them to some of the issues I'm posting here
I'm pretty sure I did the code tag thing wrong. I hope you can figure it out.
These are just a couple of excerpt from the syslog. I don't know anything what the syslog means. It might be all Trump speak to me. :)

Thanks for whatever help you can offer.


-----------------------------------------------------------------------------------------------------------------------------------

```

&#8203;snapd[20113]: 2017/08/21 12:40:21.161480 snapmgr.go:422: No snaps to auto-refresh found

Aug 21 12:40:21 ranha-system systemd[1]: Reloading.
Aug 21 12:40:22 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:40:22 ranha-system systemd[1]: Started ACPI event daemon.
Aug 21 12:40:22 ranha-system systemd[1]: Reloading.
Aug 21 12:40:22 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:40:22 ranha-system systemd[1]: Started ACPI event daemon.
< crash report>
Aug 21 12:40:22 ranha-system systemd[1]: Started crash report submission daemon.
Aug 21 12:40:22 ranha-system whoopsie[20243]: [12:40:22] Using lock path: /var/lock/whoopsie/lock
Aug  21 12:40:22 ranha-system whoopsie[20243]: [12:40:22] The default IPv4  route is: /org/freedesktop/NetworkManager/ActiveConnection/1

<Data Plan?>
Aug 21  12:40:22 ranha-system whoopsie[20243]: [12:40:22] Not a paid data plan:  /org/freedesktop/NetworkManager/ActiveConnection/1
Aug 21 12:40:22  ranha-system whoopsie[20243]: [12:40:22] Found usable connection:  /org/freedesktop/NetworkManager/ActiveConnection/1

<code>
<password warning>
Aug 21 12:40:22  ranha-system gnome-session[1581]: debconf: DbDriver "passwords" warning:  could not open /var/cache/debconf/passwords.dat: Permission denied
Aug  21 12:40:23 ranha-system gnome-session[1581]: debconf: DbDriver  "passwords" warning: could not open /var/cache/debconf/passwords.dat:  Permission denied
Aug 21 12:40:28 ranha-system dbus[809]: [system] Reloaded configuration
Aug  21 12:40:33 ranha-system gnome-session[1581]: debconf: DbDriver  "passwords" warning: could not open /var/cache/debconf/passwords.dat:  Permission denied </code>

<code>
Aug 21 12:40:33 ranha-system gnome-session[1581]:  Use of uninitialized value $template in exists at  /usr/share/perl5/Debconf/Template.pm line 86, <> line 3.
Aug 21  12:40:33 ranha-system gnome-session[1581]: Use of uninitialized value  $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 40,  <> line 3.
Aug 21 12:40:33 ranha-system gnome-session[1581]:  Use of uninitialized value $item in exists at  /usr/share/perl5/Debconf/DbDriver/Cache.pm line 40, <> line 3.</code>
Aug 21 12:41:20 ranha-system systemd[1]: Reloading.
Aug 21 12:41:21 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:41:21 ranha-system systemd[1]: Started ACPI event daemon.
Aug 21 12:41:21 ranha-system systemd[1]: Reloading.
Aug 21 12:41:21 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:41:21 ranha-system systemd[1]: Started ACPI event daemon.


<code>
Aug 21 12:41:21 ranha-system systemd[1]: Started Unattended Upgrades Shutdown.
Aug  21 12:41:45 ranha-system AptDaemon.Worker: INFO: Finished transaction  /org/debian/apt/transaction/d8a96f517ba2449582a7c49648eb5086
Aug 21  12:41:45 ranha-system org.debian.apt[809]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning:  Source ID 67 was not found when attempting to remove it
Aug 21 12:41:45 ranha-system org.debian.apt[809]:   GLib.source_remove(id)
Aug  21 12:41:45 ranha-system org.debian.apt[809]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning:  Source ID 68 was not found when attempting to remove it
Aug 21 12:41:45 ranha-system org.debian.apt[809]:   GLib.source_remove(id)
Aug  21 12:41:45 ranha-system org.debian.apt[809]: 12:41:45 AptDaemon.Worker  [INFO]: Finished transaction  /org/debian/apt/transaction/d8a96f517ba2449582a7c49648eb5086
Aug 21 12:42:12 ranha-system gnome-session[1581]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Aug 21 12:43:02 ranha-system gnome-session[1581]: /var/lib/apt/lists/lock:</code>

<code>
<warnings>

Aug  21 12:44:12 ranha-system gnome-session[1581]: (gnome-software:1744):  As-WARNING **: failed to rescan: Failed to parse  /usr/share/ubuntu/applications/org.gnome.Software.desktop.dpkg-new file:  cannot process file of type text/plain
Aug 21 12:44:12 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/ubuntu/applications/org.gnome.Software.desktop.dpkg-tmp file:  cannot process file of type text/plain
Aug 21 12:44:12 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/ubuntu/applications/org.gnome.Software.desktop file: cannot  process file of type application/x-desktop
Aug 21 12:44:13  ranha-system gnome-session[1581]: (gnome-software:1744): As-WARNING **:  failed to rescan: Failed to parse  /usr/share/applications/gnome-software-local-file.desktop.dpkg-new file:  cannot process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/gnome-software-local-file.desktop.dpkg-tmp file:  cannot process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/org.gnome.Software.desktop.dpkg-new file: cannot  process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/org.gnome.Software.desktop.dpkg-tmp file: cannot  process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/gnome-software-local-file.desktop file: cannot  process file of type application/x-desktop
Aug 21 12:44:13  ranha-system gnome-session[1581]: (gnome-software:1744): As-WARNING **:  failed to rescan: Failed to parse  /usr/share/applications/org.gnome.Software.desktop file: cannot process  file of type application/x-desktop
Aug 21 12:44:29 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse /usr/share/applications/bamf-2.index.new file:  cannot process file of type text/plain</code>

<code>
<GObject-CRITICAL>
Aug 21 12:44:29 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse /usr/share/applications/bamf-2.index file:  cannot process file of type text/plain
Aug 21 12:45:20 ranha-system  /usr/lib/snapd/snapd[20113]: snapmgr.go:504: DEBUG: Next refresh  scheduled for 2017-08-21 20:33:00.026515403 -0700 PDT.
Aug 21  12:46:01 ranha-system gnome-session[1581]: gnome-session-binary[1581]:  GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)'  failed
Aug 21 12:46:01 ranha-system gnome-session[1581]:  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session[1581]: gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session[1581]: gnome-session-binary[1581]:  GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)'  failed
Aug 21 12:46:01 ranha-system gnome-session-binary[1581]:  GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)'  failed
Aug 21 12:46:01 ranha-system gnome-session[1581]:  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session[1581]: gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system systemd[1]: Stopping Session c2 of user jess.
<end session> </code>



<excerpt>
ug  21 13:27:33 ranha-system gnome-session[1598]: Nautilus-Share-Message:  Called "net usershare info" but it failed: Failed to execute child  process "net" (No such file or directory)
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2393): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2402): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2383): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted

<usershare info" but it failed>
Aug 21 13:28:37  ranha-system gnome-session[1598]: Nautilus-Share-Message: Called "net  usershare info" but it failed: Failed to execute child process "net" (No  such file or directory)
Aug 21 13:28:54 ranha-system  org.gnome.zeitgeist.SimpleIndexer[1463]: ** (zeitgeist-fts:2055):  WARNING **: Unable to get info on  application://nautilus-autostart.desktop
Aug 21 13:30:12 ranha-system  gnome-session[1598]: Nautilus-Share-Message: Called "net usershare  info" but it failed: Failed to execute child process "net" (No such file  or directory)
Aug 21 13:38:58 ranha-system  com.canonical.Unity.Scope.Applications[1463]: Error loading package  indexes: Couldn't stat '/var/cache/software-center/xapian'
Aug 21  13:38:58 ranha-system com.canonical.Unity.Scope.Applications[1463]:  (unity-scope-loader:2512): unity-applications-daemon-CRITICAL **:  daemon.vala:144: Failed to load Software Center index. 'Apps Available  for Download' will not be listed
Aug 21 13:39:11 ranha-system dhclient[1046]: DHCPREQUEST of 192.168.0.2 on enp3s0 to 192.168.0.1 port 67 (xid=0x3e4990b8)
Aug 21&#8203;


<end excerpt>
```







-- 
[COLOR=#888888]
[FONT=arial]&#8203;"If you don't want to feel a hoof - don't stand behind the mule" - Vassar Clements&#8203;[/FONT]
[/COLOR]

---

### Post by Gnusboy on 2017-08-22
> **Futant said:**
> Hi, what hardware are you using and which version of Ubuntu? What exactly do you mean by 'system hangs'? How long have you been experiencing them and can you think of anything you did before they started that might be causing problems? Do they happen when you're using particular programs or seemingly at random? Could your hard drive be failing? A number of things could be causing lagging, freezing etc (low memory, high CPU load, driver issues, disk failure...), without more details it's hard to help.

Your update issue could be unrelated, try updating in a terminal:```
 sudo apt update && sudo apt upgrade
``` If you see any error messages or anything that seems odd, post them here using code tags. 

[This]("https://askubuntu.com/questions/749224/92-of-syslog-is-filled-with-message-regarding-ureadahead-ignoring-relative-pa") might shed some light on your syslog 'ignored relative path' messages. Couldn't tell you if it's related to you issue though...

Just out of interest what other issues have you been experiencing? As you say you might want to start new threads for them, but it's possible they could point to something that might help.

-----------------------------------------------------------------------------------------------------------
Here's the output from terminal


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```
jess@ranha-system:~$  sudo apt update && sudo apt upgrade
[sudo] password for jess: 
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Err:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                    
Get:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11.5 kB]           
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner amd64 Packages [3,124 B]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [48.9 kB]
Get:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner i386 Packages [3,124 B]
Get:10 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner Translation-en [1,616 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [171 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [64.2 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [59.9 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [52.0 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [221 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [214 kB]
Reading package lists... Done                                      
E: The repository 'cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
jess@ranha-system:~$ ^C
jess@ranha-system:~$
```

---

### Post by deadflowr on 2017-08-22
> Forgive me, but I am not experienced with code tags. I'll try to add them to some of the issues I'm posting here
I'm pretty sure I did the code tag thing wrong. I hope you can figure it out.

A primer on code tags: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by litlesam on 2017-08-22
Select Software & Updates and uncheck CDrom with Ubuntu and try to save then update.

---

### Post by Gnusboy on 2017-08-22
Deadflowr
Thank you. I looked for something like this, but couldn't find it last night
This looks like what I need.
Cheers

---

### Post by Gnusboy on 2017-08-22
Just to check if I did this right. Frankly, I don't have confidence.

 	Code Tags??
```
snapd[20113]: 2017/08/21 12:40:21.161480 snapmgr.go:422: No snaps to auto-refresh found 


Aug 21 12:40:21 ranha-system systemd[1]: Reloading.
Aug 21 12:40:22 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:40:22 ranha-system systemd[1]: Started ACPI event daemon.
Aug 21 12:40:22 ranha-system systemd[1]: Reloading.
Aug 21 12:40:22 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:40:22 ranha-system systemd[1]: Started ACPI event daemon.

```
< crash report>
```
Aug 21 12:40:22 ranha-system systemd[1]: Started crash report submission daemon.
Aug 21 12:40:22 ranha-system whoopsie[20243]: [12:40:22] Using lock path: /var/lock/whoopsie/lock
Aug  21 12:40:22 ranha-system whoopsie[20243]: [12:40:22] The default IPv4  route is: /org/freedesktop/NetworkManager/ActiveConnection/1


<Data Plan?>
Aug 21  12:40:22 ranha-system whoopsie[20243]: [12:40:22] Not a paid data plan:  /org/freedesktop/NetworkManager/ActiveConnection/1
Aug 21 12:40:22  ranha-system whoopsie[20243]: [12:40:22] Found usable connection:  /org/freedesktop/NetworkManager/ActiveConnection/1
```


```

<password warning>
Aug 21 12:40:22  ranha-system gnome-session[1581]: debconf: DbDriver "passwords" warning:  could not open /var/cache/debconf/passwords.dat: Permission denied
Aug  21 12:40:23 ranha-system gnome-session[1581]: debconf: DbDriver  "passwords" warning: could not open /var/cache/debconf/passwords.dat:  Permission denied
Aug 21 12:40:28 ranha-system dbus[809]: [system] Reloaded configuration
Aug  21 12:40:33 ranha-system gnome-session[1581]: debconf: DbDriver  "passwords" warning: could not open /var/cache/debconf/passwords.dat:  Permission denied 
```

```

Aug 21 12:40:33 ranha-system gnome-session[1581]:  Use of uninitialized value $template in exists at  /usr/share/perl5/Debconf/Template.pm line 86, <> line 3.
Aug 21  12:40:33 ranha-system gnome-session[1581]: Use of uninitialized value  $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 40,  <> line 3.
Aug 21 12:40:33 ranha-system gnome-session[1581]:  Use of uninitialized value $item in exists at  /usr/share/perl5/Debconf/DbDriver/Cache.pm line 40, <> line 3.
Aug 21 12:41:20 ranha-system systemd[1]: Reloading.
Aug 21 12:41:21 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:41:21 ranha-system systemd[1]: Started ACPI event daemon.
Aug 21 12:41:21 ranha-system systemd[1]: Reloading.
Aug 21 12:41:21 ranha-system systemd[1]: Started CUPS Scheduler.
Aug 21 12:41:21 ranha-system systemd[1]: Started ACPI event daemon.
```


```

Aug 21 12:41:21 ranha-system systemd[1]: Started Unattended Upgrades Shutdown.
Aug  21 12:41:45 ranha-system AptDaemon.Worker: INFO: Finished transaction  /org/debian/apt/transaction/d8a96f517ba2449582a7c49648eb5086
Aug 21  12:41:45 ranha-system org.debian.apt[809]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning:  Source ID 67 was not found when attempting to remove it
Aug 21 12:41:45 ranha-system org.debian.apt[809]:   GLib.source_remove(id)
Aug  21 12:41:45 ranha-system org.debian.apt[809]:  /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning:  Source ID 68 was not found when attempting to remove it
Aug 21 12:41:45 ranha-system org.debian.apt[809]:   GLib.source_remove(id)
Aug  21 12:41:45 ranha-system org.debian.apt[809]: 12:41:45 AptDaemon.Worker  [INFO]: Finished transaction  /org/debian/apt/transaction/d8a96f517ba2449582a7c49648eb5086
Aug 21 12:42:12 ranha-system gnome-session[1581]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Aug 21 12:43:02 ranha-system gnome-session[1581]: /var/lib/apt/lists/lock:
```

```

<warnings>

Aug  21 12:44:12 ranha-system gnome-session[1581]: (gnome-software:1744):  As-WARNING **: failed to rescan: Failed to parse  /usr/share/ubuntu/applications/org.gnome.Software.desktop.dpkg-new file:  cannot process file of type text/plain
Aug 21 12:44:12 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/ubuntu/applications/org.gnome.Software.desktop.dpkg-tmp file:  cannot process file of type text/plain
Aug 21 12:44:12 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/ubuntu/applications/org.gnome.Software.desktop file: cannot  process file of type application/x-desktop
Aug 21 12:44:13  ranha-system gnome-session[1581]: (gnome-software:1744): As-WARNING **:  failed to rescan: Failed to parse  /usr/share/applications/gnome-software-local-file.desktop.dpkg-new file:  cannot process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/gnome-software-local-file.desktop.dpkg-tmp file:  cannot process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/org.gnome.Software.desktop.dpkg-new file: cannot  process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/org.gnome.Software.desktop.dpkg-tmp file: cannot  process file of type text/plain
Aug 21 12:44:13 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse  /usr/share/applications/gnome-software-local-file.desktop file: cannot  process file of type application/x-desktop
Aug 21 12:44:13  ranha-system gnome-session[1581]: (gnome-software:1744): As-WARNING **:  failed to rescan: Failed to parse  /usr/share/applications/org.gnome.Software.desktop file: cannot process  file of type application/x-desktop
Aug 21 12:44:29 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse /usr/share/applications/bamf-2.index.new file:  cannot process file of type text/plain
```

```

<GObject-CRITICAL>
Aug 21 12:44:29 ranha-system  gnome-session[1581]: (gnome-software:1744): As-WARNING **: failed to  rescan: Failed to parse /usr/share/applications/bamf-2.index file:  cannot process file of type text/plain
Aug 21 12:45:20 ranha-system  /usr/lib/snapd/snapd[20113]: snapmgr.go:504: DEBUG: Next refresh  scheduled for 2017-08-21 20:33:00.026515403 -0700 PDT.
Aug 21  12:46:01 ranha-system gnome-session[1581]: gnome-session-binary[1581]:  GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)'  failed
Aug 21 12:46:01 ranha-system gnome-session[1581]:  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session[1581]: gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session[1581]: gnome-session-binary[1581]:  GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)'  failed
Aug 21 12:46:01 ranha-system gnome-session-binary[1581]:  GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)'  failed
Aug 21 12:46:01 ranha-system gnome-session[1581]:  gnome-session-binary[1581]: GLib-GObject-CRITICAL: g_object_unref:  assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system  gnome-session[1581]: gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21  12:46:01 ranha-system gnome-session-binary[1581]: GLib-GObject-CRITICAL:  g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 21 12:46:01 ranha-system systemd[1]: Stopping Session c2 of user jess.
<end session> 
```



```

ug  21 13:27:33 ranha-system gnome-session[1598]: Nautilus-Share-Message:  Called "net usershare info" but it failed: Failed to execute child  process "net" (No such file or directory)
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2393): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2402): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2383): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted

<usershare info" but it failed>
Aug 21 13:28:37  ranha-system gnome-session[1598]: Nautilus-Share-Message: Called "net  usershare info" but it failed: Failed to execute child process "net" (No  such file or directory)
Aug 21 13:28:54 ranha-system  org.gnome.zeitgeist.SimpleIndexer[1463]: ** (zeitgeist-fts:2055):  WARNING **: Unable to get info on  application://nautilus-autostart.desktop
Aug 21 13:30:12 ranha-system  gnome-session[1598]: Nautilus-Share-Message: Called "net usershare  info" but it failed: Failed to execute child process "net" (No such file  or directory)
Aug 21 13:38:58 ranha-system  com.canonical.Unity.Scope.Applications[1463]: Error loading package  indexes: Couldn't stat '/var/cache/software-center/xapian'
Aug 21  13:38:58 ranha-system com.canonical.Unity.Scope.Applications[1463]:  (unity-scope-loader:2512): unity-applications-daemon-CRITICAL **:  daemon.vala:144: Failed to load Software Center index. 'Apps Available  for Download' will not be listed
Aug 21 13:39:11 ranha-system dhclient[1046]: DHCPREQUEST of 192.168.0.2 on enp3s0 to 192.168.0.1 port 67 (xid=0x3e4990b8)
Aug 21&#8203;

```

---

### Post by deadflowr on 2017-08-22
> Just to check if I did this right. Frankly, I don't have confidence.
I fixed it
Basically you used <code>, which is the wrong form. 
You need to use [code]
The forums bbcode uses these: [ ],
and not these: <>.

Forums BB Code list with examples:
[https://ubuntuforums.org/misc.php?do=bbcode#code]("https://ubuntuforums.org/misc.php?do=bbcode#code")

---

### Post by Gnusboy on 2017-08-30
```
 ug  21 13:27:33 ranha-system gnome-session[1598]: Nautilus-Share-Message:  Called "net usershare info" but it failed: Failed to execute child  process "net" (No such file or directory)
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2393): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2402): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2383): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted

<usershare info" but it failed>
Aug 21 13:28:37  ranha-system gnome-session[1598]: Nautilus-Share-Message: Called "net  usershare info" but it failed: Failed to execute child process "net" (No  such file or directory)
Aug 21 13:28:54 ranha-system  org.gnome.zeitgeist.SimpleIndexer[1463]: ** (zeitgeist-fts:2055):  WARNING **: Unable to get info on  application://nautilus-autostart.desktop
Aug 21 13:30:12 ranha-system  gnome-session[1598]: Nautilus-Share-Message: Called "net usershare  info" but it failed: Failed to execute child process "net" (No such file  or directory)
Aug 21 13:38:58 ranha-system  com.canonical.Unity.Scope.Applications[1463]: Error loading package  indexes: Couldn't stat '/var/cache/software-center/xapian'
Aug 21  13:38:58 ranha-system com.canonical.Unity.Scope.Applications[1463]:  (unity-scope-loader:2512): unity-applications-daemon-CRITICAL **:  daemon.vala:144: Failed to load Software Center index. 'Apps Available  for Download' will not be listed
Aug 21 13:39:11 ranha-system dhclient[1046]: DHCPREQUEST of 192.168.0.2 on enp3s0 to 192.168.0.1 port 67 (xid=0x3e4990b8)
Aug 21&#8203;
```

---

### Post by Gnusboy on 2017-08-30
```

ug  21 13:27:33 ranha-system gnome-session[1598]: Nautilus-Share-Message:  Called "net usershare info" but it failed: Failed to execute child  process "net" (No such file or directory)
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:36  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2393): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:39  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2402): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (gvfsd:1516): WARNING **:  dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to  retrieve share list from server: Connection refused
Aug 21 13:27:43  ranha-system org.gtk.vfs.Daemon[1463]: ** (process:2383): WARNING **:  Couldn't create directory monitor on smb://x-gnome-default-workgroup/.  Error: The specified location is not mounted

<usershare info" but it failed>
Aug 21 13:28:37  ranha-system gnome-session[1598]: Nautilus-Share-Message: Called "net  usershare info" but it failed: Failed to execute child process "net" (No  such file or directory)
Aug 21 13:28:54 ranha-system  org.gnome.zeitgeist.SimpleIndexer[1463]: ** (zeitgeist-fts:2055):  WARNING **: Unable to get info on  application://nautilus-autostart.desktop
Aug 21 13:30:12 ranha-system  gnome-session[1598]: Nautilus-Share-Message: Called "net usershare  info" but it failed: Failed to execute child process "net" (No such file  or directory)
Aug 21 13:38:58 ranha-system  com.canonical.Unity.Scope.Applications[1463]: Error loading package  indexes: Couldn't stat '/var/cache/software-center/xapian'
Aug 21  13:38:58 ranha-system com.canonical.Unity.Scope.Applications[1463]:  (unity-scope-loader:2512): unity-applications-daemon-CRITICAL **:  daemon.vala:144: Failed to load Software Center index. 'Apps Available  for Download' will not be listed
Aug 21 13:39:11 ranha-system dhclient[1046]: DHCPREQUEST of 192.168.0.2 on enp3s0 to 192.168.0.1 port 67 (xid=0x3e4990b8)
Aug 21&#8203;
```

---

### Post by #&amp;thj^% on 2017-08-30
Is this through the software manager (Center)
Dose it do the same with:
```
sudo apt update
sudo apt upgrade
```
EDIT:...I don't know why but just your last two replys were showing while  I replied here.
But now I see that you have already run those commands.
Kindly just disregard my post. (Good Luck)

---

