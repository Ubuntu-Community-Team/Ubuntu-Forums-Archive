---
title: "where is the location of .emacs?"
date: 2007-11-02
forum: General Help
---

### Post by fyplinux on 2007-11-02
Hi,

I am using Ubuntu 7.10 with emacs 21.4a(X11) installed, I searched the whole system, I didnt find the .emacs file.

I used the "global-set-key" function to set a key binding, I thought this configuration should be saved in the profile, but there is no such a file, then, How this be done?

thanks

---

### Post by zvacet on 2007-11-02
Did you try this

```
cd /
```

```
sudo find / -name *emacs*
```

---

### Post by vambo on 2007-11-02
It's in your home directory  ~/.emacs

---

### Post by snickers295 on 2007-11-02
its in /home/<username>/.emacs or something similar.

---

### Post by mali2297 on 2007-11-02
> **fyplinux said:**
> Hi,

I am using Ubuntu 7.10 with emacs 21.4a(X11) installed, I searched the whole system, I didnt find the .emacs file.

I used the "global-set-key" function to set a key binding, I thought this configuration should be saved in the profile, but there is no such a file, then, How this be done?

thanks

**.emacs** should be found directly under the home directory if it has been created. Note that the file is hidden. To show hidden files with the ls command, type
```

ls -a

```
(Filemanagers also have an option to show hidden files.)

If you haven't got that file, perhaps you didn't to save your settings properly. Look for an entry in the menus to save options.

---

### Post by fyplinux on 2007-11-02
Thank you , guys.

I found it's because the options were not saved, so, I cannot find the .emacs file.

---

### Post by snickers295 on 2007-11-03
please mark this thread as Solved by using the Thread Tools at the top right corner of the thread.

---

### Post by strabes on 2007-11-03
```
locate .emacs
```
/usr/share/gtkhtml-3.14/keybindingsrc.emacs

---

