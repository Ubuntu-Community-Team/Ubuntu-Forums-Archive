---
title: "Duplicate Icon in App Chooser"
date: 2018-12-30
forum: General Help
---

### Post by huckle.smothered on 2018-12-30
I have two calculator icons. One does not work. When I right-click and select show details, it takes me to the software center but cant find it. The other icon, looks the same, is the proper gnome-calculator and works fine.

How do I get rid of the one that doesn't work?

Recently installed 18.10. Kept my old /home directory as it was on a different partition. Reinstalled over the old 18.04 partition.

---

### Post by clementc on 2018-12-31
Hi [**[COLOR=#000000]huckle.smothered[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115173"),

Can you please check the following directories on your system and see if you have any duplicate files for gnome-calculator (.desktop extension):

/var/lib/snapd/desktop/applications/
/usr/share/applications/
$HOME/.local/share/applications/

---

### Post by huckle.smothered on 2019-02-01
The culprit was /var/lib/snapd/desktop/applications. There were a few items there (gnome-monitor, gnome-logs, ...). When I did a search for these they did not run. Granted, they were duplicated like gnome-calculator was.

Either way, I removed the snapd directory as I removed snap earlier anyway. The dead icons disappeared and everything works as expected now.

Thank you.

---

