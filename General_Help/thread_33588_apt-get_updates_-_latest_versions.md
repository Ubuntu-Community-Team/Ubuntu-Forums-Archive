---
title: "apt-get updates - latest versions"
date: 2005-05-11
forum: General Help
---

### Post by Zelut on 2005-05-11
Noticed that gaim now has 1.3 vs the 1.2.1 that is included in the apt-get repositories.  Any idea on how long it takes for those updates to be placed where we can find 'em?

---

### Post by lt_kije on 2005-05-11
As far as I know, feature upgrades of existing packages don't happen between major releases of Ubuntu. That said, compiling the app yourself or installing .debs made by someone else (or found in Debian sid) often work well, too. Unless this is a security fix, I doubt it'll make it into the Hoary repos before the next release.

lt_kije

---

### Post by Zelut on 2005-05-11
[QUOTE=lt_kije]As far as I know, feature upgrades of existing packages don't happen between major releases of Ubuntu. That said, compiling the app yourself or installing .debs made by someone else (or found in Debian sid) often work well, too. Unless this is a security fix, I doubt it'll make it into the Hoary repos before the next release.

lt_kije[/QUOTE]
 Well I could compile it myself but I prefer using the .deb packages for easier update / removal.  Does anyone know where a .deb can be found?  The gaim site only has .rpms...

---

### Post by lt_kije on 2005-05-11
They just released yesterday -- I doubt debs will be available for a bit. You might want to encourage the Gaim developers to provide their own debs, too; that, or make one yourself (see [http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper](http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper)).

lt_kije

---

### Post by wwwolf on 2005-05-11
[QUOTE=kuyaedz]Well I could compile it myself but I prefer using the .deb packages for easier update / removal.  Does anyone know where a .deb can be found?  The gaim site only has .rpms...[/QUOTE]

You could always run alien on the .rpm. This would then give you a .deb package that could be easily managed then.

---

### Post by Zelut on 2005-05-14
[QUOTE=wwwolf]You could always run alien on the .rpm. This would then give you a .deb package that could be easily managed then.[/QUOTE]
 I'm not familiar with alien.  Can you give me an example command to run alien on a .rpm to create a useable .deb package?

thanks

---

### Post by rpgcyco on 2005-05-14
Gaim v1.3.0 is available in the backports repositry.

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Add...

```
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
```

...to the /etc/apt/sources.list file.

```
sudo gedit /etc/apt/sources.list
```

Then...

```
sudo apt-get update
sudo apt-get install gaim
```

Hope that helps,
- Rpg Cyco

---

### Post by bolamix on 2005-05-14
[QUOTE=kuyaedz]I'm not familiar with alien.  Can you give me an example command to run alien on a .rpm to create a useable .deb package?

thanks[/QUOTE]
 Hi yall

To use alien: ```
cd directory_where_example.rpm_resides
sudo alien example.rpm
sudo dpkg -i example.deb
```

---

