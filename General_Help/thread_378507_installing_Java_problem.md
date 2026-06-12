---
title: "installing Java problem"
date: 2007-03-07
forum: General Help
---

### Post by geovino on 2007-03-07
How do I install java?

 I'm trying to adding a couple programs in add and remove and it hangs up and tells me that I need java 1.4.2 I downloaded it, now how to install it?

/home/davek/Downloads/j2sdk-1_4_2_13-linux-i586.bin

why would I have to do this in the first place? It should already be installed. I have to reboot now because the add/remove program is frozen.

...after rebooting and going to Synaptic I get this message:
davek@davek-desktop:~$ sudo dpkg --configure -a
Password:
Setting up tcl8.4 (8.4.12-1.1) ...

Setting up xchat-common (2.6.6-0ubuntu3) ...

Setting up j2sdk1.4-doc (1.4.2.02-1ubuntu3) ...
warning: file `/usr/share/doc/j2sdk1.4-doc/1.4.2/index.html' does not exist at /usr/sbin/install-docs line 821, </usr/share/doc-base/j2sdk1.4-doc> line 11.
warning: file mask `/usr/share/doc/j2sdk1.4-doc/1.4.2/*/*.html' does not match any files at /usr/sbin/install-docs line 826, </usr/share/doc-base/j2sdk1.4-doc> line 11.
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

How do get this to work? The above command no + Return doesn't work either. 

Please help.

Thanks

---

