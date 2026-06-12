---
title: "I keep getting:&quot;65.2 MB will be downloaded&quot;"
date: 2023-02-05
forum: General Help
---

### Post by jgw on 2023-02-05
I keep getting "65.2 MB will be downloaded" every time I run the software updater.  I did a search on this one and it seems that it involves something to do with snap.  If I tell it to run it does and then I get the same thing again (and again, again, again, etc).  I suspect this is not real important and I can probably ignore it but, just in case I thought I would post it here and see if I am right or I have to fix it.  Oh, when I take a look inside of the software updater it says that it wants to download ubuntu base for 2.6mb and then says that 25.2mb will be downloaded.  

Kinda strange..................

---

### Post by DuckHook on 2023-02-05
I refuse to update (or, indeed, even install apps) using Software Updater for many reasons, but one of which is what you are experiencing: it's so opaque. I have no idea what it is doing behind the scenes. Maybe I'm a control freak, but that drives me nuts.

All of my updating is done on the command line using apt. That way, I see exactly what is happening and have fine grained control over the process. If I'm feeling especially paranoid, I will install apt-listchanges which gives me a complete (and sometimes overly long) changelog of each package before they get installed.

Though I don't use Software Updater, I would guess that the large file report might be due to the inclusion of the apt repo statistics in the download estimate. It's important to note that the Software Updater is nothing more than a wrapper for apt and dpkg that hides all of the nitty gritty behind a pretty GUI screen. Underneath, it's still the same processes happening and the only way for apt update to work is to download many MBs of repo metadata to check and compare for what needs updating and what doesn't. But, as noted, this is only a guess on my part. Since I don't use SU, it's just a shot in the dark.

Summary:

My solution is simple&#8212;look at what is actually happening by firing up a terminal session and using apt. That way, you will see the fine download details that are hidden by SU.

---

### Post by jgw on 2023-02-05
Thank you for the reply!

updating using terminal - great idea!  I'll give it a shot!

---

### Post by DuckHook on 2023-02-05
Here's my apt update string which has served me well for years. Others have commented on how it may be too aggressive, but I've never run into problems, so I've kept using it:```

sudo apt update && sudo apt full-upgrade && sudo apt autoremove --purge -y && sudo apt clean
```
[LIST=1]
[*]The first segment syncs with the repos.
[*]The second segment does a full upgrade (includes the kernels) instead of just partial
[*]The third segment clears all old stuff (including kernels and configuration files) and actually purges them in addition to removing them. The -y flag affirms purging without further interactive confirmation.
[*]The final segment eliminates even the residual pkg files to free up a little bit more space.
[*]The && means: "Don't run this next segment unless the last segment was a success and generated no errors."
[/LIST]
After running this command, there is no going back. But then, reinstalling is usually simple.

---

### Post by jgw on 2023-02-07
Thank you!

I will mark this as solved!

---

