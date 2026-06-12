---
title: "iPod Recognition?"
date: 2007-01-27
forum: General Help
---

### Post by Apt_Quadruped on 2007-01-27
Hello, I've installed multiple iPod programs ranging from GTKPod to Banshee. In many of them they don't recognize the iPod, or they won't copy the songs from my iPod to Linux (which is mainly what I want to do). Could someone please point me into the right direction as to how to retrieve all my valuable songs (as well as playlists) from my iPod? Thanks in advance!
*My iPod is a 5.5G Video*

---

### Post by bettlebrox on 2007-01-28
modprobe the sbp2 module. Add yourself to the plugdev, logout and login again and see if your favourite iPod access program works!

---

### Post by yahoo on 2007-01-28
Have you tried Floola?

[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

---

### Post by al1b1 on 2007-01-28
To get the files off your ipod using nautilius go to ipod control, music and thier in the folders called F01, F02 etc. However no playlists

---

### Post by Apt_Quadruped on 2007-01-28
> **bettlebrox said:**
> modprobe the sbp2 module. Add yourself to the plugdev, logout and login again and see if your favourite iPod access program works!

I don't understand what you said. Could you please help me with whatever you told me to do above? By the way Floola didn't want to give me the playlists. Thanks anyways.

---

### Post by bettlebrox on 2007-01-28
> **Apt_Quadruped said:**
> I don't understand what you said. Could you please help me with whatever you told me to do above? By the way Floola didn't want to give me the playlists. Thanks anyways.
Sure! Your userid needs to be a member of the plugdev group to access your iPod. Open up a terminal (or command line) and type *id* to show what groups you are a member of, like this (the $ is the prompt you don't need to type it):

```
$ id
uid=1000(meself) gid=1000(meself) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),44(video),60(games),**103(plugdev),**107(lpadmin),108(scanner),501(camera_z),1000(meself)

```
If you don't see plugdev listed you will need to add yourself to the group, like this:

```
sudo useradd -g plugdev username
```

Where username, is the username of the user you want to have iPod access.

Logout, and login again and your iPod should be mounted when you plug it in. If you use Gnome you can start up the “Removeable Drives & Media” configuration tool (it’s under the System -> Preferences menu). And on the Multimedia tab add the following line to have Gtkpod automatically started when your iPod is attached and told where it was mounted:

gtkpod -m %m

(Have look here: [http://timony.com/mickzblog/2007/01/27/debian-ubuntu-ipods/]("http://timony.com/mickzblog/2007/01/27/debian-ubuntu-ipods/") I wrote a blog entry for ya ;)

Now, if all that doesn't work, you may need to have the sbp2 module loaded. But, try what I've writte above first and see if it works. If it doesn't let us know and we'll see what else we need to do.

:guitar: 

Luck ;)

---

### Post by Goober on 2007-01-28
Out of sheer curiousity, does RhythmBox work with iPods?  I have a Shuffle (old Version), and, to maintain my sanity, I will need to change the music at some point.

---

### Post by bettlebrox on 2007-01-29
> **Goober said:**
> Out of sheer curiousity, does RhythmBox work with iPods?  I have a Shuffle (old Version), and, to maintain my sanity, I will need to change the music at some point.
Yes, Rhythmbox works with iPods. You may have to turn on iPod support under the plugins menu.

---

### Post by Apt_Quadruped on 2007-01-29
alright, I tryed to sync my ipod with GTKpod (uploading files to Linux) but it came up with this "Warning"
```
No directory names were stored. Make sure that you enable 'Write extended information' in the Export section of the preferences at the time of importing files.

To synchronize directories now, activate the duplicate detection ('Don't allow file duplication') in the Import section and add the directories you want to sync again.

```
By the way, Banshee still doesn't recognize my iPod...

---

### Post by bettlebrox on 2007-01-29
> **Apt_Quadruped said:**
> alright, I tryed to sync my ipod with GTKpod (uploading files to Linux) but it came up with this "Warning"
```
No directory names were stored. Make sure that you enable 'Write extended information' in the Export section of the preferences at the time of importing files.

To synchronize directories now, activate the duplicate detection ('Don't allow file duplication') in the Import section and add the directories you want to sync again.

```

Look like you need to go into Gtkpod's Preferences Menu and do what it says.

> **Apt_Quadruped said:**
> 
By the way, Banshee still doesn't recognize my iPod...

I'm not sure what you need to do to get Banshee to use your iPod, have you installed the banshee-official-plugins package?

---

### Post by insanitywetrust on 2007-02-09
hi there

been trying for days to get ipod shuffles to work, 

rhythmbox loads the music

cannot play music on the ipod, led light stays on, 
normally it should only light up for about 3 or 4 seconds

so, if anyone has a site with very extensive troubleshooting tips or help, thanks

---

### Post by bettlebrox on 2007-02-10
Looks like Apple may have done some funky stuff w/ the Shuffle firmware:

[http://www.linuxforums.org/forum/ubuntu-help/80336-2nd-generation-ipod-shuffle.html](http://www.linuxforums.org/forum/ubuntu-help/80336-2nd-generation-ipod-shuffle.html)

You might want to start a new thread, and document what you've tried to date.

Luck!

---

