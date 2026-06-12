---
title: "What is wrong with my commands?"
date: 2017-06-27
forum: General Help
---

### Post by dragomar on 2017-06-27
Those directories and files most certainly do exist... Got no idea what I'm doing wrong here...

[IMG]http://i.imgur.com/2vjGRY3.png[/IMG]

---

### Post by howefield on 2017-06-27
Thread moved to the "*General Help*" forum.

It is better to copy/paste terminal input and output back here as text rather than post an image.

Try using a leading / before the path.. ie, /etc/lightdm/lightfm.conf, the error is telling you the directory is non existent.

---

### Post by deadflowr on 2017-06-27
No need to run with sudo if already root.
It's redundant.

---

### Post by QIII on 2017-06-27
Bad idea to run as root anyway when poking around in user cam's /home.  Cam will come home to find random things owned by root.

Bad idea to sign in as root in general.

---

### Post by lisati on 2017-06-27
Here's some information on root and sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by steeldriver on 2017-06-27
Your basic error is missing the leading / from the path

```

[COLOR=#0000ff]**/**[/COLOR]etc/lightdm/lightdm.conf

```

However FWIW I think it's considered better practice to create a custom file in /etc/lightdm/lightdm.conf.d/

---

