---
title: "Kiba Dock"
date: 2007-12-05
forum: General Help
---

### Post by onlyproductions on 2007-12-05
is there any really easy way to install kiba dock or something similar on feisty

---

### Post by barney_1 on 2007-12-07
it's in the repositories:

```
sudo apt-get install kiba-dock
```

---

### Post by santiagoward2000 on 2007-12-11
Actually, kiba is not on Ubuntu's repository, you have to add [Treviño's repository]("http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/eyecandy/").

Just open **System / Software Sources**, go to the **Third-Party Software** and add:
```
 deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Then, open a Terminal and type:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Now yes, you can install it by typing:
```
sudo apt-get install kiba-dock
```

Cheers!

---

