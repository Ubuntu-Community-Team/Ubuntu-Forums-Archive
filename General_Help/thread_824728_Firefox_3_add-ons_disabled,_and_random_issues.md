---
title: "Firefox 3 add-ons disabled, and random issues"
date: 2008-06-10
forum: General Help
---

### Post by Replicon on 2008-06-10
hi,

I just picked up FF3.0 (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008060309 Firefox/3.0) a few minutes ago, and it decided that there are no compatible versions available for pretty much any of my add-ons, with the exception of flashblock. Is this a known issue that is actively being worked on? Usually, there's always a version available well before a new FF becomes "mainstream".

While I can live without most of that stuff, not having Adblock and Greasemonkey is a deal-breaker for me.

In addition, ever since my update to 8.04, which picked up FF3Beta, flash has been way more broken than normal. It used to be the case that opening a link in a new tab while doing something with flash (e.g. viewing a youtube video) would not nuke that instance of flash. Is there a work-around for this? Is it flash in general, or a broken firefox plugin?

---

### Post by Het Irv on 2008-06-10
Somethings not right if you can't get your add-ons to work, Ad-Block, No-Script work just fine after the update yesterday.  Have you tried uninstalling and reinstalling?  Just make a copy of the .mozilla file in your home folder to save all of your settings.

---

### Post by Replicon on 2008-06-10
That might do the trick; I'll try it out. I was browsing while the update was going on, and I did notice that just as I was about to log off of a forum just like this one, it froze on me completely, so I had to manually kill the process.

---

### Post by Het Irv on 2008-06-10
It seems like alot of people have been having problems with the FF RC.  The Ubuntu team is pretty good about bugs like this so it shouldn't be to long before some fixes are released.

---

### Post by Replicon on 2008-06-11
Hmm, didn't work. though I probably did it wrong. "sudo aptitude remove firefox" removed one package of size 123kB (or so it said). And ff was still installed. I did the inverse operation just in case... er... how does one do this? hehe

---

### Post by Het Irv on 2008-06-11
What reinstall:
```
sudo aptitude install firefox
```

---

### Post by MariusSilverwolf on 2008-06-11
Greasemonkey is currently only built to support through FF3 B5, so it won't work with RC1 or RC2.  Same for Stop-or-Reload buttons, and the VFox|Finder2 theme.

When I jumped from Gutsy to Hardy, many of the add-ons I had installed were initially incompatible.  I had to open the /Home/{user}/.mozilla/firefox/{profile}/extensions folder and delete every extension and re-install the ones I wanted to get it set up again.

It's bothersome and time consuming, but it worked.

---

