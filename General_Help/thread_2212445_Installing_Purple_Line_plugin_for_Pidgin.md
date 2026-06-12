---
title: "Installing Purple Line plugin for Pidgin"
date: 2014-03-21
forum: General Help
---

### Post by Matt M on 2014-03-21
I'm trying to install the Purple Line plugin for Pidgin ([https://github.com/mvirkkunen/purple-line](https://github.com/mvirkkunen/purple-line)) on Xubuntu 13.10. On typing the "make" command, I get this error message:

make: *** No rule to make target `thrift_line/line_constants.o', needed by `libline.so'. Stop.

I found the following advice on the problem for Arch Linux: ([http://forums.archlinux.fr/topic15128.html](http://forums.archlinux.fr/topic15128.html) -- it's in French, but Google Translate does a good job of making it fairly comprehensible for English speakers): it mentions the thrift-cpp and thrift-base packages, which seem to be either unavailable in Ubuntu or have other names.

Can anyone help me with this problem?

---

### Post by cybernetic12 on 2014-05-29
The tar ball is not new enough.
You have to download the latest repo:
    git clone [https://git-wip-us.apache.org/repos/asf/thrift.git](https://git-wip-us.apache.org/repos/asf/thrift.git)
then run the script ./bootstrap.sh
This is described on the install page.

PS:  But after I succeeded in making the plugin, Pidgin cannot start.  Still unsure how to solve it...

---

### Post by Matt M on 2014-05-29
Thanks... keep us posted on any success you have and how you solved the problem...

---

