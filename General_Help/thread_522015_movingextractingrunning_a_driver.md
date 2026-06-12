---
title: "moving/extracting/running a driver"
date: 2007-08-10
forum: General Help
---

### Post by Zeenomorph on 2007-08-10
I'm trying to get my Webcam to work.  I have a AsusF5V computer, and it comes equipped with a 1.3 mpx camera.  I read a post by someone else trying to get it to work, and he had moderate success.  It's at;

[http://terenzioberni.blogspot.com/2007/06/asus-z53jr-f3jr-webcam.html](http://terenzioberni.blogspot.com/2007/06/asus-z53jr-f3jr-webcam.html)

But I can't follow the instructions.  I downloaded the driver.  It's on my desktop now.  He tells me to manually move it to;

/lib/modules/2.6.20-16-generic/kernel/drivers

but it says that I don't have permission.  I tried to extract to that folder, but again, not allowed.  

I know that this question has been asked before, and I assure you that I read the other posts, I'm afraid that I'm a complete noob, and don't really understand what to do.  If you could be very basic with your answer I'd greatly appreciate it.

Thank you again;

Zeenomorph

---

### Post by BoneKracker on 2007-08-10
Try placing the word sudo before the commands.  This gives your root privileges temporarily (for that command).

---

### Post by Zeenomorph on 2007-08-10
... and what command shall I use?

You seem to underestimate my noobishness!

---

### Post by BoneKracker on 2007-08-10
The command to move a file is
```
mv
```To lean how to use the command, you can use the built in manual```
man mv
```
The command to copy a file is
```
cp
```
So if the move or copy operation requires root privileges, you just put 'sudo' in front of mv or cp.  For example, if I want to copy a file from my home directory into /root, I do:```
sudo cp ~/porno.jpg /root
```
~ is short for "/home/myusername"

man is your friend.  To learn about it type```
man man
```
Another built-in documentation system is info.  To learn about it type```
info
```

---

### Post by Zeenomorph on 2007-08-10
OMG!  That was awesome, I feel like I'm only a step or two away from being a genuine hackor!  

Now to burst my bubble, I got the file in there, but How do I extract it?

---

### Post by BoneKracker on 2007-08-10
I didn't notice you had said anything about extracting it.  Instead of moving or copying, you could have extracted it directly _to_ that location with a single command.  

There's a lot of info below, so you can understand what you're doing instead of just typing a command and forgetting how to use it for next time.  But it's actually simple, and worth learning since this is a very common thing to need to be able to do.

How to extract depends upon what type of compressed file it is (there are others, like cpio, but these are the ones most users have to work with).  Depending on whether the file is a .zip, .gz, or .bz2 the command to extract will be:

unzip somefile.zip
gunzip somefile.gz
bunzip2 somefile.bz2

How to extract also depends on whether the file is actually an archive of a bunch of files.  The common archive type on unix-like systems is tar.
```
untar somefile.tar
```

Each of the commands above has a corresponding command that _creates_ that type of file.```
zip somefile
gzip somefile
bzip2 somefile
tar somefile
```

While that seems like a lot of commands to remember, you can forget about the 'un' versions of the commands, because the 'create' version of the commands customarily have an option you can add to them that causes them to extract instead of create.```
gzip -d
bzip2 -d
tar -x
```

Now, those are the fundamentals.  _In reality it's even simpler._  You are most often going to see files that are a compressed archive.  For example:
```
somefile.tar.gz
```
Tar itself can call on the other programs, so you can extract it with a single command.  In the example below, focus on the options (the letters immediately after the dash):```
tar -xzf somefile.tar.gz
tar -xjf somefile.tar.bz2

```

To qualify yourself to use these tools, here are a couple good things for you to do (to learn):```
man gzip
man bzip2     # if your system has bzip2 installed, which it probably does
man tar
(bonus points) man -k extract
```

man -k is like saying, "list all the man pages that deal with the subject" -- this is how to get help if you don't know what command you are looking for.  This will give you broader picture of other types of extract operations and their commands.

Once you've mastered this, you can use the graphical tool available on your system _if you want_.  Most people that have mastered the command-line tools never bother with the graphical ones because they aren't as flexible or fast.  I think it's fileroller (if you're on Gnome -- I can't remember what the kde version is called).  You have to start it with root privileges if you want to be able to work with directories or files you don't normally have permissions for.
```
gksu fileroller
```

---

### Post by Zeenomorph on 2007-08-10
That was a very helpful post.  I bookmarked it for later use, I'm confused as to why it didn't work though.

I typed  what you said, then the path, and the filename;
tar -xzf lib/modules/2.6.20-16-generic/kernel/drivers/stk11xx-1.0.0.tar.gz
then the terminal went back to waiting for me to input something, and the file remains untouched.

---

### Post by BoneKracker on 2007-08-11
Ah...  I think I know what's wrong.

Normally, I would extract the file directly into the spot you want the files, like so:```

bonkracker@wtf$ tar -xvxf ~/stk11xx-1.0.0.tar.gz -C /lib/modules/2.6.20-16-generic/kernel/drivers
stk11xx-1.0.0/
stk11xx-1.0.0/stk11xx.txt
stk11xx-1.0.0/Makefile
stk11xx-1.0.0/Kbuild
stk11xx-1.0.0/README
stk11xx-1.0.0/stk11xx.h
stk11xx-1.0.0/doxygen.cfg
stk11xx-1.0.0/stk11xx-buf.c
stk11xx-1.0.0/stk11xx-dev.c
stk11xx-1.0.0/stk11xx-v4l.c
stk11xx-1.0.0/stk11xx-usb.c
stk11xx-1.0.0/stk11xx-sysfs.c
stk11xx-1.0.0/stk11xx-bayer.c
```(By the way, the v option is for verbose, which gives some feedback as to what's happening.  All those lines that start with "stk11..." are what the machine is feeding back to me after the command - saying that it's unpacking those files)

The C option stands for "change to directory".  After the C you put where you want the files to go.
The reason it's worded that way ("change to directory") is that tar is designed to extract into whatever the present workng directory is.

The "present working directory" is basically wherever you are when you issue the command.  So, if you don't specify a C option, the files will get extracted into whatever directory you were in at the time.  So, if you were in your home directory, go look there -- you might find your driver there.

Another possiblity is that you forgot to put "sudo" in front of your command, or that you forgot the / in front of lib (but I suspect those were just a typos in your post).

If you look at the tar man page, you'll see the C and v options explained in detail.  Don't get frustrated.  Everybody has to fumble around with these things the first time they use them.

You could also extract the files (in your home directory) using your graphical tool and then "sudo mv" the whole bunch, but this is the quickest way once you know how to do it.  And you are learning a bunch of stuff that applies to many other things you will do.

By the way, the files I extracted for demonstration above are source files that would need to be compiled into binaries before they should go into lib.

---

### Post by Zeenomorph on 2007-08-11
Thanx a lot.  There is was sitting in my home directory.  You da man!

---

