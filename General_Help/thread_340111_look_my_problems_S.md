---
title: "look my problems :S"
date: 2007-01-16
forum: General Help
---

### Post by BlackHero on 2007-01-16
hi ppl i have this problem when i click on any services (ex networking,services,shared folders etc)    apear this windows :S help me i need change my lan config 

screenshot

---

### Post by taurus on 2007-01-16
Open a terminal and types these two commands.  See if you get any error message especially the second one.

```
id
sudo apt-get update
```

---

### Post by BlackHero on 2007-01-16
W: GPG error: [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems



when i write sudo apt-get update

---

### Post by taurus on 2007-01-16
Edit /etc/apt/sources.list and place a # in front of [http://seveas.imbrandon.com](http://seveas.imbrandon.com) to comment it out for now.  Then see if you can update it again.

```
sudo nano -w /etc/apt/sources.list
(Hold down <Ctrl> while pressing x to exit.  Type Y for yes and then Return...)
sudo apt-get update
```

---

### Post by dexter on 2007-01-16
Do you have sudo rights ?

---

### Post by BlackHero on 2007-01-16
thnks i fix the key error but the fisrt error is here i can t open networking or services or shared folders :S

---

