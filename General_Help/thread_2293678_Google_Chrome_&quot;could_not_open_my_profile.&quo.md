---
title: "Google Chrome &quot;could not open my profile.&quot;"
date: 2015-09-06
forum: General Help
---

### Post by michael-piziak on 2015-09-06
Google Chrome "could not open my profile" or the file is corrupt or lost.

Please assist on how I can fix this - perhaps throw away a .hidden file ?

But I want to retain my passwords and everything like that, that it remembers for me.

See screenshot below of what it tells me upon opening it.

---

### Post by deadflowr on 2015-09-07
The Chrome profile is found in ~/.config/google-chrome.
So you can try either removing that folder or maybe even renaming it to something like google-chrome.old.
Then relaunch chrome.
Note that you'll have to re-set-up you chrome account.
As this will launch chrome as if you are launching it brand new.

---

### Post by michael-piziak on 2015-09-07
Much thanks for your reply.

Chrome is acting like I just installed it.

Which is fine with me - it is asking me to re-enter my logins and passwords (then asking me if I want it to remember my passwords and I click yes).

Is it ok if I just go with this, as I've already re-entered most the passwords from the majority of the websites I use - for the past hours since I posted this.

Or do you think something is corrupt and I should remove a folder or rename it or delete a folder or file (probably a .hidden folder or .file).

I'd just as soon go with this flow, as I've already re-entered my passwords to most sites I use.

If I delete a .hidden folder or file, then I'll have to re-enter them again, right?

Please advise.

If something is corrupt, then I'll surely delete it and re-enter passwords again and let it re-save them when it asks me if Google Chrome wants me to save passwords AGAIN - LOL.

Please advise.

Much thanks for your prompt reply!

Michael

---

### Post by michael-piziak on 2015-09-07
Please read my second post in my thread here, and please advise.

Thanks so much for taking your time to help me too!

Michael

---

### Post by howefield on 2015-09-07
> **michael-piziak said:**
> Chrome is acting like I just installed it. Which is fine with me - it is asking me to re-enter my logins and passwords (then asking me if I want it to remember my passwords and I click yes). Is it ok if I just go with this, as I've already re-entered most the passwords from the majority of the websites I use - for the past hours since I posted this.

Sure, be aware though that Chrome (as most browsers do) stores your passwords in plain text, a potential consideration if others have access to your pc. You could also consider setting up the sync feature so chrome backs up your passwords, meaning you don't lose them should you need to reinstall. A password manager like keepassx can also be used.

> If I delete a .hidden folder or file, then I'll have to re-enter them again, right?

Right, unless you use the sync feature.

---

### Post by michael-piziak on 2015-09-07
Thanks so much for your reply.I am not worried about others having access to my PC.  I use Chrome, and when my elderly parents use this computer, they both click Firefox browser.  Even if they used my Google Chrome, they aren't going to violate me.But that is very intriguing that I can sync chrome to back up my passwords - is that like a "cloud" that Google Chrome will store my stuff off-site securely for me?Again, thanks for taking the time to replying to help me!Michael

---

### Post by howefield on 2015-09-07
> **michael-piziak said:**
> is that like a "cloud" that Google Chrome will store my stuff off-site securely for me?Again, thanks for taking the time to replying to help me!Michael

That's pretty much it.

You can let it sync everything or specific items like passwords, addons, themes, ect... (the screenshot is from my Chromium but I believe Chrome to be identical in what it can sync for you.

---

### Post by michael-piziak on 2015-09-10
> **deadflowr said:**
> The Chrome profile is found in ~/.config/google-chrome.
So you can try either removing that folder or maybe even renaming it to something like google-chrome.old.
Then relaunch chrome.
Note that you'll have to re-set-up you chrome account.
As this will launch chrome as if you are launching it brand new.


I'm not that savvy with these files,
I tried to find the ~/.config/google-chrome.   file in the hidden files, but couldn't find it.

Chrome is messing up three times worst now.

Just please tell me how to completely remove it and then reinstall it from fresh (from terminal if you have to).

---

### Post by michael-piziak on 2015-09-10
Chrome is messing up three times worst now.

Just please tell me how to completely remove it and then reinstall it from fresh (from terminal if you have to).

It is not in my Ubuntu Software Center to easily remove then re-install.

Please tell me, even if I have to use terminal, how to completely wipe out everything Google Chrome and then tell me how to reintall it (even if I have to type a command into terminal).

Please help.

---

### Post by howefield on 2015-09-10
> **michael-piziak said:**
> I'm not that savvy with these files,
I tried to find the ~/.config/google-chrome.   file in the hidden files, but couldn't find it.

Open up your file manager which should open up in your /home folder, press Ctrl + h (to show hidden files)

That will show the .config folder, inside that folder you should find the google-chrome folder which you can either delete or rename as deadflowr explained above. Uninstalling the application in addition to that is probably overkill but if you feel you really have to, you can try...

```
sudo apt-get remove google-chrome-stable
```

or

```
sudo apt-get purge google-chrome-stable
```

which should also take out the configuration files as well as the application.

---

### Post by garyzw on 2015-09-10
I have the same problem with Chrome...  I open System Monitor KILL all instances of Chrome and restart Chrome and it works fine. Try it and see if it works for you

---

### Post by michael-piziak on 2015-09-10
> **howefield said:**
> Open up your file manager which should open up in your /home folder, press Ctrl + h (to show hidden files)

That will show the .config folder, inside that folder you should find the google-chrome folder which you can either delete or rename as deadflowr explained above. Uninstalling the application in addition to that is probably overkill but if you feel you really have to, you can try...

```
sudo apt-get remove google-chrome-stable
```

or

```
sudo apt-get purge google-chrome-stable
```

which should also take out the configuration files as well as the application.


Interesting, there was only Google Chromium in that folder - which I deleted.
There is no Chrome in that folder - ?!?!?

See attached screenshot:

---

### Post by garyzw on 2015-09-10
it is the google-chrome folder I see it in your pic

---

### Post by michael-piziak on 2015-09-10
> **garyzw said:**
> it is the google-chrome folder I see it in your pic


The Google Chrome folder must have vanished when I deleted the Google Chromium folder.

Or can I not see it again?

I only deleted google chromium, I did not delete google chrome folder "yet" as I still can't find it.

Michael

---

