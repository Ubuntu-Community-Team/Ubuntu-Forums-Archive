---
title: "chromium keeps crashing"
date: 2012-11-18
forum: General Help
---

### Post by aliasforme on 2012-11-18
Hey guys:

Noob here, I have no idea where to look for error codes for this problem. My chromium browser is unstable and I would like to know why and fix it. Could someone send me off in the right direction?

thanks in advance

---

### Post by aliasforme on 2012-11-19
No Help? I know if it crashes and closes I can send an error report, but most of the time it just locks up and forces me to restart or just displays the "aw snap" screen. Considering I don't have any ad-ons or antivirus I think it is something Ubuntu related causing it to crash

---

### Post by ForEveryman on 2012-11-20
I was experiencing the same thing with Chromium!  

I'd start the browser, go to a few sites and usually within five minutes, it would crash and I had to power-cycle my computer to recover.  

I got so frustrated that I eventually removed Chromium and went back to Firefox.  That was about a week ago and I haven't had one crash since.

---

### Post by Cope57 on 2012-11-20
Start the browser using the console, and when it does lock up you should be able to see some error in the console.  One could also check the error logs to see what has been producing the crash.

---

### Post by vasa1 on 2012-11-20
You may also consider making a new profile as described here: [http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059](http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059)

Since those instructions are for Chrome and you're using Chromium, your profile will be in ~/.config/chromium.

---

### Post by dannyboy79 on 2012-11-20
what version are you using?

```
dpkg --get-selections | grep google
```

---

### Post by vasa1 on 2012-11-20
> **dannyboy79 said:**
> what version are you using?

```
dpkg --get-selections | grep google
```
Won't return anything if OP is using Chromium.

---

### Post by aliasforme on 2012-11-21
Thanks for the suggestions guys, I'll start using the console to open chromium, I'll post an error code when I get one

EDIT: How do I open chromium with my terminal?

---

### Post by vasa1 on 2012-11-21
> **aliasforme said:**
> Thanks for the suggestions guys, I'll start using the console to open chromium, I'll post an error code when I get one

EDIT: How do I open chromium with my terminal?
Type
```
chromium-browser
```
and hit enter

---

### Post by aliasforme on 2012-11-22
Okay, first error code(s), this was from an aw snap screen 

```
[4273:4310:7120570303:ERROR:download_updates_command.cc(99)] PostClientToServerMessage() failed during GetUpdates
[4273:4310:7122571594:ERROR:download_updates_command.cc(99)] PostClientToServerMessage() failed during GetUpdates
[4273:4273:7134828306:ERROR:x11_util.cc(1221)] X Error detected: serial 13540, error_code 10 (BadAccess (attempt to access private resource denied)), request_code 142, minor_code 1 (X_ShmAttach)
[4273:4273:7134829324:ERROR:x11_util.cc(1221)] X Error detected: serial 13541, error_code 159 (BadShmSeg (invalid shared segment parameter)), request_code 142, minor_code 3 (X_ShmPutImage)
[4273:4273:7134829827:ERROR:x11_util.cc(1221)] X Error detected: serial 13551, error_code 159 (BadShmSeg (invalid shared segment parameter)), request_code 142, minor_code 2 (X_ShmDetach)
[4273:4273:7290314848:ERROR:tab_strip_gtk.cc(1267)] Not implemented reached in virtual void TabStripGtk::StopAllHighlighting()

```


More Codes:

```
[5143:5187:9171896597:ERROR:download_updates_command.cc(99)] PostClientToServerMessage() failed during GetUpdates
[5143:5187:9173898667:ERROR:download_updates_command.cc(99)] PostClientToServerMessage() failed during GetUpdates
[5143:5187:9178900183:ERROR:download_updates_command.cc(99)] PostClientToServerMessage() failed during GetUpdates

```

```
[5610:5648:10529782206:ERROR:download_updates_command.cc(99)] PostClientToServerMessage() failed during GetUpdates
[5610:5648:10531785944:ERROR:download_updates_command.cc(99)] PostClientToServerMessage() failed during GetUpdates
third_party/tcmalloc/chromium/src/free_list.cc:117] Memory corruption detected. 
Aborted (core dumped)
```

---

### Post by aliasforme on 2012-11-23
another different code:

```
(exe:3053): Gdk-WARNING **: XID collision, trouble ahead

```

Trouble ahead? not looking forward to this:confused:

---

### Post by windscape on 2012-11-23
Hi,

I suggest that you either file a bug report on chromium or switch to another browser. I personally use Google Chrome on Xubuntu 12.10 and it hasn't crashed yet *knocks on wood*. You can get Google Chrome by following the instructions here: [http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/)

---

