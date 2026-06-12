---
title: "[SOLVED] Unable to install gstreamer extra plugins"
date: 2007-10-23
forum: General Help
---

### Post by IanB2 on 2007-10-23
I have a new copy of 7.10 installed and am trying to play some mp3s.

I've tried several different methods of installing the gstreamer extra plugins via add/remove and  synaptic. On both occasions I get a message saying 'the list of applications is not available'. When I click refresh the packages appear to download (internet is working) but nothing appears to update and I end up going through the same set of dialogue boxes again.

Can anyone suggest a solution please? Is this a bug?

---

### Post by benerivo on 2007-10-23
Add/Remove asks me to refresh the available list of packages every time i use it. Luckily i only use it to remove stuff i don't want. Try adding the gstreamer codecs using Synpatic package manager. If you add gstreamer bad, ugly and ffmpeg you can play just about any format.

---

### Post by rudeboyskunk on 2007-10-23
Also, make sure all of your repositories are enabled.  System>Administration>Software Sources.

---

### Post by IanB2 on 2007-10-24
Thanks, enabling repositories has done the trick!

---

### Post by IanB2 on 2007-10-29
Question - how do I mark threads that are SOLVED?

---

### Post by Maestro23 on 2007-10-29
> **IanB2 said:**
> Question - how do I mark threads that are SOLVED?

Thread Tools.

---

### Post by zorkerz on 2007-11-05
What packages does "gstreamer extra plugins" from add/remove install.

Is there a way in general to find out what packages are being installed with the add/remove app?

---

### Post by sidmar on 2007-11-08
Pelo amor de Deus alguem me passe o GStreamer extra plugins urgente!!!!!!

Please, send me the GStreamer extra plugins.

Obrigado.
Thanks.

---

### Post by por100pre1 on 2007-11-08
> **sidmar said:**
> Pelo amor de Deus alguem me passe o GStreamer extra plugins urgente!!!!!!

Please, send me the GStreamer extra plugins.

Obrigado.
Thanks.
Check the packages from [this list]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gstreamer0.10-plugins&searchon=names&subword=1&version=all&release=all"), according to the Ubuntu version you use.

**Have you tried [this]("https://help.ubuntu.com/community/RestrictedFormats") first?** BTW, welcome to the forums.

---

