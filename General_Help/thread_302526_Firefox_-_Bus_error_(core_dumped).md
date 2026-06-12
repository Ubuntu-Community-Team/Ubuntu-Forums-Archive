---
title: "Firefox - Bus error (core dumped)"
date: 2006-11-18
forum: General Help
---

### Post by hackeron on 2006-11-18
Hey there,

I have an up to date ubuntu edgy and recently after installing the latest nvidia driver  (don't think it's actually related though) and killing X with ctrl+alt+backspace, firefox stopped starting:

```
hackeron@ubuntu:~$ firefox 
Bus error (core dumped)

```

I tried to:

```
hackeron@ubuntu:~$ mv .mozilla .mozilla-backup
```

Which made Firefox start again, but after 10 minutes of browsing, it core dumps again :(

The version I have is: 
```
ii  firefox                               2.0+0dfsg-0ubuntu3                     lightweight web browser based on Mozilla

```

I tried to apt-get install --reinstall firefox firefox-gnome-support which didn't help :(

Any ideas/suggestions?

---

### Post by hackeron on 2006-11-19
no ideas?

---

### Post by robenroute on 2007-01-13
After trying (never managed, wouldn't start) to install swiftfox (via Automatix2) on Edgy, firefox opens, attempts to open a website or two, and then just totally crashes. Same reason: bus error.

Has this been resolved in the mean time (after 19 Nov) or is this still an issue (it is for me....)? Thanks

---

### Post by hackeron on 2007-01-15
> **robenroute said:**
> After trying (never managed, wouldn't start) to install swiftfox (via Automatix2) on Edgy, firefox opens, attempts to open a website or two, and then just totally crashes. Same reason: bus error.

Has this been resolved in the mean time (after 19 Nov) or is this still an issue (it is for me....)? Thanks

The solution to my problem was to edit /etc/firefox/firefoxrc and change FIREFOX_DSP="esd" to FIREFOX_DSP="none", give it a try.

---

### Post by Tearstone on 2008-02-29
I'm running into this problem right now with my Firefox. I load up a website and takes a dump on me everytime. I did check the /etc/firefox/firefoxrc file and it was set to "none". I also attempted to reinstall with no luck either :(

---

### Post by Tearstone on 2008-02-29
I ended up moving .mozilla to .mozilla.bak in my home directory and it came back up with a Vanila load of Mozilla again. I guess that will get me by :(

---

### Post by RogerFD4-Utu on 2008-04-06
I have the same problem after getting some update (mainly related to CUPS). Firefox do not start anymore, at least nothing shown on the screen. I install another browser, galeon, and same result.
My email and PidGin still works fine !
I am a new user of Linux/Ubuntu...
I need help to find out how to permanently fix this issue.
Thanks

---

