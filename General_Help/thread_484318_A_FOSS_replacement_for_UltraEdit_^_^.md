---
title: "A FOSS replacement for UltraEdit ^_^"
date: 2007-06-25
forum: General Help
---

### Post by kung fu buntu on 2007-06-25
When you get used to something it's hard to let it go, so I just though some of you might want to know that there is an alternative.

What I liked the most in UltraEdit was the **ability to (handle and) switch between text and hex edit mode** with just one keyboard shortcut.

This editor also has other features such as:
- **cycle through open files using ctrl+tab**
- **column edit mode**
- **shortcut for word wrap mode**
- **open multiple files using drag-and-drop**
Unfortunately it has **no support for macros** :-(

This FOSS gem is **[MadEdit ]("http://madedit.sourceforge.net/")**
If you're building remember to: "apt-get install" libwx*-dev, libboost*-dev, libglib*-dev, libgtk2*-dev

Another thing I liked in UltraEdit was that I could right click on a file and click 'U' for it to open in UltraEdit.
I do not know how to do this, but I know something close **for KDE**:
nano /usr/share/apps/konqueror/servicemenus/edit.desktop
```

[Desktop Entry]
Actions=Edit
ServiceTypes=all/allfiles

[Desktop Action Edit]
Name=Edit File
Icon=madedit
Exec=madedit %F
```
Now, **right click on a file, "Actions", "Edit File"**


**What this setup is missing:**
- A keyboard shortcut (to edit a file) in the first "right click menu". For now, there is no direct keyboard shortcut and one has to go to the "Actions" menu first.
- Handle opening multiple files using the right click menu. ATM if you have MadEdit already running and you use the right click menu to open a file it doesn't work.
- I'm forgetting something but I can't remember....
NOTE: IINM these are KDE integration issues, not bugs of MadEdit. Does anybody know how I can fix them?


I find it very strange that this editor hasn't been heard of and is neither present in any distro.

BTW can any one post here the guidelines on how to make a .deb package? (Sourceforge has packaged distributions, but not for my amd64)
Maybe the usefull part of this message could go into a wiki?

OFFTOPIC:
*sigh* These past weeks with Linux (and without windows) sure makes one think.
Windows has lots of problems but also has good things... OTOH Linux ain't all roses... I sure miss programs like:
- **Sygate Firewall:** There is no application based firewall for Linux! Just because it's FOSS it doesn't mean they're all goody-two-shoes... You simply don't know what is phonning home! Besides, I got 5 apache daemons running... where the hell did they come from???!!! I could block everything but then I would break P2P.
- **Netlimiter:** No comments!
- **Media Player Classic:** Mplayer, KMplayer, etc are just awfull... (at least out of the box). I just can't drag-and-drop... the video seeking is terrible...
* Konqueror has already crashed on me and made me reboot the computer. Neither logout neither restarting X worked (and I killed all konqueror processes).
* (One of) my drives isn't unmounted correctly! When I boot I got a message saying, something like, recovering/cheking journaling for drive /dev/hdb

---

### Post by muszek on 2007-06-30
> Besides, I got 5 apache daemons running... where the hell did they come from???!!!

I'm not an expert by any means (I don't even know if "daemon" is different from "a process"), but this could be the reason:
At any given time, apache is running several processes - they handle requests concurrently.  Starting up such process is costly, so apache keeps some processes running even if it's not serving anything at the moment.

Take a look at /etc/apache2/apache2.conf and find this section:
```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10 
    MaxClients          150
    MaxRequestsPerChild   0 
</IfModule>
```
Apache starts with StartServers processes, keeps at least MinSpareServers and at most MaxSpareServers spare processes running at any time.  If it's receiving many more requests, it can open op to MaxClients processes.  The last value tells you after how many requests a process is restarted (good in case there are some memory leaks).

---

### Post by Tookelso on 2007-06-30
I give another star to MadEdit.  It's even got Find In Files feature which I sorely miss from UltraEdit!

---

### Post by kung fu buntu on 2007-08-01
The only thing I can't get to work is PGUP and PGDW :-(

Any ideas?

---

### Post by revertex on 2007-08-01
it seems that you are pretty new to linux.

it's completely different to windows, that's why there is no such thing like the firewall firewall you described, as all apps being opensource there is no point to hide a "call home" feature.

you can use tools like ethereal, ettercap, wireshark, nessus, nethogs, nmap, to monitor how your apps comunicare with internet.

try gvim

[http://www.gentoo.org/doc/en/vi-guide.xml](http://www.gentoo.org/doc/en/vi-guide.xml)

---

### Post by bogolisk on 2007-08-01
> **kung fu buntu said:**
> When you get used to something it's hard to let it go, so I just though some of you might want to know that there is an alternative.

What I liked the most in UltraEdit was the **ability to (handle and) switch between text and hex edit mode** with just one keyboard shortcut.

This editor also has other features such as:
- **cycle through open files using ctrl+tab**
- **column edit mode**
- **shortcut for word wrap mode**
- **open multiple files using drag-and-drop**
Unfortunately it has **no support for macros** :-(

This FOSS gem is **[MadEdit ]("http://madedit.sourceforge.net/")**....


Because all those features are supported by Emacs/Vim. In *nix editor war where the two behemoths Emacs and Vim clash, all other editors look wimpy.

---

### Post by kung fu buntu on 2007-08-02
> **revertex said:**
> it seems that you are pretty new to linux.

it's completely different to windows, that's why there is no such thing like the firewall firewall you described, as all apps being opensource there is no point to hide a "call home" feature.

you can use tools like ethereal, ettercap, wireshark, nessus, nethogs, nmap, to monitor how your apps comunicare with internet.

try gvim

[http://www.gentoo.org/doc/en/vi-guide.xml](http://www.gentoo.org/doc/en/vi-guide.xml)
I remember seeing a message about a media player sending information about which tracks were being played. So there is a phone-home issue. IMHO just because it's open source it doesn't mean it's a goody-two-shoes. 
Besides there is also the case of FOSS tools not included in the distro (and even if they are you have to trust on the person who packages it... A problem if it's a not-so-commonly used package).
Finally, there is also the issue of commercial tools.
IMO it makes sense to have an easy-to-use tool to control the network traffic. Not just monitor, but control it on the fly.

> **bogolisk said:**
> Because all those features are supported by Emacs/Vim. In *nix editor war where the two behemoths Emacs and Vim clash, all other editors look wimpy.
I use XEmacs for coding in C. I just know the basics (open, write, search, cycle buffers, slice windows). The learning curve is very step(?) and that is why I prefer something like UltraEdit when I have to keep multiple text files open.
They may be powerfull but are increadibly complicated to be used on time.

---

### Post by revertex on 2007-08-03
ok, maybe is kate the editor you are looking for.
does this media player send usage info without notice the user, can you name it?
i can't believe ubuntu should put such package in the repos.

it's pretty hard to find a linux firewall that monitor outgoing traffic, i don't know the existence of such tool, but there's lots of tools to monitor all traffic in realtime.

take a look at nethogs.

---

