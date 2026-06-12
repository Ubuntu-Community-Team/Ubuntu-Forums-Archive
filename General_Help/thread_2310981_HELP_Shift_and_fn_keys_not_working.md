---
title: "HELP Shift and fn keys not working"
date: 2016-01-23
forum: General Help
---

### Post by gabriel69 on 2016-01-23
Hi,

UPDATE title[SIZE=2] **'HELP Shift keys not working'** [/SIZE]  fn it's ok! 

I can't use 'shift' on my Asus x201e notebook. It's a fresh install of Ubuntu. 
After some time, the key doesn't work anymore. It's a 'qwerty' Portuguese keyboard.

I tested keyboard key listeners with:
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'

and it's not detecting this key when I press it.
I think it's a bug in the kernel or compiz. Any solutions? I'm using a UTF-8 char table to work 'copy/paste', but I'm working very slow this way.

Thank you.

---

### Post by gabriel69 on 2016-01-23
Any idea?

I tried  
sudo apt-get update and sudo apt-get upgrade
Remove all languages from configuration and maintain the Portuguese.
ibus-setup
Remove bus from keyboard entry mode
sudo dpkg-reconfigure keyboard-configuration...

Nothing worked.  And its the both shift keys.

---

