---
title: "Emerald themes?"
date: 2008-06-29
forum: General Help
---

### Post by kooldino on 2008-06-29
I'm running KDE on 8.04.

On my old 7.10 KDE setup, I had the emerald theme manager installed (just as I do now), however, I had some repositories that gave me a slew of themes to choose from that I could select from within the Emerald Theme manager.

Does anyone know how I could get those back?

---

### Post by Grishka on 2008-06-29
you can get them from Compiz git, they should work with Compiz from Ubuntu repos.

---

### Post by kooldino on 2008-06-29
How can I do that?

---

### Post by isaacj87 on 2008-06-29
The emerald-themes package was not included in anything later than 7.10 (Gutsy). However, the package from Feisty should work fine. You can find that here:

[http://packages.ubuntu.com/feisty/all/emerald-themes/download]("http://packages.ubuntu.com/feisty/all/emerald-themes/download")

---

### Post by kooldino on 2008-06-30
> **isaacj87 said:**
> The emerald-themes package was not included in anything later than 7.10 (Gutsy). However, the package from Feisty should work fine. You can find that here:

[http://packages.ubuntu.com/feisty/all/emerald-themes/download]("http://packages.ubuntu.com/feisty/all/emerald-themes/download")

That's not exactly what I had, but good enough for me.

I only have the Emerald theme manager, so I can only select a skin, but not apply it.  Maybe on reboot it will apply the new skin?

---

### Post by kooldino on 2008-06-30
Nope, that didn't work...how I have the skins, but I can't figure out how to apply them. :-/

---

### Post by munkyboy on 2008-07-01
I had this exact problem.

You need Emerald to be running as your window manager

I solved it by installing the compiz fusion tool bar thingy (Sorry for the tech speak but im a noob and away from my home pc)  and using that to choose Emerald as my window manager.

After that Emerald works perfect.

---

### Post by Mahinva on 2008-07-01
I just had the same problem, although I'm running Ubuntu.

I went into Add/Remove programs, searched for "Compiz" and installed "Compiz Fusion Icon". Right-clicked the icon that appeared on my desktop panel and highlighted "Select Window Decorator", then selected Emerald. Also, I right-clicked on my desktop and selected "Change Desktop Appearance". I had Visual Effects set to "None" - I changed this to "Normal". By turning Visual Effects on, I was then able to change my theme in Emerald. I hope that this helps you out, if you're still wondering how to get things running.

---

### Post by isaacj87 on 2008-07-01
> **kooldino said:**
> That's not exactly what I had, but good enough for me.

I only have the Emerald theme manager, so I can only select a skin, but not apply it.  Maybe on reboot it will apply the new skin?

Hey,

The version (the link I posted) is quite old. The version is 0.2.1 and the lastest version from Git is 0.6.99. I have built a deb from Git (not a checkinstall deb, but a "pure" one). If you would like to try a later version I can give it to you. Just PM me!

Take it easy,

Isaac

---

### Post by kooldino on 2008-08-05
Thank you fellas, that did the trick.

The key was to set Emerald as the window decorator...at that point any window decorations I chose applied on the fly whereas before they didn't do anything (since it would probably apply it anyway, but it was irrelevant since I was running the KDE window decorator).

Now I just have to figure out two things.

1-how to get more themes
2-What the difference between the Frame Engines are.

---

### Post by m60dude5 on 2008-08-06
Just FYI - You will need to hit ALT F2 and type "emerald --replace"
for the new themes to take effect when using emerald.
Not sure if someone already said this above (I didn't read through the whole thing).

---

### Post by kooldino on 2008-08-06
> **m60dude5 said:**
> Just FYI - You will need to hit ALT F2 and type "emerald --replace"
for the new themes to take effect when using emerald.
Not sure if someone already said this above (I didn't read through the whole thing).

Since I chose emerald as my Window Decorator using the Compiz Fusion icon, it's not necessary to do that.  But that's just another way to skin a cat!

---

