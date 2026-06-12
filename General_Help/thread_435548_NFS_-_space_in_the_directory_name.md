---
title: "NFS - space in the directory name"
date: 2007-05-07
forum: General Help
---

### Post by icpeanuts on 2007-05-07
Is there a way to exports a directory that have a space in the name ie: Download Files

I tried using the \, i tried putting " and ' in the whole path, then just the directory it does not work.. Please advise if there is a way to do it.. Thanks

---

### Post by kidders on 2007-05-08
Hi there,

This is from the man page for **exports**...
> If an export name contains spaces it should be quoted using double quotes. You can also specify spaces or other  unusual  character in  the export name using a backslash followed by the character code as three octal digits.

I hope that helps.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Jive Turkey on 2008-01-12
I'm puzzling over this one right now too.  
I've tried:
"/media/hda1/Documents and Settings" <ipaddress>(rw)
and 
/media/hda1/Documents" "and" "Settings <ipaddress>(rw)

also several variations of 
/media/hda1/Documents\040and\040Settings <ipaddress>(rw)

none of which work ;(

---

### Post by Spenzer4Hire on 2008-01-12
I'm no expert, but have you tried /media/hda1/"Documents and Settings" ?

---

