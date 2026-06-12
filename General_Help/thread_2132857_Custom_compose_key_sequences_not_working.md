---
title: "Custom compose key sequences not working"
date: 2013-04-06
forum: General Help
---

### Post by potion on 2013-04-06
Hi, I'm trying to customize the compose key sequences, and I can't get it to work. Here's what I've done, following the instructions at the bottom of [this page]("https://help.ubuntu.com/community/ComposeKey"):

1. I modified both /etc/environment and ~/.gnomerc to include the line...

```
export GTK_IM_MODULE="xim"
```

(The only reason I added the line to both is that it wasn't working.)

2. I copied /usr/share/X11/locale/en_US.UTF-8/Compose and saved it in the home directory as .XCompose

3. I tried adding some lines to the file. So for example, I added...

```
<Multi_key> <i> <i>			: "&#618;"	U026A
```

That seems to be in the exact same format as the other lines.

But nothing is working! The compose key and the usual sequences all work, but the custom sequences don't. Can anyone tell me what I'm doing wrong? I'm running 12.10, by the way. Thanks for your help!

---

### Post by potion on 2013-04-09
Hopeful bump. :)

---

### Post by potion on 2013-04-10
Never mind, it started working all of a sudden. Wish I could explain how, but I'm not actually sure. Anyway, the above instructions did end up working for me.

---

