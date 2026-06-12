---
title: "Some apps will not stay open!"
date: 2007-07-05
forum: General Help
---

### Post by osxdude on 2007-07-05
I moved my home folder to my NTFS hdd. I have it symlinked in the /home/ directory. Ever since then I have had problems with the following applications:

[LIST]
[*]Konsole (KDE Terminal Program)
[*]Gnash SWF Viewer
[*]X-Chat
[/LIST]

I'm sure there is other apps that I have missed.

Can anyone help?

---

### Post by meatpan on 2007-07-05
Can you give some more details about the problems?  Is there any error output?  Are the problems occuring consistently?

---

### Post by taurus on 2007-07-05
You cannot use ntfs filesystem for your $HOME due to permissions and ownerships.  It's not going to work.

---

### Post by osxdude on 2007-07-05
@meatpan: I have not tried in teminal: I will look at that now.

@taurus: Oh, but I have hacked it to da max to make it work. The ".dmrc" file message and this problem I am having are the only ones I have not cleared.

Edit: Here is the Konsole output in terminal. [http://paste.ubuntu-nl.org/28713/]("Click here") It seems /bin/bash/ is bad.

Edit 2: X-Chat's out is "Segmentation fault (core dumped)"

---

### Post by osxdude on 2007-07-05
Alrighty, I'm gonna make an ext3 partition on my second drive....let's hope it works.

---

### Post by osxdude on 2007-07-05
It did not work, but I did the command in terminal and it said to "chkdsk /f" in windows. One problemo: It says "Invalid parameter!" Gah!! Any help?

---

### Post by osxdude on 2007-07-09
Alrighty, I'm gonna bump the original question.

I moved my home folder to another ext3 partiton on my hard drive. I have the user folder in the user settings set to /media/disk/osxdude (/media/disk is the mount point). I have problems with the following applications:

[LIST]
[*]Konsole (KDE Terminal Program)
[*]Gnash SWF Viewer
[*]X-Chat
[/LIST]

I'm sure there is other apps that I have missed.

Can anyone help?[

---

