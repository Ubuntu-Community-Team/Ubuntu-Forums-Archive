---
title: "Accessing mac time machine backup from Ubuntu"
date: 2013-12-14
forum: General Help
---

### Post by PDavis1248 on 2013-12-14
For a while I had a macbook, which was stolen recently. Instead of getting another mac I decided to start using Ubuntu as my primary operating system. I'd like to get many of the files from the time machine backup on my external drive. I can navigate through many of the folders on the backup, but it tells I don't have permission to view any of the user folders. Is there a way that I can get access to all the files on the drive from Ubuntu, or will I need to get another mac involved? I had been using OSX 10.6, and have Ubuntu 12.04.

---

### Post by coffeecat on 2013-12-14
This problem is a bit of a tricky one because of the ugly hack Apple have used to create a Time Machine backup. The permission problem you have run into is because both Ubuntu and MacOS use the same Unix system for ownership and permissions and your Mac UID is different from your Ubuntu one. But even if you use a root owned file browser to browse your Time Machine backup to circumvent the ownership problem, you'll run into some dead-ends caused by hard links. Rather nasty.

Some links for background:

[http://carsonbaker.org/time-machine-on-linux](http://carsonbaker.org/time-machine-on-linux) 

[http://hints.macworld.com/article.php?story=20080623213342356](http://hints.macworld.com/article.php?story=20080623213342356)

Fortunately, there's a script which will automate copying the whole backup to a reconstructed directory tree, here:

[https://gist.github.com/vjt/5183305](https://gist.github.com/vjt/5183305)

And an earlier thread on this forum pointing to the same script:

[http://ubuntuforums.org/showthread.php?t=2129938](http://ubuntuforums.org/showthread.php?t=2129938)

Post #6 there tells you what to do, but if you are new to Linux, that might be a bit daunting I'm afraid. Post back if you need help with /path/to/time/machine/backup/drive and path/to/local/folder.

---

### Post by PDavis1248 on 2013-12-14
Alright, I did that, but don't know quite what it did. It returned 
Usage: /home/jon/Downloads/copy-from-time-machine.sh <source> <target>

---

### Post by coffeecat on 2013-12-14
It didn't do anything - except to tell you it needed a more precise command.

I'm going offline now, but just a quick pointer to what you need. I'll check this thread tomorrow.

You seem to be able to run the script, but just in case there are any problems with this, when you download the script, it's tarballed in a tar.gz file. If you extract it, it will extract into a folder called gist5183305-2c7113c219b71b12d54d50da0998d6d9a91e4af7, so the instruction for running might need to be varied. I suggest you extract the gist5183305-2c7113c219b71b12d54d50da0998d6d9a91e4af7.tar.gz file by right-clicking ->extract here. Then open the gist5183305-2c7113c219b71b12d54d50da0998d6d9a91e4af7 folder and move the copy-from-time-machine.sh file to your desktop. You can then run it from a terminal with:

```
~/Desktop/copy-from-time-machine.sh <source> <target>
```

However, first you need to determine what <source> and <target> are.

Plugin your Time Machine drive and then run this terminal command:

```
mount
```

There will be a line in the output with HFS+ or hfs+ (I hope) in it. This will be your Time Machine drive. It will show the mount path which is what you need for source. The path will be something like /media/jon/something. Substitute that for <source>

For <target> you will need plenty of space. I suggest you use an external USB drive. If it is plugged in before you run the mount command, there will be another line which indicates its mountpoint, something like /media/jon/somethingelse. Without knowing what filesystem is on the target USB drive, I can't give you any further pointers. I hope that's enough to get you going.

---

### Post by coffeecat on 2013-12-15
A couple of things to add to what I posted last evening:

If you substitute <source> with /media/jon/timemachine (or whatever the mountpoint is for your timemachine drive) you will copy absolutely everything, including the backed up MacOS operating system files. Which will be unnecessary. If you want to backup all the contents of your Mac home folder, <source> would have to be something like /media/jon/timemachine/Users/yourMacusername. If a specific folder in your Mac home - say Pictures - it would be /media/jon/timemachine/Users/yourMacusername/Pictures. Sorry if this is complicated - without knowing exactly where your Ubuntu system has mounted your Time Machine drive, it's impossible to be more specific.

I assumed you might want to extract all your Time Machine files to another external drive. So long as you have enough room in your Ubuntu hard drive, there's no reason why you shouldn't extract to a folder in your Ubuntu home folder instead. If you want to do that, make a folder called TimeMachine (no space - spaces add complications in the terminal) in your Ubuntu home folder, after which you can substitute ~/TimeMachine for <target>

---

### Post by PDavis1248 on 2013-12-15
Thanks for your help coffeecat. When I run the script now it spits out a few lines, and stops with the error.

s/.bash_history' -> `/home/peter/TimeMachine/.bash_history'
cp: cannot open `/media/Backups/Backups.backupdb/Jon Smith&#8217;s MacBook/Latest/HD/Users/jonsmith/.bash_history' for reading: Permission denied

I also tried just getting the music folder, which also returned "permission denied"

---

### Post by mattholl82 on 2013-12-15
Is it possible to change your UID in Ubuntu to match the OSX UID??

---

### Post by PDavis1248 on 2013-12-15
I have no idea. How would I do that?

---

### Post by coffeecat on 2013-12-15
> **mattholl82 said:**
> Is it possible to change your UID in Ubuntu to match the OSX UID??

I wouldn't recommend that. A bit of a sledgehammer to crack a nut really.

> **PDavis1248 said:**
> Thanks for your help coffeecat. When I run the script now it spits out a few lines, and stops with the error.

s/.bash_history' -> `/home/peter/TimeMachine/.bash_history'
cp: cannot open `/media/Backups/Backups.backupdb/Jon Smith’s MacBook/Latest/HD/Users/jonsmith/.bash_history' for reading: Permission denied

I also tried just getting the music folder, which also returned "permission denied"

It's been a long time since I ran this script and I don't remember this. I *think* you'll need to run it as root and then sort out the ownership of the files once you have extracted them. Try:

```
sudo ~/Desktop/copy-from-time-machine.sh <source> <target>
```

Adjusting depending on where your copy-from-time-machine.sh script is. To be honest, I'm not sure what ownership your files will end up with once they're unpacked to /home/peter/TimeMachine/, but that's trivially easy to fix.

---

### Post by mattholl82 on 2013-12-15
> **coffeecat said:**
> I wouldn't recommend that. A bit of a sledgehammer to crack a nut really.


lol good point...

---

### Post by PDavis1248 on 2013-12-15
Alright, the script is running and seems to be working just like it should. It's going to take a while to finish, so I can't yet confirm that everything has worked correctly. But it looks like it is doing everything as advertised. Files are being copied over and I can access them just fine. Thanks so much for the help coffeecat, you're a lifesaver!

---

### Post by coffeecat on 2013-12-15
I'm glad to hear that, and glad to hear you can access them. If by chance you do eventually get folders or files that give you a permission denied message, post the details and I'll give you the command that can sort the ownership out.

---

### Post by Roberto_Castilla on 2014-09-23
I think it fails when the source file is an "empty regular file". It has to be a directory. Am I right?

---

