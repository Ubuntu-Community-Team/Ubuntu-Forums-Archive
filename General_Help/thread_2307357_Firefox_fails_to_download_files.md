---
title: "Firefox fails to download files"
date: 2015-12-24
forum: General Help
---

### Post by enboig on 2015-12-24
I have two users on my laptop, on of them fails to download files using firefox, but works with chrome. I tried deleting ~/.mozilla but the error persists.

Any hint? it shouldn't be a permission issue because chrome can write to ~/Download, and it shouldn't be a profile issue because it was just regenerated.

PS: I am using xubuntu 14.04

---

### Post by bapoumba on 2015-12-25
Hello, may be a few steps to try here ? (not all apply to Linux).
[https://support.mozilla.org/en-US/kb/cant-download-or-save-files](https://support.mozilla.org/en-US/kb/cant-download-or-save-files)

---

### Post by yoshii on 2015-12-25
Maybe try using bleachbit (downloaded from Ubuntu Software Center) to clear out the Mozilla Fire cache and reset various other options.  It won't delete your preferences or anything but it can clear out cookies too and do some technical stuff that might fix it.  It can't be run while FireFox is running, you have to quit FireFox first.  Also, there are two modes that can be run, one as root, and one as the user.  Use both of them to get the jobs done.

---

### Post by enricobe on 2015-12-26
You can try to change the downloads default folder from preferences. Or maybe you can set the "ask me where to save files" option so you can choose the folder where you want to save files and check if it works

---

