---
title: "Anyone tried this with Azureus ?"
date: 2005-07-20
forum: General Help
---

### Post by bored2k on 2005-07-20
Has anyone succesfully downloaded files via Azureus on a FAT32 partition through Linux, then being able to resume the download on Windows using Azureus? It would really be a cool thing if this were possible.

What about writing to a FAT partition? Any problems doing this?

Thanks in advance.

---

### Post by lol on 2005-07-21
[QUOTE=][/QUOTE]
 I never tried to resume a torrent from Windows (I did it with aMule/eMule though), but I am quite sure this is possible, and you should even be able to do it with another bittorrent client (you can start it with azureus, and finish it with ABC for example. As least, there is no problem doing this with 2 linux client).
Just remember to setup Azureus so that it will save the .torrent file on your FAT partition as well, it will make it easier to resume your downloads.

I never had any problem writing to a FAT partition. But I never tried to write files bigger than 2Gb either. As far as I know, this may be a cause of problem.

---

### Post by bored2k on 2005-07-21
[QUOTE=lol]I never tried to resume a torrent from Windows (I did it with aMule/eMule though), but I am quite sure this is possible, and you should even be able to do it with another bittorrent client (you can start it with azureus, and finish it with ABC for example. As least, there is no problem doing this with 2 linux client).
Just remember to setup Azureus so that it will save the .torrent file on your FAT partition as well, it will make it easier to resume your downloads.

I never had any problem writing to a FAT partition. But I never tried to write files bigger than 2Gb either. As far as I know, this may be a cause of problem.[/QUOTE]
 Hmm.. thing is I'm a little skeptical about it, but I guess I won't know for sure until I try it right ?
This is one of the things I hate the most, pause a torrent because I'm switching from OS. Guess I'll give it a shot first with my _not_ important torrents (Right now If I were to damage an 8gb torrent I have I would weep..). 

So resuming eMule from aMule files worked ? For future reference, that is really nice to know !

And by the way, I know you can resume torrent using different clients, but I tend to prefer leaving files started with Azureus alone. For  some reason, I have not had good experiences with this, but still, that's why we have different clients ;).

Thanks for the words of encouragement, "lol" :D.

---

### Post by t2kburl on 2005-07-21
I tried once with an Azureus torrent in Linux (I think I was using SuSE at the time) and resumed it with BitLord in windows. 

