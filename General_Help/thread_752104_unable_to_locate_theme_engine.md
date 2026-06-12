---
title: "unable to locate theme engine"
date: 2008-04-11
forum: General Help
---

### Post by olafthekid on 2008-04-11
I get this error when running firefox or other gui-apps in x:
(<unknown>:20465): Gtk-WARNING **: Unable to locate theme engine in module_path: "mist",


I've installed gtk2-engines with apt-get, but there still a problem...


thankful for any help.
cheers.

---

### Post by kpkeerthi on 2008-04-11
What GTK theme are you using? Switch to the default human theme. Does the problem still persist?

---

### Post by olafthekid on 2008-04-11
i use royalty, I will take a look and see if it works by changing back to the default theme. thanks for the tip.

---

### Post by olafthekid on 2008-04-14
ok, I tried with the default theme and now there's no error.
Any idea how I could fix the royalty theme?

---

### Post by kpkeerthi on 2008-04-14
It appears that royalty uses mist gtk engine. Enable multiverse repository from System -> Admin -> Software Sources and install [gtk-engines-mist]("http://packages.ubuntu.com/gutsy/x11/gtk-engines-mist") using [Synaptic]("https://help.ubuntu.com/community/SynapticHowto")

---

### Post by olafthekid on 2008-04-15
hmm I have installed using the netboot version of ubuntu and i'm running xfce with pekwm. I tried to enable multiverse repoistory but when I try to install with either apt-get or synaptic the package is already installed.

---

