---
title: "LimeWireLinux RPM"
date: 2005-05-20
forum: General Help
---

### Post by D3ciph3r on 2005-05-20
How do I use alien to install Limewire on Ubuntu?  If there is a better way though, I would prefer that.  I need help asap, thank you.

---

### Post by f.prisson on 2005-05-20
Just type ```
sudo alien -d *.rpm
``` 
For installing ```
sudo dpkg -i *.deb
```

---

### Post by D3ciph3r on 2005-05-20
[QUOTE=f.prisson]Just type ```
sudo alien -d *.rpm
``` 
For installing ```
sudo dpkg -i *.deb
```[/QUOTE]

Whenever I try to install it, it says cannot find the file of my .deb generated version. I am typing this:

```

sudo dpkg -i /home/ryan/Desktop/LimeWireLinux.deb

```

What am I doing wrong?

---

### Post by D3ciph3r on 2005-05-20
[QUOTE=D3ciph3r]Whenever I try to install it, it says cannot find the file of my .deb generated version. I am typing this:

```

sudo dpkg -i /home/ryan/Desktop/LimeWireLinux.deb

```

What am I doing wrong?[/QUOTE]
 Ok, I figured out how the dpkg thing worked, but now where do I go from there?  It just says it's setting it up, then comes up just telling me to enter a new command.  What the hell?

---

### Post by bored2k on 2005-05-20
[QUOTE=D3ciph3r]Ok, I figured out how the dpkg thing worked, but now where do I go from there?  It just says it's setting it up, then comes up just telling me to enter a new command.  What the hell?[/QUOTE]
 Run limewire.
The best way is to get the .tgz and open it from source btw..

---

### Post by f.prisson on 2005-05-21
> It just says it's setting it up, then comes up just telling me to enter a new command Which command?

---

### Post by Psquared on 2005-05-29
[QUOTE=bored2k]Run limewire.
The best way is to get the .tgz and open it from source btw..[/QUOTE]

Can you post a link for the .tgz file? All I could find was rpm and zip.

---

### Post by apollyonis on 2005-05-30
Source : [Limewire Downloads](http://www.limewire.com/english/content/downloadfree.shtml) 

All Platforms download : [Limewire .ZIP download](http://www.limewire.com/LimeWireSoftOther) 

Extract Limewire, make sure to have Java installed, go to directory where Limewire was extracted, type in ./runLime.sh

---

### Post by ceti on 2005-05-30
[QUOTE=D3ciph3r]How do I use alien to install Limewire on Ubuntu? If there is a better way though, I would prefer that. I need help asap, thank you.[/QUOTE]

Why a RPM package?
Why not install LimeWire from The Ubuntu Unofficial Guide?
Follow this link:
[http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/)
Add-On Applications --> 10 [How to install P2P Gnutella Client (LimeWire)?]("http://ubuntuguide.org/temp/#limewire")
That'll do.

---

### Post by jiyuu0 on 2005-05-30
[QUOTE=ceti]Why a RPM package?
Why not install LimeWire from The Ubuntu Unofficial Guide?
Follow this link:
[http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/)
Add-On Applications --> 10 [How to install P2P Gnutella Client (LimeWire)?]("http://ubuntuguide.org/temp/#limewire")
That'll do.[/QUOTE]

don't use the link at the temp directory...

use the main instead:
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

---

### Post by derrick1985 on 2005-05-31
I did it from RPM only yesterday.

sudo alien *.rpm
sudo dpkg -i *.deb

This was all done in a folder labeled limewire

---

