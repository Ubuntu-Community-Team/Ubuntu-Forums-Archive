---
title: "screen resolution messed up"
date: 2006-10-10
forum: General Help
---

### Post by Polygon on 2006-10-10
so, my friend just installed ubuntu recently

and he tried to change his resolution (from 1200x978 to 1200x1024) and when he restarted, he reports that his monitor spazzes out and starts flickering all crazy, and then the monitor says that the frequencies are not equal or something and to change the resolution.


Problem  is that he cant actually get a GUI, even in safe graphics mode or whatever

i told him to boot up, press alt+f1 to go to a termial, and told him to do "sudo dkpg-reconfigure xorg" or whatever that command was, and he says that xorg cant be found.

i also told him to edit /etc/X11/xorg.conf and replace his current one with a backup, but he says that its saying the file or directory does not exist

so... what now? im going to go over to his house and see if i can fix it manually rather then telling him to do it, but this is really weird that xorg does not seem to exist on his system....

---

### Post by Mr Frosti on 2006-10-10
The command you instructed him to run would be:

```
sudo dpkg-reconfigure xserver-xorg
```

For the monitor sync issue, just choose the "Basic" monitor configuration when it asks which level you would like to choose. It will ask for the monitor size, and calculate the rest automatically.

---

### Post by Polygon on 2006-10-10
i just went over to his house and manually deleted the 1200x1024 entry in xorg.conf... i guess he mistyped some command or something

thanks anyway

---

