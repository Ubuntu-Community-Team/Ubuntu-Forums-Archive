---
title: "[SOLVED] vi is useless when run with sudo (help!)"
date: 2007-08-21
forum: General Help
---

### Post by malachias on 2007-08-21
Hi

I like the text editor 'vi' a lot, especially when editing configuration files from the console... the only problem is that whenever I run it as root, it seems to be buggy. Everything seems to work fine until I hit 'i' to insert text. From then on the arrow-keys stop functioning normally. The UP arrow will insert the 'A' letter and a linefeed, DOWN will insert 'B' and a linefeed, RIGHT a 'C' and linefeed, LEFT a 'D' and linefeed. So for example:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
<snip>
```

Assuming I hit 'i' immediately, then hit down to go down to where I want to edit, I get

```
B
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
<snip>

```

with the cursor now right after the B (still on the top line). Does anybody else have this problem? Does anybody know how to fix it? It's not vital to my system as I can always spawn gedit's, but I'd really like to get it fixed.

Thanks!

---

### Post by tors on 2007-08-21
Have you checked if you have any vi configuration files in your home-directory which you don't have in roots home-directory?

.vim/
.vimrc

---

### Post by kellemes on 2007-08-21
vi isn't really made with arrowbuttons in mind.. although it may work.
You better use the "vi-way" of cursor movement..
h, j, k, l

---

### Post by reverendlinux on 2007-08-27
To fix this problem, do the following:

1.  sudo vi /etc/vim/vimrc.tiny
2.  Look for the line that says *set compatible*
3.  Change that line to read: *set nocompatible*
4.  Save and exit the file.

---

### Post by Lord Illidan on 2007-08-27
Or just install vim-full from apt-get.

---

### Post by malachias on 2007-08-29
Thanks everyone!

I personally used reverendlinux's solution, editing the /etc/vim/vimrc.tiny file, and it worked perfectly.
You guys rock.

---

