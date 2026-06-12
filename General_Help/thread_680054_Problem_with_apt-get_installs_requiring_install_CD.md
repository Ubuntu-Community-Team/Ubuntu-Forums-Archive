---
title: "Problem with apt-get installs requiring install CD"
date: 2008-01-27
forum: General Help
---

### Post by nunix on 2008-01-27
This is for 7.04

I'm trying to get a program installed (dosbox 0.72) and used the build-dep line for getting the dependencies. This worked fine until it paused and asked for the Feisty Fawn 7.04 disc. The trouble is that the CD drive on this laptop is pretty much shot.

1) Why does it even want the CD?
2) I haven't found a way to mount a virtual drive (a la daemon tools or Alcohol 120% in win32) in ubuntu; is there a way to do that, and will it work for installs asking about /cdrom/?
3) How can this be worked around?

It's really irritating having it look for physical media when it could probably just grab files online somewhere, but I'd be fine with mounting a virtual copy if I knew how and if it would even work.

---

### Post by taurus on 2008-01-27
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, it will never ask you for a CDROM again.

Save it and then run

```
sudo apt-get update
```

---

### Post by nunix on 2008-01-27
Great! Worked like a charm.

Follow-up: what's the difference between gksudo and sudo, outta curiousity?

Thanks for the help!

---

### Post by taurus on 2008-01-27
Sudo is more for terminal while gksudo is more for graphical apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by nunix on 2008-01-27
Woo, great link =D Going to be spending time digging around in that..

---

