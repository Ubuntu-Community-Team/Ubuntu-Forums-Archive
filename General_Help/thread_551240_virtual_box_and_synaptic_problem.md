---
title: "virtual box and synaptic problem"
date: 2007-09-14
forum: General Help
---

### Post by hellfried on 2007-09-14
i was trying to install the latest version of virtualbox last night but for reasons i cannot remember it was terminated half way. now i cannot open synaptic up. this is the error message it get: 

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

any ideas on how to solve this?

---

### Post by Maestro23 on 2007-09-14
In terminal, try:

> sudo dpkg --force-remove-reinstreq –remove packagename

---

### Post by hellfried on 2007-09-14
sorry i pressed the wrong button 'report' button instead of the 'reply' button. this is what happens when one is sleep-deprived!
thanks for the tip. that did the trick. is it safe to try to reinstall virtualbox now??

---

### Post by Maestro23 on 2007-09-14
> **hellfried said:**
> sorry i pressed the wrong button 'report' button instead of the 'reply' button. this is what happens when one is sleep-deprived!
thanks for the tip. that did the trick. is it safe to try to reinstall virtualbox now??

Good deal man.  Give it a shot. Or wait until you've had some sleep. :smile:

---

### Post by hellfried on 2007-09-14
ok i tried reinstalling virtual box again. what do i do when it reaches the license page. when i hit 'enter' at the bottom of the page where it says <Ok> nothing happens. i am trying to do it from package installer.

---

### Post by bodhi.zazen on 2007-09-14
When you install virtual box you have to accept a license ...

It appears to freeze, but it is waiting for you ...

Hit the <tab> key untill "OK" is highlighted ... Then hit <Enter> 

:lolflag:

---

### Post by Maestro23 on 2007-09-14
> **hellfried said:**
> ok i tried reinstalling virtual box again. what do i do when it reaches the license page. when i hit 'enter' at the bottom of the page where it says <Ok> nothing happens. i am trying to do it from package installer.

Sorry man, don't know.  Never tried the program myself.

Edit:  You got help. :smile:

---

### Post by ResumeMan on 2007-09-15
Hmmm... I just had the exact same problem (for the same reason). I was actually trying to upgrade to the new version, but ended up screwing up the upload while it was waiting for me.

I tried Maestro's command, but I got 

> dpkg: need an action option

I tried it with "VirtualBox" too.

What the heck am I doing wrong?
Thanks!

----------------

Edit, never mind, I figured out that I needed two dashes before "remove" and it worked. Thanks for the tips

---

### Post by catfacts on 2007-09-26
I had the exact same problem, to put the exact remove code up
```
sudo dpkg --force-remove-reinstreq --remove virtualbox
```

---

