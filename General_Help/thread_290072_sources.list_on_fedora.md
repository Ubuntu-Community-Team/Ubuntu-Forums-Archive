---
title: "sources.list on fedora"
date: 2006-10-31
forum: General Help
---

### Post by feest on 2006-10-31
is it save to use the ubuntu sources.list in fedora (yes i installed apt) i need it to install my nvidia drivers (or somebudy should know a nvidia-glx rpm file...

---

### Post by tronica on 2006-10-31
fedora uses rpm's and ubuntu debs. so no that won't work, i'm not sure i fully understand what your wanting to do here. can you explain what it is you trying to accomplish?

---

### Post by po0f on 2006-10-31
feest,

Try adding [Livna's](http://rpm.livna.org/) repos.  I had no problem with these when using FC6.  I never tried apt on FC6 (why mix the two?).

---

### Post by feest on 2006-11-01
My fedora installation can read apt files since i've installed apt with yum so that shouldn't be a prob

the prob is that i need my nvidia card to work, therefor i need the ubuntu sources.list to download nvidia-glx to fedora

---

### Post by turkenator on 2006-11-01
feest it wont work even if u installed apt 
fedora uses RPM
ubuntu uses DEB
u cant install deb files on fedora with APT
instead you should look for fedora repositories on google 
as a last resort u can install a deb file with alien (i tink) but i dunno if that would be a good idea to use alien for drivers im sure there are RPMs for nvidia drivers out there have a good look

---

### Post by feest on 2006-11-01
well i sorta installed nvidia drivers now (and indeed i was confiusing rpm's with debs srry) but when i try to run aiglx the window borders disappear (wich also happend on ubuntu) so...

WEIRD

---

### Post by taurus on 2006-11-01
Why don't you just follow this guide and install whatever you want!!!  And try not to mix Ubuntu's repos with FC6 because you are only asking for trouble later...

[http://www.mjmwired.net/resources/mjm-fedora-fc6.html](http://www.mjmwired.net/resources/mjm-fedora-fc6.html)

---

### Post by tronica on 2006-11-01
as far as your windows decorations disappearing try running 

> beryl-manager

---

