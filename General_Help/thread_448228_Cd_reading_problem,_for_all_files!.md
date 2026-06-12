---
title: "Cd reading problem, for all files!"
date: 2007-05-18
forum: General Help
---

### Post by A2cO on 2007-05-18
Hi!
I have a big problem, i'm new to linux.
EVERY cd rom or dvd i try to browse, i get an error windows from ubuntu:

[http://img406.imageshack.us/my.php?image=screenshot1zi7.png](http://img406.imageshack.us/my.php?image=screenshot1zi7.png)
(sorry but i'm italian)  :)

...who says that  the file i'm trying to open is a "simple text file document",  so for security risk is not possible the view of that one.
is the same situation with ALL files on my dvd/cd (mpg, avi, jpg etc.).
then i try to copy-paste these files on my  desktop,  but after the same advice,  the result is an Input/Output error...
i try to open my cds on win aand they are all readable under this os!

so,  what's the problem in your opinion?
i'm waiting to  erase win from my  pc, but as i can't read my backup cds from linux, i can't do that!

anyone can help me, please?
thanks a lot and sorry for bad english :)

ps.  i'm running ubuntu feisty, tuned up with ubuntustudio!

---

### Post by GhostZrydA on 2007-05-18
Try going into the terminal (Applications/accessories) then using the "sudo nautilus" command (without the quotes).

Then navigate to the cdrom folder from their and try copy/paste again.

Since you may not have root access to the drive.

GhostZrydA

---

### Post by A2cO on 2007-05-18
GhostZrydA thanks for the help!
but with sudo nautilus the problem is the same, the format is not recognized! could be an hardware problem?

---

### Post by mdurham on 2007-05-19
Many people have this problem including me. I can see a VOB file and click on it, the icon and filetype changes to text and I can't read the file.
It's some weird driver error (I think!). Anyway there are many reports about this in Bug #94119. Take a look and add to the list.
I sure hope they fix it soon as it's a real pain having to boot into Edgy just to read a CD. I had an email from the Ubuntu_devel_mail_list talking about a 'world class OS' I think they have to fix this basic sort of problem before they can even think of writing words like that!
Cheers

---

