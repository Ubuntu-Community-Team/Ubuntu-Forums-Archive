---
title: "Accidently added files to root directory; unsure which to remove"
date: 2014-07-02
forum: General Help
---

### Post by jhawthorne13 on 2014-07-02
Hey all,
    I'm running Lubuntu 14.04 LTS, and in the process of learning how to use cmake, I think I built part of Bullet Physics in my root directory (not /root).  I'm pretty sure I know which ones aren't supposed to be there, but I thought I'd double check before I messed around in there. (Things like the root directory are still a bit intimidating to me.  I feel like this mess up actually won't effect my system, but I honestly don't know.) I also wanted to double check that once I know the files/folders to delete, using "sudo rm -rf /filename" would be the easy/safe way of deleting them.

So, here's a list everything in my root directory (stars are next to ones I think I should delete, and directories are bolded):
***** **tmp**
*** src**
* Makefile
* [B]Extras
[/B]*[B] Demos
[/B]* cmake_install.cmake[B]
* CMakeFiles[/B]
* CMakeCache.txt
* BulletConfig.cmake* bullet.pc[B]
* run
* etc
dev
sys
proc
var
root
boot
bin
sbin
usr
svr
opt
mnt
media
lib
[/B]vmlinuz
initrd.img[B]
home
cdrom
lost+found[/B]

Thanks for your time,
Josh

---

### Post by bapoumba on 2014-07-02
Please do not delete any directory. Please do not use the rm command with -rf on the root file unless you are absolutely certain of what you are doing. The bolded directory files above you need.

Is there an uninstall procedure ? Any readme or directions ?

If I'm building something myself outside of my /home file, I usually dot it in /opt.

---

### Post by Elfy on 2014-07-02
You're pretty sure includes /run and /etc - so I would seriously think about stopping and thinking again ;)

> **bapoumba said:**
> Please do not delete any directory. Please do not use the rm command with -rf on the root file unless you are absolutely certain of what you are doing. The bolded directory files above you need.

Is there an uninstall procedure ? Any readme or directions ?

If I'm building something myself outside of my /home file, I usually dot it in /opt. +1 to that

Frankly I would just leave them where they are - they'll not hurt anything afaik - just start again.

---

### Post by The Cog on 2014-07-02
Do **NOT** delete **/tmp /run** or **/etc** - those three are critical to the system.
The others you propose look unusual to me.
I don't think /svr is normal - it may be worth checking the contents to see if that's part of your misplaced install.

---

### Post by sudodus on 2014-07-02
> **jhawthorne13 said:**
> Hey all,
    I'm running Lubuntu 14.04 LTS, and in the process of learning how to use cmake, I think I built part of Bullet Physics in my root directory (not /root).  I'm pretty sure I know which ones aren't supposed to be there, but I thought I'd double check before I messed around in there. (Things like the root directory are still a bit intimidating to me.  I feel like this mess up actually won't effect my system, but I honestly don't know.) I also wanted to double check that once I know the files/folders to delete, using "sudo rm -rf /filename" would be the easy/safe way of deleting them.

So, here's a list everything in my root directory (stars are next to ones I think I should delete, and directories are bolded):
[COLOR=#0000cd]**tmp -- keep**[/COLOR]
*** src**
* Makefile
* [B]Extras
[/B]*[B] Demos
[/B]* cmake_install.cmake[B]
* CMakeFiles[/B]
* CMakeCache.txt
* BulletConfig.cmake* bullet.pc[B]
[COLOR=#0000cd]run -- keep
etc -- keep
[/COLOR]dev
sys
proc
var
root
boot
bin
sbin
usr
svr  [/B](is it srv?, anyway keep it)[B]
opt
mnt
media
lib
[/B]vmlinuz
initrd.img[B]
home
cdrom
lost+found[/B]

Thanks for your time,
Josh

Most of your list seems OK, but it is very important to keep the three directories that I marked [B][COLOR=#0000cd] -- keep
[/COLOR][/B]
You can make a long list and check the date with the terminal window command

```
ls -latr /
```

and you can look into each of the directories you intend to remove, for example **/src** to be even more sure, that it does not belong to something else, and should be kept.

---

### Post by jhawthorne13 on 2014-07-02
> **sudodus said:**
> Most of your list seems OK, but it is very important to keep the three directories that I marked [B][COLOR=#0000cd] -- keep
[/COLOR][/B]
You can make a long list and check the date with the terminal window command

```
ls -latr /
```

and you can look into each of the directories you intend to remove, for example **/src** to be even more sure, that it does not belong to something else, and should be kept.

Thanks!  The way I got most of the list was through sorting by last modification time in the gui folder viewer, but the command you gave me made it much clearer, as all the one's you said were okay for me to delete were last modified within a two-minute time-frame.  (There were also two hidden files. "**.**" and "**..**" modified at the same time.  Can/should I delete these too?

I looked through the directories and saw that the one's you marked seemed like root directory files, and that **/src** only had BulletPhysics-related files.

What's the verdict on "sudo rm -rf /filename"? Should I not use the "-f" option?  Is it that dangerous if I know that those files don't belong there?

> **The Cog said:**
> I don't think /svr is normal - it may be worth  checking the contents to see if that's part of your misplaced  install.

It's actually **/srv**. It doesn't have anything in it as far as I can tell (I checked for hidden files too), but it was last used around the time I installed Lubuntu, so I'm going to keep it anyway.

Don't worry people, I had no intentions of blindly deleting stuff from my root directory. If I did, I wouldn't have asked for your guy's help.

Thanks for the info,
Josh

---

### Post by sudodus on 2014-07-02
No you must leave these directories.

 '.' is the current directory and '..' is the host directory (above the current directory).

It is a peculiar behaviour that these are displayed in the listing.

I suggest that you remove the files and directories with an extra interactive chance to cancel the removal (unless there are too many files in the directories, so you would get tired of confirming),

Try first without sudo

```
cd /
rm -ir directory1
...
rm -i file1
...
```

and only if that does not work

```
cd /
sudo rm -ir directory1
...
sudo rm -i file1
...
```

I don't think you need the f option. But these commands are dangerous enough anyway in the root directory. You must get the directory names and file names right, so that you do not remove what you want to keep.

-o-

This might be a good time to take a good ***backup*** of your system. It would give you peace of mind doing the cleaning job. And once you have a backup, you can consider not only what kind of backup you need but also how frequent you need to take new backups.

---

### Post by jhawthorne13 on 2014-07-02
> **sudodus said:**
> No you must leave these directories.

 '.' is the current directory and '..' is the host directory (above the current directory).

It is a peculiar behaviour that these are displayed in the listing....


This might be a good time to take a good ***backup*** of your system. It would give you peace of mind doing the cleaning job. And once you have a backup, you can consider not only what kind of backup you need but also how frequent you need to take new backups.

Gotcha, I didn't make the connection between the ".." file and the terminal command. I saw similar files in my emacs folder too, and was curious about what they did; thanks for clearing that up.  About backups, thanks for the reminder. I know how useful and important they are, but I haven't gotten into the habit or mindset of doing them yet.

Will report soon if my computer doesn't explode :p. Thanks again for all your help.

EDIT:  SOLVED! Files gone, computer rebooted fine, and my major applications are running smoothly.  Can I mark this thread as solved (if so, how?), or do the mods take care of that?  Also wanted to mention how much I love Linux, Ubuntu, and the great community around it.  You guys rock!

Best,
Josh

---

### Post by sudodus on 2014-07-02
Congratulations :KS

You did it the right way, asked before doing things you didn't know. Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

