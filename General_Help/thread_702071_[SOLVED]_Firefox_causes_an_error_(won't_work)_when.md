---
title: "[SOLVED] Firefox causes an error (won't work) when I try to open it"
date: 2008-02-19
forum: General Help
---

### Post by ECPCLINUX on 2008-02-19
Hello, I use Firefox for all my browsing. I recently try to open Firefox and I got this error. "Could not initialize the Browser's security componet.  The most likely cause is problems with file in your browse's profile directory. Please check that this directory has no read/write restrictions and your hard disk  is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behavior when accessing security features" press "ok". 

1- I installed  an add-on called allpeers navigator (it installed well but did not get around to use it, hence I was unable to find out if it worked). I turned off my computer came back the next day try starting Firebox when I got the above messg. I looked at the allpeers forum to no avail.

2- When I press "ok" the browser won't work at all.

3-  My Hard Drive is 500GB and is far from full.

4- Can't open the browser so I can't check the read/wirite problem even if I knew how.

5- I decided to use Sypnaptic to uninstall Firefox rebooted and tried reinstalling it again. It installed well but it has the same problem. Given that I'm new I tried to use "shred Firefox" but it cannot find it, guess is just for files and there might not be a firefox file. Please keep in mind I'm not an expert, at all!

Could someone please help me with this problem? In advance, thank you for all or anyone who is willing to help me with this. I currently installed Opera to browse but I'm so used to Firefox and it's features hence, I would really like to get it up and running. PLease forgive any misspelled words, no spell check on Opera by default and I'm not familiar with Opera. lol Thank you for reading my post.

---

### Post by freelinuxhelp on 2008-02-20
It sounds like something in your Firefox profile directory is messed up. I don't know of an absolute fix for you, but you might try this in a terminal window.
Note: This will most likely cause your plugins and themes for firefox to become unusable.
```
mv ~/.mozilla ~/mozilla.backup
```

Now try to run firefox. If it doesn't work, run this command to undo the rename:
```
mv ~/mozilla.backup ~/.mozilla
```

Good luck!

---

### Post by ECPCLINUX on 2008-02-20
> **freelinuxhelp said:**
> It sounds like something in your Firefox profile directory is messed up. I don't know of an absolute fix for you, but you might try this in a terminal window.
Note: This will most likely cause your plugins and themes for firefox to become unusable.
```
mv ~/.mozilla ~/mozilla.backup
```

Now try to run firefox. If it doesn't work, run this command to undo the rename:
```
mv ~/mozilla.backup ~/.mozilla
```

Good luck!

 Thank you so very much freelinuxhelp, the fist code worked like a charm!!! I'm, now back in business with Firefox. Regards, Edward :guitar:

---

### Post by freelinuxhelp on 2008-02-21
Glad to know it worked!
Could you mark this thread as solved? It helps other users when looking for solutions.
Thanks. :-)

---

