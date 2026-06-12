---
title: "How to change back 18.10 sound effects to factory default?"
date: 2018-11-03
forum: General Help
---

### Post by jvhummel on 2018-11-03
Hi everyone, 

I've been distro-hopping lately and am now trying Ubuntu 18.10. I was playing around in the *settings->sound->sound effects* tab and noticed that none of the entries set the sound effect scheme back to factory defaults. For instance, when I change my speaker volume, the sound effect that plays is not the same as it was before I played around in those settings, regardless of which option I choose.

I've tried the *default* option, of course, but this sets the sound effect scheme to *drip*. This is, if I recall correctly, the default sound scheme for previous versions of Ubuntu. 

Did I run into a bug? Am I simply missing something?

I realize this is a small issue, but it's been slightly annoying me for a few days now, hence the decision to post.
I tried googling and searching this forum for answers, but given the relatively young age of 18.10, I couldn't find much.

---

### Post by silverspr on 2018-11-04
hi, not sure how much help I can provide, but three things come to mind:
1) the most reliable way would be to re-install ubuntu from live cd, [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) 
2) you could try this: [https://www.ostechnix.com/reset-ubuntu-factory-defaults/](https://www.ostechnix.com/reset-ubuntu-factory-defaults/) and report back if successful
3) I use timeshift to take snapshots of the OS/system which can be restored later if you run into a problem like you've described
cheers

---

### Post by jvhummel on 2018-11-05
> **silverspr said:**
> hi, not sure how much help I can provide, but three things come to mind:
1) the most reliable way would be to re-install ubuntu from live cd, [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) 
2) you could try this: [https://www.ostechnix.com/reset-ubuntu-factory-defaults/](https://www.ostechnix.com/reset-ubuntu-factory-defaults/) and report back if successful
3) I use timeshift to take snapshots of the OS/system which can be restored later if you run into a problem like you've described
cheers
Issue is now fixed, thanks for your input though.

Fixed the issue by using dconf-editor and resetting  /org/gnome/desktop/sound/theme-name to "Yaru" by using its "Use default  value" toggle.
Selecting "default" inside the sound effects settings tab sets it to "freedesktop". Have reported a bug here: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1801780](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1801780).

---

