---
title: "alpine and spell checking"
date: 2007-12-12
forum: General Help
---

### Post by lackhead on 2007-12-12
Hey all-

    I've recently installed feisty, and noticed the pine->alpine switch. The only issue I have is that spell checking seems to not work.  At least, when I run nano or pico from the command line, I can hit ^T and it spell checks the buffer.  Under alpine though, when I hit ^T all I get is "Unknown Command".  Has anybody else seen this, and if so, has a fix been found yet? 

                        Thanks!


                                               -c

---

### Post by jayson.rowe on 2007-12-18
To enable Spell checking in Alpine, first, ensure that you have the package 'ispell' installed. 

Once, ispell is installed, start alpine, and press "S" for setup, "C" for Config and then do a ^W to search for the word "spell" you will find an option labled "Spell-Check-Before-Sending", tick that box, and do a ^W and search for spell again, you will find an option "Speller= " add ispell after the = sign.

From now on, when you hit ^X to send, it will check your message before sending.

Hope this helps!

---

### Post by bigtyme99 on 2008-01-07
I have done as you said.. and it still doesnt spell check. And yes ispell is installed. Any other ideas ?

---

### Post by wayover13 on 2008-03-19
Same problem here. Alpine .999. Did you finally resolve this? Somethin's wrong here. 

I got both ispell and aspell installed. I can do ispell myfile and it spellchecks the file just fine. Also aspell -c myfile. But specifying either ispell or aspell as the spellchecker in Alpine and setting the config to check messages before sending--it just don't work. Alpine doesn't actually check the message, but just sends it. I crafted a special message full of misspellings to check this, btw.

Any resolution?

James

---

### Post by wayover13 on 2008-03-19
RESOLVED

I resolved this issue by installing the latest version of Alpine (1.10). I found a deb for it at [http://www.washington.edu/alpine/acquire/](http://www.washington.edu/alpine/acquire/) and just did sudo dpkg -i on it. I think the problem with the version contained in the Ubuntu reps is that Pico, the alternate editor, was somehow miscompiled to lack spellcheck support. I tested this by opening a file using Pico (independently of Alpine) and then hitting ctrl-t to try and spellcheck it. Despite the fact that the Pico help screen claimed either ctrl-t or f12 would invoke the spellchecker, neither key combination would invoke the spellchecker, each simply eliciting the system bell (error indicator). This problem was apparently fixed in later Alpine/Pico releases, because spellchecking from within Alpine now works using this updated version.

James

---

