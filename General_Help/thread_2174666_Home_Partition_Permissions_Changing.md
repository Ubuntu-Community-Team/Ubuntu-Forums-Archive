---
title: "Home Partition Permissions Changing?"
date: 2013-09-15
forum: General Help
---

### Post by EternalLiberty on 2013-09-15
I'm using a headless Ubuntu machine that I either VNC or SHH into. This computer only acts as a simple file and MineCraft server. Everything was working great until it said I couldn't copy files to it because it was full and MineCraft couldn't save progress.

I logged into the server and seen a "Low Disk Space" error. It says, "The volume "home" has only 1.4MB disk space remaining. If I examine it with Disk Usage Analyzer, at the top it says "Could not scan folder "/home" or some of the folders it contains. I'll include a screenshot.

I never changed any of the file/folder permissions. I'll also include some screenshots of some important folders with their current permissions. 

Their locations are:
home - It's own partition mounted at root.
cord - User folder within home
MineCraft_Servers - Within cord
Share - Within cord
Cords Backup - Within Share (This along with everything else in this folder were copied over by the remote computer.)

Note, this same issue happened a about a week ago on an older fresh install of Ubuntu. I was able to fix it by manually changing the folder/file permissions but after a day or two, the issue happened again. After trying a few more times, I reformatted and started fresh. That brings me to today, with the same issue again.

If anyone has any ideas, please share.

 [ATTACH=CONFIG]246260[/ATTACH] [ATTACH=CONFIG]246259[/ATTACH]

---

### Post by jamesisin on 2013-09-15
How do you send files to that system?  If you are using rsync (or something which relies on rsync), and depending upon the switches you choose, you can alter containing folder permissions if you are not careful.

(I ran into this on my server where I use rsync to transfer files.  I both created a transfer folder where I set the permissions to match those of the destination hierarchy and for good measure added a permissions-fix line to my backup script.)

---

### Post by EternalLiberty on 2013-09-15
I use the shared folder more as a temporary storage solution. I use Google Drive for anything important. On Ubuntu, I simply right clicked the folder, enabled share with samba and allowed guest the ability to create and delete files. On the Windows 8 computer, I just open the network share and drop files.

Unless Ubuntu can't calculate the file sizes due to permissions and therefore reports the partition as full, I'm not sure if it's a file sharing issue.

---

### Post by jamesisin on 2013-09-15
Is this fullness report on your client system(s) or on the server?  There are *many* reasons why a client might misunderstand available space on a share.

---

### Post by EternalLiberty on 2013-09-15
The Ubuntu server is reporting the space issues. I attached a screenshot of that in the first post.

---

### Post by jamesisin on 2013-09-15
What do you get if you run df on that partition?

```
df -h
df -h /home/cord/
```

---

### Post by EternalLiberty on 2013-09-16
Here you go, James.


```
cord@Ubuntu-Server:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        38G  3.9G   32G  11% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.7G  4.0K  1.7G   1% /dev
tmpfs           342M  900K  341M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.7G   76K  1.7G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sda6       252G   90G  151G  38% /home
cord@Ubuntu-Server:~$ df -h /home/cord/
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       252G   90G  151G  38% /home
```

---

### Post by jamesisin on 2013-09-16
Well, that's not full.  Something is causing the file measure to count more than is actually there.  Shortcuts/links?

---

### Post by jamesisin on 2013-09-16
I'm not sure if this will give us useful clues, but it certainly can't hurt to look:

```
du --max-depth=2 /home/cord | sort -n
```

This will list files/folders in ascending order of size.  You can adjust the max depth or path if you'd like to see something in particular in more detail.

---

### Post by EternalLiberty on 2013-09-16
Sure, here's the more detailed list. Everything seems normal.

