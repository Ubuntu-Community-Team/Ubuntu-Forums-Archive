---
title: "goutstream files"
date: 2013-08-22
forum: General Help
---

### Post by kimberley2 on 2013-08-22
Since downloading 12.4, files entitled 'goutstream' have appeared in the home folder. Before the forum went offline there were several threads mentioning this problem but now I cannot find a single one!

Has this problem been fixed or is there a way to delete them en masses?

Many thanks to someone who can come up with an asnwer.):P

---

### Post by mc4man on 2013-08-22
see here for bug (not fixed in 12.04 though no longer an issue in 13.04/.10
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)
various methods to rm in some replies ( a script, terminal command, ect.
I just shift click them all > delete from time to time.
It's possible that a patched glib in 12.04 would resolve..

---

### Post by Impavidus on 2013-08-23
I think you can avoid creation of those files by logging off before shutting down. However, it's easier to just delete them once a month or so. I always use the terminal (old habit, I use the terminal for all file management as I started using Unix on a machine that didn't have a graphical file manager):```
rm .goutputstream-*
```

---

### Post by VMC on 2013-08-23
I added an entry in "Startup Applications Preferences" to remove those files
```
#!/bin/bash
find . -type f -name ".gout*" -exec rm -f {} \;
``` Didn't know there was a bug report against it.
 First time I noticed anyone has complained. I'll have to check out that bug report. Thanks.

edit:actually I forgot about it, since I created that entry such a long time ago.

---

### Post by kimberley2 on 2013-08-24
Thank you mc4man - I shall do the same and delete from time to time until there is a more permanent solution

---

### Post by kimberley2 on 2013-08-24
Thank you for taking the time to respond. Think I will use a terminal command to remove them every so often.

---

### Post by kimberley2 on 2013-08-24
Thank you Impavidus. I shall use the terminal command as logging off before shutting down didnt seem to make any difference.

---

### Post by strimmer1 on 2013-11-22
".goutputstream" files are created when Xsane is building a multipage pdf or other variations. They are used during the build pdf file then should be deleated when the project is deleted. It looks like editing this file might allow appending additional ".pnm" files to a document, although I have not found a method that works.

---

### Post by a-you on 2014-07-15
Hi all. I too have often wondered about this, and then the other  day I happened to come across this in the apparmor profile for evince  (look in /etc/apparmor.d/usr.bin.evince):

# evince creates a temporary stream file like '.goutputstream-XXXXXX' in the
# directory a file is saved. This allows that behavior.
owner /**/.goutputstream-* w,

So now we know the source of those files!!!

Btw I'm using ubuntu studio trusty 64 bit but those files were piling up  in previous versions too, like definitely in quantal for example; I  don't recall whether I had that issue in natty, which was what I was  using before quantal, probably so though.

---

