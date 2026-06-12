---
title: "[SOLVED] Ever since Gutsy, Print Screen no longer takes a screenshot (w/ error msg)"
date: 2007-10-18
forum: General Help
---

### Post by ticopelp on 2007-10-18
And I don't know why. Sort of. 

The thing is, I don't think it's a problem with Gutsy, as I have another machine with a vanilla install of Gutsy and Print Screen works fine on that. I think there's some sort of conflict with Compiz. When I hit Print Screen under Compiz, nothing happens -- but when I revert back to Metacity and press print-screen, I get this:

```
There was an error running "/usr/share/compiz/take-screenshot.sh":
Failed to execute child process "/usr/share/compiz/take-screenshot.sh" (No such file or directory
```

I've already tried resetting the keyboard shortcut in System > Prefs > Keyboard Shortcuts, and I've established that the key itself is, in fact, working. 

Any ideas on how to fix this problem?

---

### Post by chrisccoulson on 2007-10-18
I had this when I upgraded to Gutsy. take-screenshot.sh doesn't actually exist. To correct, you need to open Advanced Desktop Effects Settings, click General, open the Commands tab, and set the defaults on  Screenshot Command Line and Window Screenshot Command Line so that they read 'gnome-screenshot' and 'gnome-screenshot --window' respectively

---

### Post by ticopelp on 2007-10-18
That worked. You rock! Thanks.

---

### Post by lopzided on 2007-10-23
I'm having the same problem...where do I find this Advanced Desktop Effects Settings?

Thanks!

---

### Post by chrisccoulson on 2007-10-23
You may need to install it first
```
sudo apt-get install compizconfig-settings-manager
```

It will then appear under your Settings -> Preferences menu

---

### Post by santiagoward2000 on 2007-10-23
Hi there!
I was wondering: is there any command in Xubuntu for this, or do I have to install gnome-screenshot?
Thanks

---

