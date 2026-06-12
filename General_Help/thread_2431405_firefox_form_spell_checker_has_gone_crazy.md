---
title: "firefox form spell checker has gone crazy"
date: 2019-11-16
forum: General Help
---

### Post by Skaperen on 2019-11-16
the firefox form spell checker has gone crazy.  it is flagging every word with the red sqiggly line under them.  oddly, it didn't flag its own name.  maybe it is unable to read the dictionary file?  i can read the system one OK but i know there is a special language pack for firefox so it's probably trying to read a different one.  when i right click on every word, the suggestion list is gone and it has a greyed-out "No Spelling Suggestions".  anyone have any idea what file it is trying to read?  any idea what could have caused this?  i've made no system changes, today.  ooh, it didn't flag "i've".  i just did a 3rd screenshot and all the red sqiggly lines went away at the instant i did that.  that screenshot did capture them so they went away after it.  now i see that the spell checker is not working at all.  maybe it gave up or crashed due to so many errors.

these screenshots are 1920x1080 (HD size) taken while editing this post:
the 3rd screenshot that captured the red lines is at:  [http://ipal.net/ubuntu/201911152326371154169559.png](http://ipal.net/ubuntu/201911152326371154169559.png)
the 4th screenshot that shows the red lines now gone: [http://ipal.net/ubuntu/201911152331261930468797.png](http://ipal.net/ubuntu/201911152331261930468797.png)
the 5th screenshot that shows it not even working: [http://ipal.net/ubuntu/201911152352581776734113.png](http://ipal.net/ubuntu/201911152352581776734113.png)

---

### Post by John_Patrick_Mason on 2019-11-16
I'm by no means an expert, but do you have more than one spelling dictionary installed?

Usually, if I change languages in Firefox, Firefox will immediately highlight everything I've written in the previous language. Try closing and opening a new instance of Firefox and see if you're able to reproduce the behavior you described. Then try to write something in the English language.

If Firefox decides to highlight what you wrote, right-click on the highlighted word, make sure "check spelling" is checked, and scroll to where it says "languages." If you live in the U.S., "English (United States)" should be checked. But for any language to be available, you have to make sure the right spelling dictionary is installed prior to that.

---

### Post by Skaperen on 2019-11-16
i do have many dictionaries installed, some of the many languages i read, such as Norwegian, Swedish, and Danish.  all the words are underlined, again.  do you think it has chosen a different language?

her er en testlinje på norsk.
här är en testlinje på svenska
her er en testlinje på dansk
hier is een testlijn in de Nederlandse
voici une ligne de test en français
ecco una linea di test in italiano
jen provo-linio en Esperanto

the words in Esperanto are not underlined.  but i have no packages installed for Esperanto.

"Check Spelling" is checked.  English (United States) is already chosen.  i have been having issues with firefox flagging US words as mispelled but not British.  this has been happening all year, even back in 16.04 (i am running Xubuntu 18.04 since July 1 this year and that didn't get fixed.  and today is the first time it is flagging everything.  it is flagging the Esperanto, now.  but it is not flagging "Xubuntu".  it's as if it has the true/false state backwards.  it flags "colour", now but not "color".  strange.

---

### Post by Skaperen on 2019-11-16
i have rebooted, upgraded, then rebooted twice.  it changed my language setting to "English (Canada)" so i changed it back to "English (United States)".  it is behaving well under both settings.  no idea what the trouble was.  i'll assume a memory corruption issue until i have a reason to believe otherwise.

---

### Post by John_Patrick_Mason on 2019-11-16
[QUOTE=Skaperen]i do have many dictionaries installed, some of the many languages i  read, such as Norwegian, Swedish, and Danish.  all the words are  underlined, again.  do you think it has chosen a different language?[/QUOTE]

That was my initial hunch, but, to be honest, I'm not sure.

Go under Tools > Add-ons > Dictionaries. What dictionaries do you have installed, if you mind me asking? I'm not talking about Language Packs, those are different.

Edit: Just noticed your most recent post. Based on your latest post, I think you might be confusing language packs with spelling dictionaries. If you go under Edit > Preferences > Language and Appearance > Language, that particular setting isn't referring to spellcheck. That particular setting is referring to language packs, which are the language that Firefox uses in its menus. Think: File, Edit, View, History, Bookmarks, Tools, and Help. The default for that setting is "English (Canada)". To change the spellcheck dictionary language, you need to go under Tools > Add-ons > Dictionaries and add whatever *spelling dictionary* language you want there.

I'm glad it worked out for you. I often use multiple languages, too, and, at least, in my experience, when I encountered the same problem, it was because the wrong language was set.

---

### Post by Skaperen on 2019-11-16
there is one thing different today.  i started using Thunderbird + IMAPS for my email.  that seems to be working OK.

---

### Post by Skaperen on 2019-11-16
Tools > Add-ons > Dictionaries only lists English United States and the 2 dialects of Norwegian.

---

### Post by John_Patrick_Mason on 2019-11-16
[QUOTE=Skaperen]Tools > Add-ons > Dictionaries only lists English United States and the 2 dialects of Norwegian.[/QUOTE]

But you said you upgraded and it solved the problem. Do you remember which languages you had installed under Tools > Add-ons > Dictionaries before you upgraded? Maybe you had the right languages installed, but they were disabled under Tools > Add-ons > Dictionaries. Otherwise, you could be right.

---

### Post by Skaperen on 2019-11-16
i do not recall what was under Tools > Add-ons > Dictionaries before.  when i did look, i was dealing with the British vs. American issue.  it might have had British English.  every time i would see the language selection not be United States i would change it back wonder how it got changed.  maybe someday they will have a tracker for all settings changes showing what program made changes, its process ancestry, and what it puts in the "why" comment.

---

