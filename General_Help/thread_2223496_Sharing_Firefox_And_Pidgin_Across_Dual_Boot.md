---
title: "Sharing Firefox And Pidgin Across Dual Boot"
date: 2014-05-11
forum: General Help
---

### Post by theskitter on 2014-05-11
I had a great deal of trouble putting all of this information together, so I thought I would put it in one place.
[HR][/HR]
I am newly dual booting Windows 7 Ultimate and CAELinux 2013 (Xubuntu 12.04).
I have primary partitions for the Windows boot loader (ntfs), Windows system (ntfs), shared files (ntfs), and one subdivided into swap, / (ext4), and /boot (ext4) extended partitions.
It's important for me to have my tools function identically whether in Windows or Xubuntu, so I have shared my Firefox profile and Pidgin conversation logs.

[HR][/HR][B]
Automatically Mount Shared Partition:[/B]
Windows automatically loads ntfs partitions (except for the boot loader), so I created one to use for shared files, kept separate from the C:/ drive where the operating system is installed.
Xubuntu knows the ntfs partitions are there, creates shortcuts on the desktop, and will open them in the Thunar file exporer.
In order to have profiles, documents, desktop pictures, and music mounted automatically during bootup, I followed the instructions on the [Mounting Windows Partitions]("https://help.ubuntu.com/community/MountingWindowsPartitions") page.
In Terminal, I used "sudo blkid" to get the UUID strings for each drive.
Then I navigated to "cd mkdir /media/Data" and opened "gksudo leafpad /etc/fstab" and modified the end to look like this:
```
# mounts shared Library partition during bootup
UUID=stringofnumbers  /media/Library  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
# hides Windows System Reserve from desktop and file manager
UUID=numbersandletters  /mnt/System\040Reserve  ntfs  noauto,umask=222  0 0
```

[HR][/HR]
[B]Saving Pidgin Logs In The Same Place On Windows And Xubuntu
[/B]I put together the instructions on the [Using Pidgin]("https://developer.pidgin.im/wiki/Using%20Pidgin") page and [Solved: Pidgin Log Directory]("http://ubuntuforums.org/showthread.php?t=1231012").
In Windows, I entered a new location (E:/profiles) in Start > Settings > Control Panel > System > Advanced > Environment Variables.
I think I remember it putting in the .purple folder by itself, then I just pasted my conversation logs in that directory.
In Linux, I right clicked on the Pidgin launcher, went to properties, used the pencil edit button, and then changed the terminal command* to:
```
pidgin -c /media/Library/profiles/.purple
```
Make sure you change all of your launchers to match this.

*It took me a long time to figure out I could put terminal commands in Keyboard > Application Shortcuts, then use a key combination to match my pause-play across systems.

[HR][/HR]
**Pointing Firefox To One Shared Profile Folder**
I think I started using Mozilla's profile manager, but gave up and instead just launched it each time to see if my settings appeared.
I don't remember the exact process I followed, because it took many tries to get the syntax and sequence right.
I definitely copied my Firefox profile to a new location, backed up the original, and then removed the original to test whether it loaded with my settings or not.
At the same time, I modified C:/Documents and Settings/(USERNAME)/AppData/Roaming/Mozilla/Firefox/profiles.ini file to read:
```
[General]
StartWithLastProfile=1

[Profile0]
Name=shared
IsRelative=0
Path=E:\profiles\firefox
Default=1
```

On the Linux side, /home/(USERNAME)/.mozilla/Firefox/profiles.ini was changed to:
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/Library/profiles/firefox
Default=1
```

[HR][/HR]
This was more than an afternoon's work for me, and I hope it will save time for someone else.

---

