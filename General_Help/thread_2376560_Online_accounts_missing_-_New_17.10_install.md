---
title: "Online accounts missing - New 17.10 install"
date: 2017-11-03
forum: General Help
---

### Post by obiwanjakeobi on 2017-11-03
Hi all, I recently installed Ubuntu 17.10, and in the process of trying to setup Evolution went looking for the Online Accounts app.
Its missing in Settings and when launching gnome-control-center, the menu comes up blank.
Ive tried a uninstall\reinstall of control-center, online-accounts and Ubuntu-desktop, and nothing.
Funny thing is two days ago, on a different machine, this option existed and I install Evolution and got up and running with no issues.

Any help would be greatly appreciated. I am a novice Linux user.

---

### Post by Frogs Hair on 2017-11-03
Hello and Welcome

Install the dconf editor and navigate to org/gnome/online-accounts and see if all providers are whitelisted. This is the default setting.


```
sudo apt install dconf-editor
```

---

### Post by jbicha on 2017-11-04
Are you using the default Ubuntu desktop?

Did you install any other desktop environments?

Did you upgrade from a previous install?

---

### Post by bendecksuarez on 2018-03-14
Same problem with my Ubuntu 16.04. The "Online Accounts" is missing in the Settings.

---

### Post by bendecksuarez on 2018-03-14
Install gnome-online-accountsjust use "sudo apt-get install gnome-online-accounts"

---

