---
title: "Can't save downloads to external hard drive"
date: 2018-05-20
forum: General Help
---

### Post by robotsheepboy on 2018-05-20
Recently installed ubuntu having a problem saving downloads to an external hard drive. The hard drive mounts and I can view copy paste, delete files on it etc however when I go to e.g. Chromium or Firefox or vuze and try to select the hard drive as a download location it doesn't appear in the file selection screen.

I tried pressing the little plus sign to display other drives but it does not appear.
I then tried adding the hard drive folder to my favourites so that it appears in the side bar but when I select this from the file download screen it says it doesn't have permission to access that folder.

Any help would be greatly appreciated.

---

### Post by aeronutt on 2018-05-20
Can you use a terminal and command line to view the properties of the mounted hard drive?
Open a terminal, use cd to go to the directory where hard drive is mounted. It will most likely be at /media, but possibly /mnt.
In the terminal at the location of the hard drive (likely /media or /mnt), run the following commands:
> ls -l
df -aTh | grep ^/dev

and post results.

---

### Post by robotsheepboy on 2018-05-20
I'm not at my computer at the moment, but I will be this evening so I'll do this and post the output ASAP, probably about four hours. Thank you for your reply.

---

### Post by robotsheepboy on 2018-05-20
Hi, I am home now, I ran the commands as asked and this is the output

```
~$ ls -ltotal 48
drwxr-xr-x   2 slg slg  4096 May 13 08:56 Desktop
drwxr-xr-x   4 slg slg  4096 May 13 09:12 Documents
drwxr-xr-x   3 slg slg  4096 May 20 13:27 Downloads
drwxr-xr-x 445 slg slg 20480 May 13 09:49 Music
drwxr-xr-x   5 slg slg  4096 May 18 10:52 Pictures
drwxr-xr-x   2 slg slg  4096 May 13 08:56 Public
drwxr-xr-x   5 slg slg  4096 May 18 13:27 snap
drwxr-xr-x   2 slg slg  4096 May 13 08:56 Videos
```

```
$ df -aTh | grep ^/dev/dev/sda2      ext4             325G  263G   46G  86% /
/dev/loop0     squashfs         3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/loop4     squashfs         141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop2     squashfs         181M  181M     0 100% /snap/vlc/190
/dev/loop7     squashfs          38M   38M     0 100% /snap/handbrake-jz/132
/dev/loop8     squashfs         1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop9     squashfs          21M   21M     0 100% /snap/gnome-logs/25
/dev/loop10    squashfs          87M   87M     0 100% /snap/core/4486
/dev/loop14    squashfs          22M   22M     0 100% /snap/gnome-logs/31
/dev/loop15    squashfs          13M   13M     0 100% /snap/gnome-characters/69
/dev/loop16    squashfs         2.4M  2.4M     0 100% /snap/gnome-calculator/167
/dev/loop20    squashfs         3.8M  3.8M     0 100% /snap/gnome-system-monitor/39
/dev/loop18    squashfs         140M  140M     0 100% /snap/chromium/283
/dev/loop5     squashfs         171M  171M     0 100% /snap/filebot/9
/dev/loop11    squashfs         197M  197M     0 100% /snap/firefox/85
/dev/loop1     squashfs         147M  147M     0 100% /snap/skype/30
/dev/loop12    squashfs         163M  163M     0 100% /snap/spotify/13
/dev/loop3     squashfs         173M  173M     0 100% /snap/retroarch/113
/dev/loop6     squashfs         281M  281M     0 100% /snap/vuze-vs/3
/dev/loop13    squashfs          13M   13M     0 100% /snap/gnome-characters/86
/dev/loop17    squashfs         140M  140M     0 100% /snap/gnome-3-26-1604/64
/dev/loop19    squashfs          87M   87M     0 100% /snap/core/4571
/dev/sda1      vfat             487M   30M  457M   7% /boot/efi
/dev/sdb1      fuseblk          1.9T  1.4T  462G  76% /media/slg/Seagate Expansion Drive



```

---

### Post by deadflowr on 2018-05-20
You've got the snap versions
snaps are confined by nature.
But you can give them access by adding them to the snap interface removable-media
Open a terminal and run these:

For firefox try
```
sudo snap connect firefox:removable-media
```
For chromium try
```
sudo snap connect chromium:removable-media
```
(Check my spelling)
See if that helps.

An understanding and listing of snap interfaces (currently):
[https://docs.snapcraft.io/reference/interfaces]("https://docs.snapcraft.io/reference/interfaces")

---

### Post by robotsheepboy on 2018-05-20
great, thank you for this! it worked for firefox, but for vuze and chromium I got the errors 

error: snap "chromium" has no plug named "removable-media"
and

error: snap "vuze-vs" has no plug named "removable-media"


thank you so much for your help so far, also is there any way to get non snap versions in future so that I don't have these issues? (not really sure how I got these ones tbh!)

---

### Post by deadflowr on 2018-05-20
> is there any way to get non snap versions in future so that I don't have these issue
Not sure about vuze, but chromium can be installed from Ubuntu's regular package archives via
```
sudo apt install chromium-browser
```
It should now show two chromium icons when you look at the installed apps.
One will be the snap version, the other will be the apt package version.

Apt packages are not confined like snaps are and can access the whole system if you want.
(Firefox also has an apt package, which should have already been installed, it's a default package for Ubuntu)

> not really sure how I got these ones tbh
The Ubuntu Software center/store shows both the snap version and the apt versions and makes it hard to know which is which.
And some snaps were probably pre-installed during Ubuntu's installation.

Is this Ubuntu 18.04 bionic?

---

### Post by robotsheepboy on 2018-05-20
Yes it's 18.04

any ideas about the error messages or how I can work around them? Just for vuze now, since chromium is working with the apt version

thank you for your help

---

### Post by aeronutt on 2018-05-20
You can list your current snap applications with
> snap list

Other useful snap commands:
> snap disable <nameofsnapapp>
man snap

I removed all snap applications, and snap. And use only the apt versions.

---

### Post by robotsheepboy on 2018-05-20
thank you, more generally is there a reason why it's so difficult to tell snap apps apart in the ubuntu software centre? Also for anyone else out there with a similar issue I found an old version of vuze using the deb installer and I'm going to use that instead. I'll mark this as solved. Thanks all for the input

---

### Post by howefield on 2018-05-20
> **robotsheepboy said:**
> more generally is there a reason why it's so difficult to tell snap apps apart in the ubuntu software centre?...

Scroll down to the details section of the application that you want to install and check out the source. Snap packages will be in the Snap Store. Regular deb packages will have the repository identified.

---

