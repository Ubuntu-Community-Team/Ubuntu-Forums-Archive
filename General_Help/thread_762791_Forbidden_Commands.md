---
title: "Forbidden Commands"
date: 2008-04-22
forum: General Help
---

### Post by measekite on 2008-04-22
I read some replies that included a command that had **[COLOR=Red]-rf *[/COLOR]** in the reply.  I do not have a clue what this command means but some say that this type of command is [COLOR=Red]**banned**[/COLOR] in the forum.

Can someone explain :confused:why?

---

### Post by Catalyst2Death on 2008-04-22
these switches turn on recursion and forced removal of files if used with the rm command.  They asterix is a regular expression which matches all the files and folders in a directory.  If this command were run from the mount point: /  it would wipe the hard drive (you would need root privileges to do this)

---

### Post by lespaul_rentals on 2008-04-22
rm -rf * means force (-f) removal (rm) of all files (*), recursively (-r).  Very dangerous command, and some trolls were posting it as a "fix" to certain problems that newbies were having.  Although it is a prank that has the potential to be funny in certain situations, it has absolutely no place on an Ubuntu help forum.

---

### Post by IanW on 2008-04-22
As the above posters say, this is the Linux equivalent to getting someone to run "format c:" on a Windows box.

---

### Post by lespaul_rentals on 2008-04-23
> **IanW said:**
> As the above posters say, this is the Linux equivalent to getting someone to run "format c:" on a Windows box.

No, it's not.  Any somewhat modern version of Windows (starting with Windows 95 and possibly earlier) will not let you format the system drive while it is in use.  Go on, go into cmd and try to format your C: drive.

The Windows equivalent is:

```
del /s /f /q C:\*.*
```

---

### Post by enchantedsky on 2008-04-23
> **lespaul_rentals said:**
> No, it's not.  Any somewhat modern version of Windows (starting with Windows 95 and possibly earlier) will not let you format the system drive while it is in use.  Go on, go into cmd and try to format your C: drive.

The Windows equivalent is:

```
del /s /f /q C:\*.*
```

What he probably means is Microsoft's former operating system, MS-DOS, format c: would wipe out the hard drive. Later versions of MS-DOS and then Windows 95 made it harder to wipe out a hard drive using this method. But people back in the early 1990s used to trick others into running commands like this to wipe out your computer. Del and erase commands weren't as threatening, in my opinion.

---

