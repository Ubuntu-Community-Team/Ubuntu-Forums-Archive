---
title: "Recovering Ubuntu 10.04 w/ Lubuntu 12.04 Live CD"
date: 2012-11-04
forum: General Help
---

### Post by ndm13 on 2012-11-04
AskUbuntu really hasn't been helpful with this at all, so I thought I'd try asking here.
[Question on AskUbuntu]("http://askubuntu.com/q/211517/104276")

Text of question:


My younger sister's computer suffered some major problems recently.  The  BIOS corrupted and attempted to load Ubuntu 10.04 in a way it shouldn't  have.  I'm not sure of the exact details, but the computer wouldn't  start.  Anyway, I put the drive in a new computer and attempted to  recover it with a Lubuntu live CD.  When I access her root folder on the  mounted drive, it tells me I can't.  What do I do?  I'm not that  experienced with Linux.

What's the specific error message? &#8211; [ObsessiveSSO&#8498;]("http://askubuntu.com/users/54298/obsessivesso") [20 hours ago]("http://askubuntu.com/questions/211517/recovering-ubuntu-with-lubuntu-live-cd#comment262536_211517")
                                
Error opening directory '/media/lubuntu/string-of-numbers/home/user' Permission denied. &#8211; [ndm13]("http://askubuntu.com/users/104276/ndm13") [20 hours ago]("http://askubuntu.com/questions/211517/recovering-ubuntu-with-lubuntu-live-cd#comment262541_211517")



Any help would really be appreciated.  Thank you so much.

---

### Post by black veils on 2012-11-04
only thing i can offer here, is try ```
gksudo pcmanfm
``` to open the lubuntu file manager with root permissions, and see if you can access the files.

maybe the drive is dying.

Edit:

i'm having a dopey moment, but shouldnt the path be /media/the drive(string of numbers)/home/user

---

### Post by ndm13 on 2012-11-04
> **black veils said:**
> only thing i can offer here, is try ```
gksudo pcmanfm
``` to open the lubuntu file manager with root permissions, and see if you can access the files.

maybe the drive is dying.

Edit:

i'm having a dopey moment, but shouldnt the path be /media/the drive(string of numbers)/home/user
Thank you for a prompt (relatively) response!  Much better help here.

I will try that.  I have to boot the computer again.  I'll get back with the results.

And I thought I copied the line off the screen correctly.  Maybe Lubuntu mounted the drive weird or something, but it was definitely the drive in the computer.  An I did use an old drive in the computer, so after I recover the files, I'll try a different drive.

Thanks again!

---

### Post by ndm13 on 2012-11-04
I've been able to open /media/lubuntu/string-of-numbers/home/user (which does seem to be the right dir) and it contains a message saying this data has been encrypted.  It says I can click a link to unprotect it and make it visible, but it doesn't seem to be working, maybe because of a difference in file managers?  It also gives command line code that doesn't seem to do anything.

Text of notice:
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

For the graphical desktop, click on:
"Access Your Private Data"

or

From the command line, run:
encryptfs-mount-private

I don't know what to do.  Any help?

---

### Post by ndm13 on 2012-11-04
I found an old copy of Ubuntu 10.04 and used it to repair Ubuntu.  Evidentally there was an issue with GRUB and an issue with the graphics settings being set wrong (from the previous system).  From there I recovered the files.  I'm still going to put Lubuntu 12.04 on in lieu of Ubuntu because it runs significantly faster.

Thanks for your help!

---

