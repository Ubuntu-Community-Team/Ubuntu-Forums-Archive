---
title: "Default keyboard layout"
date: 2006-10-21
forum: General Help
---

### Post by vmalep on 2006-10-21
Hi,

I now this is a very simple question, but I failed finding an answer on Internet...

Where is the parameter for the default keyboard in Ubuntu (or Debian)? I mean the keyboard layout used in the console (Ctrl-Alt-F1, etc), not in the graphical session.

From one distrib to another, the paramter is written in different places and I am still looking for it in Ubuntu.

Thanks in advance,
Pierre

---

### Post by Sef on 2006-10-21
Do you mean keyboard shortcuts?  System > Preferences > Keyboard Shortcuts

---

### Post by vmalep on 2006-10-21
No, I mean the keyboard layout (us, fr or ch) when you are in the console (Ctrl-Alt-F1), not in the graphical interface.

---

### Post by vmalep on 2006-10-22
Ok, so I eventually found (by looking in /etc/init.d/keymap.sh): it is the file /etc/console/boottime.kmap.gz

The solution was to rename that file and to create a symlink with the same name to the right keyboard mapping from /usr/share/keymaps/...

Thanks anyway,
Pierre

---

### Post by unless on 2006-10-24
Thanks for posting your discovery... You just saved me a ton of time... And a few hairs.

A+

---

### Post by cilynx on 2006-12-20
The official *buntu solution used to be
```

sudo dpkg-reconfigure console-data

```
but that's been superceeded by
```

sudo dpkg-reconfigure console-setup

```
console-data is still around, but updating the configurating won't fix anything anymore.

---

### Post by MasterOfMuppets on 2007-02-12
I don't have console-data, but he second command you mentioned worked for me, and I changed the codeset to Hebrew (the 2nd language I need) and nothing happened :/...

---

