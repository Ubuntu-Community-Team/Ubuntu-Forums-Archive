---
title: "Error while booting udevd[372]: NAME=&quot;%k&quot;"
date: 2013-03-14
forum: General Help
---

### Post by geraldanand on 2013-03-14
Hi,

I recently encounter a problem whereby when I start to boot it shows this error.
fsck from util-linux 2.20.1
[COLOR=#ff0000]udevd[372]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /etc/udev/rules.d/99-disable-persistent-net.rules:1

[/COLOR]I tried to delete NAME="%k" in the file /etc/udev/rules.d/99-disable-persistent-net.rules:1 but can't because it's a read only file. Even tried to chmod -r 777 but still unable to change the file permission.
Please help, is there any other way that this error ([COLOR=#FF0000]udevd[372]: NAME="%k") [/COLOR]can be resolved? Or anyway I can change the file permission to try to remove that particular string there.

---

