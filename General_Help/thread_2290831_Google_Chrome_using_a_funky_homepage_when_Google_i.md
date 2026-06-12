---
title: "Google Chrome using a funky homepage when Google is set to homepage"
date: 2015-08-15
forum: General Help
---

### Post by michael-piziak on 2015-08-15
Something has changed about my Google Crhome version of Google.

I even went into settings and told it to use [http://www.google.com](http://www.google.com)

But for some reason I'm getting this "myway powered by Google" search and search results.

I want the classic Google search and search result.

See my 2 attached screenshots where I searched for "donkey" and it gave me this funky new search result "powered by myway"

---

### Post by kerry_s on 2015-08-15
google "remove myway redirect virus", suggest you use a different browser to google that. lol

---

### Post by ruzekle on 2015-08-15
Wow, this is the first time I've seen what we've called a "top hat virus" on an Ubuntu computer. That must mean you've installed something to either reset your homepage or create a google redirect. It's a nasty thing.

At work, we'd do a virus scan, but since this is Linux, you may be better off removing Google Chrome and purging the files, then reinstalling.

Maybe you infected a different machine that set your homepage differently?

I can't say, but I've only seen this as a virus on Windows computers.

---

### Post by michael-piziak on 2015-08-15
I have clamTk virus scanner.  I'm running it now to see if it will help me get rid of this booger.

I think I can remove Google Chrome in the software center, but do tell me the instructions on "purging the files, then reinstalling"  just in case ClamTk can't destroy this nasty booger.

I'm using Ubuntu 12.04 LTS - supported through 2017 I do believe.

p.s. I have not installed anything in the past month.  I don't recall created a google redirect in any way (that I can recall doing).

---

### Post by michael-piziak on 2015-08-15
OK, ClamTk found lots of threats and quarantined them; however, it did not kill this nasty booger.So, please advise.  what's the best way to purge my system of Google Chrome, as suggested previously, and reinstall it.Below is a screenshot of all the threats that ClamTk found and I quarantined them all.

---

### Post by kerry_s on 2015-08-15
from the image it looks like it's just in your cache, clear your cache. ctrl+shift+delete in google chrome

---

### Post by Irihapeti on 2015-08-15
I don't see that it's necessary to remove Google Chrome itself, but you should remove the user directory with the cache etc in it.

I use Chromium, not Chrome, so it might be a bit different, but the user files are kept in ~/.cache and ~/.config

Removing those should obliterate your profile and allow you to start again.

If that doesn't work, someone else with more clues than me will need to take over.

---

### Post by michael-piziak on 2015-08-15
> **kerry_s said:**
> from the image it looks like it's just in your cache, clear your cache. ctrl+shift+delete in google chrome


Thanks so much for your reply; however, I did that ctrl+shift+delete and cleared *EVERYTHING*.   I even had to retype my username and password to get to this forum.

But, sadly, the same homepage comes on.    I even changed it to [http://www.yahoo.com](http://www.yahoo.com) to be my homepage, but it keeps going to myway powered by google when I start the browser or when I click the icon to "open the homepage."

Quite a nasty little booger I've got here.

---

### Post by michael-piziak on 2015-08-15
> **Irihapeti said:**
> I don't see that it's necessary to remove Google Chrome itself, but you should remove the user directory with the cache etc in it.

I use Chromium, not Chrome, so it might be a bit different, but the user files are kept in ~/.cache and ~/.config

Removing those should obliterate your profile and allow you to start again.

If that doesn't work, someone else with more clues than me will need to take over.

Please give me more specific directions to use my GUI (my mouse) to navigate to the suer files/cache files to delete.

I imagine these are in my home folder somewhere, and I may have to tell Ubuntu to show me the hidden files to get to it.

I'm not very command line savvy, so if you could direct me to where these files are exactly when I click "home folder" and then click "file system" then I will attempt to find them and delete/trash them.

Thanks so much for your help!

---

### Post by kerry_s on 2015-08-15
did you try the "settings> advanced settings-> reset settings" in chrome ? it's all the way at the bottom of settings.

usually it's not needed in linux, but i'd also recommend a reboot, just to get any parts of chrome that may be in ram/swap.

---

### Post by michael-piziak on 2015-08-15
> **Irihapeti said:**
> I don't see that it's necessary to remove Google Chrome itself, but you should remove the user directory with the cache etc in it.

I use Chromium, not Chrome, so it might be a bit different, but the user files are kept in ~/.cache and ~/.config

Removing those should obliterate your profile and allow you to start again.

If that doesn't work, someone else with more clues than me will need to take over.

I found the following 2 folders in my hidden folders.   Should I trash both the cache folder and trash the config folder that are connected to Google Chrome, or should I open each folder and delete all files and contents in the 2 folders.

See screenshot below:

---

### Post by monkeybrain20122 on 2015-08-15
> **michael-piziak said:**
> Please give me more specific directions to use my GUI (my mouse) to navigate to the suer files/cache files to delete.

I imagine these are in my home folder somewhere, and I may have to tell Ubuntu to show me the hidden files to get to it.

I'm not very command line savvy, so if you could direct me to where these files are exactly when I click "home folder" and then click "file system" then I will attempt to find them and delete/trash them.

Thanks so much for your help!

```
rm -r .cache/google-chrome && rm -r .config/google-chrome
```

Not sure if you need to delete the entire .config and .cache directories. Anyway, try this first.

Edited: of course close Chrome first before you do this.

---

### Post by michael-piziak on 2015-08-15
> **kerry_s said:**
> did you try the "settings> advanced settings-> reset settings" in chrome ? it's all the way at the bottom of settings.

usually it's not needed in linux, but i'd also recommend a reboot, just to get any parts of chrome that may be in ram/swap.

I will try this now and re-post here what my results are.   Thanks for your help.   Here I go, be right back!   LOL

---

### Post by michael-piziak on 2015-08-15
> **kerry_s said:**
> did you try the "settings> advanced settings-> reset settings" in chrome ? it's all the way at the bottom of settings.

usually it's not needed in linux, but i'd also recommend a reboot, just to get any parts of chrome that may be in ram/swap.


I'm back.  Yes I did this and it *WORKED* !

Thanks so much!

I will mark this thread as solved in a few hours.  I usually mark a thread as solved immediately when I get the solution, but I think this is a good thread for the Ubuntu community to study.  
Perhaps a Software Up To Date Security Update will be created for this issue.

Again, thanks and I'll mark this as solved in a few hours.

Have a great evening and night - depending where you are in the Ubuntu World !

Michael

---

### Post by kerry_s on 2015-08-16
i think you should get some "noscript" & "adblock" it will pretty much stop all the bad unless you allow it.

---

### Post by michael-piziak on 2015-08-16
> **kerry_s said:**
> i think you should get some "noscript" & "adblock" it will pretty much stop all the bad unless you allow it.


ok thanks.

So how do I get this "nonscript" and "adblock?"

I am a power users, but I don't know much code or caommand lines unless peeps like you tell me what to type in to terminal.

:)

---

### Post by kerry_s on 2015-08-16
there chrome extensions, you just go to the app store & search. there are many to choose from, boils down to personal preference.

i like things simple, i hate when there's to many settings & i don't like extensions that slow the browser.
the 1's i use:
 [https://chrome.google.com/webstore/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg?utm_source=chrome-app-launcher-info-dialog](https://chrome.google.com/webstore/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg?utm_source=chrome-app-launcher-info-dialog)

[https://chrome.google.com/webstore/detail/noscript-suite-lite/ahnanjpbkghcdgmlchbcfoiefnifjeni?utm_source=chrome-app-launcher-info-dialog](https://chrome.google.com/webstore/detail/noscript-suite-lite/ahnanjpbkghcdgmlchbcfoiefnifjeni?utm_source=chrome-app-launcher-info-dialog)

sorry, for the slow response, i was watching movies full screen, notifications don't show in full screen.

---

