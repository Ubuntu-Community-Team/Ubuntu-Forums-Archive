---
title: "Updating Open Office"
date: 2014-08-27
forum: General Help
---

### Post by gordon99 on 2014-08-27
I am running on Xubuntu 14.04
I have Apache Open Office v.4.1.0 already installed. I wish to update to v.4.1.1 and to this end have the 4.1.1 folder 'en-GB' in downloads.
How should I proceed to replace the old version with the new please?

---

### Post by azgrel on 2014-08-27
Open terminal and change the directory to where you have downloaded AOO, then type
```

sudo dpkg -i en-GB/DEBS[COLOR=#008000]/*.deb
[/COLOR]
```
and
```

sudo dpkg -i en-GB/DEBS/desktop-integration[COLOR=#008000]/*.deb
[/COLOR]
```[COLOR=#008000]
[/COLOR]

---

### Post by gordon99 on 2014-08-27
Thank you very much azgrel. Your precise instruction has worked 100%. I am very obliged.

---

