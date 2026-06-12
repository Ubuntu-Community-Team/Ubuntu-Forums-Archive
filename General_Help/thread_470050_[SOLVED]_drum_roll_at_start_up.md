---
title: "[SOLVED] drum roll at start up"
date: 2007-06-10
forum: General Help
---

### Post by unebaguettesvp on 2007-06-10
this might not seem like too much of a problem but it actually is.

sometimes when i boot up my computer, i don't hear that little ubuntu drum roll at the gdm screen. i'm trying to get mednafen (an emulator) to work on my system. but the problem i was having with it was that there was no sound.

here is a link to the problem i was having with that issue which is still not resolved:
[http://forum.fobby.net/index.php?t=tree&th=296&start=0]("http://forum.fobby.net/index.php?t=tree&th=296&start=0")

so. when i don't hear the drum roll, i can't use amarok with the oss sound engine. however, it does work with alsa and esd. also, i can not hear the sound in mednafen using either the alsa or oss engine.

so, my question is what would make the drum roll at the gdm screen not play?

thanks for any help.

---

### Post by Bakerman on 2007-06-10
Hi,

I occasionally have the same problem. I've got Intel HDA sound. I believe it is a known bug with Ubuntu not always recognising/initialising the sound card during start up.

When I boot up and don't hear the 'drum roll' I know that the sound is not going to work. I know it's not ideal, but I just reboot until I hear the damn drum roll! The most I've had to reboot before the sound works is twice so far, so it's not too bad a work around at the moment. I suppose I'm also fortunate because my PC is on 24/7 so I don't have to re-boot that often anyway...

Just noticed you're also running Edgy. Maybe the bug has been fixed in Feisty?

---

### Post by unebaguettesvp on 2007-06-10
thanks for reminding me to update my profile. i'm actually using feisty.

i also restart my computer until i hear the drum roll but its really annoying.

does anyone else have this problem? should i post a bug on launchpad?

---

### Post by unebaguettesvp on 2007-06-11
sorry for the bump!

can anyone else offer any suggestions?

---

### Post by unebaguettesvp on 2007-06-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/121433](https://bugs.launchpad.net/bugs/121433) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				fyi, here is the launchpad url.

---

### Post by unebaguettesvp on 2007-11-02
fixed.

to fix this issue,

sudo gedit /etc/gdm/gdm.conf

and find the line for "SoundOnLogin" and uncomment it. don't pay attention to gdmsetup. i don't know why but the checkbox for this option in gdmsetup is checked but it is uncommented in gdm.conf?!

if you want to know how i fixed the other sound problems, go to the launchpad bug url.

---

