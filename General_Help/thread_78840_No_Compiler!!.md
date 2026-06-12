---
title: "No Compiler?!?!?"
date: 2005-10-19
forum: General Help
---

### Post by Ocxic on 2005-10-19
I was just trying to install Beep-media-player, and relized that i don't have a compiler to install the thing, so is there a way to get one??? and where??
i also did some fiddle with "Add programs" and it seemed to almost fix it, now i get an "error: C++ preproscessor "lib/cpp" fails sanity check..... what does that mean?

Thank u again....

---

### Post by Pablo_Escobar on 2005-10-19
1. Beep media player is available in the repos.
2. If You want to compile Yourself - install a package called "build-essentials" via apt-get (Synaptic)

---

### Post by Ocxic on 2005-10-19
thank you, I acttually figured that out, but now i get
"configure: error: Cannot find X11 headers/Libraries"
when i run ./configure

---

### Post by Pablo_Escobar on 2005-10-19
If You compile the program Yourself, You need the "dev" packages the compiler spits out as errors.
Just look for "dev" packages in Synaptic - in that specific case that would be : libx11-dev (I pressume)

---

### Post by Ocxic on 2005-10-19
I did as you said but to no avail.....it didn't work, is there anything else i could do, I still get the same error

---

### Post by RAOF on 2005-10-19
You should be able to install Beep from apt-get/synaptic.  This will be **much** easier than installing from source.  Just search for "beep" in synaptic, select it to install, and hit "apply".  Done, complete with menu items :)

The only time you should ever need to install something from source is if you want something really, totally bleeding edge that hasn't been packaged yet, or you actually want to hack on something :)

---

### Post by Ocxic on 2005-10-19
Thank you, it installed fine, but I have yet to hear it play anything, it looks/acts like my music is playing, but i hear nothing, although i hear all other system sounds and gaim sounds?????

---

### Post by RAOF on 2005-10-19
I've no experience with Beep (I'm a banshee man, myself :)), but I'd suspect that you just need to select the right output plugin.  It'll be under preferences, or something.

You probably want to select "ESD" or "ALSA", if they're available, but try everyting.  Failing that, try searching synaptic and installing all the beep plugins and trying that again :)

---

### Post by Ocxic on 2005-10-19
[QUOTE=RAOF]I've no experience with Beep (I'm a banshee man, myself :)), but I'd suspect that you just need to select the right output plugin.  It'll be under preferences, or something.

You probably want to select "ESD" or "ALSA", if they're available, but try everyting.  Failing that, try searching synaptic and installing all the beep plugins and trying that again :)[/QUOTE]


Thank you, it was the ALSA thing, YAY i got music!
i'm done in this thread now, thanks to everyone.

---

### Post by Neutrino on 2005-10-19
Do you know the list of package needed to install the gcc compiler? 
I installed the gcc package but it is not working fine.
It is sometimes important to compile the packages from the source (mplayer for example).

THnaks for you help.

---

