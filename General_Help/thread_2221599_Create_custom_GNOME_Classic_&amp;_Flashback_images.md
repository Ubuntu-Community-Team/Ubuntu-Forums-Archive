---
title: "Create custom GNOME Classic &amp; Flashback images"
date: 2014-05-02
forum: General Help
---

### Post by lpm11 on 2014-05-02
Hi!

I am trying to create modified iso image for my workers - and override some default settings. For example I set the gnome-terminal to be black with unlimited scroll and many other things. Everything OKay. I removed whole Unity (and ubuntu-desktop), and installed gnome-classic.
I currently have one little problem, described here: [http://askubuntu.com/questions/134172/window-title-bars-missing-occasionally-in-unity](http://askubuntu.com/questions/134172/window-title-bars-missing-occasionally-in-unity) . After first login, when I type dconf write ... [array with 'decor' included] - or just enable plugin in ccsm; title bars come back!.... but I have to do it manually for every new account which is really bad for me :/

And I want it to be fully automated. Every other option is written in /usr/share/glib-2.0/...gschema.override - and that works excellent. The problem is /org/compiz/profiles/unity/plugins/core/active-plugins is ignored - actual value is being restored to some default (without 'decor').

The problem exists only with gnome-fallback-compiz session. Metacity is great.
How to deal with it? 

I tried other locations (injecting dconf into /etc/skel) but it didn't help - the same problem.

I modify images with uck, and test on virtualbox qemu and real machines.

---

### Post by cariboo on 2014-05-02
Seeing as trusty has been released, and this is off topic, moved to a thread of it's own in General Help.

---

### Post by lpm11 on 2014-05-03
OK, the reason is simple - migration scripts force disabling this plugin.
It is here: /usr/share/compizconfig/upgrades/com.canonical.unity.unity.04.upgrade
You should copy this file to /usr/share/compizconfig/upgrades/com.canonical.unity.unity.08.upgrade and replace "-" with "+".

Now decor plugin is enabled by default.
Problem is SOLVED!

---

