---
title: "googlep-chrome corrupted"
date: 2023-07-14
forum: General Help
---

### Post by jerrywo on 2023-07-14
after a routine update about 4 - 5 days ago, the google-chrome window was corrupted, sometimes with a mosaic
of colors, sometimes not.  At the same time, scrolling my mouse across the chrome window leaves "mouse tracks",
a trail of arrows (mouse pointer) changing into a symbol of a hand.

running 22.04 LTS

and I must say, I'm using Firefox at the moment and it's a poor substitute for chrome

Jerry
Warrenton, VA

---

### Post by ActionParsnip on 2023-07-14
If you make a new chrome profile, is it OK?

---

### Post by jerrywo on 2023-07-14
Darned if I can find a profile setting - I welcome your help!

Oh yeah - I uninstalled and re-installed chrome when the problem initially surfaced -  but no change

Jerry

---

### Post by ajgreeny on 2023-07-15
Uninstalling chrome does not remove its profile which i think you'll find in ~/.config but as I don't use chrome I don't know the details of this.

Just rename the profile folder rather than remove it to avoid losing any settings you want to keep and a new profile will be created next time you start chrome. You can then restore any files from the old profile if you need to.

---

### Post by jerrywo on 2023-07-15
Baffled
I cannot find a google-chrome profile in my /.config file in my google-chrome home folder.
any other hints?

Jerry

---

### Post by deadflowr on 2023-07-15
> I cannot find a google-chrome profile in my /.config file in my google-chrome home folder.

What's the google-chrome home folder?
Do you mean the ~/.config/google-chrome folder?
That's the profile, more or less, there is no specific config file.

if it's truly Google Chrome then you can just move the folder like
```
mv .config/google-chrome .config/google-chrome.old
```
which will basically rename the existing profile and  when you launch chrome a new empty profile will automatically be generated.


*** if we want to get technical the true true user profile is actually ~/.config/google-chrome/Default,
but it's just easier to nuke the whole google-chrome folder and start with a fresh one, in case some general setting was the issue,
instead of some profile setting.

---

### Post by ActionParsnip on 2023-07-16
As above, just delete the profile folder for the browser. It'll be in a folder under ~/.config
Don't delete the ~/.config folder itself. It holds settings for other applications. When you launch the browser you will get vanilla settings but it may help

---

### Post by jerrywo on 2023-07-16
Thanks deadflowr - that did it...and sorry for the "duh" moment - was looking for a folder 
named "profile" in the chrome folder.  

Tanks
Jerry

---

