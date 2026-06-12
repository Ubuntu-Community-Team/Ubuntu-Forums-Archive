---
title: "Google Chrome install location."
date: 2016-05-07
forum: General Help
---

### Post by Lappert on 2016-05-07
I am running Google Chrome under Kubuntu. No real problems in its operation.

I've been cleaning up my drives and I discovered what appears to be Chrome installed at /opt/google/chrome as follows:[INDENT]file:///opt/google/chrome/cron[/INDENT]
[INDENT]file:///opt/google/chrome/default_apps[/INDENT]
[INDENT]file:///opt/google/chrome/locales[/INDENT]
[INDENT]file:///opt/google/chrome/PepperFlash[/INDENT]
[INDENT]file:///opt/google/chrome/natives_blob.bin[/INDENT]
[INDENT]file:///opt/google/chrome/snapshot_blob.bin[/INDENT]
[INDENT]file:///opt/google/chrome/icudtl.dat[/INDENT]
[INDENT]file:///opt/google/chrome/nacl_irt_x86_64.nexe[/INDENT]
[INDENT]file:///opt/google/chrome/chrome_100_percent.pak[/INDENT]
[INDENT]file:///opt/google/chrome/chrome_200_percent.pak[/INDENT]
[INDENT]file:///opt/google/chrome/chrome_material_100_percent.pak[/INDENT]
[INDENT]file:///opt/google/chrome/chrome_material_200_percent.pak[/INDENT]
[INDENT]file:///opt/google/chrome/resources.pak[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_128.png[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_16.png[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_22.png[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_24.png[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_256.png[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_32.png[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_48.png[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_64.png[/INDENT]
[INDENT]file:///opt/google/chrome/libwidevinecdmadapter.so[/INDENT]
[INDENT]file:///opt/google/chrome/libwidevinecdm.so[/INDENT]
[INDENT]file:///opt/google/chrome/product_logo_32.xpm[/INDENT]
[INDENT]file:///opt/google/chrome/chrome[/INDENT]
[INDENT]file:///opt/google/chrome/chrome-sandbox[/INDENT]
[INDENT]file:///opt/google/chrome/default-app-block[/INDENT]
[INDENT]file:///opt/google/chrome/google-chrome[/INDENT]
[INDENT]file:///opt/google/chrome/nacl_helper[/INDENT]
[INDENT]file:///opt/google/chrome/nacl_helper_bootstrap[/INDENT]
[INDENT]file:///opt/google/chrome/xdg-mime[/INDENT]
[INDENT]file:///opt/google/chrome/xdg-settings[/INDENT]

Nothing else is in the /opt directory.

But I then find in /home/user/.config/google-chrome what also appears to be an install, as follows (partial list):
[INDENT]file:///home/user/.config/akonadi
file:///home/user/.config/audacious
file:///home/user/.config/autostart
file:///home/user/.config/autostart-scripts
file:///home/user/.config/chromium
file:///home/user/.config/dconf
file:///home/user/.config/google-chrome
file:///home/user/.config/google-chrome.dist
file:///home/user/.config/gtk-2.0
file:///home/user/.config/gtk-3.0
file:///home/user/.config/kdeconnect
file:///home/user/.config/libaccounts-glib
file:///home/user/.config/libreoffice
file:///home/user/.config/menus
file:///home/user/.config/oxygen-gtk
file:///home/user/.config/plasma-workspace
file:///home/user/.config/pulse
file:///home/user/.config/session
file:///home/user/.config/software-center
file:///home/user/.config/VirtualBox
file:///home/user/.config/vlc

and many more files.[/INDENT]

So my question is if the /opt directory is the real install directory, is it correct, and can I delete it (or move it elsewhere)?

Thank you for any guidance.

---

### Post by Bashing-om on 2016-05-07
Lappert; Nope;

