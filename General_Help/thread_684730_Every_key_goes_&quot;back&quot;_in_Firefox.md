---
title: "Every key goes &quot;back&quot; in Firefox"
date: 2008-02-01
forum: General Help
---

### Post by lmarr28 on 2008-02-01
**[I'm using Gutsy on an IBM ThinkPad T41 laptop.]**

I've just noticed that when I press any key on my keyboard while in Firefox, it will go "back" a page.  If I keep pressing any key, once I've reached the first page in my history (i.e., I can't go "back" any further), the next time I press any key, it will go "forward" one page, then start going "back" again with any subsequent key presses.  I can't say how long it's been doing this, but it hasn't been very long.

A while back, I made a change to _**/usr/lib/firefox/chrome/browser/content/browser/browser.xul**_ in order to allow me to use the "back" and "forward" keys on my keyboard in Firefox.  I added the following lines under **_<keyset id="mainKeyset">_**:
```

<key id="goBackKb" keycode="XF86Back" command="Browser:Back" />
<key id="goForwardKb" keycode="XF86Forward" command="Browser:Forward" />

```

In order for that to work, I also had to modify **_~/.Xmodmap_** with the following:
```

keycode 234 = XF86Back
keycode 233 = XF86Forward

```

After making those two changes, my "forward" and "back" keys worked perfectly in Firefox.  Now, for some reason, EVERY single key (even the "forward" key) makes it go "back".

Does anyone have any suggestions?  This is driving me nuts!

---

### Post by pointone on 2008-02-01
First, try undoing the changes you made to see if they're causing the problem.

---

### Post by lmarr28 on 2008-02-01
I suppose that would be the next logical thing to try!  :)

I checked to make sure the changes that I made were correct, and they were, but I'll try undoing them as soon as I get home from work today to see what happens.

---

### Post by lmarr28 on 2008-02-13
I figured it out...

According to [this page]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration"), mapping your Back and Forward keys to XF86Back and XF86Forward does not work correctly in Firefox.  So, I went in and changed them to use F19 and F20 instead, and now it's working great!

---

