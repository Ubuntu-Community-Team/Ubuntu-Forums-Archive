---
title: "[SOLVED] sudo firefox has destroyed my browser :("
date: 2008-05-20
forum: General Help
---

### Post by Irishpolyglot on 2008-05-20
Since the "Check for updates" was greyed out, I ran "sudo firefox" to check for updates (next time I'll just wait for Synaptec). After I did that I was browsing around as normal and was in the process of installing one add-on (Fission), when the browser crashed.

Now I have several problems in it; first my bookmarks have completely disappeared and the Restore option doesn't work (even though the files themselves for restoring are fine). The Back/Forward buttons are greyed out and I can only use them by right clicking and selecting from the drop-down menu. It crashes MUCH more regularly AND I can't see the web address in the address bar!! There are likely other problems I'm not aware of. Everything else (other add-ons, greasemonkey etc.) seem unaffected.

Advice hugely appreciated for this!! I'm at a loss at what to do.. if I reinstall will I lose all my add-ons?
Thanks guys!!

---

### Post by chrisccoulson on 2008-05-20
'sudo firefox' is bad, as you've just learned. As you've realised, you should let Synaptic handle updates for anything you've installed via the package manager. If you must run a graphical tool as root, always use 'gksudo' (NOT sudo)

Your problem is most likely that root now owns some or all of your Firefox profile. To fix:

```
sudo chown -R <*user_name*>:<*user_name*> ~/.mozilla
```
...where <*user_name*> is your user name

---

### Post by robertchahine on 2008-05-20
> **chrisccoulson said:**
> 'sudo firefox' is bad, as you've just learned. As you've realised, you should let Synaptic handle updates for anything you've installed via the package manager. If you must run a graphical tool as root, always use 'gksudo' (NOT sudo)

Your problem is most likely that root now owns some or all of your Firefox profile. To fix:

```
sudo chown -R <*user_name*>:<*user_name*> ~/.mozilla
```
...where <*user_name*> is your user name
+1.
is totally right

if this don't work, i suggest a reinstallation of firefox from the synaptic.

---

### Post by Irishpolyglot on 2008-05-20
Wow! Completely solved the problem in one line of code :) I've learned my lesson!!! I'll use sudo sparingly from now on; cheers mate!

---

### Post by robertchahine on 2008-05-20
glad to hear that.

---

### Post by aysiu on 2008-05-20
> **Irishpolyglot said:**
> Wow! Completely solved the problem in one line of code :) I've learned my lesson!!! I'll use sudo sparingly from now on; cheers mate!
It's a little more complicated than that. It's not that *sudo* is inherently bad (though it should be used sparingly for other reasons), but *sudo* should not be used with graphical applications like Firefox. For that, you should use *gksudo* or *kdesu*

For more details read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Irishpolyglot on 2008-05-20
Of course your right aysiu. I've used it many many times before... but I had never been shown it's potential for evil until now :P I got that suggestion from a comment on the lifehacker blog. It just goes to show that I can't use code that ANYONE says would be a good idea. I'll not stop using sudo, but I will think twice before I use it in questionable situations like that one! Or at least use its graphical counterpart!!
Thanks for the advice!

---

### Post by aysiu on 2008-05-20
By the way, the *gksudo firefox* to check for updates works only if you're using the .tar.gz from the Mozilla website.

If you're using the Firefox that Ubuntu packages, you just wait for the updates with your regular software updates for the entire Ubuntu system.

---

### Post by Rewarp on 2008-06-03
Bloody hell. So that was what's wrong with Firefox 3!

I have been stuck using the Extension-less Epiphany or the surprisingly Extension-install/uninstallable Firefox 2.0.0.14 (which I downloaded to replace FF3) because I ran sudo firefox.

Thanks a whole a lot.

---

### Post by swegner on 2008-09-29
> **chrisccoulson said:**
> 'sudo firefox' is bad, as you've just learned. As you've realised, you should let Synaptic handle updates for anything you've installed via the package manager. If you must run a graphical tool as root, always use 'gksudo' (NOT sudo)

Your problem is most likely that root now owns some or all of your Firefox profile. To fix:

```
sudo chown -R <*user_name*>:<*user_name*> ~/.mozilla
```
...where <*user_name*> is your user name
Had to help my brother who decided to run 'sudo firefox', and this did the trick.  Thanks for posting the tip-- I also didn't realize the difference between sudo and gksudo (other than the graphical password prompt).

---

### Post by lookslikepat on 2009-11-07
I know this is an unnecessary reply given that this problem is Solved, but I Had to thank you guys for this: you saved me Hours!
The sudo chmod really worked, and I will Never update Firefox using "sudo firefox" - ever again ;)

---

