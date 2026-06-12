---
title: "A Day In Ubuntu"
date: 2007-09-11
forum: General Help
---

### Post by Bill Collecta on 2007-09-11
I have no idea if this is in the right forum. However, right now I've been using Ubuntu all day and not until now I realised I was using Ubuntu all day! It felt so natural, heck even using Gaim instead of MSN was something I didn't really notice.

 I tell you, Ubuntu is so easy. One thing that does annoy me is that I can't go to the desktop with "Windows Button + D", I tried keybinding it in the Keyboard Shortcuts, but as soon as I hit the "Windows Button", it shows: Super L.

Next to that I tried using World of Warcraft, on Cedega it didn't run AT ALL. And in Wine it ran fairly ok. However, I've never run it from an External HDD (And I have USB1.1) So that explains the slowness.

Currently I'm loving Ubuntu. I got my music, I got my pictures, I got Firefox. I got **NO Firewall or Antivirus**. xD

I had to install a patched driver though, but it was fairly easy with a guide. At the moment I think I'm gonna stick around in Ubuntu for a while, I might keep you guys updated. :D

- Holla!

---

### Post by dpar on 2007-09-11
How about that little square on the lower left of your screen to go to the desktop?

---

### Post by mali2297 on 2007-09-11
> **Bill Collecta said:**
> 
 I tell you, Ubuntu is so easy. One thing that does annoy me is that I can't go to the desktop with "Windows Button + D", I tried keybinding it in the Keyboard Shortcuts, but as soon as I hit the "Windows Button", it shows: Super L.

You don't think that Ubuntu would call it "Windows button", do you? :)
Type "Super L + D" and it will work.

---

### Post by ubuntukerala1980 on 2007-09-11
If your are using gnome
Ctrl + Alt + D 
will give you desktop
:guitar:

---

### Post by ubuntukerala1980 on 2007-09-11
For firewall try firestarter, its so easy :guitar:
Try the  link below too
[http://www.linux.com/articles/55319]("http://www.linux.com/articles/55319")

---

### Post by Bill Collecta on 2007-09-12
> **mali2297 said:**
> You don't think that Ubuntu would call it "Windows button", do you? :)
Type "Super L + D" and it will work.

If only I could manually type that <.<

---

### Post by Delkster on 2007-09-12
> **mali2297 said:**
> You don't think that Ubuntu would call it "Windows button", do you? :)
Type "Super L + D" and it will work.

Unfortunately, I'm not sure if it's possible to use super (a.k.a. the Windows key) as a modifier in X. It works as an independent key, though.

Bill, you could try editing the keyboard shortcut settings by hand by hitting Alt+F2 and entering "gconf-editor", then navigating the tree to "apps > metacity > global_keybindings" and typing a value for the show_desktop key by hand, but again, I'm not sure if you can directly use super as a modifier like alt and ctrl.

---

### Post by Bill Collecta on 2007-09-12
Nope, you can't use it as a modifier :)

---

### Post by stchman on 2007-09-12
> **Bill Collecta said:**
> I have no idea if this is in the right forum. However, right now I've been using Ubuntu all day and not until now I realised I was using Ubuntu all day! It felt so natural, heck even using Gaim instead of MSN was something I didn't really notice.

 I tell you, Ubuntu is so easy. One thing that does annoy me is that I can't go to the desktop with "Windows Button + D", I tried keybinding it in the Keyboard Shortcuts, but as soon as I hit the "Windows Button", it shows: Super L.

Next to that I tried using World of Warcraft, on Cedega it didn't run AT ALL. And in Wine it ran fairly ok. However, I've never run it from an External HDD (And I have USB1.1) So that explains the slowness.

Currently I'm loving Ubuntu. I got my music, I got my pictures, I got Firefox. I got **NO Firewall or Antivirus**. xD

I had to install a patched driver though, but it was fairly easy with a guide. At the moment I think I'm gonna stick around in Ubuntu for a while, I might keep you guys updated. :D

- Holla!

Ubuntu has all your ports stealthed by default (iptables).  AV is not needed as Ubuntu is virtually immune to viruses.  The only reason to use AV is if you send email to your Windows friends.

---

### Post by mali2297 on 2007-09-12
> **Bill Collecta said:**
> Nope, you can't use it as a modifier :)

Alright, I'm running XFCE where that isn't a problem.

---

### Post by Dylnuge on 2007-09-12
X is not the problem, GNOME is. Both XFCE and KDE allow the Super key(s) to be used as modifiers. GNOME treats it as a single key.

Of course, if you like GNOME, there is probably a way to get the Super key to act as a modifier. Not entirely sure how.

If I ever get one of those new Optimus keyboards (which are over $1500 and therefore I never will) I am making the "Windows" key a penguin ;-)

---

### Post by telemenar on 2007-11-29
> **Delkster said:**
> Unfortunately, I'm not sure if it's possible to use super (a.k.a. the Windows key) as a modifier in X. It works as an independent key, though.

Bill, you could try editing the keyboard shortcut settings by hand by hitting Alt+F2 and entering "gconf-editor", then navigating the tree to "apps > metacity > global_keybindings" and typing a value for the show_desktop key by hand, but again, I'm not sure if you can directly use super as a modifier like alt and ctrl.

What you can do to use the windows key a modifier in a short-cut is open gconf-editor as described above, Navigate to the spot Delkster mentioned using the tree on the left. Find the entry "show desktop" on the right. Right click, and select edit. Then replace what it says in that box with "<Super>d" and then the windows key will work for that. Its weird but for some reason the Gnome settings manager won't let you use the key as a modifier when setting up short cuts but it works if you get it setup some other way.

---

