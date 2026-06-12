---
title: "Login as root using FreeNX"
date: 2005-06-14
forum: General Help
---

### Post by SGC on 2005-06-14
When I try to login as a root to kubuntu from windows using nomachine windows client, I got the following message: "you cannot login as root"

Is there is a workaround to that or other freenx windows clients that can log as a root.

---

### Post by ubuntu_demon on 2005-06-15
You should never log in as root ..  use sudo instead

---

### Post by SGC on 2005-06-15
[QUOTE=demon666_nl]You should never log in as root ..  use sudo instead[/QUOTE]
 I always login as root  (2 months know), I know about the securety isuues but its more convenient.

---

### Post by ubuntu_demon on 2005-06-15
It doesn't cost very much time to type sudo and type your password once in a while (it will remember it for a while .. and this time CAN be customized)

---

### Post by SGC on 2005-06-15
[QUOTE=demon666_nl]It doesn't cost very much time to type sudo and type your password once in a while (it will remember it for a while .. and this time CAN be customized)[/QUOTE]
 I tried that for a whole month, and I almost was giving up on linux, Its annoying  to see the password popup for eveything (synaptic, kcontrol, kpackage,...) even you can't apt-get anything without typing the paswword.

---

### Post by ubuntu_demon on 2005-06-15
$sudo visudo

and adding this line beneath # Defaults
 will set timeout to 30 instead of default 15 minutes :

Defaults:ALL timestamp_timeout=30

---

### Post by SGC on 2005-06-15
[QUOTE=demon666_nl]$sudo visudo

and adding this line beneath # Defaults
 will set timeout to 30 instead of default 15 minutes :

Defaults:ALL timestamp_timeout=30[/QUOTE]
 I didn't know about that, I try it and it works, thanks, But still I prefere to login as root.

Is there is away to login as root with freenx?

---

