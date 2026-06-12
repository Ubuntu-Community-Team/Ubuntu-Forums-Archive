---
title: "file location"
date: 2006-12-27
forum: General Help
---

### Post by squrl on 2006-12-27
Can someone please tell me where the email files are parked for kmail.

Thanks

---

### Post by dannyboy79 on 2006-12-27
not sure, why don't you do a find for them. use a terminal and do sudo find / -name subjectlinehere
use any subject line that you know of!! I know in xubuntu, evolution mail was kept in my home folder within a folder that was hidden. did you check in your home folder showing hidden files?

---

### Post by squrl on 2006-12-27
Thanks dannyboy.  I tried it but didn't find anything

---

### Post by squrl on 2006-12-27
Might be because I'm not sure what to show as what i'm trying to find.

---

### Post by dannyboy79 on 2006-12-27
ok, well what was the filename you used at the end of the find command? if you use kmail on your computer right now, then open kmail, then look in your inbox and read what one of the emails subject line is. once you know a subject line, then go back to the terminal and do the command again using one of the words in the subject line. or if there is a preferences tab in kmail, there has to be a setting for where your mail is stored. I know that I have that setting for my Splyheed mail client I use in Xubuntu.

---

### Post by RichBR549 on 2007-05-20
> **squrl said:**
> Can someone please tell me where the email files are parked for kmail.

Thanks

I use Gnome, Evolution in Ubuntu and Kmail with PCLinuxOS.  So my answer will be for Kmail in PCLinuxOS which is probably the same.

As someone said they are in a hidden folder in the users home directory.

Kmail is KDE so it is in my [COLOR="Black"]**/home/*username*/.kde/share/apps/kmail/mail/inbox/cur**[/COLOR]

Make sure in your file browser to enable viewing hidden files, if you want to see them.

Hope this helps,
Rich

---

