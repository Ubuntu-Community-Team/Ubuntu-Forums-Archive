---
title: "Changing to new hardrive have a question"
date: 2007-01-28
forum: General Help
---

### Post by d.j.schroeder on 2007-01-28
Ok this is probably a really noobish question but I'm going to ask it anyway.

First some background.  I have an older machine that I've set up to host a couple of web pages, a forum for my wife and some friends, and a teamspeak server.  It runs Dapper and everything is working fine.  My problem is that my wife and friends like to put a lot of large photos on the forum and the hard drive on that machine is not that big.  It's also old.  I know I could add another hard drive and direct the photos over to it, but what I want to do is to replace the existing one with a new one.  That would give me more space and reduce the risk of hard disk death.

I was a complete linux beginner when I started setting that machine up and it took me a long time to get all of that stuff set up and running smoothly.  I think I'd be faster the next time through, but I don't want to test that hypothesis.

So what I'd like to do is to format the new drive and creat boot and swap partitions on it and then just copy the whole existing hard drive to the new one.  Then configure in the BIOS to boot from the new drive.  Will that work?  It seems too easy to actually work.

Any advice on this would be appreciated.

---

### Post by kidders on 2007-01-28
Hi there,

Theoretically, you *should* just be able to **dd** one hard disk onto the other. Although it *seems* like that should work, I haven't ever tried to do it with two different disk geometries, so I can't be 100% sure what would happen.

A slightly more involved approach would go something like this:

[LIST]
[*]Set up some disk partitions on your new hard drive.
[*]Where a new partition matches the size of its corresponding old partition exactly (ie right down to the last block), you could just do something like **dd if=/dev/sda3 of=/dev/sdb3** to do a byte-for-byte copy.
[*]In other cases, format the destination partition first. Then a **sudo cp -dpR /path/to/src /path/to/dst** would do the trick.
[/LIST]

Overcomplicating the process like this has a few advantages:

[LIST=1]
[*]You are free to choose different filesystems on your new hard disk. Now that you've had a chance to play with Linux a bit, you might like to try something new. :-)
[*]You can change the sizes of your partitions, rather than just adding new ones, or maybe re-order them.
[*]Using **cp** rather than **dd** will eliminate any filesystem fragmentation that may have accumulated.
[/LIST]

After you're done, you may be able to just reboot your machine and carry on as though nothing had happened, athough you should read your /etc/fstab carefully to make sure it still matches your configuration. If you **dd** your entire hard disk you won't need to, but otherwise, don't forget to reinstall your bootloader!

The most important thing to remember is *never* to do any of this from a graphical environment. There would be far too much uncontrolled writing to files going on, that would invariably leave you with an inconsistent duplicate of your Ubuntu system. If possible, performing the copy with a LiveCD would be best.

---

### Post by Irony on 2007-01-28
Copying is simple I've done it with Ubuntu many times see here;

[http://www.pclinuxos.com/forum/index.php?topic=13404.0](http://www.pclinuxos.com/forum/index.php?topic=13404.0)

---

### Post by d.j.schroeder on 2007-01-28
Thanks for the replies.  Doesn't sound too bad.  I think I'll give it a shot.

---

### Post by kosmic on 2007-01-28
If you are a noob in backup and restore, I recomend that you try Partimage, it is simple and fast :)

---

### Post by dexter on 2007-01-28
Remember to create a backup of your important files first so that you won't lose anything in case something would go wrong.

---

### Post by d.j.schroeder on 2007-02-07
Well I think I did something stupid, not too stupid I haven't lost any data, I was hoping someone could tell me why what I tried didn't work.

I decided to try backing up my primary drive onto a larger drive using the dd command.  The larger, target drive, was attached to the system via a USB enclosure.  My plan was to copy everything, verify that everything was there and ok, then swap the drives.

First, I formatted the target drive ext3, then I used:

sudo dd if=/dev/hda of=/dev/sda

Both hard drive lights started going and I thought things were going fine.  After 3 or 4 hours it stopped and reported something like 38 GB copied and returned to the command prompt.

However, when I looked at the USB drive there is nothing on it.  In the disk manager it says that it is a windows FAT32 file system which is just about full, 181 GB.

So, apparently I did something wrong.  Will dd just not work to transfer something to a drive attached via a USB enclosure or did I miss something else?

---

### Post by kidders on 2007-02-10
That should've worked just fine, I think. Weird :confused:

Sorry for not posting back sooner, but I have no idea what to suggest! :-( Sorry. Does anyone else have any ideas?

---

### Post by d.j.schroeder on 2007-02-20
Just thought I'd bump this one more time.  Still hoping to get an answer.

---

