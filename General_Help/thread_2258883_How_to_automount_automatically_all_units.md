---
title: "How to automount automatically all units?"
date: 2014-12-31
forum: General Help
---

### Post by fkervin on 2014-12-31
Hi all,

I have a quite annoying problem with xubuntu, it is, it doesn't automount units and i have to double click on them in thunar to make them usable.

I've enable "mount external devices when connect", "mount external devices when inserted" and "mount external support when connect" in section "External devices and supports" but it doesn't work.

I want the system to automount all units, USB ones and also internal ones (SATA), how can I enable this feature?

Many thanks in advance

---

### Post by JKyleOKC on 2014-12-31
For full automatic mounting of devices at boot time, each such device must be added to the /etc/fstab file. The best way to do this is through the command line in a terminal window, with the command "sudo nano /etc/fstab" which will result in a request for your password. It wants your login password, and will appear to do nothing as you enter it -- not even a "*" to indicate that it's received each keystroke. When you hit Enter at the end of the password, the editor window should appear. Scroll down to the end of the file and you can then enter the desired devices, one to a line.

However be extremely careful with this; a typo or bad syntax can make your system unbootable. You can then recover, by booting from your installation CD or USB drive, but it's difficult. You can prevent the problem by issuing the command "sudo mount -a" immediately after saving the file; this will remount everything using the new copy. If it fails, go back to the editor and delete your additions to restore the original content, save the file, and check with "mount -a" again before powering down.

The requirements for each device line in the "fstab" file are critical; you can use the existing entries as guides, or search the forums for "fstab" to see other posts that may help. Be very careful when working under "sudo" since you have no safety belt there; good luck!

EDIT: The settings you checked originally apply when a device is connected or powered up after logging in. They're ignored for devices that are already connected when you power up the CPU, which is why they're not doing what you expect.

Once you've gotten them mounted manually as you are doing now, you can issue the command "mount" from a terminal window to see the list of all mounted devices. The entries shown there for the additional devices can sometimes be used as guides for the entries to be added to the fstab file, but not always. If you have any doubt, ask here before making changes!

---

### Post by slickymaster on 2014-12-31
I recommend you to have a good read at [Mounting Partitions Automatically]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by Dennis N on 2014-12-31
Besides fstab, you can mount devices at login by using **udisksctl** and add the commands to the startup applications. Everything gets mounted in a subdirectory of /media/<username>.  See manpage for udisksctl.

EDIT:

This works for partitions. I tested it for a USB flash drive and it failed to mount. So it is perhaps useful for partitions you want to have mounted. Fstab is your best bet to get this to work, I would imagine.

---

### Post by fkervin on 2015-01-01
Hi all, and happy new year :D

Many thanks for all the answers, they seem very usefull, I have to read carefully all information.

I know there is a way to mount at start one disk, I mean, one of the disks you have, but it is not ok for me, I want the system to automount ANY disk connected, so if I install a new disk I don't have to add it to any list.

I'm going to research in the info you have gave me to find how to do this, of course, if someone tell me how to do this I'll thank a lot

Regards

---

### Post by fkervin on 2015-01-01
Hi all again,

I've read all the info you've provide me, but I can't get what I need (automount all units connected when boot without having to configure them one by one).

In Kubuntu I did is in this way:

see systemsettings -> removable devices -> attached drives

for all removable drives:
1) -> enable automatic mounting .........., click preferences
or for only that 1 drive:
2) -> select the usb driv -> click automount on login & automount on attach 

But with Xubuntu I don't find how to. Can anyone help?

Regard

---

### Post by schragge on 2015-01-01
Check that Thunar Volume Manager is enabled.

Launch File Manager. Go to menu **Edit** > **Preferences...**. Select the tab **Advanced**. Check **Enable Volume Management**. Click on _Configure_. Check boxes **Mount removable drives when hot-plugged**, **Mount removable media when inserted**, **Browse removable media when inserted**. **Close**. **Close** again.

Thunar should now detect and automatically mount removable media.

---

