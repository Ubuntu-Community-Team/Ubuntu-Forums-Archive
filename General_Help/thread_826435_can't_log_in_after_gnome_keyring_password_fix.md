---
title: "can't log in after gnome keyring password fix"
date: 2008-06-11
forum: General Help
---

### Post by johnplov on 2008-06-11
I've been having problems with thepop up window for default keyring password.  I googled it and found a solution by Johnny Chadda from April 27, 2007.
I opened the terminal, typed in 
gksudo gedit /etc/pam.d/gdm
and then added 
@include common-pamkeyring
and saved it.

Hoping the problem would be solved, I tried to restart, but now when it gets to the point where I would log in, I get a pop up
that says authentification failed.  I don't get the opportunity to enter my name or password at all.  I would happily undo the fix and be back where I started, but I can't get into Ubuntu to do it.  Anyone have a way around this problem?

---

### Post by iaculallad on 2008-06-11
The problem maybe is that you did not delete the default.keyring file before you restarted your system.

```
rm ~/.gnome2/keyrings/default.keyring
```

Try to login using the restore mode and delete the file manually.

---

### Post by johnplov on 2008-06-11
Are you saying that I can go into recovery mode and edit the line out?  I am a newie at this and I can't figure out how to get from recovery mode to the place where I can edit the lines.  I run recovery and at the end in gives me the recovery menu: resume, dpkg, root, and xfix.  I haven't been able to figure out how to get to a point where I can do a line by line edit.

---

### Post by iaculallad on 2008-06-11
> **johnplov said:**
> Are you saying that I can go into recovery mode and edit the line out?  I am a newie at this and I can't figure out how to get from recovery mode to the place where I can edit the lines.  I run recovery and at the end in gives me the recovery menu: resume, dpkg, root, and xfix.  I haven't been able to figure out how to get to a point where I can do a line by line edit.

Yes you can. Try it.

---

### Post by johnplov on 2008-06-12
Are you saying that I can go into recovery mode and edit the line out?  I am a newie at this and I can't figure out how to get from recovery mode to the place where I can edit the lines.  I run recovery and at the end in gives me the recovery menu: resume, dpkg, root, and xfix.  I haven't been able to figure out how to get to a point where I can do a line by line edit.

---

### Post by johnplov on 2008-06-12
I still haven't found a way to log on.  I thought I had it by hitting Ctrl-Alt-F2 for a command line
I get "John Desktop Login:"
I then entered my user name and Got "Password:"
at that point I thought I was in, but it won't let me type anything after the colon.
I hit enter, and got "John@John-desktop: ~$"
It seemed like it should log in, but I just must be missing something.  Can anyone help me here.  I think once I get logged in I should be able to delete the line I added that caused the problem, but I just can't seem to get past the log in.
Thanks

---

### Post by molotov00 on 2008-06-13
You're logged in. You just don't have a GUI.

use "cd" to change directories, "ls" to list contents of the directories, and "nano filename" or "vim filename" to edit files. "rm filename" to delete files. if you get "permission denied" errors, prepend "sudo " to your command. read that again, and again, it should be everything you need, even if its all lowercase ;)

oh, and if you have any questioned about any commands:
commandname --help
or
man commandname

(in the terminal of course)

---

### Post by johnplov on 2008-06-14
I finally figured out how to delete the offending line that I had entered.  now I can log in normally again.  I still have the original problem of the keyring password window, but at least I can get around again. Thanks to iacullad and molotov00 for your help.
I learned quite a bit in just snooping around, but I have a long way to go. I feel like the scarecrow from the wizard of Oz- still no brains, but at least I have a diploma.
Thanks again

---

