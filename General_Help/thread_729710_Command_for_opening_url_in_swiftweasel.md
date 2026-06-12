---
title: "Command for opening url in swiftweasel?"
date: 2008-03-20
forum: General Help
---

### Post by luisjorge on 2008-03-20
Hi!

I installed swiftweasel through automatix, and I have it as my default browser. I'd like to know if there is a command or something to put after the command for opening swiftweasel, so that when I click on a URL in openoffice, evolution, or something else, it opens swiftweasel in that url, and not just my homepage. 
Anyone know about this?

Thanks in advance!

---

### Post by keratos on 2008-03-20
for DESKTOP shortcuts, 

there should be a line in the /usr/share/applications/defaults.list file that associates the desktop entry with the mime-type (e.g., images/png=gthumb.desktop). 

then..

```

sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list.backup
sudo gedit /usr/share/applications/defaults.list

```
Add/change appropriate line to: 
```

mimeType=newApp.desktop

```
To figure out what newApp should be (if necessary): 
```

ls /usr/share/applications/*.desktop | sed -e "s@/usr/share/applications/@@g" | less

```
To figure out what mimeType should be (if necessary): 
```

find /usr/share/mime/ -mindepth 2 -maxdepth 2 -name "*" | sed -e "s@/usr/share/mime/@@g" -e "s@[.]xml@@g" | less

```
Restart Nautilus and the Gnome Panel: 
```

killall gnome-panel nautilus

```

Trouble is, you are refering to links in other apps. I think these may need a plugin to handle the links, but the above (albeit chaning the desktop for url links) might be a pointer?

---

### Post by ryanhaigh on 2008-03-20
System > preferences > preferred applications and change your web browser to swiftweasel.

---

### Post by sirancestor on 2008-03-20
Here is what worked for me:

System > Preferences > Preferred Applications

but there was no Swiftweasel there so I had to go for "custom" and in the "Command" box I wrote:

```
/opt/automatix/swiftweasel/swiftweasel -new-tab "%s"
```

that is if you want Swiftweasel to open your link from other applications in a "New Tab." If you want "New Window" you can just say something like:

```

/opt/automatix/swiftweasel/swiftweasel %s
```

---

