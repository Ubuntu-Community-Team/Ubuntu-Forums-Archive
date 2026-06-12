---
title: "Can't get Lubuntu to prefer Google Chrome over Chromium"
date: 2013-03-01
forum: General Help
---

### Post by Rocket J Squirrel on 2013-03-01
I like Lubuntu a lot. Being a lightweight DE, it doesn't tax this weenie ACER Aspire One as much as Ubuntu did. But Chromium, the default browser, ate into memory and (possibly) swap memory to the point where the machine simply packed up and I had to press the big ol' hardware reset button to get it to respond. (NB: I can't claim that Chromium was responsible for filling Swap, but it filled, per HTOP, but after switching to Chrome I'm seeing much less of a problem, so work with me here).

But I can't get the machine to accept Chrome as the default browser. 
I've googled this. I have done this:
[FONT=Ubuntu Mono]
[/FONT]```
sudo update-alternatives --config x-www-browser
```

and what's described here: [http://superuser.com/questions/308290/how-to-really-set-chrome-as-the-default-ubuntu-browser](http://superuser.com/questions/308290/how-to-really-set-chrome-as-the-default-ubuntu-browser)

And, no joy. If I click on a link in an email, or my rss reader, Chromium gets launched.

---

### Post by Rex Bouwense on 2013-03-01
I didn't like Chromium either but I installed Firefox and simply went to menu->Preferences->Preferred Applications and changed the browser to Firefox.  Perhaps because Chrome isn't in the repositories it won't take.  Not sure.  My change was easy.

---

### Post by Rocket J Squirrel on 2013-03-01
Thank you, Rex. Under Settings > Default Browser, Chrome reports that "Google Chrome cannot determine or set the default browser."

---

### Post by Iowan on 2013-03-01
Moved to "General Help" as it doesn't seem to be a Networking/Wireless issue.

---

### Post by Rocket J Squirrel on 2013-03-01
Thank you, I put it in the wrong forum. My bad.

---

### Post by Rex Bouwense on 2013-03-01
How is Chromium being launched if you uninstalled it and installed Chrome?  Did you change the preference where I suggested?

---

### Post by Rocket J Squirrel on 2013-03-02
Oh for crying out loud. I was tired last night. Your solution works, many thanks. BTW, I have not uninstalled Chromium, I'm keeping the two here for side-by-side comparison of memory usage. This issue is solved. 

Again, thanks.

[EDIT: Um, I don't see "Mark as Solved" under "Thread Tools" at the top. Did that get moved or something?]

---

### Post by Rex Bouwense on 2013-03-02
Hey that happens to all of us.  About the solved thing, I don't know if it has been moved but it is not under thread tools.

I think that I have discovered why it isn't where it used to be.
[http://ubuntuforums.org/showthread.php?t=2121377&highlight=mark+thread+solved](http://ubuntuforums.org/showthread.php?t=2121377&highlight=mark+thread+solved)

---

