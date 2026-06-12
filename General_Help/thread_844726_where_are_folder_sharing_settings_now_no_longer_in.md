---
title: "where are folder sharing settings now? no longer in /etc/samba/smb.conf"
date: 2008-06-29
forum: General Help
---

### Post by nix4me on 2008-06-29
Hi,

I shared a few folders from nautilus with smb and I trying to find the config file that controls these shares.  Back in the day, and on all other distros right now, all folder sharing was handled by the /etc/samba/smb.conf file.  There is no mention of my shares in that file now.  i can only assume that there is a another file somewhere which controls the shares made within nautilus now.  Any hints?

nix4me

---

### Post by nix4me on 2008-06-30
bump, still looking where the share definitions are at when sharing folders from nautilus.

---

### Post by soccerboy on 2008-06-30
see if there is anything in gconf.
Alt+F2 followed by gconf-editor.
under /system/smb

---

### Post by nix4me on 2008-06-30
Nope, not there.  I've also looked in gnome and gfs directories everywhere.  The share definitions have to be somewhere.  Sure would have been nice if they would have left a hint in the smb.conf file.

---

### Post by nix4me on 2008-06-30
Ahh forget it.  I ditched the nautilus shares and set them up manually in smb.conf.  That really bugs me when stuff changes for no reason.  All they had to do was make the shares show up in the bottom of the smb.conf like they are suppose to.

I might just file a bug to voice my displeasure.

nix4me

---

### Post by soccerboy on 2008-06-30
> **nix4me said:**
> Ahh forget it.  I ditched the nautilus shares and set them up manually in smb.conf.  That really bugs me when stuff changes for no reason.  All they had to do was make the shares show up in the bottom of the smb.conf like they are suppose to.

I might just file a bug to voice my displeasure.

nix4me

Just curiou,s what was in the smb.conf file that you wanted to edit?  I started to use samba shares after they had been emptied from the smb.conf files.

---

### Post by nix4me on 2008-07-01
I was wanting to add specific options to each share suck as force user and umask settings.  This is eas if you add the shares to the smb.conf individually.  But, the new fangled share ability in nautilus adds the information somewhere (never found it) so there is no way to add specific options to each share.  I'm still hunting, but in the meantime i added all my shares to the smb.conf.

---

### Post by soccerboy on 2008-07-01
how about /usr/share/samba/smb.conf?  Does that have the settings in it?

---

### Post by soccerboy on 2008-07-07
the settings are in /var/lib/samba/usershares/<name-of-share>

---

### Post by db9s on 2008-07-09
this is so stupid. Spent the entire morning trying to fix samba.

---