### Post by Dennis N on 2015-01-01
> **schragge said:**
> Check that Thunar Volume Manager is enabled.

Launch File Manager. Go to menu **Edit** > **Preferences...**. Select the tab **Advanced**. Check **Enable Volume Management**. Click on _Configure_. Check boxes **Mount removable drives when hot-plugged**, **Mount removable media when inserted**, **Browse removable media when inserted**. **Close**. **Close** again.

Thunar should now detect and automatically mount removable media.

Isn't this for media inserted during the user session? I think he also wants to mount anything connected when the computer is started.

---

### Post by schragge on 2015-01-01
@**Dennis N**: The OP specifically gave KDE as an example. Is KDE's behaviour any different from XFCE's in this regard?

@OP: as **Dennis N** said it won't automatically mount removable media already connected when computer was started. Is that what you want?

---

### Post by Dennis N on 2015-01-01
> **schragge said:**
> @**Dennis N**: The OP specifically gave KDE as an example. Is KDE's behaviour any different from XFCE's in this regard?

@OP: as **Dennis N** said it won't automatically mount removable media already connected when computer was started. Is that what you want?

I don't use KDE, so don't know how it behaves. I have the settings set as you describe for volume management in XFCE (they must be default, since I haven't changed them) and I know that when a flash drive is inserted before starting the computer, it is never mounted after I log in. I have to take it out and plug it in again to mount it.

---

### Post by fkervin on 2015-01-01
Many thanks Dennis N and schragge,

That is just my problem, I want connected drives/disks/units to be mounted automatically on boot when they're connected in the moment of boot, so Dennis N has just describe it.

In kubuntu it solved as I told, but now with Xubuntu I don't know how to. I've spent a lot of time and can't get a way to, I only read about including the disk in /etc/fstab, but I want ANY NEW UNIT to have this behaviour without having to add manually.

I've found some information about Pysmd, but seems to be outdated.

I honestly think it should be like this by default and don't understand why works as it does, It has nosense at all that you boot a computer and units connected are not avaiable until you click them in the file manager.

Regards and thanks again, I hope someone can help me.

---

### Post by schragge on 2015-01-01
Ok, if you're going down the udisksctl path

Basically you can enumerate removable media with something like
```

udisksctl dump|awk -F':\n' -v'RS=\n\n' '/[ \t]*HintAuto:[ \t]*true/&&/\.Filesystem:/{sub(/.*\/UDisks2\//,"",$1); print $1}'

```
You can then directly mount them with
```
udisksctl mount -p path/from/the/command/above
```
Then put the commands into a script, glue them with some shell code and make the script be invoked automatically on login.
```

#!/bin/sh

udisksctl dump |
  awk -F':\n' -v'RS=\n\n' '/[ \t]*HintAuto:[ \t]*true/&&/\.Filesystem:/{
                             print $1
                           }' |
  while read dev
  do
    udisksctl mount --object-path "${dev##*/UDisks2/}"
  done

```

 There are also [some]("https://gist.github.com/ledti/7eed3cb4356e20540c80") [ready-made]("https://gist.github.com/ledti/838039") [scripts]("https://github.com/jamielinux/bashmount") that work with udisks.

Another possibility is [gvfs-mount]("http://manpages.ubuntu.com/manpages/trusty/en/man1/gvfs-mount.1.html").

---

### Post by Dennis N on 2015-01-01
I did an test with Lubuntu 14.04. I inserted a USB flash drive (4gb stick) into a usb port and started up. After loging in, I found the flash drive had mounted automatically (no commands needed) and was accessible to applications. I was thinking I had noticed this before in Lubuntu, and was right. This is apparently the default in Lubuntu (but other disk partitions are not mounted automatically).

By the way, I checked and found the udisksctl did not work to mount a flash drive automatically on login in Xubuntu - I amended my post #4 to reflect this. Maybe a different formulation would work, but I don't need that feature - working for partitions is enough. The command I have been using for mounting a partition at login is one of these: 

```
udisks --mount /dev/disk/by-label/CommonData
udisksctl mount -b /dev/disk/by-label/CommonData

```
depending on the OS. Ubuntu 12.04 uses udisks.

---

### Post by schragge on 2015-01-01
@**Dennis N**: I amended my post, too. It's actually simpler than I thought. Thanks for useful hints. I've just tried it in Xubuntu with the shell script from my post above put in ~/bin/massmount, this ~/.xsessionrc:
```

PATH=$HOME/bin:$PATH

```
and this ~/.config/autostart/massmount.desktop:
```

[Desktop Entry]
Encoding=UTF-8
Exec=massmount
Name=Automatically mount removable media
Comment=
Terminal=true
Type=Application
StartupNotify=false
OnlyShowIn=XFCE;
NoDisplay=true

```
and it successfully mounts *unmounted* flash drives on login (the state they are in after boot up). OTOH, after the flash drive is *ejected*, it cannot be mounted by the script.

---

### Post by fkervin on 2015-01-02
Many thanks again to both of you.

I'm not sure  if I understand the procedure, schragge, I've do this having a USB drive connected but not mounted:

```
udisksctl dump|awk -F':\n' -v'RS=\n\n' '/[ \t]*HintAuto:[ \t]*true/&&/\.Filesystem:/{sub(/.*\/UDisks2\//,"",$1); print $1}'
```

Output:

```
block_devices/sdb1
```

Then I run:

```
udisksctl mount -p /block_devices/sdb1
```

And the result:

```
(udisksctl mount:2294): GLib-GIO-CRITICAL **: g_dbus_object_manager_get_object: assertion 'g_variant_is_object_path (object_path)' failed
Error looking up object with path /block_devices/sdb1
```

(usb drive is not mounted)

I don't really understand what you told in the last post, where you menction ~/bin/massmount, this ~/.xsessionrc and ~/.config/autostart/massmount.desktop. I mean, I'm not sure if you told to add those lines of code to those files or using the ones you wrote on last post.

Many thanks again for the help, I hope we can get some way of doing what I need, I'm sure many people will find it usefull.

Regards

---

### Post by schragge on 2015-01-02
No. If you want to mount it manually, you should use *exactly* the output of the first command, i.e. without the leading slash:
```
udisksctl mount -p block_devices/sdb1
```

[quote=fkervin]I don't really understand what you told in the last post, where you menction ~/bin/massmount, this ~/.xsessionrc and ~/.config/autostart/massmount.desktop. I mean, I'm not sure if you told to add those lines of code to those files or using the ones you wrote on last post.[/quote]
I'm afraid I was not very clear. So here it once again.

Make directory ~/bin:
```
mkdir ~/bin
```

Take this script:
```

#!/bin/sh

udisksctl dump |
  awk -F':\n' -v'RS=\n\n' '/[ \t]*HintAuto:[ \t]*true/&&/\.Filesystem:/{
                             print $1
                           }' |
  while read dev
  do
    udisksctl mount --object-path "${dev##*/UDisks2/}"
  done

```
Put it into the file named *massmount*. Save the file in ~/bin/ directory. Add executable permissions on the file:
```
chmod +x ~/bin/massmount
```

Create the file *.xsessionrc* in your home directory. It should contain
```
PATH=$HOME/bin:$PATH
```
Create the file *massmount.desktop*. It should contain
```

[Desktop Entry]
Encoding=UTF-8
Exec=massmount
Name=Automatically mount removable media
Comment=
Terminal=true
Type=Application
StartupNotify=false
OnlyShowIn=XFCE;
NoDisplay=true

```
Put it into directory *~/.config/autostart/*.

Check that all pieces of the puzzle are in place. This commands should output the contents listed above:
```

cat ~/bin/massmount
cat ~/.xsessionrc
cat ~/.config/autostart/massmount

```
Now your flash drives should get mounted automatically on login.

---

### Post by fkervin on 2015-01-02
Thanks schragge!!!! :D

I've just try and it works!! So i can't give you thanks enought :)

Everyways I still have a pair of questions:

-It mounts USB hard drives and USB thumb drives but doesn't mount other internal hard drives than the system one. Any way of modifying it in way that works also with internal disks? (I suppose it would be modifying this:

```
awk -F':\n' -v'RS=\n\n' '/[ \t]*HintAuto:[ \t]*true/&&/\.Filesystem:/
```

In way that also pass the internal drives to the next "while".

-When computer boots I see for a moment the terminal window mounting the disks, is there any way to execute it in "silent mode", I mean, to avoid the window appear.

Many many thanks again, really, if I can meet those two things it would be great, but with the thing I've yet I'm very happy anyway :)

Regards

---

### Post by schragge on 2015-01-02
> **fkervin said:**
> Any way of modifying it in way that works also with internal disks?
While it is certainly possible, there's absolutely no point in doing so. Internal disks should be mounted through /etc/fstab (see [uhelp]community/Fstab[/uhelp], [uhelp]community/MountingWindowsPartitions[/uhelp], [uhelp]community/InstallingANewHardDrive[/uhelp], [uhelp]community/AutomaticallyMountPartitions[/uhelp], [uhelp]community/UsingUUID[/uhelp]). Permanently attached devices may be addressed by UUIDs, labels, whatever thingies that unambiguously identify them.

> -When computer boots I see for a moment the terminal window mounting the disks, is there any way to execute it in "silent mode", I mean, to avoid the window appear.
Oh sure, there are many ways to automatically execute a script on startup that not involve opening separate terminal window. Instead of invoking it from ~/.config/autostart/massmount.desktop, you could call it from /etc/rc.local, or as part of an upstart job in /etc/init/,  or as session-setup-script from lightdm.conf, and so on. The first problem with these approaches is that the script would be then called unconditionally. Using freedesktop.org autostart specification we can restrict its execution to specific desktop environment(s) (see **OnlyShowIn=XFCE;** stanza in the massmount.desktop file). The second problem is that it would be then executed by root unless we call it like *sudo -u <user> massmount* or *su - <user> -c massmount*.

TBH, I'm even not sure that the line **Terminal=true** in *massmount.desktop* is really needed. Just remove it, and see if the script still works as intended. Maybe you'll need to redirect the output of *udisksctl mount* to /dev/null in this case.

---

### Post by fkervin on 2015-01-03
Hi again schragge,

I've change **Terminal=True** to **Terminal=False** and it works but doesn't show terminal window :). 

Besides that, I didn't like having bin folder on home, so I've move bin folder from home to another location, modifiyng then *.xsessionrc to point the correct folder "***PATH=/etc/fkervin/bin:$PATH**".

With this I only have to learn using /etc/fstab to add internal drives, with the links you've provide me I'm sure it will be easy ;)

Again, my biggest possible thanks to you and all the others who has interest in my question.

Regards

---

### Post by schragge on 2015-01-03
Well, *$HOME/bin* is more or less standard way to handle executables that only needed by you. If your machine has several user accounts, and you want the script to be executed for them all on logon, you can put it into */usr/local/bin*. You don't need *.xsessionrc* to amend PATH at all in this case as /usr/local/bin is already on system PATH by default. And *massmount.desktop* should be put in */etc/xdg/autostart* then.

Please mark this thread SOLVED, if it's solved (see [uwiki]UnansweredPostsTeam/SolvedThreads[/uwiki]).

---

### Post by fkervin on 2015-01-03
Many thanks again, schragge,

I'll try what you told me, althought it's working now it seems to be "cleaner" in this way in my case :)

I'm goint to mark the issue as solved.

Regards :)

---

### Post by ladiko on 2015-11-11
Thank you for hinting me to udisksctl ! I was looking for a way to automount on boot for more than a year and almost gave up on that issue. Now i just do it like that: ```
udisksctl dump | grep -Po "(?<=^/org/freedesktop/UDisks2/)block_devices/[hsv]d.*?(?=:$)" | xargs -r -n1 udisksctl mount -p 2>/dev/null
```

---

