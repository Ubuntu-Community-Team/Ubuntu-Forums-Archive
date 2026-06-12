---
title: "apt-get blacklist"
date: 2008-05-01
forum: General Help
---

### Post by eriqjaffe on 2008-05-01
I've run into some issues with samba that require me to [keep an older version](http://ubuntuforums.org/showthread.php?p=4822817#post4822817) on my systems - however, whenever I try to apt-get upgrade, it wants to replace them with the current versions...which don't work for me.

Is there a way of blacklisting these packages so that when I try to upgrade via apt-get, it'll ignore them and process the rest?  A text file or something somewhere?

I tried locking the packages in Synaptic, but that didn't seem to do anything to apt-get.  Also...I don't even have Synaptic on my older laptop, so even if that fix **did** work, it still wouldn't really help me.

---

### Post by warp99 on 2008-05-01
> **eriqjaffe said:**
> I've run into some issues with samba that require me to [keep an older version](http://ubuntuforums.org/showthread.php?p=4822817#post4822817) on my systems - however, whenever I try to apt-get upgrade, it wants to replace them with the current versions...which don't work for me.

Is there a way of blacklisting these packages so that when I try to upgrade via apt-get, it'll ignore them and process the rest?  A text file or something somewhere?

I tried locking the packages in Synaptic, but that didn't seem to do anything to apt-get.  Also...I don't even have Synaptic on my older laptop, so even if that fix **did** work, it still wouldn't really help me.

Yes there is just run the following:

```
echo "foo hold" | sudo dpkg --set-selections
```
and that will hold the current package and not allow an update with apt-get unless it's a dist-upgrade. Now of course replace 'foo' with the name of your package. More info on the powerful apt-get package management tools can be viewed here:

[https://help.ubuntu.com/community/AptGet/Howto?highlight=%28apt-get%29](https://help.ubuntu.com/community/AptGet/Howto?highlight=%28apt-get%29)

and here:

[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by eriqjaffe on 2008-05-01
Thank you, I missed that page.

---

