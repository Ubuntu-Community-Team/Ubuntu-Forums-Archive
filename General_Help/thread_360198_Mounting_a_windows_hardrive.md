---
title: "Mounting a windows hardrive"
date: 2007-02-12
forum: General Help
---

### Post by GregLH on 2007-02-12
Now so far I'd like to say is since October of last year I been using ubuntu as my first Linux experience  and I've just love it. Now I really only use my window XP for games I can't use on Linux. One thing that I been wondering is how can I mount my windows hardrive in linux so I can access data and get my music off it and bring it to my Linux hardrive? I've seen it for partition single hardrives but I'm not 100% sure if it will or will not work the same way and I don't feel like blowing up a hardrive today. Also it does not show up on computer. Anyway to get into it?

Oh! before I forget I am running edgy and the XP install is home

---

### Post by kidders on 2007-02-12
Hi there,

Assuming you're talking about two hard disks in the same machine, you can access the second one with a single command. If you're nervous about causing damage, you can always perform a read-only mount though, in which case Ubuntu will make no attempt to make changes of *any* sort.

Basically, what you want is a command like **sudo mount /dev/sdb1 /mnt/windows** or something, to plug the Windows filesystem into your Linux one (temporarily).

[LIST=1]
[*]Create a mount point with something like **sudo mkdir /mnt/windows**
[*]Identify the right /dev node with something like **sudo fdisk -l**
[*]Perform the mount, perhaps with **sudo mount -o ro /dev/whatever /mnt/whatever** for a read-only mount.
[/LIST]

Assuming Ubuntu can recognise the filesystem type, it will figure the rest out on its own.

---

### Post by GregLH on 2007-02-12
Works, thanks for the help. Now let's say if I wanted to take my music off of it and bring it to my linux hardrive? I tried terminal but we all know how much terminal hates anything with a space in it . :P

---

### Post by azazel00 on 2007-02-12
Go into nautilus,

browse to /mnt/windows (or the folder you used) and the just drag and drop the files.

Regards

---

### Post by yopnono on 2007-02-12
> **GregLH said:**
> Works, thanks for the help. Now let's say if I wanted to take my music off of it and bring it to my linux hardrive? I tried terminal but we all know how much terminal hates anything with a space in it . :P

to create a folder with spaces from in side the terminal
```
mkdir ee\ rr\ tt
```
to enter a folder
```
cd ee\ rr\ tt
```

---

### Post by ndefontenay on 2007-02-12
For the sake of not scaring new users, I want to underline that this task is perfectly doable with KDE graphical Interface.

I would:

1)  go to system setting
2) Press the "Advance" button
3) Login is as an Admin
4) Right click on the disk and select "modify"
5) Choose the correct type for the disk (NTFS)
6) Select a mount point (a map point is a folder. It's possible to create it at that time.) I've choosed /media/windows
7) Select the privileges. I gave read and write to my main user. I also specify my user to be the owner of the device. (Default is root)
8)  Press the "Enable" button at the bottom of the configuration screen. A green light should show next to the selected hard drive.
9) Go to Nautilus and browse happily. The folder selected as a mount point (/media/windows) should be a hard disk icon
10) Enjoy a cup of Ubu... Coffee

oh and yes.... It's much more confusing to explain that way. But that's what beginners understand the best... Command line is scary

To the beginner going through this: Try the command line! It's easy. Fall back on the graphical interface after you have tried and consider it too difficult : )

Happy mounting of windows partition.

---

### Post by kidders on 2007-02-12
> **ndefontenay said:**
> For the sake of not scaring new users, I want to underline that this task is perfectly doable with KDE graphical Interface.Sorry... the need to make that comment was probably my fault! Oops. I mentioned KDE because I know it better. KDE rocks hehe. :-P

> **GregLH said:**
> Works, thanks for the help. Now let's say if I wanted to take my music off of it and bring it to my linux hardrive? I tried terminal but we all know how much terminal hates anything with a space in it . :PSpaces don't really present a problem. Quoting paths/filenames is another alternative to yopnono's suggestion, which also works perfectly. Backslashes are commonly used in Linux to escape characters that would otherwise have special meanings, like '$' or '/', or spaces.

---

### Post by highneko on 2007-02-12
> **GregLH said:**
> Works, thanks for the help. Now let's say if I wanted to take my music off of it and bring it to my linux hardrive? I tried terminal but we all know how much terminal hates anything with a space in it . :P
If you're wanting to change the file permissions so they're readable and writable then I suggest this:
```
# First change the directory into where the files you want are. Make sure to use quotes like in the following example:
cd "/mnt/windows/music example"
# Copy the files to your ubuntu home folder or somewhere else with sudo:
sudo cp *.mp3 $HOME
# Change current directory to your home folder for reasons which I won't explain:
cd "$HOME"
# Then make the files readable and writeable:
sudo chmod 644 *.mp3
# Then make the files owned by you:
sudo chown $USER:$USER *.mp3
```
Then you can play all your music with a music player. Good luck, have fun.

---

### Post by GregLH on 2007-02-13
Thanks everyone everything is working well now. I'm very impressed that linux can do all this still, going into another OS and reading copying the files without damaging the other OS at all. 

>_>)b

---

