---
title: "Check Gmail &amp; Beryl"
date: 2006-12-21
forum: General Help
---

### Post by linuxbun on 2006-12-21
checkgmail, awesome bit of kit for the taskbar. It allowed me to delete spam messages or mark other things as read right from my desktop.

Then I installed beryl. Also totally cool, my dell seems to handle it very well and it looks so much cooler, so that's staying.

However, since installing beryl (& emerald) the checkgmail proggy doesn't work properly :( It'll still tell me when I have new mail etc etc, but I couldn't delete it or mark it as read like I used to from my desktop.

Anybody else had this? did you find a fix for it? :confused:

---

### Post by ciscosurfer on 2006-12-21
> **linuxbun said:**
> checkgmail, awesome bit of kit for the taskbar. It allowed me to delete spam messages or mark other things as read right from my desktop.

Then I installed beryl. Also totally cool, my dell seems to handle it very well and it looks so much cooler, so that's staying.

However, since installing beryl (& emerald) the checkgmail proggy doesn't work properly :( It'll still tell me when I have new mail etc etc, but I couldn't delete it or mark it as read like I used to from my desktop.

Anybody else had this? did you find a fix for it? :confused:I can confirm that this happened to me as well when I was running Beryl (or Compiz)...I never did find a fix for it.  Basically, the checkgmail drop-down would simply vanish if I tried to click a link...and sometimes, a HUGE black box would appear at the top.  :(

---

### Post by linuxbun on 2006-12-21
> **ciscosurfer said:**
> I can confirm that this happened to me as well when I was running Beryl (or Compiz)...I never did find a fix for it.  Basically, the checkgmail drop-down would simply vanish if I tried to click a link...and sometimes, a HUGE black box would appear at the top.  :(

Hmmmmmmerrrrmmm :( :( :( :-| [-( [-( [-(

---

### Post by raul_ on 2006-12-21
err....no problems here...I tried clicking "compose new mail" and it worked perfectly..or is that working with you 2?

---

### Post by xopher on 2006-12-21
What versions of Beryl are you running and with what? (eg. NVIDIA with TFP, or ATI with fglrx and XGL etc..)

Have you asked the beryl devs about this? Or posted a bug at bugs.beryl-project.org ?

You should try the advanced options in the context menu of beryl-manager. They might fix it for you too. (beryl => 0.1.3)

I personally haven't even tried this app (check gmail), I only have the extension for firefox, where can I find more information on this? It sounded really interesting :rolleyes:

---

### Post by eXisor on 2006-12-21
I think there is a generic problem with beryl z-order painting that is causing this behaviour. (In any event none of my tweaking of the setup options consistently nails the problem). You need to restart beryl (or reboot) until the problem goes away. It occurs on every beryl version to date.

The generic problem is that beryl often (on both the machines I use it on) loses the ability to enforce the correct painting z-order. This, IME, occurs, and does not fix itself, after a particularly heavy load spike.

Examples of this are: 
-  A dropdown appears under the title bar.
-  Modal dialogues are under owner windows
-  Popups are under owner windows.
-  The sequence of panel items change. (When running 1600x1200 in 24-bit colour I often get my system monitor to the right of the logout button, and that despite them all being locked to panel).

Since there are many threads alluding to this problem, here and on the beryl forum, perhaps they will fix it in some future incarnation.

---

### Post by linuxbun on 2006-12-21
> **raul_ said:**
> err....no problems here...I tried clicking "compose new mail" and it worked perfectly..or is that working with you 2?

The right clicking works, it's just if you try clicking the menu that appears when you hover over it, it just disappears :( 

Grr it's so annoying, but I love Beryl too much to change ](*,)

---

### Post by ciscosurfer on 2006-12-21
> **linuxbun said:**
> The right clicking works, it's just if you try clicking the menu that appears when you hover over it, it just disappears :( 

Grr it's so annoying, but I love Beryl too much to change ](*,)There are other gmail-checking apps out there as well, in addition to **checkgmail**.  The **kcheckgmail** app is one you can try -- it's KDE based but works just fine in GNOME (enable your universe repo).  There's also the **gmail-notify** app (also in universe).  There are also other apps/extensions that will check gmail from within Firefox (I don't know if you want to go this route or not)...the particular extension I'm thinking of is called **Gmail Notifier** and can be found here: [https://addons.mozilla.org/firefox/173/](https://addons.mozilla.org/firefox/173/)

There are also other extensions for Firefox that will grab not only your Gmail, but also your other mail (if you have accounts with them) from the likes of Yahoo!, MSN, etc., all simultaneously.

---

### Post by arnieboy on 2007-01-03
From the official [checkgmail project page]("http://checkgmail.sourceforge.net/"):
_CheckGmail and XGL/Compiz_  
Sorry, but these two don't seem to like each other very much (CheckGmail still works, but you won't be able to use a lot of the nifty features). I don't have a system running XGL and can't bugfix this one myself, but from what I can tell the issue lies with incompatibilities in the Gtk2-perl modules (and more specifically the signal_connect methods) rather than my own code. Please stop reporting this issue!! At the moment there's nothing I can do about it, and anyone experiencing this problem would be better off reporting it to the Gtk2-perl developers. Thanks!

---

