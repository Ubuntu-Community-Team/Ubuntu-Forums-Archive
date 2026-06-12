---
title: "Editing .ini file with vim command - Some Queries"
date: 2013-03-18
forum: General Help
---

### Post by StevieTNZ on 2013-03-18
Hi there,

I am completely new to using Lubuntu (version 12.10 x86 alternative version). I am familiar with Windows interfaces but I see Linux is, in respect to installing/configuring programs, command based.

The instructions to change host from 127.0.0.1 to 0.0.0.0 (to allow remote access) is to run "sudo vim /etc/schooltool/standard/paste.ini" in the command terminal. Apart from getting messages saying vim was not a command, I managed to install the necessary program/files to make it so.

All good; I run the above command and get a box with the content of paste.ini. I press the Insert key to replace the host IP. But from thereon I have no clue how to save that. I see no save option under File (or any menus at the top of the window). When it comes to reopening the file with "sudo vim...." the host has retained what it was before: 127.0.0.1. This also occurs after restarting the schooltool service.

How do I enforce the changes I make to the host so that they stick?

Many thanks,
Stevie

---

### Post by steeldriver on 2013-03-18
- hit the ESC key (to get you out of insert mode)

- type : (colon - to get to the vim command line)

- type wq (**w**rite and **q**uit)

... or you could just use nano, or since you presumably have the lubuntu desktop, use a graphical editor 

```
gksudo leafpad /etc/schooltool/standard/paste.ini
```

---

### Post by Impavidus on 2013-03-18
If you want to use vim you'll have to learn it. Here is an excellent although somewhat verbose manual, the size of the manual reflecting the feature set of the program: [ftp://ftp.vim.org/pub/vim/doc/book/vimbook-OPL.pdf](ftp://ftp.vim.org/pub/vim/doc/book/vimbook-OPL.pdf)

If that's to much for this moment, stick to the graphical editors like **leafpad** or **gedit** (if you need root permissions start from the command line with **gksudo leafpad**, **gksudo gedit**) or try **nano** (if you need root permissions **sudo nano**). Pay attention to the difference between sudo and gksudo. Use gksudo to start graphical programs: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

