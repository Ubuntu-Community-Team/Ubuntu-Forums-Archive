---
title: "Moved files from old laptop to new desktop, broke sound"
date: 2007-09-18
forum: General Help
---

### Post by treb0r on 2007-09-18
Hi All,

I've been using Ubuntu on a P4 laptop for a couple of years, and recently decided to start using a newer Dell desktop instead. I rsynced my home directory to an external USB drive, then copied the lot to my new home directory on the Dell.

Everything seemed fine until I realised that sound was no longer working on the Dell. At first I thought it was an issue with the built in intel sound card - then I realised that sound was working up to the point of login - I could still hear the ubuntu bongo sample when the machine booted up.

To test this, I created a new user account and logged in, and the sound was working fine.

I then realised I must have broken the sound when I copied all the dotfiles over from the old laptop.

My problem is that I need a lot of the dotfiles for things like my evolution mail accounts, and I don't know which ones contain the settings for sound. 

Questions:

What is the best method for migrating data and settings from one machine to another?

How can I get the sound working for my user account on the dell.

Thanks in advance!

---

### Post by dcstar on 2007-09-19
> **treb0r said:**
> Hi All,

I've been using Ubuntu on a P4 laptop for a couple of years, and recently decided to start using a newer Dell desktop instead. I rsynced my home directory to an external USB drive, then copied the lot to my new home directory on the Dell.

Everything seemed fine until I realised that sound was no longer working on the Dell. At first I thought it was an issue with the built in intel sound card - then I realised that sound was working up to the point of login - I could still hear the ubuntu bongo sample when the machine booted up.

To test this, I created a new user account and logged in, and the sound was working fine.

I then realised I must have broken the sound when I copied all the dotfiles over from the old laptop.

My problem is that I need a lot of the dotfiles for things like my evolution mail accounts, and I don't know which ones contain the settings for sound. 

Questions:

What is the best method for migrating data and settings from one machine to another?

How can I get the sound working for my user account on the dell.

Thanks in advance!

You may have to fix the permissions of all the files you copied over to your current user account, check these in a terminal:
```
man chown
man chmod
```
and this terminal command will show you the current permissions:
```
ls -al
```

---

### Post by treb0r on 2007-09-19
Hi David,

That was the first thing I did after I copied the files over.

Everything else is working - the problem is the old laptop uses different sound settings from the new desktop, and I'm not sure which file contains the settings, although I think it must be something to do with gnomeconf.

---

### Post by treb0r on 2007-09-19
If I click on the gnome volume applet, I get the following error:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

---

### Post by treb0r on 2007-09-19
I get the feeling that nobody around here can help - why is it so hard to migrate from one machine to another in Ubuntu?

Gnomeconf is a black art. It seems I can't move my evolution account setting without also breaking sound on my new machine. Help!!

---

### Post by treb0r on 2007-09-19
I get the following error when I run gconf editor:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

---

