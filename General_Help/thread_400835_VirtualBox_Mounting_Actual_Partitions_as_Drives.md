---
title: "VirtualBox: Mounting Actual Partitions as Drives"
date: 2007-04-04
forum: General Help
---

### Post by fj34r on 2007-04-04
I am rather new to VirtualBox, and I'm already in love with it. I just had one question regarding the use of a Windows XP guest OS on a Ubuntu Edgy host OS.

I am looking for a way to 'mount' other partitions (NTFS partitions) as a seperate drive in the guest OS. The closest thing I could find to this was the option to add shares, but I couldn't get that to work for me. If anybody has a suggestion, it would be _greatly_ appreciated.

---

### Post by mertle on 2007-04-04
I had a little trouble in the beginning using shared folders, as well, but I finally got the hang of it. If I'm reading your question correctly, you want a similar setup that I have on mine.

1. Make sure you install Guest Additions on the guest OS. If you've tried to get shared folders to work, chances are you've already installed these.

2. Before firing up VBox, type this in a terminal:

```
$ VBoxManage sharedfolder add WinXP -name Stuff -hostpath /media/win
```

Replace "WinXP" with whatever you named your virtual hard drive and replace "/media/win" with the path to the partition you wanna mount. I used "Stuff" just as a reference name and I don't think the name you choose makes a difference.

3. Now boot up your guest OS and open up a DOS-like shell, typing this:

```
net use x: \\vboxsvr\Stuff
```

Replace "x:" with whatever drive letter you wanna use and "Stuff" with whatever you named it.

That should be it- if it says the command was successfully completed, yer good to go. Just open up My Computer and the drive should be listed as a network share.

Oh.. and as a warning- try not to save files within a program on the guest OS /to/ the network share drive. Some programs hiccup with that, but I'm using Windows 2000, not XP, so I dunno if it's a universal issue. For example, let's say you got PhotoShop open in your virtual XP and you wanna save the image you've been working on to the shared folder... I'd save it to the desktop and then copy it to the shared folder with the file manager instead.

Good luck!

- mertle

---

### Post by fj34r on 2007-04-04
Works beautifully my man.  I knew it would be possible to do this, but was a little confused on how to do it.  Thanks!

---

### Post by mertle on 2007-04-04
I'm so glad that it worked. You're very welcome. :)

- mertle

P.S.
I think ya mean, "Works beautifully, my wo-man." *giggles* Sorry, had to say it and be silly. :P

---

### Post by St. Coin on 2007-05-01
Glad I was able to find this thread, it helped me get access to my physical drive!

However, I get a blue screen of death in WinXP when I actually enter the drive through my computer. :( 

Any help would be much appreciated!

Edit: Strange, i'm no longer getting the errors.. So nevermind!

---

### Post by hums07 on 2007-11-20
Was about to post a query, then suggested to this thread by Ubuntu Forum. It works. Thanks :)

---

