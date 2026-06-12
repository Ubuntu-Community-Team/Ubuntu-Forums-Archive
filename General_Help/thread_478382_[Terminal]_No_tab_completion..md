---
title: "[Terminal] No tab completion."
date: 2007-06-19
forum: General Help
---

### Post by Snakiej on 2007-06-19
Hiya, 

I just reinstalled Feisty, without formatting my /home.

Now I'm back, and I try to 'sudo apt-get install msttcorefonts'

Before the format I could enter 'sudo apt-get ins<tab> mstt<tab>' and then it would complete it by default.

None of this works, any way how to fix this? :)

Thank you :)

---

### Post by mitch.c on 2007-06-20
This is a function of programmable completion. Normally, the file /etc/bash_completion is sourced by your shell. If the file is not sourced, or does not exist... no completion. Start by checking ~/.bashrc for the following lines:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```
Then make sure that /etc/bash_completion exists, if not get it from the bash package, or download a copy here: [http://www.caliban.org/bash/#completion_download](http://www.caliban.org/bash/#completion_download)

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by Ansible on 2007-07-13
In my /etc/ folder I have /bash_completion.d/  is this related, should it be renamed?  Is this supposed to be on by default in ubuntu, or is this typically something that you have to install?  I just did a fresh install of 7.04, the only things I've done since have been to run the envy script and install VLC player.

---

