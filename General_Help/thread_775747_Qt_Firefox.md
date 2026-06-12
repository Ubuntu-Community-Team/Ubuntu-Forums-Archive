---
title: "Qt Firefox?"
date: 2008-04-30
forum: General Help
---

### Post by Zorael on 2008-04-30
As the topic implies. I'm on a rampage to try to get rid of all Gtk-based apps I have installed.

Does a Qt version of Firefox exist, at all?

---

### Post by raul_ on 2008-04-30
I don't think so, but I use Konqueror for my daily use and it works fine :)

---

### Post by ibutho on 2008-04-30
No there isn't a QT version of Firefox. I think there was some talk about it in the past, but so far nothing has come out of it. Konqueror and Opera make good alternatives to Firefox. I think there is a QT4 webkit based browser in the [making]("http://labs.trolltech.com/blogs/2008/03/05/webkit-demobrowser/").

---

### Post by Zorael on 2008-04-30
> **ibutho said:**
> Konqueror and Opera make good alternatives to Firefox.
I must admit I've never tried Opera, but it doesn't seem to be in the repositories. Regardless; would it work with flashplugin-nonfree?

```
zorael@sunspire:~$ sudo aptitude install opera
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for opera
No candidate version found for opera
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
```

---

### Post by ibutho on 2008-04-30
Yes Opera works with Mozilla/Firefox plugins. There are Ubuntu packages available at the [Opera download site]("http://www.opera.com/download/").

---

### Post by der_joachim on 2008-04-30
Although opera is my favourite browser, flash support is flaky at best.

---

### Post by KeyserSoze93 on 2008-04-30
You can build firefox with QT from source...

I have tried but so far not been able to though...

Search google for "build qt firefox"

---

### Post by DirtDawg on 2008-04-30
> **der_joachim said:**
> Although opera is my favourite browser, flash support is flaky at best.

The "stable" release is ironically unstable with Flash, but try the [preview release(9.50b2)]("http://www.opera.com/download/linux/?ver=9.50b2"). It's a big improvement and runs Flash flawlessly. I was pleasantly surprised.

---

### Post by der_joachim on 2008-05-01
> **DirtDawg said:**
> The "stable" release is ironically unstable with Flash, but try the [preview release(9.50b2)]("http://www.opera.com/download/linux/?ver=9.50b2"). It's a big improvement and runs Flash flawlessly. I was pleasantly surprised.

[Off-topic]I already have the 2nd beta of 9.50, but no flash whatsoever. The flash version isn't correctly recognized ('wrong version') or does not work at all. I tried all the fixes and workarounds I could find on the forums (both Opera and Ubuntu). It's just a matter of luck I guess. 

Apart from flash support, which is probably Adobe's fault anyway, Opera is a very very good browser.

---

### Post by SunnyRabbiera on 2008-05-01
well you can just install gtk-qt, it will make firefox behave...
But there are some GTK apps I prefer over QT ones, I like Pidgin more then Kopete, Synaptic more then adept and Gimp more then krita...

---

### Post by Mandor on 2008-05-01
The qtwebkit demo browser eventually was forked into a more comprehensive, but still demo, browser - [http://code.google.com/p/arora/](http://code.google.com/p/arora/)

It is still in demo stage, but chances are that it will be usable some day.

---

### Post by Zorael on 2008-05-02
I'd love to get something Mozilla-based (or whatever is necessary to get it compatible with my FF2 addons), but I guess that if there were Qt Mozillas there would be, by extension, Qt Firefoxes. :<

I couldn't get the beta of Opera running; I had to force i386 architecture (running amd64) and, the resulting installation just didn't start. Just output errors to the terminal.

The "stable" one worked but flash support was garbage.

---

### Post by der_joachim on 2008-05-02
> **Zorael said:**
> I'd love to get something Mozilla-based (or whatever is necessary to get it compatible with my FF2 addons), but I guess that if there were Qt Mozillas there would be, by extension, Qt Firefoxes. :<

I couldn't get the beta of Opera running; I had to force i386 architecture (running amd64) and, the resulting installation just didn't start. Just output errors to the terminal.

The "stable" one worked but flash support was garbage.

Have you tried searching the Opera forums? I had a few problems when installing opera 9.5b over 9.2x, but a quick search on the opera forums helped me out in a few minutes. Also, you do not have a paste of the errors in question, do you?

IIRC, I had to start opera 9.5 for the first time with the following command:
```

opera -pd /tmp/testopera &

```
Do use google though before trying this command. My earlier problem may be entirely unrelated to yours.

---

### Post by lapubell on 2008-08-21
In case anyone reads this and doesn't know, after Nokia bought Trolltek, they decided to port Firefox to Qt.  It should be out soon!

I for one am very excited.

---

### Post by prince_niceguy on 2008-10-22
Ya am too looking forward to using qt based mozilla rather than gtk based.

---

