---
title: "Google Chrome doesn't start after update"
date: 2015-10-14
forum: General Help
---

### Post by pbhill on 2015-10-14
After an update today I can no longer open Google Chrome:
I get the following response using the terminal:

pbhill@Systemax-Ubuntu:~$ google-chrome
[2043:2043:1014/201057:ERROR:content_settings_pref.cc(468)] Invalid pattern strings: chrome-extension://mfgdmpfihlmdekaclngibpjhdebndhdj/,
[2043:2043:1014/201057:ERROR:content_settings_pref.cc(278)] Invalid pattern strings: chrome-extension://mfgdmpfihlmdekaclngibpjhdebndhdj/,
Illegal instruction (core dumped)
pbhill@Systemax-Ubuntu:~$

I uninstalled and reinstalled to no avail. Same problem. 
I am using Ubuntu Mate 15.10
Thanks in advance for any suggestions.

---

### Post by CantankRus on 2015-10-14
Try starting with extensions disabled...
```
google-chrome --disable-extensions
```

Rename or delete your **~/.config/google-chrome** folder to start  afresh with no extensions
and try running google-chrome normally.

---

### Post by pbhill on 2015-10-16
Thanks CanTankRus,
Followed your suggestion but it didn't help.
     pbhill@Systemax-Ubuntu:~$ google-chrome

[Illegal instruction (core dumped)
pbhill@Systemax-Ubuntu:~$ ]

Something's amiss...

---

### Post by CantankRus on 2015-10-16
Can you start google-chrome in your guest account?

---

### Post by pbhill on 2015-10-20
No, that doesn't work either. Seems the command "/usr/bin/google-chrome-stable %U" is not recognized any longer.  Did the update move Chrome to a different location? How would I find it it it were?

---

### Post by howefield on 2015-10-20
> **pbhill said:**
> ...  Did the update move Chrome to a different location? How would I find it it it were?

In terminal type..

```
whereis google-chrome
```
```
whereis google-chrome-stable
```

If CantankRus' suggestion of renaming the ~/home/user/.config/google-chrome folder didn't work, I'd look to purge and install from a fresh deb.

---

### Post by CantankRus on 2015-10-20
ok here.
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] which google-chrome-stable**
/usr/bin/google-chrome-stable
```

---

### Post by pbhill on 2015-10-20
After trying all your suggestions, I found a [thread]("http://http://askubuntu.com/questions/686884/google-chrome-wont-launch-on-a-pentium-4") that indicates that the newer version of Chrome is no longer working in machines with older Pentium 4 processors. (Those without SSE2).  Although mine is older it has SSE2, I downloaded an older version of Chrome, and it works perfectly. I also had to disable auto updating of it in Synaptic.
Thank you for your help!

---

