---
title: "Dell n5110 random process crash"
date: 2013-05-12
forum: General Help
---

### Post by pustynnikov on 2013-05-12
[COLOR=#000000]Hi.[/COLOR]
[COLOR=#000000]I have laptop dell n5110 with intel video card. no nvidia card.[/COLOR]
[COLOR=#000000]And I have really random process crash.[/COLOR]
[COLOR=#000000]I tried different versions of ubuntu, then tried fedora.. even installation app on livecd crashed once. [/COLOR]
[COLOR=#000000]Sometimes its some background processes, sometimes its tabs of chrome, skype crashes a lot.. sometimes ubuntu just log out.. and sometimes it was logging out so often that couldnt even start browser..[/COLOR]
[COLOR=#000000]Sometimes its just horribly often, sometimes - its ok. I cannot give any pattern..[/COLOR]

[COLOR=#000000]Please help me to figure out where is the problem.[/COLOR]
[COLOR=#000000]I guess good idea is to install windows and see what happens... but I would like not to do it, if its possible.[/COLOR]

[COLOR=#000000]Tell me please what info I should provide.[/COLOR]

---

### Post by Toz on 2013-05-12
Please don't create duplicate threads for the same issue - it dilutes community effort. I have removed the other thread.

---

### Post by Toz on 2013-05-12
If the same problem is happening on different distros, I'd look towards a hardware issue. Try running the Memory Test from the live CD.

---

### Post by pustynnikov on 2013-05-13
Sorry for duplicate, I thought I have rights to delete topics.
I ran memory test today - no errors..

---

### Post by Toz on 2013-05-13
Are you able to get any error/crash messages? I'd look at the following log files:
- /var/log/syslog
- $HOME/.xsession-errors

You can upload and post back links to those uploads like this:
```
pastebinit /var/log/syslog
pastebinit $HOME/.xsession-errors
```
...this will allow others to view those log files.

---

### Post by pustynnikov on 2013-05-13
Here
[http://pastebin.com/bThgLu0r](http://pastebin.com/bThgLu0r)
[http://pastebin.com/FqiBvJxM](http://pastebin.com/FqiBvJxM)

---

### Post by Toz on 2013-05-13
I can see instances of chrome crashes:
> May 10 18:44:18 maxim-laptop kernel: [23765.733006] traps: chrome[12659] general protection ip:7fb6b589d9db sp:7fff67ce0808 error:0 in chrome (deleted)[7fb6b4050000+5378000]
May 10 18:55:31 maxim-laptop kernel: [24438.519827] chrome[13174]: segfault at 254caa700019 ip 00007fb6b5872ad6 sp 00007fff67ce26c0 error 4 in chrome (deleted)[7fb6b4050000+5378000]
Do the crashes happen when chrome is not running or when you use another browser (i.e. firefox).

---

### Post by pustynnikov on 2013-05-14
It also happens without browser.
some process can crash even when I install fresh new system. the first thing that I see - crash reporter %)

---

### Post by pustynnikov on 2013-05-16
Guys, can somebody help me?...

---

### Post by pustynnikov on 2013-05-22
Installed windows... the same problem. So its smth about hardware. )

---

