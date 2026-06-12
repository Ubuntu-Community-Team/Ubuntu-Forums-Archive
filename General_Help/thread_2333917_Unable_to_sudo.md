---
title: "Unable to sudo"
date: 2016-08-14
forum: General Help
---

### Post by wjbmd48 on 2016-08-14
hi:

in the course of editing a new file in the /etc/sudoers.d, i created a new script, networkrestart

i now find i can't sudo, i get this,


>>> /etc/sudoers.d/networkrestart: syntax error near line 1 <<<
sudo: parse error in  near line 1
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin


and, of course, since i can't sudo, i can't delete this file that i named networkrestart.

is there a way around this?

thanks!


bill

---

### Post by sisco311 on 2016-08-14
Yes, you can use *pkexec* to run another command as root in the same way you would use sudo.

```
pkexec mv /path/to/file1 /path/to/file2
```

Next time you edit the sudoers file(s) you should use visudo. See: [uhelp]community/Sudoers[/uhelp]

---

### Post by wjbmd48 on 2016-08-14
thanks, but no joy:

pkexec leafpad

leafpad: Cannot open display: 



or, 

pkexec nautilus

Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(nautilus:3895): Gtk-WARNING **: cannot open display:

---

### Post by wjbmd48 on 2016-08-14
ah, Ok, i see: pkexec su gets me in to directory as root, and from there i deleted the offending file.

Outstanding!

Thanks again,

Bill

---

### Post by sisco311 on 2016-08-14
Oh, pkexec, by default, does not allow you to run whatever X11 applications as another user or root.

You either remove the file with rm or edit it with a CLI editor (visudo defaults to nano in Ubuntu if memory serves):
```
pkexec visudo -f  etc/sudoers.d/networkrestart
```

In nano press Ctrl+o to save the file then Ctrl+x to exit.

---

### Post by sisco311 on 2016-08-14
> **wjbmd48 said:**
> ah, Ok, i see: pkexec su gets me in to directory as root, and from there i deleted the offending file.

Outstanding!

Thanks again,

Bill

Cool and you're welcome!

---

