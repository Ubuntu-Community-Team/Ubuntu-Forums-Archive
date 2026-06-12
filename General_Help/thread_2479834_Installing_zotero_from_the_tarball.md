---
title: "Installing zotero from the tarball"
date: 2022-10-09
forum: General Help
---

### Post by drpjkurian on 2022-10-09
Dear members
I am sharing my experience of installing Zotero in my Ubuntu 22.04. My experience might help others to install it.
I downloaded the tarball from the Zotero website. I extracted the tarball to my Downloads by right clicking the downloaded folder; and selecting the 'extract here' from the pop-up menu. I opened a terminal and used the command to navigate to the Downloads folder. ```
cd Downloads
``` I moved the extracted folder to the opt folder using the terminal command:  ```
sudo mv -v Zotero_linux-x86_64 /opt/zotero/
```

To create the launcher, I used the following commands
```
cd
```
```
/opt/zotero/set_launcher_icon

```
```
ln -s /opt/zotero/zotero.desktop ~/.local/share/applications/zotero.desktop
```
It took a whole day today to figure out the commands. Hope these instructions will save your day.

---

### Post by dragonfly41 on 2022-10-09
You need two downloads.
The desktop app
and
The browser connector which is installed into the browser.
And of course the Zotero Discussion Group.

there are other plugins to be explored to integrate with other apps.

[https://www.zotero.org/support/plugins](https://www.zotero.org/support/plugins)

---

