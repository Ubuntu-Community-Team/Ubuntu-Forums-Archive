---
title: "Nautilus CD/DVD Crash when I just open Nautilus"
date: 2006-12-24
forum: General Help
---

### Post by alphaomega on 2006-12-24
Since I installed the last gnome updates(just as a time reference), when I open up nautilus, a Report Bug window pops up and says the CD/DVD Burner has crashed. Thru the bug reporting box, I sent off an email and I was told:
This is a crash in swfdec.
However, swfdec does not track its bugs in the GNOME Bugzilla. We kindly ask
you to report the bug to the application authors.

 The original report is located here: [http://bugzilla.gnome.org/show_bug.cgi?id=388916]("http://bugzilla.gnome.org/show_bug.cgi?id=388916")

I have tried reinstallation of everything, Nautilus, the CD/Burner, the libraries, etc and am stuck. It's very annoying since it happens everytime I open up Nautilus.  ](*,)

---

### Post by cilynx on 2006-12-24
Not sure why your flash player (swfdec) is linking up with Nautilus, but try
```

sudo apt-get remove swf-player libswfdec0.3 gstreamer0.8-swfdec 

```

As a wizardry trick: if you get a weird error, start throwing things at apt-cache and see what it gives you:
```

rcw@esquire:~$ apt-cache search swfdec
gstreamer0.8-swfdec - SWF (Macromedia Flash) decoder plugin for GStreamer
libswfdec0.3 - SWF (Macromedia Flash) decoder library
libswfdec0.3-dev - SWF (Macromedia Flash) decoder library
swf-player - Mozilla plugin for SWF files (Macromedia Flash)
rcw@esquire:~$ 

```

---

