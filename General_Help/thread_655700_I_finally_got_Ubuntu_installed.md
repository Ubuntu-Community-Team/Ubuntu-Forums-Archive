---
title: "I finally got Ubuntu installed"
date: 2008-01-01
forum: General Help
---

### Post by HackCoders on 2008-01-01
OK well, I installed 7.10, 32bit edition. -- Finally got it working, no grub errors at all this time, which was odd, and I'm wired by ethernet now, so I can get online. I've updated the OS etc..

A few problems, whenever I go to install an application, it tells me I need to go install something else, so I go to install that something else, and that tells me to go install something else too, it's like one giant loop, never ends!

It says something like "depend: <xxx", something like that, I'm currently in XP so can't really remember.

By the way, if someones going to tell me to paste something here, to run a command line or whatever, please tell me how to do that too, I'm not really good with linux yet.

So  yeah, does anyone know how to fix the package problem? I cant even install normal applications like Xchat, which I really need, it tells me I need to go install something else, If you need more info just tell me what you need and how to do it, and I'll try :)


Thanks for reading.

---

### Post by ~LoKe on 2008-01-01
This is what you'd need to install xchat from the terminal.  I'm going to assume you know how to open the terminal.

Once it's open, type this:
```
sudo aptitude install xchat
```

It *should* be that simple.  It should also automatically download any dependencies.

---

### Post by Mze on 2008-01-01
[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by brownknight on 2008-01-01
You can install xchat via Add/Remove from the applications menu. Just search for xchat. All dependencies will be automatically fetched and installed.

You can also install it the terminal . I personally use aptitude
sudo aptitude install xchat

Or you can use Tools> Synaptic Package Manager. Search for xchat. Tick the box and press Apply.

---

### Post by knutschr on 2008-01-01
Have you opened for the repositories that is not connected by default?
In Synaptic, go to Preferances-->Archiv (I am not sure of it is called that in English) and mark for all except Sources. Mark also for the third-party packages.
Klick Read again at the left.
Then try installing again.

---

### Post by HackCoders on 2008-01-01
OK thanks guys, I'll boot into Ubuntu now and try that

---

### Post by HackCoders on 2008-01-01
This is what i got when doing that command, Also where do installed applications go? Because when I click applications and go to all the tabs, internet, games etc, there's nothing new. And if I go to synaptic it still gives same errors as before

**```
Massive CODE taken out, I got the thing installed...**
```

If I go to synaptic and try to install xchat, I get this

```
xchat:
 Depends: tcl8.4 (>=8.4.5) but it is not installable


```

Sorry for massive post



**Update: It worked via Add/Remove programs!, I changed repositories as knut mentioned, and it seemed to work from there. But why doesn't it work via Synaptic?**

---

### Post by HackCoders on 2008-01-01
Hmm, now my HDD does not show up in Ubuntu, It was always on the desktop as sda1, why is it gone?

It was pretty much my C drive, so I could access all my movies etc, now it only shows "File system", and thats with all the Ubuntu files in it..

---

### Post by knutschr on 2008-01-01
Open Dolphin File Manager.
It should be in Storage Media at the left.

---

### Post by HackCoders on 2008-01-01
Hmm, I think I know why it's gone.

Last night I changed something on windows, I forgot what it was called, S-ID or something , it was like a bunch of numbers, and it scanned through every file on the HDD and did something to all of them, not sure.

It doesn't really matter, I'll just put my media on an external hard drive, or transfer them to another PC on the network and then back here.

---

### Post by HackCoders on 2008-01-03
Never mind HDD works.

I got Wine installed too, and all my windows applications! thanks for the help guys, loving ubuntu.

Only problem now is audio is only through left speaker, wasn't like that yesterday =\. Searching the problem here on the forum, many threads on it, I might find a fix ^_^

Never mind it's all good, I went to sound properties up near the time, then I went over to File > Change device > then I slid both sliders to the top. Yay ubuntu is going heaps good for me now!

---

