---
title: "Cincom Smalltalk Visual Works NC Net Installer"
date: 2007-09-08
forum: General Help
---

### Post by clarkburbidge on 2007-09-08
Dell Inspiron 530, Dell Inspiron 1420 both with Feisty 7.04

I was struggling getting this installed. For reasons explained better in this [COLOR="Green"]**[solution]("http://marc-abramowitz.com/archives/2006/10/09/the-trick-to-installing-cincom-smalltalk-on-ubuntu/")**[/COLOR], the net installer wasn't working. I had the same problem on my laptop so I think it is a software issue rather than a hardware one. 

On my laptop the install cd was recognized as containing an autorun component. No dice on my desktop. The cdrom mounted but all the files needed other permissions or mountings. Here is the error I was getting:
```
clark@dell:/media/cdrom$ sudo sh /media/cdrom/installUnix
exec: 45: /media/cdrom/vw7.5nc/bin/linux86/visual: Permission denied
The virtual machine for your platform:
    /media/cdrom/vw7.5nc/bin/linux86/visual
exists but cannot be executed.  The file system/CDROM containing
the virtual machine must provide execute permissions.
Please remount the file system/CDROM and try again.
clark@dell:/media/cdrom$ 

```

After following the instructions linked above I was able to use the Network Installer, but I'd still like to know why:

The cd didn't autorun on my desktop as it did on my laptop.
What all the permissions and remount stuff was about when I tried to manually sh the installUnix file.

---

### Post by clarkburbidge on 2007-09-08
To finish things off I needed to add this:
```

VISUALWORKS="/home/clark/vw7.5nc"
```

to this:
```

sudo gedit /etc/environment
```

---

