---
title: "Uptime applet for Gnome-panel?"
date: 2006-12-31
forum: General Help
---

### Post by Balaam's Miracle on 2006-12-31
I've been looking all over the net for an uptime applet that will sit in the Gnome panel but so far, i've only found an ancient (2002) version in the "oldstable" Debian repos and that's all i've found.
The problem with that version is that it has all kinds of dependencies on packages that have been fased out a long time ago and i do not know the consequenses of installing those old packages it depends upon. For all i know it can make my system seriously unstable.

I am specifically looking for a Gnome-panel applet. I already have GKrellm and GDesklets, but somehow the GDesklets won't play nice with Beryl on my system and using GKrellm just to monitor my uptime feels like using a Swiss army knife just to peel some potatoes.

So my question is if someone has ever updated [the old uptime applet]("http://packages.debian.org/oldstable/x11/uptime-applet") to work with current versions of Gnome. Or perhaps if someone has build a new one from scratch that would be awesome too because i really miss looking at my toolbar (erm... i mean panel) and see for how long my machine has been running since the last reboot...

---

### Post by Balaam's Miracle on 2006-12-31
Anyone? Please?

---

### Post by Balaam's Miracle on 2007-01-06
Hmm... The reactions have been overwhelming...

Anyway, in case someone else will ever have the same question as i had, i have made a little script that will do exactly what i wanted but not without much trial and error.
What this script does it it puts an icon in the panel, when moving your mouse over the icon, it shows the current uptime. To refresh/update the text, just click the icon.

```

#!/bin/bash
function uptim {
export UPT=`uptime`
    zenity --text "Uptime is$UPT" --notification
uptim
}
uptim

# Line-by line explanation:
# 1 - Set the shell to be used (if using Dapper, change this line to #!/bin/sh )
# 2 - define a function and call it "uptim" (without "e" so as not to not confuse
# things too much)
# 3 - Read the output of the 'uptime' command.
# 4 - Use Zenity to create a status icon (click to refresh!)
# 5 - Have the funtion call itself to keep the status icon in the tray.
# 6 - The accolade marks the end of the function.
# 7 - This line gets the script running. Doesn't work without it.

```

---

### Post by techamed on 2007-03-02
has anyone else been able to verify that this works?

EDIT:

Works nicely

---

### Post by yell0w on 2007-05-12
There's a very neat Gnome applet called GUTime that does just that thanks to Joseph Acosta:
[http://home.earthlink.net/~joseph-ja/programs.html#C-Gtk](http://home.earthlink.net/~joseph-ja/programs.html#C-Gtk)

First, install libpanel-applet2-dev and build-essential
Then, just get the GUTime-0.0.6.tar.gz file, "tar - zxvf" to untar it, then "make" and "make install" to put things where they should be, then maybe "bonobo-slay" to activate it.

Works perfect for me on Feisty Fawn. 
Cheers!

---

### Post by tgalati4 on 2008-01-23
If you have several machines on your network that you want to monitor, then install rwhod on each one (sudo apt-get install rwhod).

I've modified the script to use ruptime--to get the uptimes of several machines on the local network:

```


#!/bin/bash
function uptim {
export RUPT=`ruptime`
    zenity --text "$RUPT" --notification
uptim
}
uptim

# Line-by line explanation:
# 1 - Set the shell to be used (if using Dapper, change this line to 
#!/bin/sh )
# 2 - define a function and call it "uptim" (without "e" so as not to 
not confuse
# things too much)
# 3 - Read the output of the 'uptime' command.
# 4 - Use Zenity to create a status icon (click to refresh!)
# 5 - Have the funtion call itself to keep the status icon in the tray.
# 6 - The accolade marks the end of the function.
# 7 - This line gets the script running. Doesn't work without it.
```

---

### Post by didriksmidt on 2008-01-24
Thanks works great for me. Easy and great :)

---

