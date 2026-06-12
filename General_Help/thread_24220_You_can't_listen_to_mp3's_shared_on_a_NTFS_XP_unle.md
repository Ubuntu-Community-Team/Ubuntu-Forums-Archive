---
title: "You can't listen to mp3's shared on a NTFS XP unless you download it?"
date: 2005-04-05
forum: General Help
---

### Post by Francisco on 2005-04-05
I was wondering, I have tried to listen or add a bunch of (approx 6Gb of songs) into my media player, but it seems like I can't play it remotely, but I have to download it to my linux computer (will use as double space, I use my windows for work and I have three years of songs there...)

 Do any of you know if this is supposed to be this way?  :-s 

thanks

---

### Post by shof2k on 2005-04-06
I'm not sure what you mean.  Do you have a dual boot computer with a linux and NTFS partition?  If so, you can mount your NTFS partition and play mp3's from there.

If you have another XP computer then you'll need to share your NTFS drive, and set up SAMBA on your linux computer.

Let us know and we'll give you more help

---

### Post by bonifacio on 2005-04-06
Yes you need to mount it up first, check the ubuntu starter guide on how to do this.  Coincidentally it is also the same if you are trying to open up say an office document (on a remote location) with Oo.

---

### Post by Francisco on 2005-04-06
[QUOTE=shof2k]I'm not sure what you mean.  Do you have a dual boot computer with a linux and NTFS partition?  If so, you can mount your NTFS partition and play mp3's from there.

If you have another XP computer then you'll need to share your NTFS drive, and set up SAMBA on your linux computer.

Let us know and we'll give you more help[/QUOTE]

 Hi,

 What I ment is that a network Windows Server is sharing files thru Samba but I cannot open them remotely on my linux PC, I have to download it for it to work.........

---

### Post by shof2k on 2005-04-06
I don't know alot about SAMBA, but this sounds like a permissions issue.  Make sure you you have read, and execute access on your share

It would be helpful if you can show what command you use to mount and your fstab entry if you use that.  Also see who is the owner / group of that share?

Keep at it....

---

### Post by Francisco on 2005-04-06
[QUOTE=shof2k]I don't know alot about SAMBA, but this sounds like a permissions issue.  Make sure you you have read, and execute access on your share

It would be helpful if you can show what command you use to mount and your fstab entry if you use that.  Also see who is the owner / group of that share?

Keep at it....[/QUOTE]

 Hmm, I don't know how permissions work on windows, but the shared folders are public (not password protected to other windows users).

 I tried to do this remotely without mounting the partition with smbfs, should I do it? If a new file is created on the virtual machine will it show up instantly once mounted?

Thanks

---

### Post by bonifacio on 2005-04-06
You need to mount it first.  Otherwise you will always have problem with its URL.  You will notice that it tries to append the remote location to your $HOME.

I think the offending URL will look like this: (example only adjust the environment variable accordingly)
[INDENT]file:///$HOME/smb://$HOSTNAME/$SHARENAME/$SOMEFOLDER/your.mp3[/INDENT]

The correct one should be:
[INDENT]file:///$MOUNTNAME/$SOMEFOLDER/your.mp3[/INDENT]

That is after you have mounted the remote location successfully.

---

### Post by Francisco on 2005-04-06
[QUOTE=bonifacio]You need to mount it first.  Otherwise you will always have problem with its URL.  You will notice that it tries to append the remote location to your $HOME.

I think the offending URL will look like this: (example only adjust the environment variable accordingly)
[INDENT]file:///$HOME/smb://$HOSTNAME/$SHARENAME/$SOMEFOLDER/your.mp3[/INDENT]

The correct one should be:
[INDENT]file:///$MOUNTNAME/$SOMEFOLDER/your.mp3[/INDENT]

That is after you have mounted the remote location successfully.[/QUOTE]

 Ok, I mounted it and now works :)

---

