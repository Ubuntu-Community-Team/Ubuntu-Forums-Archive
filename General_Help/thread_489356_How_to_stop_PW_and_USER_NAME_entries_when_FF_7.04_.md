---
title: "How to stop PW and USER NAME entries when FF 7.04 Boots up?"
date: 2007-07-01
forum: General Help
---

### Post by intricate on 2007-07-01
Is there any way to boot into FF 7.04 and NOT HAVE to type in a USER NAME or PASSWORD or KEYRING PW? Id like to boot into FF 7.04 straightaway and not have the delays typing in all this crap entails.

Thanks Ubuntuers!

---

### Post by ThrobbingBrain66 on 2007-07-01
In System > Adminstration > Login Window > Security Tab you can tick the automatic login box and select your user.  This will automatically log you in, but you'll have to enter your password.

Or

You can install a package from the repos called libpam-keyring. You then have to edit a file:
```
gksu gedit /etc/pam.d/gdm
```
and add the following line at the end of the file:
```
@include common-pamkeyring
```

This won't ask you for a password, but you'll have to do a regular login.  Unfortunately, there's not a way to have both....yet.

---

### Post by truico on 2007-07-01
=D>Dear keyring victims, I wrestled all day to get in FF my wireless working (Yes, also after re-boot). Finally I did a new install of FF on my Ahtec with a Intel/Pro 3945. Network manager was as fickle as before: did not remember my keyring password, did not 'hold' the wep key, connected sometimes and sometimes not. If this is familiar to you guys/gals, do yourself a favour, download wifi-radar  asap:

sudo apt-get install wifi-radar 

as a back up.

Or: go Applications-Ad/Remove, Search: wifi-radar in All Available Applications and apply Wifi-radar

for the Network Manager by default is not good enough (yet).](*,)

---

### Post by sailor.nir on 2007-07-02
Does wifi-radar have all the functionality and interface options of NM? Does it not use a keyring?

Does anyone know why NetworkManager was selected to be included in Ubuntu then?

---

### Post by truico on 2007-07-02
> Does wifi-radar have all the functionality and interface options of NM? Does it not use a keyring?
Haven't tried everything out yet, but NO KEYRING. Although Wifi-radar is very simple and a bit slow, it is stable enough.  I'm afraid Network Manager is somewhere in conflict with itself and it beats me why it was put into 7.04... To keep us all here communicating???:lolflag:

---

