---
title: "how to edit system files"
date: 2016-12-13
forum: General Help
---

### Post by juntjoo2 on 2016-12-13
I keep  running into permission errors every time I want to edit a system file.  I'd rather not have to dig into system  files but nothing works out of the box.   Every time I google a problem I get the same results: a bunch of  different things to punch into the command terminal, most of which  don't work. The end result is a lot of time spent and nothing learned.  I want to be able to AT LEAST be able to  edit system files without hassle, and I'd like one simple solution.  This way I could start the typical 3 hour  process of fixing something so simple as my bluetooth mouse disconnecting  without going through the one hour process of getting able to change things  in the system.  So can anyone tell me  how  to stop  running into this permissions wall that  keeps getting in my way?  

out of curiosity, what should the average user expect with linux as far as what's needed to perform daily computer office related tasks?  Should one be taking weekly courses or the equivalent? Feels like I'm being forced to go to school but unable to easily put in my calendar as I never know when something won't work.

---

### Post by QIII on 2016-12-13
Hello!

Elevate your privileges appropriately with su, sudo, gksudo, etc, as appropriate when dealing with system files.  But don't get in the habit of just modifying things - and especially as instructed by random google hits.

Did you learn Windows in a day?

---

### Post by juntjoo2 on 2016-12-13
Windows was like Othello, a minute to learn, but a lifetime of suffering, which is why I quit. I don't mind learning... well maybe I do especially if it involves memorizing gibberish which is what "su, sudo, gksudo, etc" are to me. I feel like somewhere it should be stressed to those considering Linux that the requirement is one must devote X hours of mastering a bunch of commands, because until you do that you'll spend 3x more time to  get whatever you need done. 

So what should I google that will give me one simple answer if possible? "Elevate permissions" will this solve my problem for at least a month? I don't want to have to come back and be told type in strange combinations of letters with dashes and spaces put in specific places.

---

### Post by howefield on 2016-12-13
> **juntjoo2 said:**
> So can anyone tell me  how  to stop  running into this permissions wall that  keeps getting in my way? 

I'd suggest taking half an hour and learning nano, or at least the main key combinations, there are only about half a dozen you will need and use it to open any text file system or otherwise, eg

```
sudo nano path/to/file
```

You will only need to use sudo if the file is a system file, ie, not in your /home folder.

> out of curiosity, what should the average user expect with linux as far as what's needed to perform daily computer office related tasks?  Should one be taking weekly courses or the equivalent? Feels like I'm being forced to go to school but unable to easily put in my calendar as I never know when something won't work.

You say nothing works out of the box <shrug> if that were the case for me I'd find something that did work and suited my capabilities or time/inclination to learn. Of all the setups I have here there is only one system file that I need to edit and that is through choice because I want my web browser profile on a non default path. I suspect not too many people would bother with that. 

I'd suggest that having to edit system files on a continual basis indicates a problem that isn't universal.

---

### Post by juntjoo2 on 2016-12-13
Thank you. What is "nano". I have no idea what that means. Sorry, I'm horrible at memorizing things without some sort of tangible info attached. As far non universal problems, it's been a lot of things. Off the top of my head, Bluetooth mouse, wifi printer/scanner, WINE, screen brightness... or maybe I'm remembering incorrectly and I've got an old computer. Idk.

---

### Post by QIII on 2016-12-13
nano is a command line text editor.

Some hardware fiddling is inevitable if OEMs don't provide good Linux support.  Not much to be done in those cases but to modify config files.  That's not a problem with Linux, but it is a frustration for Linux users.

Wine is a kludge to try to get some Windows software to work.  It's not "Standard Issue" for Linux.  So that's a Wine issue.

When you use aftermarket parts, sometimes you do have to bang on stuff with a hammer to get the bolt holes to line up.

---

### Post by howefield on 2016-12-13
> **juntjoo2 said:**
> Thank you. What is "nano".

Nano is the name of a text editor used via the terminal.

> Sorry, I'm horrible at memorizing things without some sort of tangible info attached.

The key combinations can be found at the terminal, as per the attached screenshot of nano ready for editing a file.

---

### Post by juntjoo2 on 2016-12-13
Yeah, just like working on cars which I love to do for fun, not for work. I shall study up on "nano". Thanks

---

### Post by oldos2er on 2016-12-13
[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

Just to forestall any frustrations, where you see a caret "^" at the bottom of nano, you're meant to hold down Ctrl and press the corresponding key.

---

### Post by juntjoo2 on 2016-12-13
> **howefield said:**
> Nano is the name of a text editor used via the terminal.



The key combinations can be found at the terminal, as per the attached screenshot of nano ready for editing a file.

Thank you. Now I'm learning something. I used nano a few times so far just randomly following some solution and was clueless as to the nature of this sudden new second little black window. The skies are clearing a bit. On my way to get the BT mouse connected, WINE printing, screen brightness remembering, scanner remotely scanning, carburetor breathing, ...

---

