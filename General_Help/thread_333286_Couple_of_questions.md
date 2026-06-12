---
title: "Couple of questions"
date: 2007-01-07
forum: General Help
---

### Post by bash on 2007-01-07
Hello ubuntu community,

I have a couple of problems/questions. Hope they are not too noob for you :)

1. I installed truecrypt. Now I have some truecrypt partitions, actually hidden volumes, i created in windows. I manage to mount it to /mnt/. But then comes my problem. On windows there just appears a new drive and I can easily browse and access my files on the mounted volume. How can I do that on Linux? And I don't mean browse'em through the shell. I mean graphically through Nautilus

2. Got wine up and running. Does work all smooth. But one thing is buggin me. Some windows programs have tray icons. They used to be shown in the right corner of the upper gnome bar (next to the clock, the speaker button and so on). Now since a while they appear in a sepperate window on the desktop and not in the top bar anymore. Any way to get them back up there.

3. I use Evolution. Really great Outlook 2003 replacement which I used to use on windows (yes i know M$, but it has some features no other client has that way). But one thing I miss or haven't found out how to do is: In Outlook you can set a kind of a master password. So when you start up Outlook you have to enter this password or you can't use Outlook. Can this be done in Evolution as well? 

And Im runnin Ubuntu Edgy (6.10). Hope some of you can help me

Cheers

---

### Post by bash on 2007-01-07
Bumpage

And I got another question:

4. How can I print out of Microsoft Office. I installed Crossover Office and installed MS office. Office even displays the printe, but gives me an error if I try to print from it. Normally my printer works perfectly

---

### Post by bash on 2007-01-07
Anyone? :(

---

### Post by justifier on 2007-01-07
right, in no specific order

4/. try savign your files as either a PDF or as a .doc , if you are trying to print it from a windows computer, if you are trying to print from a linux computer to a windows printer you need to set up printers, thre are some how-too's somewher eon these forums

3/. im not 100% sure on how to do it, man chown might help, but try changing the permissions of evolution to root so that it asks for the root password, as if you were changing a setting.

2/. no, idea

1/. to view a directory and launch nautilus from terminal (shell). in terminal type nautilus <path> or sudo nautilus <path> for root permissions, you can also navigate to it normaly in nautilus 

hope this all helps

---

### Post by bash on 2007-01-08
ok:

1. Managed to open nautilis through sudo. But if I copy files out of the mounted directory, they are files "owned" by root. Tried to use sudo chmod on them, but I only managed to change the rights the root has. How can I "transfer ownership" from root to "me" the standard user?

2. Solved that

3. Looks complicated. But Im looking at it now.

4. I meant that I have MS Office installed in wine. So I can run it in Ubuntu. But now I want to print something out of the wine emulated MS Office. It shows the printer correctly, but it gives me an error when I try to print

---

