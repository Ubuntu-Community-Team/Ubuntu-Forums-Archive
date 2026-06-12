---
title: "can't drag and drop in Firefox"
date: 2022-04-10
forum: General Help
---

### Post by cylon6 on 2022-04-10
Hi

I'm using the Ubuntu 22.04 beta and I can't drag & drop tabs and bookmarks in Firefox. Is this a bug that others experience too? Or is it something on my system?

I installed Vivaldi and the Firefox Flathub (with same bookmarks and extensions) and dragging & dropping does work there. So only the Firefox snap is affected.

---

### Post by TheFu on 2022-04-10
I don't know what you mean by "drag & drop tabs and bookmarks". Is that 100% inside firefox or is some other program involved?   My guess is that it is related to Firefox conversion to a snap package. snaps often break workflows where different programs need to communicate.  So if 2 separate instances of firefox are started, running in different processes, then dragging 1 tab to the other FF instance would likely be blocked.

You might look through the snap constraint options to see if there is a connection available that allows 
[https://ubuntuforums.org/showthread.php?t=2449022](https://ubuntuforums.org/showthread.php?t=2449022) has more ... for a different browser, but the method would be the same.

BTW, this still belongs in the Development Release subforum until the official release. 22.04 is only an RC now.

---

### Post by cylon6 on 2022-04-11
I'll try to explain it differently, my first post might not be clear enough (English isn't my native language). With dragging and dropping, I meant rearranging the order of the tabs. For example: when I have 3 tabs open: Ubuntu | Ubuntu Forums | AskUbuntu. When I want to drag AskUbuntu to the first position, it doesn't work. I can click and right-click on the tabs, but I can't 'drag' them by clicking and holding the button pressed down. 

The same problem occurs when I try to rearrange the bookmarks in the bookmarks bar.

So there are no other programs involved, just Firefox. It's not like I want to drag an image from a browser tab to a text editor or something similar.

My mouse is working correctly because the same actions in Vivaldi (browser) and the Firefox Flathbub work fine.

---

### Post by ajgreeny on 2022-04-11
There has been a similar thread to this recently and the reason for not being able to move tabs was the use of wayland rather than X11 as the graphics system.

At the login screen see if the problem is still present if you login using X11 instead of the default in Ubuntu of wayland.
I suspect things will be back to what you know and want.

---

### Post by cylon6 on 2022-04-11
I had a similar problem with adding online accounts, that was only possible using X11.

I tried starting Firefox using X11 but only the flatpak worked, I couldn't launch the snap version. I tried multiple times and waited for half a minute. Nothing happened. So it might by a X11/Wayland problem but I can't seem to test it. Is there a way to log what goes wrong when I try to launch the snap using X11.

---

### Post by vanadium on 2022-04-11
Indeed, this is because of Wayland. It will work when switching to Xorg.

---

### Post by cylon6 on 2022-04-11
Small update: ajgreeny is right. I rebooted the computer and I could launch Firefox as snap using X11 and rearranging the tabs and bookmarks worked fine. So it seems to be a problem with Wayland.

Thanks for the help @ajgreeny, vandium & TheFu!

I don't know if I should mark this thread as 'solved' because it's a workaround using X11 in stead of solving the problem using Wayland. Or should I make a bug report about this?

---

### Post by TheFu on 2022-04-11
Marking SOLVED will let others find the workaround easier. Please do.
I'd open a bug with Mozilla, if they are the team creating the snap package.

1 more reason that snaps and Wayland aren't ready for prime-time use.

---

### Post by cylon6 on 2022-04-11
Ok, marked it as solved. I'll open a bug report with Mozilla. Thanks again for the fast feedback.

I'll use the Firefox flatpak for now.

Edit: The bug was already reported here: [https://bugzilla.mozilla.org/show_bug.cgi?id=1760449](https://bugzilla.mozilla.org/show_bug.cgi?id=1760449) It has something to do with gtk/mutter (but I don't understand exactly what's going on): [https://bugzilla.mozilla.org/show_bug.cgi?id=1760449](https://bugzilla.mozilla.org/show_bug.cgi?id=1760449)

---

