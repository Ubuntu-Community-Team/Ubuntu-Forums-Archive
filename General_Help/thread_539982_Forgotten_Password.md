---
title: "Forgotten Password"
date: 2007-08-31
forum: General Help
---

### Post by j01101111sh on 2007-08-31
So heres the deal, i am a high school student and I am fairly knowledgable about linux, unix, etc.  My computer science teacher installed Edubuntu on a spare machine he had in the lab and has since forgotten the password to the administrator account.  He doesn't know very much about linux so i offered to help him fix the machine.  I booted into recovery mode, and i ran ```
/usr/bin/passwd facilitator
```
(Facilitator is the account created at install) But when i enter in the new password and re-enter it, it gives me an error saying something along the lines of "Authentication Lock Busy".  I've done this a couple different times with a reboot in between each attempt but every time it's the same error.

Any help you could give me would be greatly appreciated by myself as well as by my computer science teacher.

---

### Post by merlinus on 2007-08-31
Try this, because you cannot retrieve your password but can reset it.

At the grub menu choose recovery mode. This will log you into a terminal as root.

to find out your username:

```

ls /home

```to set a new password:

```

passwd your_username

```then reboot via

```

reboot

```-merlin

---

### Post by j01101111sh on 2007-08-31
Well, i did that, but i get an "Authentication Lock busy" error.  I don't know what that means or how to get around it.

---

### Post by merlinus on 2007-09-01
A workaround would be to create a new account, and then give that user admin privileges.

Then the contents of /home[COLOR=black]/faciitator can be copied to the new/home/user folder.
[/COLOR] 
-merlin

---

### Post by meierfra on 2007-09-01
I googled  "authentication lock busy passwd" and the solution seems to be:


```
mount -o remount,rw /
```

(Type that this in recovery mode  before your do "passwd")

The links I looked at:

[http://forums.fedoraforum.org/archive/index.php/t-92959.html]("http://forums.fedoraforum.org/archive/index.php/t-92959.html")

and

[http://bliki.rimuhosting.com/space/start/2007-04-02/1#Remount_/_]("http://bliki.rimuhosting.com/space/start/2007-04-02/1#Remount_/_")

---