Do not mess with /opt/google/chrome . That is the proper install location for 3rd party softwares.
Mine:
```

sysop@1404mini:~$ ls -al /opt/google/chrome
total 143016
drwxr-xr-x 6 root root      4096 Apr 28 13:59 .
drwxr-xr-x 3 root root      4096 May 19  2013 ..
-rwxr-xr-x 1 root root 100662016 Apr 27 16:13 chrome
-rw-r--r-- 1 root root    665272 Apr 27 16:13 chrome_100_percent.pak
-rw-r--r-- 1 root root   1003905 Apr 27 16:13 chrome_200_percent.pak
-rw-r--r-- 1 root root      1109 Apr 27 16:13 chrome_material_100_percent.pak
-rw-r--r-- 1 root root      1693 Apr 27 16:13 chrome_material_200_percent.pak
-rwsr-xr-x 1 root root     14528 Apr 27 16:13 chrome-sandbox
drwxr-xr-x 2 root root      4096 Apr 28 13:59 cron
-rw-r--r-- 1 root root       482 Apr 27 16:13 default-app-block
drwxr-xr-x 2 root root      4096 Apr 28 13:59 default_apps
-rwxr-xr-x 1 root root      3050 Apr 27 16:13 google-chrome
-rw-r--r-- 1 root root  10209568 Apr 27 16:13 icudtl.dat
-rw-r--r-- 1 root root     80176 Apr 27 16:13 libwidevinecdmadapter.so
-rw-r--r-- 1 root root   7961028 Apr 27 16:13 libwidevinecdm.so
drwxr-xr-x 2 root root      4096 Apr 28 13:59 locales
-rwxr-xr-x 1 root root   2423176 Apr 27 16:13 nacl_helper
-rwxr-xr-x 1 root root      8960 Apr 27 16:13 nacl_helper_bootstrap
-rw-r--r-- 1 root root   3343920 Apr 27 16:13 nacl_irt_x86_64.nexe
-rw-r--r-- 1 root root    407837 Apr 27 16:13 natives_blob.bin
drwxr-xr-x 2 root root      4096 Apr 28 13:59 PepperFlash
-rw-r--r-- 1 root root      8791 Apr 27 16:13 product_logo_128.png
-rw-r--r-- 1 root root       714 Apr 27 16:13 product_logo_16.png
-rw-r--r-- 1 root root      1080 Apr 27 16:13 product_logo_22.png
-rw-r--r-- 1 root root      1111 Apr 27 16:13 product_logo_24.png
-rw-r--r-- 1 root root     22754 Apr 27 16:13 product_logo_256.png
-rw-r--r-- 1 root root      1575 Apr 27 16:13 product_logo_32.png
-rw-r--r-- 1 root root      7279 Apr 27 16:13 product_logo_32.xpm
-rw-r--r-- 1 root root      2465 Apr 27 16:13 product_logo_48.png
-rw-r--r-- 1 root root      3653 Apr 27 16:13 product_logo_64.png
-rw-r--r-- 1 root root  18820456 Apr 27 16:13 resources.pak
-rw-r--r-- 1 root root    628052 Apr 27 16:13 snapshot_blob.bin
-rwxr-xr-x 1 root root     37394 Apr 27 16:13 xdg-mime
-rwxr-xr-x 1 root root     33273 Apr 27 16:13 xdg-settings
sysop@1404mini:~$ 

```
User configs, profiles and such do go in the home directory  for all installed applications There the user has control .

Housecleaning, we can address in a separate thread. Linux is light and does not require much . However, attention to detail is a good thing.
[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Lappert on 2016-05-07
Thanks for your reply. After I posted, I found another directory with the same subdirectory: /mnt/sdc/google/chrome with all the same sub-directories and files. Are you sure this isn't just an uncompressed directory used to install chrome in its final destination?

---

### Post by Bashing-om on 2016-05-07
Lappert; Welp

" /mnt/sdc/google/chrome" looks to me to be a different install on a different hard drive.
/mnt is the attachment point of another external device;
/sdc would be the 3rd hard drive
/google/ a directory on the hard drive
/chrome a subdirectory of /google
```

sudo parted -l

```
to know what is for hard drives.

Now depending on the mount options in /etc/fstab, OR how you are mounting sdc - if 'sdc' is not present i can see the system screaming and hollering .

[INDENT][INDENT]so far, so good
[/INDENT][/INDENT]

---

### Post by Lappert on 2016-05-08
Bashing-om,

Thanks for your reply. But yes, I am aware of which hard drives I have, and that's not my question. 

So far I've discovered:
[COLOR=#000000]/opt/google/chrome[/COLOR]
[COLOR=#000000]/home/user/.config/google-chrome
[/COLOR][COLOR=#000000]/mnt/sdc/google/chrome

The first and third directories appear to be identical.

The question I have is whether or not the first and third directories are needed to run chrome. Or, are they just an uncompressed set of files from which I would use to install chrome? If that's the case, I should be able to safely delete those directories.[/COLOR]

---

### Post by Bashing-om on 2016-05-08
Lappert; Well ..

I can not know what you have done/installed. IF and I stress IF the device sdc is not a booting hard drive, and you have no intention of booting that drive AND having access to google-chrome on this device; Sure remove /mnt/sdc/google/chrome . How one would manage this feat depends on whether sdc is a bootable device.

The install process is that the .deb packages are fetched, and there are a number of control files to direct where the individual files are copied to. Have a read in the files that :
```

ls -al /var/lib/dpkg/info/google*

```
return. It only happens once.

I do make the supposition that you have installed google-chrome twice, and that 'sdc' is or was a bootable drive. This is the only way you will have a duplication of the google-chrome install .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Lappert on 2016-05-09
Thanks,
In this machine, sdc is not - and never been -- a bootable drive. That's always been sda.

---

