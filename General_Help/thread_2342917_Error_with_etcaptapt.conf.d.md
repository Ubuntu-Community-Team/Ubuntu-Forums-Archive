---
title: "Error with /etc/apt/apt.conf.d/"
date: 2016-11-11
forum: General Help
---

### Post by checoimg on 2016-11-11
When I do [B]apt-et -f install
[/B]
I get this line :

N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/'34


What should I do ?

[IMG]http://i1085.photobucket.com/albums/j436/checo_evo/Untitled_1.png[/IMG]

Thanks in advance

---

### Post by howefield on 2016-11-11
It's more informational than an actual error. Move the file to your Documents folder in case you want to use it later.

---

### Post by ian-weisser on 2016-11-11
Your unattended-update settings changed, usually during a release-upgrade.
Your old settings are preserved in that file.

If you prefer the old settings, restore from that file.
If you prefer the new settings, delete the old file.
If you don't have a preference, live with the warning for a few weeks until you do have a preference.

---

