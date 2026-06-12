---
title: "[SOLVED] totem taking over mp3 despite preferred application setting"
date: 2008-03-11
forum: General Help
---

### Post by DouglasAWh on 2008-03-11
I have rhythmbox set up as my default media player, but totem keeps opening up my mp3s.  Additionally, if I drag some files into rhythmbox they don't seem to automatically import.  now, the files already in the library...rhythmbox plays them fine. This is a fresh install of ubuntu, minus the ubuntustudio-look, gstreamer and thunderbird packages and some other random things.  The reformat happened yesterday and I've been going back and forth between this machine and the laptop all day, so it's not like I've been busy installing stuff all day.  All my music is setting on /media/sda5, not on the same partition as the OS.  Let me know if you need any more info.

Thanks!

---

### Post by itix on 2008-03-11
Right click on an mp3, go to properties then klick open with and select rhythmbox

---

### Post by DouglasAWh on 2008-03-11
rhythmbox is already an option when I right click, but if I go to the open with menu, it isn't there.  When you go through the system -> Preferences though it's set up as the default.

---

### Post by itix on 2008-03-11
The "open with" tab in right click => properties option on mp3s??
That's strange,
You can add it by clicking add and search the available programs. If you still don't find it, use the custom command
```
rhythmbox
```

---

### Post by DouglasAWh on 2008-03-11
hmm, I had thought my laptop defaulted to rhythmbox, but that doesn't seem to be the case.

As you can see [img]http://farm3.static.flickr.com/2345/2327398441_25daf60a82_o.png[/img]

I have rhythmbox set as the default, but when I double click, it opens in totem.  This happens whether it is .ogg or .mp3.  I'd show you what my right click looks like, but I can't seem to take a screen shot at that point.  This isn't as big of a deal as it was, because it seems adding to the library was taking a long time because it was still going through the first time and there are lots of music files.  If I could get it fixed, great, but I was just freaking out because I couldn't get that one song in a playlist and once rhythmbox finished parsing the dir added that file worked fine.

Thanks for the help and if you think of something else easy, let me know!

---

### Post by itix on 2008-03-11
Did you try the custom command line in the "open with" section?
It's the last entry when you right click.

It overrides the "preferred application" menu. I just tested on my desktop.

[IMG]http://img522.imageshack.us/img522/1276/screenshotoc7.png[/IMG]

---

### Post by Bubba64 on 2008-03-12
beside the ways suggested here you can also go to edit preferences in the Firefox browser click on contents then file types and depending on the type of media players and other files you have and what you want them to open with change the opener.

---

### Post by DouglasAWh on 2008-03-12
@itix THANKS!

Now, is it a bug that needs to be filed that the "Preferred Applications" way to do it doesn't work?

---

### Post by itix on 2008-03-12
Glad it helped :)

I have no idea. It may have been a design choice to make the "open with" tab higher ranked than preferred applications. If there is any staff here that could answer the question I'd love to know.

Btw, mark the thread as solved. Helps other people looking for answers to the same question.

---