```
4    /home/cord/.cache/dconf
4    /home/cord/.cache/gnome-screenshot
4    /home/cord/.cache/unity-lens-photos
4    /home/cord/.config/enchant
4    /home/cord/.config/eog
4    /home/cord/.config/update-notifier
4    /home/cord/Desktop
4    /home/cord/Documents
4    /home/cord/Downloads
4    /home/cord/.gvfs
4    /home/cord/Music
4    /home/cord/Pictures
4    /home/cord/Public
4    /home/cord/Templates
4    /home/cord/Videos
8    /home/cord/.cache/indicator-appmenu
8    /home/cord/.cache/unity-lens-video
8    /home/cord/.config/evolution
8    /home/cord/.config/gnome-session
8    /home/cord/.config/gtk-3.0
8    /home/cord/.config/ibus
8    /home/cord/.config/software-center
8    /home/cord/.config/totem
8    /home/cord/.dbus/session-bus
12    /home/cord/.cache/indicator
12    /home/cord/.cache/ubuntuone
12    /home/cord/.compiz/session
12    /home/cord/.config/compiz-1
12    /home/cord/.config/dconf
12    /home/cord/.dbus
16    /home/cord/.cache/update-manager-core
16    /home/cord/.compiz
16    /home/cord/.config/gedit
20    /home/cord/.config/nautilus
28    /home/cord/.cache/sso
28    /home/cord/.gconf/apps
32    /home/cord/.gconf
32    /home/cord/.pki/nssdb
36    /home/cord/.pki
44    /home/cord/.cache/fontconfig
48    /home/cord/.config/libaccounts-glib
52    /home/cord/.cache/evolution
68    /home/cord/.config/pulse
72    /home/cord/.cache/oneconf
112    /home/cord/.cache/compizconfig-1
352    /home/cord/Share/Screenshots
372    /home/cord/.cache/wallpaper
576    /home/cord/.cache/gstreamer-1.0
624    /home/cord/.config/chromium
876    /home/cord/.config
1032    /home/cord/.cache/thumbnails
1624    /home/cord/.local/share
1628    /home/cord/.local
4364    /home/cord/.cache/chromium
16000    /home/cord/.cache/software-center
22740    /home/cord/.cache
186436    /home/cord/Share/Pictures Backup
197168    /home/cord/Share/eq
237720    /home/cord/MineCraft_Servers/The_Ranch_Server
237724    /home/cord/MineCraft_Servers
326568    /home/cord/Share/ToughBook Backup
923992    /home/cord/Share/Autmn Backup
932736    /home/cord/Share/Microsoft Office 2011 - Mac (Backup)
1221088    /home/cord/Share/Dogs
1263664    /home/cord/Share/Game Soundtracks
1683908    /home/cord/Share/Game Screenshots
1894032    /home/cord/Share/Amber Backup
2389608    /home/cord/Share/Visual Studio 2010 Ultimate (x86) - DVD (English)
2399708    /home/cord/Share/Wedding
2889108    /home/cord/Share/Video Edits
3173160    /home/cord/Share/Daz 3D
3308052    /home/cord/Share/Temp Desktop
4302652    /home/cord/Share/Random
5889596    /home/cord/Share/Fraps Videos
7204392    /home/cord/Share/Desktop
9552612    /home/cord/Share/BBC The World at War
12484072    /home/cord/Share/Cords Backup
21881192    /home/cord/Share/EQ Stuff
93007260    /home/cord/Share
93389456    /home/cord
```

---

### Post by jamesisin on 2013-09-16
Yes, that does look pretty normal.  This suggests that the problem lies with Nautilus?  It's confused about... something in your home directory.  Note that du didn't encounter any permissions issues.

---

### Post by EternalLiberty on 2013-09-16
Now that you mention permission issues, I should tell you that if I run the command without sudo, I get the following first results:

```
[FONT=arial]cord@Ubuntu-Server:~$ du --max-depth=2 /home/cord | sort -n[/FONT]
[FONT=arial]du: cannot read directory ‘/home/cord/.config/enchant’: Permission denied[/FONT]
[FONT=arial]du: cannot read directory ‘/home/cord/.cache/dconf’: Permission denied[/FONT]
[FONT=arial]du: cannot read directory ‘/home/cord/.gvfs’: Permission denied[/FONT]
[FONT=arial]4    /home/cord/.cache/dconf[/FONT]
[FONT=arial]4    /home/cord/.cache/gnome-screenshot[/FONT]
```

---

### Post by jamesisin on 2013-09-16
Hmmm... .gvfs is your mounted shares I think.  But you said this was the server?

Not sure about the other two.  I would dig inside and see if you can find a specific problem file.  You can adjust that du command to look just into those directory trees.  See what is having permissions issues.

---

### Post by EternalLiberty on 2013-09-17
I'm running the Desktop version of Ubuntu but it is being used essentially as a server and headless. I ran the command at 6 levels deep and it still only returned the three original results.

Below are the folder contents:

**enchant**

```
-rw-r--r--  1 root root    0 Sep  8 18:58 en_CA.dic
-rw-r--r--  1 root root    0 Sep  8 18:58 en_CA.exc
```

**dconf**

```
-rw-rw-r--  1 cord cord 8436 Sep 17 23:29 user
``` 

**.gvfs**

```
empty
```

---

### Post by jamesisin on 2013-09-18
Those first two should not likely be owned by root.  Not sure why that third one would give a permission error.  Must be a containing folder?  It is my understanding that you should be the owner for everything in your home directory.

Of course this doesn't help your size disparity.  Or at least I don't think it will.

Just a guess but you could try running a find command looking for any links (shortcuts) in /home which might be causing Nautilus (or whatever) to double-count occupied space?

If I think of more I"ll offer it.

---

### Post by EternalLiberty on 2013-09-23
I've solved it!

I used a program called "IOTop" to see what processes were writing to the hard drive. After looking one up, I noticed VNC was writing log entries. Using BleachBit, I was able to find the large log (.xsession-errors). Check out the screenshot, the file was 180GB in size.

So VNC (Desktop Sharing) was rejecting connections and logging them. All I did was delete the log and change the default 5900 VNC port. Funny thing is, VNC locking up and failing to connect, was the other major issue I was having with Ubuntu.

Everything seems to be fine now.

[ATTACH=CONFIG]246450[/ATTACH]

---

### Post by jamesisin on 2013-09-23
Yep, right in the root of your home directory.  Nice catch.

---