I don't recall exactly what happened, but I'm absolutely certain I had ro restart the torrent completely  :(

I have had no trouble at all writing to fat32 partitions

---

### Post by lol on 2005-07-21
[QUOTE=t2kburl]I don't recall exactly what happened, but I'm absolutely certain I had ro restart the torrent completely  :([/QUOTE]

That's really surprising... I don't see any reason why it would have to redownload everything, so I decided to try it and see can go wrong.

Conclusion: the test was *almost* a complete failure, because *almost* nothing went wrong.

I started a useless download (waited until I got 25Mb) with Azureus on Linux and tried to resume it with ABC on windows => it worked perfectly. I then waited for ABC to download a few megs and tried to resume with Azureus: again, *almost* no problem...

- The first time you resume the dl with the other client, you just have to be careful to save the file at exactly the same place, that's all.
- The *almost* above is because when I tried to resume the second time with Azureus, it didn't do a check on the file and continued to download from where it previously stopped. To avoid this, you should always do the following: Stop/Pause all your downloads before shuting down the bittorrent client. The next time you will start the client, select all your downloads and force a re-check. This way it will really resume from where the other client stopped. I had the problem only with Azureus, because ABC automatically recheck the file each time you start it.

> So resuming eMule from aMule files worked ? For future reference, that is really nice to know ! 

Well, the last time I tried this was about 1 year ago, but there is no reason it would have changed. On the other hand, there is now a Windows version of aMule, it may be better to use it. I remember seeing a post explaining how to share the aMule setup between Windows and Linux. IMHO, this is the best solution.

---

### Post by t2kburl on 2005-07-21
[QUOTE=lol]That's really surprising... I don't see any reason why it would have to redownload everything, so I decided to try it and see can go wrong.

Conclusion: the test was *almost* a complete failure, because *almost* nothing went wrong.[/QUOTE]

I probably just screwed something up somewhere along the line ...  however, I have done a bit of checking since the previous post and noticed that the BitLord incomplete files are all .bc! and the Azureus files all end in their original extentions. Probably why my experiment failed, and an indicator that Az -> Az would likely work.

My current downloads are WAY too big to risk any testing.

---

### Post by bored2k on 2005-07-21
[QUOTE=t2kburl]I probably just screwed something up somewhere along the line ...  however, I have done a bit of checking since the previous post and noticed that the BitLord incomplete files are all .bc! and the Azureus files all end in their original extentions. Probably why my experiment failed, and an indicator that Az -> Az would likely work.

My current downloads are WAY too big to risk any testing.[/QUOTE]
 Bitlord just like Bitcomet, makes your incomplete files have a .bc! extension. I don't know about BL, but with Bitcomet there is an option to remove this, -possibly- allowing this tow ork.

---

### Post by bored2k on 2005-07-21
[QUOTE=lol]Conclusion: the test was *almost* a complete failure, because *almost* nothing went wrong.
[/QUOTE]
Veery nice. I'm a happier kid now :D.

---

### Post by lol on 2005-07-21
> I probably just screwed something up somewhere along the line ... however, I have done a bit of checking since the previous post and noticed that the BitLord incomplete files are all .bc! and the Azureus files all end in their original extentions. Probably why my experiment failed, and an indicator that Az -> Az would likely work.

Ok, if BitLord has it's own file format, that would explain a lot.

bored2k, I just thought about something... Using Azureus on both Linux and Windows, you can probably share the setup folder (the same way it can be done for aMule). All you have to do is probably to create a link between .Azureus in your home and the Azureus folder on Windows. If this can work, it would make things a lot more easy (I believe that in this case, you wouldn't have to stop/recheck your downloads each time).

---

### Post by bored2k on 2005-07-21
[QUOTE=lol]Ok, if BitLord has it's own file format, that would explain a lot.

bored2k, I just thought about something... Using Azureus on both Linux and Windows, you can probably share the setup folder (the same way it can be done for aMule). All you have to do is probably to create a link between .Azureus in your home and the Azureus folder on Windows. If this can work, it would make things a lot more easy (I believe that in this case, you wouldn't have to stop/recheck your downloads each time).[/QUOTE]
 I'll try the regular load/resume first. As long as anything works, I'll be a happ-E man.

---

### Post by roman_PL on 2005-07-21
[QUOTE=lol]Ok, if BitLord has it's own file format, that would explain a lot. [/QUOTE]

Actually it's NOT different file format, its just an extra filename extension for files that are not completely downloaded...

Example:
ubuntu_hoary_hedgehog.iso.torrent - this is an torrent file...
ubuntu_hoary_hedgehog.iso - this is a file you will download (in Azureus for example)
ubuntu_hoary_hedgehog.iso.bc - this is same file as above but BitComet will rename it (add extension .bc) until it is 100% completed (and frankly speaking it's quite convenient - you just look into your download directory and see if any files are already done)

---

### Post by bored2k on 2005-07-21
[QUOTE=roman_PL]Actually it's NOT different file format, its just an extra filename extension for files that are not completely downloaded...

Example:
ubuntu_hoary_hedgehog.iso.torrent - this is an torrent file...
ubuntu_hoary_hedgehog.iso - this is a file you will download (in Azureus for example)
ubuntu_hoary_hedgehog.iso.bc - this is same file as above but BitComet will rename it (add extension .bc) until it is 100% completed (and frankly speaking it's quite convenient - you just look into your download directory and see if any files are already done)[/QUOTE]
 Yeah its just an extension, but still, you can't load it in azureus without removing it so you really don't have a smooth pause-resume using BLord or BComet.

---

### Post by GTvulse on 2005-07-21
As long as the bittorrent client doesn't try to create a sparse file, you will be fine. But heed the warning on force checking the torrents (the mainline client always checks the files at start up for that very reason).

Problems with sparse files are the reason behind Azureus allocating the whole file sizes when first creating the target dumps: FATxx filesystems do not support sparse files, only NTFS 5.x as seen in Win2K and later versions do, and some older versions of ReiserFS have terrible problems as well (and now that I think about it... Some UFS thinggamagicks do as well, older Solaris and BSDs me bleakly remembers). Yet, there is a problem with Linux's vfat driver that won't allow it to write to a fully allocated, zeroed file on a FATxx filesystem; don't know the technical reason.  it is not a problem under Windows. Azureus solves this problem by incremental file creation, which is not the default.

---

### Post by bored2k on 2005-07-21
I'll make this one short: It worked :D !

After I set up Azureus to incrementally allocate files and pointed the download to my FAT32 partition, it worked on both. I downloaded about 40megs on Linux then booted my to Windows XP and there it is,  happily downloading ^_^. BTW I set Windows' Azureus to use incrementel file allocation too.

I wanted to do this on a light client like BitTornado, but I couldn't get it to save, so I used the blue frog. No regrets, its working yippy no more "X downloads during Linux, Y downloads on XP" :D.

---

