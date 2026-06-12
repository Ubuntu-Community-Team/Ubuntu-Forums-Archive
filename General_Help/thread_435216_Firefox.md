---
title: "Firefox"
date: 2007-05-06
forum: General Help
---

### Post by Robbyx on 2007-05-06
I am trying to run the firefox profilemanager but I  have failed to find the directory with the program.  How do I run the firefox profilemanager?

Robin

---

### Post by KeeNeR on 2007-05-06
firefox-bin -p

---

### Post by Robbyx on 2007-05-07
Could you please give me that in a longer form because as typed ino Alt F2/ terminal it did not work.

---

### Post by dj9866 on 2007-05-12
You can find the path to firefox-bin by executing 'updatedb' in a terminal window.  After completion, execute 'locate firefox-bin' and the path will be displayed.  This is useful for finding any file.  Mine was at /usr/lib/firefox.  I used 'firefox -ProfileManager'  to launch the profile manager.

---

### Post by Robbyx on 2007-05-14
Thank  you for your help

---

