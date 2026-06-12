---
title: "Firefox crashes on right click"
date: 2014-05-27
forum: General Help
---

### Post by ct2034 on 2014-05-27
Hi
I am using firefox 29.0 on Ubuntu 12.04. 
(But I have had the same problem with ff before the last update, too)
[SIZE=4]**Whenever**[/SIZE] I click the right mousebutton or try to open another menu, like a bookmar toolbar folder, firefox freezes. It doesn't respond anymore until after some seconds Ubuntu tells me that it has crashed.
What I tried so far:
* starting in _save-mode_
* disabling all plugins
* resetting the profile
* disabling some graphical features in compiz
But non of these helped in any way

Thank you for your help

---

### Post by tgalati4 on 2014-05-27
Run *firefox --debug* in a terminal and see what errors come up.

---

### Post by ct2034 on 2014-06-03
Hi tgalati,

I get no error. This is the output:

[http://pastebin.com/neMQaKfi](http://pastebin.com/neMQaKfi)

( I right clicked just before the 
[Thread 0x7fffdf4ca700 (LWP 31802) exited] 
line 92)

---

### Post by tgalati4 on 2014-06-03
Well, that is not helpful.  I presume you have a bunch of tabs open and one tab has become pathological or your cache/profile has become corrupt.  Try clearing your profile or reinstall firefox.

The folks at Google refactored their web browser (Chrome) such that each tab runs in a jail (as a separate thread) such that if one tab goes bad, it doesn't take down the entire browser with all your tabs with it.  The Mozilla folks tried to do the same thing, but I don't think they performed a complete refactoring, so firefox runs as a main process with several threads, one for each tab, but it might not be as robust as Chrome in this situation.

Do you remember the last tab that you opened?  Also, there is a "safe" mode (just like in Windows) to run firefox without any extensions.  Perhaps there is a plug-in that has failed and is causing the problem.  You will have to look it up because I can't remember the switch for it.

```
firefox --help
```

You can open a JAVA console to see if there is a JAVA issue.  There is also a fatal warnings panel.  Let us know if you have any luck.

---

### Post by ct2034 on 2014-06-04
Thanks for your help.
The thing is, it appens every time. No matter which tabs are open. Whenever I right click or open some other thing thats overlaying in ubuntu. ( I think those are all UI elements that are handled by Ubuntu like menus and such ) -> crash
And as I said earlier, I have tried reinstalling and resetting already.

---

### Post by monkeybrain20122 on 2014-06-04
What is the specs for your computer. How much ram do you have? FF freezes and crashes on my roommate's lubuntu laptop with similar symtoms, turned out he has a huge cache and the system just can't handle it. Deleting the cache and limiting its size ( Edited > Preferences > Advanced > Network > Override automatic cache management and set some small number) fixed his problem.

---

### Post by LastDino on 2014-06-04
This used to happen to me on 13.10 quite frequently, FF would crash at every right click (I'm in habit of opening new tap from there). I did not find any working solution for this but I did try few more things which I can suggest.
By the way, I came to conclusion that this is not Ubuntu problem, its a FF problem.

Have you tried starting FF in safe mode? 
[https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode](https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode)
Also, please list the plugins you've installed. 

If you've hardware acceleration turned on, please turn that off too.

+1 to above post for system config and cache tip as well.

---

### Post by ct2034 on 2014-06-27
@[**[COLOR=#000000]LastDino[/COLOR]**]("http://ubuntuforums.org/member.php?u=1919686"): Sorry for beeing rude but please simply read my first post ...
@[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403"): Thanks for the tipp. But this doen't seem to be the case. ff crashed EVER SINGLE TIME i right click. also when freshly started having 28KB cache.
@[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895"): please look in my first post, too. I really tried safe-mode and disabling plugins. And as also said before it not depends on the number of open tabs.

---

### Post by Dax9108 on 2014-10-27
did you find a solution to this problem? the same thing is happening for me. seemed to start in firefox, but now if i right click at all, whether or not firefox is running, the cursor freezes. no key commands work either.

---

### Post by Peter_Parsley on 2015-07-23
I had exactly the same thing in Ubuntu 14.04. Every time I right clicked in Firefox, it crashed. I found the problem to be a tweak in Unity Tweak tools (UTT). 
Somehow not all tweaks from UTT work for me. For instance I choose the black cursor, but I didn’t work, but I left it anyway and I forgot. 
When I changed it back to the default white cursor, rebooted, my problem of the right click crash disappeared. 

Try setting all the Unity Tweak Tool settings to default and reboot.

---

