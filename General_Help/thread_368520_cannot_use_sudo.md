---
title: "cannot use sudo"
date: 2007-02-23
forum: General Help
---

### Post by naseem on 2007-02-23
hy i messup the etc folder permissions and now if I use sudo I get sudo: /etc/sudoers is mode 0460, should be 0440
how to solve this:( 
If I use ~$ sudo chmod  /etc/sudoers 0440
sudo: /etc/sudoers is mode 0460, should be 0440
again i feel locked
please help!!!!!!!

---

### Post by taurus on 2007-02-23
Boot into recovery mode from GRUB menu and at the prompt, type

```
chmod 440 /etc/sudoers
shutdown -r now
```

---

### Post by naseem on 2007-02-23
now Im gonna trie, the trouble is that I think I messed the all etc folder ?recursivli? so shall I do it now or shall I add more instruction to that comand:confused:

---

### Post by naseem on 2007-02-23
:guitar:  yes great!!!!
thank you!!!
now it sems allright

---

### Post by taurus on 2007-02-23
Please be real careful with the permissions outside $HOME.  If you change it wrong, then you can trash the whole system.  Therefore, try not to use the chmod command outside of $HOME and ask first if you are not sure what to do things.

---

