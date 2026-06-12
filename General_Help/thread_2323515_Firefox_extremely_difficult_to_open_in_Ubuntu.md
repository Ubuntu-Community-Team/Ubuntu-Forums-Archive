---
title: "Firefox extremely difficult to open in Ubuntu"
date: 2016-05-05
forum: General Help
---

### Post by elvis6 on 2016-05-05
Ubuntu Version is 12.04
I have been using this version on this PC for 2 years, and just now recently started having this problem.
I have searched other threads for this issue and there only partial similarities to the error messages I receive, therefore I could not find a working solution from any previous threads.
The following scenario happens every single time I try to open Firefox.

I start up the PC, wait a few minutes to make sure everything is loaded.
I hit the browser icon. Wait a few minutes. Nothing at all happens.
I hit the browser icon again. Wait a few minutes. Again, nothing happens whatsoever.
So, instead of waiting minutes at a time, I now click the browser icon every few seconds.
After hitting it a total of about 6 times, with a few second intervals, I get the following message :

***"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."***

I click OK, to make that pop-up go away. So, since it told me it's "already running" even though I don't see it, I wait a few more minutes.
A few minutes goes by, and Firefox still hasn't opened. Nothing.

So I click the browser icon again. Again, after getting zero response, I repeatedly click it, and after a few times, I get the following response :

[I][B]"Your Firefox profile cannot be loaded. It may be missing or inaccessible."
[/B][/I]
I click a couple more times, and I get this message :
[I][B]
"Firefox closed unexpectedly while starting. This might be caused by add-ons or other problems. You can try to resolve the problem by torubleshooting in Safe Mode. You can also skip troubleshooting and try refreshing Firefox. Choose one of the following options :
Refresh Firefox or
Start in Safe Mode"
[/B][/I]
The next pop-up says :

[I][B]"Start fresh to fix problems or restore performance.
This will :
Remove your add-ons and customizations
Restore your browser settings to their defaults"[/B][/I]

Then I see a processing bar, and another message states :
[I][B]
"Import Wizard :
Import Complete
The following items were successfully imported
Cookies
Bookmarks, etc etc"[/B][/I]

Then finally, the browser actually opens, with the following statement on screen :
[I][B]"Well this is embarrassing.
 Firefox is having trouble recovering your windows and tabs. This is usually caused by a recently opened webpage.
You can try :
Removing one or more tabs that you think may be causing the problem.
Starting an entirely new browsing session."[/B][/I]
At this point, I am able to restore to the previous web page I was on, or navigate to a new one.
So I am able to finally get online, but only after jumping through half a dozen hoops, and several minutes of this, which of course is very frustrating, inconvenient, time-consuming, not to mention the anxiety of wondering if one day the Import Wizard will fail to import all my bookmarks in the above-mentioned process.

All in all (in between multiple pop-up messages that appear and then do nothing) I have to click the browser icon about 15 or more times, over a period of several minutes and a dozen pop-ups
to go through.
Since I am not computer proficient, I only know how to take drastic measures to try to fix the problem, such as the following :
Uninstalled Firefox, re-started computer, then reinstalled Firefox. Still have the same problem.
Uninstalled and re-installed the ENTIRE Ubuntu OS from scratch. Still, the same exact problem.

The above scenario literally happens exactly the way I described above, literally 100% of the time I try to open the Firefox browser, whether I just 
booted up the PC, or re-booted it. Or even if the PC was already running, and I had just closed the browser, and then try to immediately re-open it,
it still happens.

Thanks in advance for help and suggestions.

---

### Post by PhilGil on 2016-05-05
Have you tried opening Firefox in Safe Mode? Does it open right away?

Open a terminal and enter ```
firefox -safe-mode
```

If Firefox open quickly and without errors in safe mode then your problems are likely the result of two years of accumulated crud and/or out of date extensions. Try clearing you history first, that won't effect your settings or add-ons. If things are still messed up you may have to refresh your profile.

---

### Post by vasa1 on 2016-05-05
Re. safe mode, the man page for Firefox in 12.04 and in 16.04 has this:```
       -safe-mode
              Start  firefox  in  safe-mode.  This  disables  all  third-party
              extensions, and may be necessary if you are having problems with
              an extension you installed.

```

---

### Post by vasa1 on 2016-05-05
Re. safe mode, the man page for Firefox in 16.04 has this:```
       -safe-mode
              Start  firefox  in  safe-mode.  This  disables  all  third-party
              extensions, and may be necessary if you are having problems with
              an extension you installed.

```

---

