---
title: "EXE File Associations with Wine"
date: 2007-02-26
forum: General Help
---

### Post by graphicw on 2007-02-26
I am having problems being able to double click a Windows Executable through Konqueror to start it.  I have already tried right clicking the file and adding typing wine as the application to start with.  I still cannot perform a double click to start the file despite the effort.

I ran Konqueror out of the terminal to attempt to determine what the issue was.  Here is what I get when I double click on an exe file:

```
/media/cdrom0/setup.exe: 1: MZ@: not found
/media/cdrom0/setup.exe: 2: Syntax error: word unexpected (expecting ")")
```

Just looking for any help that I can get with this matter.  Thanks ahead of time.

---

### Post by nereid on 2007-02-26
Sometimes the exe files need you to be in their directory so have you tried this?

```

cd /media/cdrom0
wine setup.exe

```

---

### Post by graphicw on 2007-02-26
Thanks for quick reply.  Wine works perfectly out of the terminal.  No issue at all.  The problem is that I desire to be able to double click from Konqueror to execute the file.  I am also trying to get the autorun feature on the CD's to operate as well.

---

### Post by nereid on 2007-02-26
Ok, right click on an exe file in Konqueror. Goto Properties and then click on the little icon at the right (still being in the first tab) right from the "Type: Windows-Application". In the new window there should be an entry like "Wine Windows Emulator", click on it and edit it. In the Program tab there should be the command to start wine (something like "wine %f").

Supported file types should be application/x-msdos-program.

---

