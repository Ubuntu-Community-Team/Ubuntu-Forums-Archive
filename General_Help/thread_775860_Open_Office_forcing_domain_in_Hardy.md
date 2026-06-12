---
title: "Open Office forcing domain in Hardy"
date: 2008-04-30
forum: General Help
---

### Post by j00b on 2008-04-30
Problem summary:
Open Office locks the work group as "MSHOME". As a result I cannot open files from a different domain.

User Steps:
1) Connect and authenticate to a samba share using a different domain than "MSHOME"
2) Double click a file that opens automatically in Open Office
3) Open office prompts for an additional username and password: "Please enter user name and password for "MSHOME" on $DIRNAME here."

As a contrast, in Gusty I was able to open the file without additional authentication. However, if I left the file open too long without saving, the same message would appear and I would have to cancel and then use "Save As" to save my file. Perhaps Hardy's behaviour is "better" since it is now consistent, however it has the draw back that I can no longer use files on samba shares with Open Office.

Is there a way I can change the assumed domain for OpenOffice?
Is a certificate not being passed properly from Nautilus to OpenOffice?

Thanks for any help you can offer.

---

### Post by j00b on 2008-05-01
Just thought I'd document the odd fix I found to this problem.

I was having trouble attaching files from windows shares in Evolution as well, even though I could browse the folder structure. [I should note that I was able to do this previously in Gutsy] So it seemed it was a related permissions issue, where authentication wasn't being passed from Nautilus to secondary programs. 

As a test I tried opening an image on the windows share with the default Gnome program and was prompted to use the Key Ring associated with that directory. After clicking "yes" multiple times, the pop up went away and I was able to view the image. This opened the door to let the other programs have access as well.

So if anyone is having trouble with Windows share permissions, but can use Nautilus to view the directory structure, try opening a single file with a program that properly prompts for updated permissions.

To Hardy's credit, I use Windows shares extensively since I work in a Windows environment, and my initial impression is that Hardy is much snappier when browsing Windows network drives.

---

### Post by jaburr on 2008-05-09
I can verify that I ran into the same thing.  Same fix worked.  Still cost a half-hour of head-scratchin'.  Thanks for the tip!!

JB

---

