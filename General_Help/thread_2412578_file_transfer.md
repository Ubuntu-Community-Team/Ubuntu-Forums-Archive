---
title: "file transfer"
date: 2019-02-14
forum: General Help
---

### Post by j3984 on 2019-02-14
from Google Nexus 7 tablet earlier model to Ubuntu 14.04 via USB
How do I transfer downloaded files in a Google Nexus 7 tablet to Ubuntu 14.04?

---

### Post by TheFu on 2019-02-14
[https://askubuntu.com/questions/785834/how-do-i-transfer-files-to-and-from-nexus-7-ubuntu-14-04](https://askubuntu.com/questions/785834/how-do-i-transfer-files-to-and-from-nexus-7-ubuntu-14-04) was found via google for "Nexus 7 tablet ubuntu udev 14.04"

Does that help?  There are a few links in the answer about modifying udev rules. I vaguely remember having to do that for my Nexus4.

If the USB method doesn't work, you can use a network connection to transfer the files. Setup openssh-server on the ubuntu machine, then using any Android sftp client to connect to it and pull the files over.  This is generally how I move file over.

---

### Post by him610 on 2019-02-14
Not sure about 14.04, but in 18.04 install package mtp-tools. It works for both Nexus 7 and Android phones. There are some configuration changes you need to make in the Nexus 7 settings to allow transfer of files and photos.

---

### Post by ssreddy555 on 2019-02-16
Can use KDE connect or Air Droid.

---

