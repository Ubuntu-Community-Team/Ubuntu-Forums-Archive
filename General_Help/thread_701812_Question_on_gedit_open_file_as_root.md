---
title: "Question on gedit open file as root?"
date: 2008-02-19
forum: General Help
---

### Post by cpthk on 2008-02-19
In text editor in ubuntu desktop, gedit, is there any way to do like in windows vista to open file as root. Everytime I finish edited a file, then I press save, it gives me an error saying no permission to save. I understand that in text mode I can do chmod or sudo. But regular users don't know. How do I open text file and do sudo save?

Thanks.

---

### Post by Crooksey on 2008-02-19
```

sudo gedit /path/to/file
```

---

### Post by seventhc on 2008-02-19
should use gksu with gedit..example:
```
gksu gedit /boot/grub/menu.lst

```

---

### Post by erfahren on 2008-02-19
actually it should be (EDIT: seventhc is correct as well):
```

gksudo gedit /path/to/file

```
use gksudo when it's a GUI application you're launching. ("sudo" *will* work for Gedit, but it's a good habit to get in to - some GUI applications can have problems with just using "sudo".)


**cpthk** - there really isn't a way (that I know of) to open a system file with Gedit as a regular user and then (through the GUI) save it as root (or superuser). I think that's what you're asking.

What you can do however, is launch Nautilus (the file browser) as superuser - browse to the file you want to edit and open it with privledges. (Be careful when you do that though!) - to do that, open up the run command with Alt+F2 and enter "gksudo nautilus" - you'll get a new file browser window with root privledges. You can then do whatever you want (again though, be careful!!!)

---

### Post by seventhc on 2008-02-19
you can open a file system with vim, it isn't gedit but it is an editor. :) **Edit:** I mean open a directory with vim
for vim you would use sudo
vim will open them as a normal user too but it wouldn't allow editing of system files unless you use sudo.
I use gksu for anything with a gui but I use gksudo nautilus b/c gksu gives strange output in the terminal when used with nautilus.

---

### Post by erfahren on 2008-02-19
oh - I wanted to mention - there is a great little application called "nautilus-open-terminal" - I don't think Ubuntu Gutsy has something like it by default.

what it does is puts a option in the right-click context menu to open a folder in the terminal. So to open the /boot/grub/menu.lst file, instead of typing in "sudo gedit /boot/grub/menu.lst" you can just browse to the /boot/grub directory and right-click on it and "Open in terminal". The working directory in the terminal would be /boot/grub

It comes in real handy! (Xubuntu 7.10 has something like it by default) - check it out! 

search Synaptic for it - or just
```

sudo apt-get install nautilus-open-terminal

```

---

### Post by oldos2er on 2008-02-19
> **erfahren said:**
> oh - I wanted to mention - there is a great little application called "nautilus-open-terminal" - I don't think Ubuntu Gutsy has something like it by default.

what it does is puts a option in the right-click context menu to open a folder in the terminal. So to open the /boot/grub/menu.lst file, instead of typing in "sudo gedit /boot/grub/menu.lst" you can just browse to the /boot/grub directory and right-click on it and "Open in terminal". The working directory in the terminal would be /boot/grub

It comes in real handy! (Xubuntu 7.10 has something like it by default) - check it out! 

search Synaptic for it - or just
```

sudo apt-get install nautilus-open-terminal

```

 Or install nautilus-gksu, then right-click on a file and choose 'Open as administrator.'

---

### Post by NineseveN on 2008-02-19
Unless I'm missing something...just try this:
[http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/](http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/)

You'll have to know beforehand if the file you're editing needs sudo to edit, but that shouldn't be too hard to figure out (system files and such) as your regular text documents shouldn't require sudo.

---

