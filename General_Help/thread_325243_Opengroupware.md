---
title: "Opengroupware"
date: 2006-12-25
forum: General Help
---

### Post by drito on 2006-12-25
I would like to install Opengroupware, but when I tried:

```
sudo aptitude install opengroupware
```

I got message to try gnustep-make-ogo. So I tried:

```
sudo aptitude install gnustep-make-ogo
```

What should I do next?

---

### Post by lothar_m on 2007-02-25
well i did (on debian):

i) edit /etc/apt/sources.list
ii) added
 ```
deb http://download.opengroupware.org/nightly/packages/debian sarge trunk
```
iii) apt-get update
iv)apt-get install opengroupware.org

never tried this in ubuntu.

---

### Post by itzpapalotl on 2007-09-17
Me 2 Me 2. I have got to get opengroupware working on Dapper. Their site says to do it like a Sarge setup. So okay. That's the Repo. I'm going to give this a shot and see if it works. If anybody has any expirience getting opengroupware to work under Dapper, please chime in. This is the last chunk of a big puzzle!.

---

