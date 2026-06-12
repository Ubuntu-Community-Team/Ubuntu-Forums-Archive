---
title: "Help! Firefox just went nuts!"
date: 2008-05-30
forum: General Help
---

### Post by LeoSolaris on 2008-05-30
Ok, I have a major issue that just struck today. Firefox (default install from 8.04 64bit) just decided to start doing the following:

1.) forget all of my bookmarks,

2.) no longer allows the back button to be clicked, even though it is there

3.) no longer display current address. It will display something if I type it in, but it will not change until I type something else in.  For instance, If I type in 'gmail.com' It will only display 'gmail.com' and not the normal string of things displayed when you are redirected to the login page. If I Click on something, say in the forums, it will just show a blank line at the top rather than the address.

4.) It has stopped accepting cookies, dispite being set to accept them until Firefox is closed. I discovered this by re-downloading the theme I use, and when I restarted, it was just a blank page rather than the list of theme downloads.

5.) yesterday firefox mysteriously added a Toolbar menu entry for my recently visited pages, even though it had never been there before. There was also a recent history folder in my bookmark menu.

I have purged it from my system, restarted, then installed it again. It came back partially, but it wasn't "default" I tried to re-import my bookmarks from the HTML I made of my last install. I had used it before, and it did work. I can open the page still, but even when I try to add them one at a time manually, it doesn't do anything. I tried to restore the bookmarks from the auto restore backups that FF3 makes, but it did nothing.

I did an rkhunter and a chkrootkit, and chkrootkit returned only this:
```
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[8740], /sbin/dhclient3[8762])

```

I am at my wits end on what the heck happened!

Something is seriously wrong here.

Leo

---

### Post by TheFuzzy0ne on 2008-05-30
It sounds to me like you may have installed an extension that's messing with Firefox, possibly because the XUL code is not valid (or something like that).

A good start might be to shut down Firefox, and then backup all of the files in /home/your_username/.mozilla/ directory and then delete it. Just moving the directory should do it. When you restart Firefox, you should have a new profile created, and everything should be working.

Let me know how you get on with that, and I can hopefully help you get your bookmarks back if all is well.

---

### Post by LeoSolaris on 2008-05-30
Thanks! It was the upgrade to the release candidate from beta 5. It did not transition smoothly. Grr.

Add one more to the Updates that don't update fully...  Evolution. I just updated it before noticing all of this crap with Firefox and poof...   part of evolution is there, part of it is not.

This is getting old. It also deleted my alacarte menu editor!  Talk about annoying.

I think it may be time to turn the proposed updates off.

Leo

---

### Post by TheFuzzy0ne on 2008-05-30
Yeah, I had heaps of trouble getting Firebug to work with Firefox 3. I have actually manage to get them installed side-by-side. Are you able to run "firefox-2" from the console? In my case, "firefox-2" starts Firefox 2 and "firefox" and "firefox-3.0" both start Firefox 3 beta. "firefox" is just a symlink which can be easily changed to run Firefox 2 by default.

Hope this helps.

---

