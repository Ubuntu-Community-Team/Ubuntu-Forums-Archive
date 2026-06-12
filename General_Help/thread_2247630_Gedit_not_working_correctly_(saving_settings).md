---
title: "Gedit not working correctly (saving settings)"
date: 2014-10-09
forum: General Help
---

### Post by james25 on 2014-10-09
Hello, I've got a server that I connect to over SSH and I'd like to use Gedit on it. This is what I did to install it:
```
apt-get install gedit
```
Now, I can get Gedit running okay with it's graphical interface but the graphics are basic as the whole desktop interface and whatnot is not installed. I'm fine with simple graphics. However, if I try to go into the settings to enable line numbers, disable autosaves and whatever else needs doing, it doesn't work. The settings simply go back to what they were as soon as I change the values. Tweaking the settings results in this message in the comand line:
```
(gedit:4963): dconf-WARNING **: failed to commit changes to dconf: Failed to execute child process "dbus-launch" (No such file or directory)
```

Is there anything I can do about this? It works fine with the desktop environment installed, but I don't want to do that 'cause it takes up a lot of space. Also, please don't give answers like "just use vi or edit locally" because that just won't help.

---

### Post by Habitual on 2014-10-09
Filezilla allows editing over your ssh connection (sftp protocol actually), but that will cause you to use gedit locally.
Maybe that is an option?

---

### Post by james25 on 2014-10-09
> **Habitual said:**
> Filezilla allows editing over your ssh connection [...] Maybe that is an option?
Filezilla won't connect to my server 'cause of my long password, but that's easily fixed. I've used it in the past so as long as you can save directly to the server with a quick ctrl+s, that should be something to try. Also, it won't have to constantly be sending graphics back and forth which should be a plus.

I'll leave this open for a little longer to see if any other suggestions come through. If not, this'll definitely do.  :D

---

