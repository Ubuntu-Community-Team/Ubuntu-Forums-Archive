---
title: "Create limited/restricted user accounts"
date: 2007-12-15
forum: General Help
---

### Post by psychotonomy on 2007-12-15
I would like to create a limited/restricted user account for my Kubuntu 7.10 (Gutsy) system. here's what I envision:

have the system automatically boot/log-in to this limited account of which everyone will use. I want the limited users to be able to search the web, create/save office documents, watch DVD movies, listen to music, etc.... however, I don't want them to be able to change any of the settings, programs or permissions. it'll be a care-free way to run my system. as an analogy, and though I hate microsoft, it would be similar to XP's limited account except it would default to that account and if I wanted to make any non-superficial changes, I would be prompted and then enter a  password. I plan on having this system be a music server so, though I want them to listen to the music, I don't want them to be able to make any changes (move/delete/rename tracks).

ideas? thanks.

---

### Post by JackandJohn on 2008-01-30
There would be a few ways to do this..

Traditional use would be to create a user account, then remove it's sudo permissions by editing the sudoers file.
After this, you can run through and chmod (change permissions) and chown (change ownership) of all the files you don't want them to edit, and all the programs you don't want them to run.

A newer, and possibly better option would be to set up Ubuntu the way you want (Including network shares/internal hard drive storage space, etc), remove the default user from sudoers (create your own admin account), set auto-login, and then create your own LiveCD.

Then, they could only change minor things, and a reboot would wipe it back to the base config.

Updating in this case would mean creating a new livecd, but you could simply build on each one and not have to make it from scratch.

---

### Post by JackandJohn on 2008-01-30
Oh, and for hardware: format your hard drive as EXT3, and then set the permissions; Ubuntu will take care of not letting users change anything. Example:

/media/InternalHD/Music (RW for root, read for users)
/media/InternalHD/Documents (RW for all)

then boot from the cd (it will show the HD on the desktop), and let them go at it

---

### Post by ^Albe^ on 2008-02-01
hi to all, i'm looking just now for a similar setup

i thinked about to create a normal user with chance to browse, use program, printer configured etcetc
then "lock" the administration right

and "copy" that $HOME every boot (or better every login: the guest users have only this account), at least i can permit a "shared" folder where put some data

do you think that is possible?
any suggestion for how made it?

another: do you think that is possible to have the ubuntu updated withouth any administrator login? (in automatic)

regards

---

### Post by ^Albe^ on 2008-02-01
in other words:
a "Master user" that can use his account, and can configure and save his own configuration in his home

a guest user that use the same home but copied (deleted at start, and then copied at every boot or better every login)

---

