---
title: "Firefox Keeps Asking Whether to &quot;Restore Previous Session&quot;"
date: 2006-10-31
forum: General Help
---

### Post by edwin11 on 2006-10-31
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi all,

i'm using Edgy and Firefox 2.0.

Everytime i start up firefox, it would ask me whether to "Restore Previous Session". Everytime. Even when i did shut it down properly the previous time. In fact, i would start firefox, choose "New Session", did nothing else, loaded nothing, and shut it down, and when i start it up again, it would still ask me whether to "Restore Previous Session".

Anyone else faces this? What could be causing it?

i have one prime suspect though.

When i start firefox, and look at the Error Console (before doing anything else or loading any page), it would have one entry:

```
Error: uncaught exception: [Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIStringBundle.GetStringFromName]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: chrome://browser/content/browser.js :: anonymous :: line 3930"  data: no]
```

i tried
a) disabling all extensions
b) re-installing firefox (via Synaptic)

but the error is still there.

i'm suspecting that this error is serious enough for firefox to "think" that it has crashed even when i close it properly. Even if not, its disconcerting at best. To be sure, i did a search, and indeed, the file browser.js does not exist anywhere on my filesystem.

Any advice, please?



TIA and Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by JimTDI on 2006-10-31
I have the exact same problem with a clean install (not an upgrade) of Edgy.  Haven't had a chance to figure out why yet, but if I do I'll post back to this thread. ](*,)

---

### Post by pillypoon on 2006-10-31
i have the same problem too.  I did a fresh install of Edgy on my desktop and on my Laptop.  The desktop has the error and the laptop does not.  the funny thing is I also had this problem with Dapper on my Laptop and not my desktop.

---

### Post by edwin11 on 2006-10-31
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]> **JimTDI said:**
> I have the exact same problem with a clean install (not an upgrade) of Edgy.  Haven't had a chance to figure out why yet, but if I do I'll post back to this thread. ](*,)

Same here, mine was also a clean Edgy install.



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by noynac on 2006-10-31
As a workaround, did you try disabling one of the session-restore options, as explained at:

[http://kb.mozillazine.org/Browser.sessionstore.enabled](http://kb.mozillazine.org/Browser.sessionstore.enabled)

or

[http://tinyurl.com/ye9bwd](http://tinyurl.com/ye9bwd)

The session-restore wiki also has a brief discussion of session-restore preferences that might be helpful:

[http://wiki.mozilla.org/Session_Restore](http://wiki.mozilla.org/Session_Restore)

modred

---

### Post by edwin11 on 2006-11-02
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Well, if i turn off the session restore option, then naturally, the dialog will never appear (not even in a "real" crash).

But the underlying problem (i feel) is still there. i.e. i still get an uncaught exception in the Error Console when i start Firefox.

i have posted in the Firefox Support Forum regarding this ([http://forums.mozillazine.org/viewtopic.php?t=482179](http://forums.mozillazine.org/viewtopic.php?t=482179)), but no reply yet.

Have also filed a bug report ([https://bugzilla.mozilla.org/show_bug.cgi?id=359078](https://bugzilla.mozilla.org/show_bug.cgi?id=359078)).



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by fragos on 2006-11-02
Me same, frequent but not always.  I just select "new session."

---

### Post by traneHead on 2006-11-02
Have you tried to (re)move your .mozilla/firefox directory?
Some settings file in there might be corrupted.

---

### Post by edwin11 on 2006-11-02
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]> **traneHead said:**
> Have you tried to (re)move your .mozilla/firefox directory?
Some settings file in there might be corrupted.

Good point. No, i haven't tried that. Will give it a go later and let you guys know.



Thanks and Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by edwin11 on 2006-11-02
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Guys, good news...

Basically i was trying out what traneHead suggested. i renamed my .mozilla folder (i didn't have Thunderbird or other Mozilla applications, so its ok for me), restarted firefox, and the error is no longer there.

But that's not the end of it...

i then set about changing the Firefox preferences to my usual settings, and when i restarted firefox, the error was back.

So it had to be one of the settings i changed...

i tried out all the settings that i had changed, one by one, and finally found out the cause of this.


The long and short of it is that, if your "Home Page" field (under Preferences -> Main -> Startup) is left empty, this error will show up, even if your "When Firefox starts" setting is set to "Show a blank page". Put a URL there, or even "about:blank", and the error doesn't show up.


Thanks traneHead and everyone else! :)



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by greybirds on 2006-11-03
I have the same problem, but only when Firefox is running while I log out. If I manually close Firefox and then restart it there's no problem. If I am running Firefox and log out without first closing it, the next time I start Firefox it asks me whether to restore the session or not.

Interestingly, I don't have the error message Edwin has, and the fix regarding the home page has no effect.

Anyone having similar problems?

PS @ Edwin: Thanks for taking the time to go through each and every possible cause and isolating the black homepage issue. I (and pretty much everyone else, I suspect) really appreciate that kind of dedication.

---

### Post by ronmarley1 on 2006-11-03
> **fragos said:**
> Me same, frequent but not always.  I just select "new session."
I would say that I get it infrequently.  I saw it do this on my friend's Kubuntu install also.

---

### Post by puppy on 2006-11-03
I have a homepage set under my options as instructed, and sorry but it still does it - only when I logout with firefox still running however - as I think I said in a previous thread, is this a bug or a feature?? :-k

---

### Post by auroraborealis on 2006-12-23
Has anyone found a working solution yet? I've tried all the ones listed here and Firefox still does it on a fresh install of Edgy.

---

### Post by fragos on 2006-12-23
If you terminate Firefox before you shut down this won't happen.  Actual seems more like a feature than a problem.  Now you can start where you were as well start a fresh session.  I like it.

---

