---
title: "Trouble getting xrdp working"
date: 2024-02-08
forum: General Help
---

### Post by p4rdner on 2024-02-08
I have a mostly fresh install Ubuntu 22.04 on a remote computer. I plan on using the Ubuntu computer as a workstaion and will mostly be using ssh, but sometimes I would like to use a GUI. I installed xrdp and tested it and it worked (*slowly*). Rebooted the computer and now I cannot start a Xsession. 

I am remoting in from a Win11 machine. Upon connecting to the Ubuntu computer I am greeted with the Xrdp login screen:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293396&stc=1[/IMG]

But after entering my username and password I am greeted with this error:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293397&stc=1[/IMG]

```
Xsession: unable to start X session --- no "/home/brett/.xsession" file, no "/home/brett/.Xsession" file, no session managers, no window managers, and no terminal emulators found; abouting.
```

I tried purging and installing the xrdp package, but I still get the above error.

I know I screwed something up, any help would be fantastic.


EDIT: cool, my first post after luking for 13 years..... and its because I screwed up the gnome dependencies (python3 maybe). Reinstalled gnome and everything is fine. Guess its hard to start a remote desktop when you done have a desktop manager installed huh!

---

### Post by umangwah67 on 2024-02-09
hi
reinstall GNOME or necessary desktop managers, it will certainly resolve issue you're facing.

---

### Post by ActionParsnip on 2024-02-09
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

