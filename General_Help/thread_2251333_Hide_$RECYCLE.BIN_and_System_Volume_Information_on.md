---
title: "Hide $RECYCLE.BIN and System Volume Information on mounted Windows shared drive"
date: 2014-11-03
forum: General Help
---

### Post by Miguel_Santos on 2014-11-03
Hi everyone,

I'm mounting a Windows shared drive on Ubuntu and I'd like the "$RECYCLE.BIN" and "System Volume Information" folders not to show when i do a ls command on its mount point.
How can I do this?

Thanks!

---

### Post by CaptainMark on 2014-11-03
Well in short, you can't.


You can place a period (full stop) at the start of their name and they will become 'hidden' folders but then of course your windows machine will get confused that they appear to be missing, because ".file.txt" is not the same as "file.txt" however similar it may look to us.
You can hide them from appearing in the file manager by typing the name into a file named ".hidden" in the directory they appear, but this won't affect the ls command.

Apologies for the egg sucking tutorial if you already knew this.

---

