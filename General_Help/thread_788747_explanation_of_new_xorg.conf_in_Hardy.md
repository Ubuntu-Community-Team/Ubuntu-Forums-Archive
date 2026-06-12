---
title: "explanation of new xorg.conf in Hardy"
date: 2008-05-10
forum: General Help
---

### Post by pytheas22 on 2008-05-10
The xorg.conf file in Hardy is very different than it was in earlier versions of Ubuntu and other Linux distributions.  As far as I can tell, most things are now supposed to be configured "on the fly" by the system, not specified explicitly in xorg.conf.  I understand the benefits of this, but there are still situations where I would like to override what the system thinks it should be doing--for example, if I have both the i810 and intel xorg drivers installed, how can I tell X which one it should be using?

So I was wondering if there's any good information anywhere on exactly how the new xorg.conf works and what can be put in it.  If I add certain values, will it follow them, or will X try to auto-configure stuff before looking at xorg.conf?  I can't find any good documentation on how this new version of X works; if anyone could point me in the right direction, it would be helpful.  Thanks in advance.

---

### Post by pointone on 2008-05-10
```
man xorg.conf
```

```
dpkg-reconfigure xserver-xorg -plow
```

---

### Post by sdennie on 2008-05-10
For information about what X is using, you could look in the file /var/log/Xorg.0.log.  The stuff you are interested in is probably towards the bottom.

As far as configuration, the Device section that describes my nvidia card still works exactly the same, and I was able to explicitly set things like Driver and various options on an intel machine in the section as well.  That's not a definitive answer but, it's something.

---

