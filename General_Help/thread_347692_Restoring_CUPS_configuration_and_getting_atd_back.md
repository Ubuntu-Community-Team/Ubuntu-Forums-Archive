---
title: "Restoring CUPS configuration and getting atd back"
date: 2007-01-27
forum: General Help
---

### Post by steevc on 2007-01-27
I had a few issues during a hardware upgrade. Somehow I broke cupsd to the extent that I had to uninstall/re-install it. It's running again now, but I can't print. When I installed I did not get the cupsd.conf file and I'll admit I did not back mine up. I've installed one I found on the web, but it's obviously not right. When I try to print I get:

```
cupsdoprint -P 'i455' -J 'unitinfo.txt' -H '/var/run/cups/cups.sock:631' -U 'steve' -o ' copies=1 cpi=10 lpi=6 multiple-document-handling=separate-documents-collated-copies orientation-requested=3' '/tmp/kde-steve/kdeprint_6hn8fTlh' : execution failed with message:
client-error-document-format-not-supported 
```

Previously I was working fine with Turboprint. I hadn't made any special configuration changes to cups. Where can I get a basic Ubuntu conf file from?

Ignore the atd part. I seem to have fixed it.

Thanks in advance.

---

### Post by steevc on 2007-02-09
Is there any sort of facility to get the cups configuration files that would have been installed when I installed Ubuntu?  I'm guessing that these are part of Ubuntu rather than cups itself as re-installing that did not restore them. I just need default files so that I can get my printing working again. It seems like overkill to have to re-install Ubuntu to do this.

Thanx

---

### Post by llamakc on 2007-02-09
Yes, you could reinstall the package. The configuration file /etc/cups/cupsd.conf is in the cupsys package.

---

### Post by steevc on 2007-02-10
There's some problem with the install

Unpacking cupsys (from .../cupsys_1.2.4-2ubuntu3_i386.deb) ...
Setting up cupsys (1.2.4-2ubuntu3) ...
chown: cannot access `/etc/cups/cupsd.conf': No such file or directory
dpkg: error processing cupsys (--configure):

I've cleared all the files out to make sure nothing was blocking it, but end up with no cupsd.conf. Any ideas what could cause this error?

Update: I manually extracted the files from the deb and it seems to be working again now. I'd like to know why it failed to extract.

---

### Post by llamakc on 2007-02-10
Here's what my /etc/cups directory looks like. Is yours the same?

drwxr-sr-t  5 cupsys lp        4096 2007-01-08 15:46 cups

---

### Post by yb202 on 2007-02-20
Hi , I have a similar problem . I managed to ruin my cups.conf and deleted it thinking that reinstalling cupsys will get me a default new one (....windows user :(  ) Anyway , I am pretty sure by now it doesnt as I have tried several times and the only vanilla version I found on the net didnt work + looked different from what I first saw. Is there anywhere I can obtain this file. Where did it come from ?The  Ubuntu installation or cupsys? Oh , and about .conf files in general , were are the default files usually kept (if u forget to back up that is  ;) ). Thanks for any help.

---

### Post by drpaul on 2007-02-20
Should be part of the cups/cupsys packages in the repos.

HTH

Paul

---

