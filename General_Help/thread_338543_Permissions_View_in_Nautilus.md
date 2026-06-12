---
title: "Permissions View in Nautilus"
date: 2007-01-14
forum: General Help
---

### Post by Buck2348 on 2007-01-14
I have Nautilus set to display file/folder permissions in octal.  The number is either 7 or 8 digits.  I understand the last four digits--they represent the standard numerical way to show permissions.  I'd like to know what the first four (or sometimes only three) digits mean.

Thanks,
Buck

---

### Post by Buck2348 on 2007-01-15
I'll try a bump.  I'm sure someone knows the answer.

Buck

---

### Post by Buck2348 on 2007-01-20
Another bump.  This has me stumped--I hate not knowing even though i realize it may not be of great importance.

Thanks,
Buck

---

### Post by maggotbrain on 2007-01-21
The first 3/4 digits are used to represent setuid,setgid, and sticky bits 

There is a nifty little chart here:
[http://binarios.com/lnb/shell.html]("http://binarios.com/lnb/shell.html")
wikipedia is your friend

see:
[http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation]("http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation")
and
[http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation_and_additional_permissions]("http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation_and_additional_permissions")

Hope this helps.

---

### Post by Buck2348 on 2007-01-21
Thank you very much for replying.

These articles talk about three or four-digit octal numbers, with the first digit (fourth from the right) representing the setuid, setgid, and sticky bits.  But my files and directories show either a **six or seven** digit number, e.g. 1600755 for a folder in my ~/ directory, and 600644 for a file.  (This is in a Nautilus window, with Edit --> Preferences --> Display Tab, and, under "Icon Captions, "Octal Permissions" selected in the first chooser.)  Can you tell me what the "160" and "60" (the leading digits in front of the last four) mean?

Thanks a lot,
Buck

---

### Post by Endolith on 2008-06-16
This system really couldn't be more obfuscated.  Nautilus should show little icons for permissions instead of codes.

---

