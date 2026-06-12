---
title: "numlock in ubuntu 18.10"
date: 2019-01-02
forum: General Help
---

### Post by alain.roger on 2019-01-02
Hi,

i have installed a fresh version of KUbuntu 18.10 on laptop but on login screen the numlock is not ON even if i set it in settings.
for an unknown reset the numlockx is not working.

Someone already solved this issue as GDM user does not exist in KUbuntu ?

thx

---

### Post by clementc on 2019-01-02
Hi [**alain.roger**]("https://ubuntuforums.org/member.php?u=1337364"),

After making sure that the numlock option is still set to ON in the settings, can you please try running the following command then restart your PC and confirm if it has worked or not:

sudo sed -i s/Numlock=none/Numlock=on/ /etc/sddm.conf

---

### Post by alain.roger on 2019-01-04
Hi,

unfortunately, it did not work but i discovered that in the /etc/sddm.conf file i had to add

```
Numlock=on[FONT=sans-serif] in the [/FONT][General][FONT=sans-serif] section

```
and everything works as expected.[/FONT]

---

### Post by clementc on 2019-01-04
Hi [**[COLOR=#000000]alain.roger[/COLOR]**]("https://ubuntuforums.org/member.php?u=1337364"),

I am glad to hear that you managed to resolve your issue.

The command listed in my previous post assumed that Numlock=none was already present in /etc/sddm.conf and therefore replaced it with Numlock=on.

---

