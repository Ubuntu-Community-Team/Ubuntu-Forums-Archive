---
title: "Ubuntu Studio on CD (not DVD)"
date: 2007-10-26
forum: General Help
---

### Post by Th3Professor on 2007-10-26
I would like to install Ubuntu Studio on an extra partition but am not able to do so from DVD - must use CDs instead.

How do you create Ubuntu Studio CDs instead of DVD?

---

### Post by OA-5599 on 2007-10-26
You could install your standard ubuntu distribution from cd and later update it to studio with synaptic.

---

### Post by Th3Professor on 2007-10-26
Is there a way to put Ubuntu Studio on CDs instead of DVD?

---

### Post by zach12 on 2007-10-26
No but you can install ubuntu studio from ubuntu just download the iso for ubuntu 
and install from ther as would.
when you have install ubuntu on your harddrive start you computer up. Then open from the command line> sudo gedit /etc/apt/sources.list then paste this > deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio)Gutsy main at the top of the file

then just use > sudo apt-get install to install the ubuntustudio art packages
and programs

worked for me on dapper(6.06)

---

### Post by MetalMusicAddict on 2007-10-26
As Gutsy is out, and all of our packages are in the Ubuntu proper repos, please don't recommend people use the Feisty repo. We will also soon be taking it down.

---

### Post by zach12 on 2007-10-26
But for dapper users  the Gutsy reps will not work so is dapper going out sooner then 2009:confused:

---

### Post by por100pre1 on 2007-10-26
> **Th3Professor said:**
> Is there a way to put Ubuntu Studio on CDs instead of DVD?

First, please ignore Zach12's suggestion. Second, install regular Ubuntu Gutsy. Finally, copy, paste and ENTER this command in Terminal (**Applications> Accessories> Terminal**):

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

This will convert Gutsy to Ubuntu Studio Gutsy with all stuff.

---

### Post by Th3Professor on 2007-10-26
Does that method of the studio install result in the exact same system as what comes with the Ubuntu Studio DVD?

edit:
Any idea how much hard drive space Ubuntu Studio uses? (Excluding space needed for large audio, video, etc. files.)

Thank you everyone for the input.

---

### Post by Th3Professor on 2007-10-26
It looks like studio is over 800MB prior to install, how large is it after install?

Would the install method, noted above, give the exact same system as the DVD version?

Thanks.

---

### Post by Th3Professor on 2007-10-26
Anybody? :confused:

---

### Post by por100pre1 on 2007-10-26
Ubuntu Studio Gutsy uses the same Ubuntu Gutsy repositories so yes, it will be the same Ubuntu Studio. The installation will be slightly bigger than a regular Ubuntu Gutsy install but I don't remember exactly how much space it requires.

---

### Post by Th3Professor on 2007-10-26
Please? Anybody? <sigh>

EDIT:
nevermind, someone replied. THank you! :)

---

### Post by Th3Professor on 2007-10-26
> **por100pre1 said:**
> Ubuntu Studio Gutsy uses the same Ubuntu Gutsy repositories so yes, it will be the same Ubuntu Studio. The installation will be slightly bigger than a regular Ubuntu Gutsy install but I don't remember exactly how much space it requires.

Thanks.

I was wondering how much space to reserve for it before I donate a partition into it.

---

### Post by LinuxSoundMan on 2007-11-14
> **por100pre1 said:**
> First, please ignore Zach12's suggestion. Second, install regular Ubuntu Gutsy. Finally, copy, paste and ENTER this command in Terminal (**Applications> Accessories> Terminal**):

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

This will convert Gutsy to Ubuntu Studio Gutsy with all stuff.

Does anyone know if this method will work for fluxbuntu? if so it would complete my linux audio system. i welcome any info and/or advice. thanks

---

### Post by Th3Professor on 2007-11-16
> **LinuxSoundMan said:**
> Does anyone know if this method will work for fluxbuntu? if so it would complete my linux audio system. i welcome any info and/or advice. thanks

Actually, on that note, I've got an additional question regarding the main topic of this thread... Does anyone know:

Is Ubuntu Studio available pre-set-up with all of the Studio features but running on Fluxbox *instead* of Gnome?

Or would I just be better off creating my own "Fluxbustu" from scratch?

I could go ahead and do that but curious of a fluxbustu type set-up is available already.

---

