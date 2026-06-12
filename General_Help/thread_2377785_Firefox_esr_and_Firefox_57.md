---
title: "Firefox esr and Firefox 57"
date: 2017-11-16
forum: General Help
---

### Post by SuperFreak on 2017-11-16
How do I keep Firefox ESR as is with all it's legacy addons and update Firefox 56 to 57? It appears that they both share the same profile. Is it simply a matter of creating a new profile in Firefox 56 and then updating to 57? How would one do that?
Thanks

---

### Post by Frogs Hair on 2017-11-16
You should check you add-ons for 57 + updates as the legacy extensions are obsolete in 57.  You can create a new profile by opening hidden folders and deleting or renaming the .mozilla folder. Export your bookmarks if you are not a sync user.

---

### Post by SuperFreak on 2017-11-16
I am not sure if I am being clear. I want to try Firefox 57, but I want to keep my legacy addons by having Firefox 56 ESR on my system also(even if that will only last for the next several months). Unfortunately they seem to share the same profile even when I make a new profile in one the other acquires it also. Looks like that is not the way to keep legacy extensions.

---

### Post by Frogs Hair on 2017-11-16
You may have build FF 57 from source and lock the old version in synaptic if installed. I've been using the next build/57 for a while and the few add-ons in use were updated before the 57 stable release.

---

### Post by mc4man on 2017-11-16
It's possible the best you can do is keep your existing profile, (rename maybe),  create a new profile, set firefox to prompt which profile to use & just use one profile for esr & one for 57

You can see what i mean by opening firefox from a terminal with firefox -profilemanager (ff must not be already running

(- if wanting the working xul-ext-ubufox ext. then don't update it, new package is empty..

---

### Post by &amp;KyT$0P# on 2017-11-16
No need to do anything special with the Ubuntu package version of Firefox.  The following procedure should get you running both versions on the same system -

1) Download Firefox 52 ESR from [here]("https://www.mozilla.org/firefox/organizations/all/"), extract it to your home directory

2) Run Firefox 52 ESR like mc4man suggested -
```
~/firefox/firefox -profilemanager
```

3) Create a new profile, give it a unique name, **leave the default folder location**

4) Start Firefox 52 ESR with the new profile

5) Run Firefox 57 with the [FONT=Courier New]-profilemanager[/FONT] flag, select your original profile, and select to start Firefox.  This step is to ensure that Firefox 57 will always use the original profile.

6) **Now, when you want to run Firefox 52 ESR, use this command -**
```
~/firefox/firefox -no-remote -new-instance -P <profilename>
```
replacing [FONT=Courier New]<profilename>[/FONT] with the name you gave your Firefox 52 ESR profile.  The [FONT=Courier New]-no-remote -new-instance[/FONT] is there to allow you to run Firefox 57 at the same time as Firefox 52 ESR.
**Be careful to only use this command to run Firefox 52 ESR.  Getting the profiles mixed up [will result in corruption]("https://www.ghacks.net/2017/08/02/you-cannot-downgrade-firefox-55-profiles/").**


You now have Firefox 52 ESR and Firefox 57 installed and running concurrently on the same system.  If you wish to copy any information into the newly-created Firefox 52 ESR profile, see [this article]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox").

Hope this helps.

---

### Post by SuperFreak on 2017-11-16
Thanks all for your support.
I tried backing up my Firefox 56 install with FEBE before I attempted your suggestions. Firefox froze and eventually reset itself with no addons at all. This happened twice after restoring Firefox with a previous FEBE backup. I have given up on the idea of using Firefox ESR and Firefox 57 concurrently and instead I am using Waterfox to maintain legacy addons and will update  Firefox 56 to Firefox 57. Waterfox uses a separate folder than .Mozilla and is unaffected by changes to Firefox.

---

### Post by ChuangTzu on 2017-11-16
you could also research why Mozilla is doing away with legacy extensions, they posed a huge security risk.  

NoScript for 57 will be out any day or hour now, the dev. said between 16Nov-19Nov..  other major ones are available.  I am temporarily using UMatrix until NoScript is updated/added.  Ublock Origin is there etc...

---

### Post by SuperFreak on 2017-11-16
> **ChuangTzu said:**
> you could also research why Mozilla is doing away with legacy extensions, they posed a huge security risk.  

NoScript for 57 will be out any day or hour now, the dev. said between 16Nov-19Nov..  other major ones are available.  I am temporarily using UMatrix until NoScript is updated/added.  Ublock Origin is there etc...

You are no doubt right about security issues but the extensions were what made Firefox the browser of choice for me

---

### Post by vasa1 on 2017-11-16
> **SuperFreak said:**
> ... extensions were what made Firefox the browser of choice for me
And a lot of other people! CTR was my favorite. I realized over the years that extensions can break or that their devs may move on to other things which is why I kept a bare minimum around.

I have Google Chrome as well but I still feel Firefox is more customizable. If they kill off userChrome.css (as is rumored), that will shake me!

---

