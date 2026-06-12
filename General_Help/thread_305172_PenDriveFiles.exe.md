---
title: "PenDriveFiles.exe"
date: 2006-11-22
forum: General Help
---

### Post by kondorman on 2006-11-22
I'm a writer and found a piece of software called yWriter to help organize story content. It's free software that was made for the Windows environment. However, there are instructions on how to run this software in the Linux environment.

My setup is: Pentium 4 laptop, Kubuntu 6.10, Wine 0.95

The instructions are as follows (to install this software with WINE) --

[I]Here's a more detailed set of steps of what worked for me: First, the Linux user should install Wine ([http://www.winehq.org](http://www.winehq.org)) or Cedega ([http://www.transgaming.com](http://www.transgaming.com)) which allow some Windows programs to be run within Linux/Unix systems.
Then, using Wine or Cedega, run yWriter.exe to do the setup as normal, but at the end of the setup, *uncheck* the option to run yWriter after install.
Then, use Wine or Cedega to run PenDriveFiles.exe and tell the installer to put the files in the C:\Program Files\yWriter2 directory.
With that, a Linux/Unix user should be set![/I]

Now, with KDE, I'm using the Krusader file browser in ROOT-mode to browse the directory. I've found the ".wine" directory in my home folder.

Following the installation instructions above, I installed the software. However, now I am looking to go to Step 2, which is to click on 'PenDriveFiles.exe'. That file is nowhere to be found anywhere on my drive. I've done a hard target search all through the ".wine" directory of my home folder and have not found anything. When I click on the executable file on my desktop (geesh, never thought I'd have to type that again) I get the following error:

**Unable to run the command specified. The file or folder file:///mnt/winc//Program Files/yWriter2/yWriter2.exe does not exist.**

Unsure how to proceed next. Any thoughts? Anyone come across this before?

](*,) :-k

---

### Post by creaturex on 2006-11-23
if that's the exact error, shouldn't it be looking in /mnt/wine not /mnt/winc? looks like a typo but I haven't seen any errors like that before. Perhaps you could try putting yWriter2,exe in that directory and see if it works.

---

### Post by gshoustionus on 2007-03-10
Hi, I'm a writer too, and I just got sonar working on linux as per the instructions. I was a bit stumped for pendrivefiles.exe, but I did a search, that's how I found this post.

You have to download pendrivefiles.exe from the same website as you got sonar2, Simon made it so that his programs will run off a memory stick. Stick the pendrivefiles in any directory and run it (from wine) to install: set the installation directory as the one which sonar2 is already installed into.

This is made easier if you use 'winefile' so you get a windows style explorer.

Hope this helps. if your still stuck email me, maybe I can help.

I'm not an ubuntu user, I'm a suse user, but that shouldn't matter, its all a wine thing.

Best regards,

Graeme Houston
[email]graeme@etheral.co.uk[/email]

---

