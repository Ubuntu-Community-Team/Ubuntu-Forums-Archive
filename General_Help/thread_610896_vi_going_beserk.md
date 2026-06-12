---
title: "vi going beserk"
date: 2007-11-12
forum: General Help
---

### Post by the_dark_light on 2007-11-12
This is a problem I've encountered on a fresh installation of Gutsy.

In previous versions of ubuntu, vim has behaved itself.  I press the insert key, edit text, move the cursor with the arrow keys etc etc

After installing (fresh, not an upgrade) Gutsy on my desktop system vi(m) seems to be acting odd.  Well ok, going beserk.

The insert key no longer indicates that I'm in insert mode
Then moving the arror keys does not move the cursor.  Instead it inserts a new line and as capital letter (up becomes A, down B, right C, left D)

the only time I've ever encountered this was when I (very) briefly tried out FreeBSD

Can anyone help, please :confused:

---

### Post by kellemes on 2007-11-12
[http://ubuntuforums.org/showthread.php?t=368129]("http://ubuntuforums.org/showthread.php?t=368129")

---

### Post by geirha on 2007-11-12
This is the behaviour of vi. Either you are using vi, or you are using vim in vi-compatibility mode. ```
md5sum `which vi vim`
``` Does vi and vim have the same checksum? and do you run **vi** or **vim** to start the editor?

---

### Post by aJayRoo on 2007-11-12
I usually install the package 'vim-full' after a fresh install. Its a fairly big set of packages but if you have hard disk space to spare then it is worth it to get the functionality you are used to. If you do this then there will also be a fairly good template vimrc file located at '/usr/share/vim/vim71/vimrc_example.vim' which you can copy to your home directory as '.vimrc' and make any changes you need. Thats what I usually do anyway.

---

### Post by the_dark_light on 2007-11-13
That sorted it.  Thanks :)

---

