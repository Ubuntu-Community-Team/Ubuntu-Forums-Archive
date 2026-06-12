---
title: "knotes recovery after rebuild"
date: 2013-10-30
forum: General Help
---

### Post by madsmaddad2 on 2013-10-30
I have just rebuilt my system after  a reformat of the hard disk to remove the Dual boot XP portion. It was Kubuntu 13.04. and is now 13.10. 
I backed up my /home directory manually to my backup disk using Dolphin to copy the directories. 

I have managed to restore my Thunderbird emails and other things, but cannot find a way to restore my knotes. Can anyone help? 

Thanks,

---

### Post by Habitual on 2013-10-30
may be in a hidden (**.**) directory in the backup...
look for similar to these:
```
/home/jj/.local/share/notes
/home/jj/.kde/share/config/kresources/notes
/home/jj/.kde/share/apps/knotes/notes
```

Obviously you're name isn't "jj" so use yours in place of there. :)
You may have to show hidden files in your File Explorer|Manager using Ctrl+h

Once you find them, copy them back to your currently installed /home/<user> directory

---

### Post by madsmaddad2 on 2013-10-31
Done that. but knotes doesn't pick them up.

in .kde/share/apps/knotes/ notes are files such as:
[email]peterm@peterm-Kubuntu:~/.kde[/email]/share/apps/knotes/notes$ ls
libkcal-1134522767.1038  libkcal-1411340184.193  libkcal-1665423106.959  libkcal-949333107.526
libkcal-1222908312.351   libkcal-1574319463.535  libkcal-476407002.399
These are copied back from my backup.

But knotes doesn't pick them up. 

one level up is notes.ics:

[email]peterm@peterm-Kubuntu:~/.kde[/email]/share/apps/knotes$ cat notes.ics
BEGIN:VCALENDAR
PRODID:-//K Desktop Environment//NONSGML libkcal 4.3//EN
VERSION:2.0
BEGIN:VJOURNAL
DTSTAMP:20131030T194044Z
X-KDE-KNotes-BgColor:#ffffbd
X-KDE-KNotes-FgColor:#000000
X-KDE-KNotes-RichText:false
CREATED:20131030T161056Z
UID:libkcal-1411340184.193
LAST-MODIFIED:20131030T161056Z
SUMMARY:30/10/2013 16:10
END:VJOURNAL
BEGIN:VJOURNAL
DTSTAMP:20131030T194044Z
X-KDE-KNotes-BgColor:#ffffbd
X-KDE-KNotes-FgColor:#000000
X-KDE-KNotes-RichText:false
CREATED:20131030T193728Z
UID:libkcal-949333107.526
LAST-MODIFIED:20131030T193728Z
SUMMARY:30/10/2013 19:37
END:VJOURNAL
END:VCALENDAR

---

### Post by madsmaddad2 on 2013-10-31
Mark this one as  fixed. 

I edited the file notes.ics as shown above with the contents of the notes.ics file from my backup keeping only the first three lines as shown above. All the sections marked with a BEGIN:VJOURNAL to END:Vjournal I copied from the backup and pasted into the 'current'  file, then stopped and started knotes and they were there. Note that I had copied all those libkcal-xxxx files across first. 

I am a happy bunny, now can I have a nice cup of coffee?

P.

---

