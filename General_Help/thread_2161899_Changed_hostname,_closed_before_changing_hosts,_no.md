---
title: "Changed hostname, closed before changing hosts, now sudo is broken, catch-22!"
date: 2013-07-12
forum: General Help
---

### Post by begtognen on 2013-07-12
[COLOR=#333333][FONT=UbuntuRegular]I'm using Lubuntu 12.04.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I was trying to change my computer name to "main" and I messed up, I'm not sure what to do now.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I was following the directions on [this page]("http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-change-your-computer-name/").[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Here's what I did:[/FONT][/COLOR]

[FONT=courier new]sudo leafpad /etc/hostname[/FONT]
[COLOR=#333333][FONT=UbuntuRegular]
I changed the name, then stupidly closed the file, *before* changing "/etc/hosts"[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Now when I try to move on to the next step (sudo leafpad /etc/hosts), or try any command that begins with "sudo" I get this error:[/FONT][/COLOR]

[FONT=courier new]sudo: unable to resolve host main
No protocol specified
No protocol specified[/FONT]
[COLOR=#333333][FONT=UbuntuRegular]
I can see that the problem is that I've changed the hostname, so the computer's bewildered by my efforts to use sudo because now hostname and hosts don't match. All I need to do is change the name in hosts, but of course I can't do that without sudo.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
Any ideas?
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]And if there isn't a way to fix it, reinstalling Lubuntu 12.04 will work, yes?[/FONT][/COLOR]

---

### Post by steeldriver on 2013-07-12
You should be able to fix it from the recovery console, you will need to remount the filesystem with rw permissions and then use a commandline editor e.g. after dropping to the root shell,

```

# mount -o remount,rw /
# nano /etc/hosts

```

and make your changes... Ctrl-o to save and Ctrl-x to quit

--> [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by begtognen on 2013-07-12
Thank you so much! This worked a treat.

---

