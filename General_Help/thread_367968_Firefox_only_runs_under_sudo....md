---
title: "Firefox only runs under sudo..."
date: 2007-02-22
forum: General Help
---

### Post by Pikestaff on 2007-02-22
I've installed Firefox 2.0 (using the great "Install New Firefox" script) but when I try to open it... it doesn't.  It appears to be loading, as the cursor changes into the little bouncing icon you get in KDE... but then it disappears and it just doesn't open at all.  If I go into the terminal and type "Firefox" it doesn't do anything either.  If I type "sudo firefox", though, it opens.

I'm not sure what's going on, but any advice would be appreciated, because I don't like the idea of using sudo every time I run Firefox.  :???:  I don't have this problem on my other computer that runs the same Kubuntu 6.06 and installed Firefox via the same script.  Thank you in advance for any help!

---

### Post by aidanr on 2007-02-22
can you run it in a terminal and post the output, i had a similar problem months back, if i remember correctly it was something to do with the theme or theme engine i was using

---

### Post by Pikestaff on 2007-02-22
I get this:

```
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0

```

---

### Post by aidanr on 2007-02-22
ok, thats completely different from the errors i got :???:

although just a quick search on the error throws back this [http://ubuntuforums.org/showthread.php?t=263816](http://ubuntuforums.org/showthread.php?t=263816)
so maybe try commenting out an unused devices from your xorg.conf, for example the wacom stuff

---

### Post by Pikestaff on 2007-02-22
Hmm okay, thanks for the help anyway :)

I should add that this sometimes happens with other programs too, not just Firefox... but I think Firefox is only the one that does this every single time.

---

### Post by Pikestaff on 2007-02-23
> **aidanr said:**
> although just a quick search on the error throws back this [http://ubuntuforums.org/showthread.php?t=263816](http://ubuntuforums.org/showthread.php?t=263816)
so maybe try commenting out an unused devices from your xorg.conf, for example the wacom stuff

Didn't see this the first time I replied, I tried it just now though and it didn't seem to do anything except freeze the computer on bootup... I might have done it wrong though.

I think this issue is also making it so when I click on a link someone sends me an an IM or something, instead of opening it up in Firefox it doesn't do anything :(

---

### Post by Pikestaff on 2007-03-02
I just wanted to say to anyone that comes across this problem in the future that I've got it figured out: The .mozilla folder that had firefox in it ( /home/yourusername/.mozilla) had its permissions set root-root, so I did chown on it and changed it to my regular username, and it works now :)

I also fixed the wacom tablet thing, thanks again for that link aidanr!

---

