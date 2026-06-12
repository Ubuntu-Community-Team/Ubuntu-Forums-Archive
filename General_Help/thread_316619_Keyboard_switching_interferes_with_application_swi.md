---
title: "Keyboard switching interferes with application switching"
date: 2006-12-11
forum: General Help
---

### Post by metafile on 2006-12-11
Hello there, Ubuntu people.
I have a problem with one thing in Ubuntu, I think, this is a bug and it must be corrected.

So, the problem is:

I use english and russian keyboard layouts. I`ve tuned GNOME via Keyboard Options or whatever to switch layouts using Alt+Shift combination. This is one of the most popular (at least, in Russia) method of switching layouts.

But. When I have Alt+Shift keys binded to switch layout, I can`t switch between my applications with Alt+Shift+Tab (which is a reverse of Alt+Tab). Actually, for about a year of using Ubuntu I`ve been wondering, why couldn`t they make Alt+Shift+Tab working -- just because right after installation I immedatly activated second layout and the switching method described above.

Thus, I have to use another combination for language switching now, which is really really annoying, because at work I use winblows ekspee with that classic Alt+Shift method.

Please, somebody help me.
I think this should not stand :)

---

### Post by PurplePenguin on 2006-12-12
Privet metafile! :)

I never knew (until today!) about Alt-Shift-Tab, but since I'm also an Alt-Shifter, I can't use it, either. :(  Linux, or at least Ubuntu, definitely seems to allow Alt-Shift to act without paying much attention to other key-presses at the same time.

Although I can't be of any help, I hope somebody here has an answer for you!

---

### Post by _Artem_ on 2006-12-14
PREVED from Russia!
I'm also have problems with keyboard layout switching. My favorite method 'SHIFT+CTRL' cause so much troubles (seem to yours) so I've decided to use right 'ALT' for this task.
But it is not the end of sad story. Sometimes (o those f..g times!) layout switching stop to work. Hot keys o mouse click on the keyboard aplet don't help. However, X restarting helps.
Probably, someone overcome this bug??
Thanks for any advise..

---

### Post by PurplePenguin on 2006-12-14
Hmmm.... I've never run into this problem (thankfully!).  Although I don't really use hotkeys or combos for anything aside from switching layouts with ALT+Shift.

Clicking on the applet in the taskbar also doesn't work?  It sounds like there might be a part of Ubuntu that needs to be reinstalled - seems like something is acting up.  I'm not sure, though... hopefully somebody else knows!

---

### Post by _Artem_ on 2006-12-14
Right now (after just another X restarting) switching works only via mouse click on applet. Pretty story! While answering on your post I have made "last" try to change situation. And!..
I've gone to System-> Administration->Language Support (previously all times I worked with System->Preferences->Keyboard), and gnome announcement has appeared about not full language support. Gnome offered me to install some packages and in their name KDE was figured. And I've got it! Yesterday I installed K3b. After that problems have begun. I didn;t mention them for a wile, but now I know fault reason.
And, after installing those packages (and a little bit magic passages in Preferences->Keyboard :)) ), all has become fine.
Thank you for your answer! Without you period of solving this trouble might be much more greater! :)

---

### Post by PurplePenguin on 2006-12-14
> **_Artem_ said:**
> Yesterday I installed K3b. After that problems have begun. I didn;t mention them for a wile, but now I know fault reason.
And, after installing those packages (and a little bit magic passages in Preferences->Keyboard :)) ), all has become fine.

Molodets! :)

I'm glad that you followed up with this post.  Now if anybody else has this problem, hopefully they'll be able to help themselves after reading your post.

So it seems that installing kde-specific programs might have some unwanted side-effects in gnome.  Very interesting... I guess it does make sense, though!

---

### Post by andyba on 2006-12-17
I have found another related problem in ubuntu6.10. 
If I add the third language I can't switch the keyboard layout with hotkeys.
for example I have the following groups.
USA
Russian winkey
Romanian standard

when Russian or Romanian group is active, the hotkeys work until I reach the USA layout and then they stop.
the USA layout is default.
If I remove one of the languages and leave only 2 of them the hotkeys start to work normally.
Is there a solution to this problem?

---

