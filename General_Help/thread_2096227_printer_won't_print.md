---
title: "printer won't print"
date: 2012-12-19
forum: General Help
---

### Post by freemant on 2012-12-19
Hi,

My EPL-6200L was detected properly by Ubuntu 12.10 (x64). But if I print to it, the job appears in the "processing" state and nothing happens in the printer. In the cups error_log file, there are some errors:

W [19/Dec/2012:22:39:02 +0800] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_EPSON_EPL_6200L
W [19/Dec/2012:22:39:02 +0800] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_EPSON_EPL_6200L


Any idea? Thanks for any help!

---

### Post by Rexilion on 2012-12-19
[This]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1053443") mentions the same error, but the printer functions.

Usually, when I open cups @ [http://127.0.0.1:631](http://127.0.0.1:631) I get more detailed error messages if I look directly at the printers status page (just after you give a command to print).

Does it say anything?

---

### Post by freemant on 2012-12-19
There is no error at all on the web admin interface (after sending a test page). All the job status are marked as completed.

---

### Post by Rexilion on 2012-12-20
Before you proceed with the procedure below, could you give me the output of:

```
sudo find / -xdev -iname \*epson\*
```

The above command will take a while, but I need this to confirm the software is not installed already.





I looked around and someone else had your problem too:

[http://ubuntuforums.org/showthread.php?t=1558950](http://ubuntuforums.org/showthread.php?t=1558950)

Make sure to read post #4 and #5!

It seems that the printer uses non-standard procedures and that the license status of the package being used is 'undetermined'.

---

### Post by freemant on 2012-12-20
Thanks for the help. Below is the output of the "find" command:

/usr/lib/x86_64-linux-gnu/sane/libsane-epson.la
/usr/lib/x86_64-linux-gnu/sane/libsane-epson.so.1
/usr/lib/x86_64-linux-gnu/sane/libsane-epson2.so.1.0.23
/usr/lib/x86_64-linux-gnu/sane/libsane-epson.so.1.0.23
/usr/lib/x86_64-linux-gnu/sane/libsane-epson2.la
/usr/lib/x86_64-linux-gnu/sane/libsane-epson2.so.1
/usr/lib/cups/filter/rastertoepson
/usr/lib/cups/filter/commandtoepson
/usr/share/cups/ppdc/epson.h
/usr/share/man/man5/sane-epson2.5.gz
/usr/share/man/man5/sane-epson.5.gz
/var/cache/cups/EPSON-EPL-6200L.data
/etc/sane.d/epson2.conf
/etc/sane.d/epson.conf
/etc/cups/ppd/EPSON-EPL-6200L.ppd

---

### Post by freemant on 2012-12-21
I've tried both the thread you mentioned and [http://ubuntuforums.org/showpost.php?p=11125929&postcount=3](http://ubuntuforums.org/showpost.php?p=11125929&postcount=3), unfortunately neither made any difference.

---

### Post by freemant on 2012-12-21
I also tried converting a .ps file to epl language and send it as raw data to the printer, but there is absolutely no effect on the printer:

#./ps2epl epl_test.ps 
# file epl_test.epl
epl_test.epl: Epson ESC/Page language printer data
# lpr -o raw epl_test.epl

---

### Post by Rexilion on 2012-12-21
From the output you gave it seems that you already have the proper software installed. I noticed some people referring to the fact that stuff only works in 32bit mode.

Could you try to print from a 32bit LiveCD?

---

### Post by freemant on 2012-12-28
Tried it with the 32bit 12.10 desktop booted from USB key. Same result, i.e., absolutely nothing even when using the "print test page" or the "print self-test page".

---

### Post by Rexilion on 2012-12-28
Well, I have no more ideas? Does it work under Windows? Maybe the driver is indeed broken. Maybe the printer does not function. Lack of errors makes stuff kind of hard to help out. I ran flat out of ideas, sorry.

---

### Post by freemant on 2012-12-28
Thanks for the help anyway. Yes, it does work in Windows. It also worked in Kubuntu 12.04.

---

### Post by Rexilion on 2012-12-28
Then it's a regression of some form. I would recommend comparing relevant package numbers (see what changed). And file a bug.

---

### Post by freemant on 2012-12-28
thanks. I think it has been excluded from Ubuntu because it has patent issues: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/560254/comments/3](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/560254/comments/3)

---

### Post by Rexilion on 2012-12-29
Good thing you found out.

Maybe just stick to 12.04? It's an LTS so it's supported for 5 years. Maybe during that time the patent issue's will get resolved???

---

