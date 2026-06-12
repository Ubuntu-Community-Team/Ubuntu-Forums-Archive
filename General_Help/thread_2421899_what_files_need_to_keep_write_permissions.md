---
title: "what files need to keep write permissions?"
date: 2019-06-28
forum: General Help
---

### Post by Skaperen on 2019-06-28
i am trying to maximize the number of files i make read-only, especially in /bin, /etc, /lib64, /sbin, and /usr.  i am leaving /var unchanged.  is there a decent resource to find out what files need to keep existing write permissions?

i have already changed my development files to all read-only and modified my edit wrapper script to change the file to writable for the duration of editing it.

---

### Post by Impavidus on 2019-06-29
What's the point? Most system files are already read-only for all users except root. The owner of a file can always give himself write permission, so making a file read-only for the owner only helps against accidental edits. You'll probably confuse the package manager.

---

### Post by HermanAB on 2019-06-29
If you are worried about access control, enable AppArmor.

---

### Post by Skaperen on 2019-07-02
AppArmor is already enabled.

---

