---
title: "&quot;System is strange&quot; error with Museek"
date: 2005-07-25
forum: General Help
---

### Post by chazm on 2005-07-25
Museek is a program that connects to the SoulSeek network on Linux. It's located at: [museek.thegraveyard.org](http://museek.thegraveyard.org/).
I typed the *python scons/scons.py install* to start and then end up with the "System is strange" error.

Can anyone see if they can get it working? I'm currently on Windoze right now using the official client, which is pretty decent, but getting away from M$ is a high priority for me :)

---

### Post by Xian on 2005-07-25
Try this instead as a normal user:

$ python scons/scons.py

That should begin the configuration process.

---

### Post by chazm on 2005-07-25
[QUOTE=Xian]Try this instead as a normal user:

$ python scons/scons.py

That should begin the configuration process.[/QUOTE]

Ohh, so it's like I used *make install* before using make or configure? I'll try that when I boot to Ubuntu next. Hope it works, then I can delete Windoze :)

---

### Post by angkor on 2005-07-25
If you can't get it to work there's always nicotine.

```
sudo apt-get install nicotine
```


```
apt-cache show nicotine
[.......]
Description: graphical client for the SoulSeek peer-to-peer system
 Nicotine is a client for SoulSeek, a light and efficient file sharing
 system, written in Python and using the GTK2 toolkit, based on the
 PySoulSeek project.
 .
 It features uploading, downloading, searching and chatting, with
 strict bandwidth control, and tries to look like PySoulSeek.
 .
 URL: http://nicotine.thegraveyard.org/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by chazm on 2005-07-25
[QUOTE=angkor]If you can't get it to work there's always nicotine.[/QUOTE]

Yeah, I used it before. Not exactly to my liking though. But it would be good enough if Museek doesn't work. I want Museek because of the screenshots, lol.

---

### Post by angkor on 2005-07-26
[QUOTE=chazm]Yeah, I used it before. Not exactly to my liking though. But it would be good enough if Museek doesn't work. I want Museek because of the screenshots, lol.[/QUOTE]

:)

Ah, ok..well it get's the thing done.

---

