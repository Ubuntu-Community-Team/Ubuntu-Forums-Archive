---
title: "Nautilus fails to launch, Xubuntu 14.04"
date: 2014-04-30
forum: General Help
---

### Post by RallyDarkstrike on 2014-04-30
Hi all,

Seems Nautilus is pre-installed on Xubuntu 14.04 alongside Thunar, although Thunar is the default. I prefer Nautilus, so I tried setting it as the preferred File Manager in settings....when nothing seemed to happen, I tried running it from Terminal and received this error:

(nautilus:2945): Gtk-WARNING **: Failed to register client: GDBus.Error:eek:rg.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

Is this a bug? This is a fresh install of Xubuntu other than some minor theme tweaks and installing of the usual packages (LibreOffice, Skype, etc.)

Any help would be appreciated! :)

---

### Post by brainwash on 2014-05-01
Nautilus is _not_ pre-installed by default. I get the same warning message on my system, but nautilus still launches just fine. Did you already try to reinstall it?

---

### Post by RallyDarkstrike on 2014-05-01
> **brainwash said:**
> Nautilus is _not_ pre-installed by default. I get the same warning message on my system, but nautilus still launches just fine. Did you already try to reinstall it?

I didn't try to reinstall it, no (and if what you say is the case, it's not installed on my machine at all then!)...so it may just work fine when I get home and try it! I assumed it was pre-installed as it is listed as the only other option under the 'Preferred Programs' settings for 'File Managers' aside from Thunar......a stupid mistake on my part, I guess, but at the same time, *logically*, why would it be listed there if it WASN'T installed...? Seems a poor idea...

---

### Post by RallyDarkstrike on 2014-05-06
Ok, tried reinstalling Nautilus, same issue as before...I still get the same error message as above when running it from Terminal and, instead of Nautilus launching, I get the 'Files' file manager v.3.10.1 (according to its 'About' page), NOT Nautilus.

Any reason why its not launching properly? I've installed it twice now...once from the Ubuntu Software Center, and once from Terminal using apt-get...

---

### Post by maglin2 on 2014-05-06
I think Files is probably just a rebranding of what was Nautilus.

(I'm still on 12.04 - so I've still got Nautilus)

---

### Post by RallyDarkstrike on 2014-05-06
Oh, I guess you're right....I'm not a big fan of it :/

There's no Menu Bar and you can't save view settings per folder....seems like a step backwards to me!

---

### Post by ibjsb4 on 2014-05-06
Why nautilus?

[http://en.wikipedia.org/wiki/Nemo_(file_manager)](http://en.wikipedia.org/wiki/Nemo_(file_manager))

---

### Post by RallyDarkstrike on 2014-05-06
Nautilus because it was what I have installed and am used to (and like very much) on my Linux Mint 14 netbook. However, I just installed Nemo on this new desktop with Xubuntu 14.04 and it's VERY similar to Nautilus, so I am very happy with it...thanks for the suggestion! :)

---

