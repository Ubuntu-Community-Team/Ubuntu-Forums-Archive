---
title: "dual booting problems"
date: 2008-04-26
forum: General Help
---

### Post by 500sd on 2008-04-26
Hi
I was dual booting windows xp and ubuntu 7.10. I just upgraded my xp to vista and now it flashes this weird screen with stuff I don't understand :P It used to not show the dual boot screen but I got supergrubdisc and now it shows the menu...but it says windows xp instead of vista and I can't boot into linux from it, it says that the file doesn't exist or something like that. So how can i fix this mess?

---

### Post by 500sd on 2008-04-27
Help??

---

### Post by catalina on 2008-04-27
Hi There,

When you are upgrading you cannot upgrade a windows machine when you already have 2 os's.  Rule of thumb is if you are going to install windows (even upgrade from xp to vista) you need to reformat and start fresh.  Windows gets very "protective" if you have more than 1 OS installed.

There are probably some guys that have done it in reverse order but there are a lot of technical details that you need to consider (of which I am not help to you).

If you need to recover files I would boot in with a live CD and try to copy as many files as possible onto an external drive and install xp, vista upgrade, then Ubuntu.

---

### Post by 500sd on 2008-04-27
Hmm but the thing is that I dont want ubuntu anymore :\

---

### Post by 500sd on 2008-04-27
any advice...?

---

### Post by forrestcupp on 2008-04-27
You haven't really described what you did very well.  From your first post, I couldn't tell that you don't want Ubuntu anymore.  I thought you just wanted to restore GRUB so you could get to either Vista or Ubuntu.

So did you format your Ubuntu partition to use for Vista?  Is Ubuntu still on your computer?  If you want to get rid of Ubuntu, just format the partition with Ubuntu on it as an NTFS drive.  You can use the [GParted Live CD](http://gparted-livecd.tuxfamily.org/) to delete that partition and create a new NTFS partition if you need to.  Then boot to your Super Grub CD and choose to restore the Windows boot loader.  It doesn't have an option for Vista, but the option to restore XP's boot loader will work; I've done it before.  Then you should be able to take your CD out and boot to Vista without having Ubuntu anymore.

Sorry Ubuntu didn't work out for you.

---

### Post by 500sd on 2008-04-27
Uh ok so what i want to do is get rid of ubuuntu and boot into vista normally.
According to your post, just to clear things up, what i should do is use that gparted thing to delete the ubuntu partition? Than restore my windows boot loader using super grub?

Hmm but i posted this somewhere else and this one guy said to do something with super grub disc. I did it and now whenever i turn on my comp the boot loader gives me options for ubuntu and xp...even though i cant load either of them

---

### Post by forrestcupp on 2008-04-28
Well, you just did the wrong thing with your Super Grub disk.  The primary purpose of Super Grub is to either have a CD based boot loader, or to fix GRUB.  But it also has other tools.

I don't have the very latest version, so I don't know if the menus have changed.  But in my version, in the first menu you choose 'Advanced'.  Then in that menu, you choose the 'Windows' option.  Then in the Windows menu, there is an option to 'Fix the boot of Windows'.  That is what you need to do to fix your Windows boot loader.  In my version of Super Grub, it doesn't include Vista, but choosing XP in the 'Fix the boot of Windows' tool worked for me back when I defected from Ubuntu.  But as you can see, I'm back now.

If I were you, I'd make sure to delete your Ubuntu partitions and format them as a new NTFS drive before you do the Super Grub thing.

---

### Post by 500sd on 2008-04-28
Ok I see now. 
So I delete my ubuntu partition using...the live cd that i have?  But the thing is I want that space from the ubuntu partition to go to my windows partition. So would it automatically get transferred to my windows after i delete the ubuntu partition?

---

### Post by 500sd on 2008-04-29
?

---

### Post by 500sd on 2008-04-30
Answer question please?

---

### Post by 500sd on 2008-05-01
...anybody

---

### Post by 500sd on 2008-05-02
Wow come on ?

---

