---
title: "Keyboard back/forward=Firefox back/forward?"
date: 2007-07-12
forum: General Help
---

### Post by tkrisz on 2007-07-12
The question is simple, how to set my keyboard back/forward button to Firefox back/forward action?
I searched for a FF back/forward command line but could not find them.

---

### Post by tkrisz on 2007-07-12
In Gnome.

---

### Post by kerry_s on 2007-07-12
press alt+left arrow or alt+right arrow. enjoy.

---

### Post by tkrisz on 2007-07-13
I think i was misunderstood. Of course i know these. There are back and forward buttons on my keyboard. I would like to use them as back and forward in FF. It is enough if someone tells me the command line for back and forward, then i suppose i can make the rest.

---

### Post by Saxomophone on 2007-07-13
Did you try looking in system>>Preferences>>Keyboard shortcuts? I'm not in ubuntu right now so I can't check, but browser back/forward might be an option there?

---

### Post by kerry_s on 2007-07-13
how about some more info?

is this a thinkpad? [https://bugs.launchpad.net/xorg-server/+bug/20204](https://bugs.launchpad.net/xorg-server/+bug/20204)

have a look at this> [http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work)

---

### Post by tkrisz on 2007-07-13
It's a Genius LuxeMate Scroll keyboard. The problem was exactly, that there is no such option in System>>Preferences>>Keyboard shortcuts.
Thank you, kerry_s, one of those link led to the solution.

The solution is that you have to add the following 2 lines to /usr/share/firefox/chrome/browser/content/browser/browser.xul 

```
    
<key id="goBackKb"  keycode="VK_FXXXXX" command="Browser:Back"/>
<key id="goForwardKb"  keycode="VK_FYYYYY" command="Browser:Forward"/>

```

right after the lines starting similarly, where FXXXXX and FYYYYY are your names for the your Back and your Forward button previously defined (probably in ~/.Xmodmap). You can enjoy the buttons after restarting FF.:popcorn:

**Edit:**
Updated to Ubuntu 7.10 and FF 2.0.0.8, don't know which one made the problem, but my settings gone. 
But i could make it work again by following kerry_s's 2nd link:

1. cd  /usr/share/firefox/chrome/
2. sudo unzip browser.jar
3. cd content/browser
4. sudo gedit browser.xul
5. Edit the content as above described.
6. cd .. (2x)  
7. sudo zip -rD0 browser.jar content/browser/
8. Restart FF and enjoy.

---

