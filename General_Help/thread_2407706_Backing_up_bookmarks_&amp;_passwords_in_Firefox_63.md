---
title: "Backing up bookmarks &amp; passwords in Firefox 63.0.3"
date: 2018-12-07
forum: General Help
---

### Post by Autodave on 2018-12-07
Running Xubuntu 18.04 with Firefox 63.0.3.  I used to know where the files were that needed to be backed up for preserving bookmarks, passwords, etc.  However, they are no longer there.  Even a web search gave me nothing but bad info.  Anyone know how to do that now?

---

### Post by howefield on 2018-12-07
Should be in your ~/.mozilla folder.

---

### Post by l33ch on 2018-12-07
As howefield also said, all versions of firefox put their profiles in ~/home/username/.mozilla/firefox/

That will have everything, such as bookmarks, history, installed browser extensions, etc.

---

### Post by Autodave on 2018-12-08
That's where it used to be, but I don't believe it is there now.  I tried copying those 2 files from one machine to another (after moving the original ones to another location) but it did not work: nothing was on Firefox when I opened it even after a reboot.  I tried twice.

---

### Post by deadflowr on 2018-12-08
Add the profile to firefox's profile manager.
Run
```
about:profiles
```
in firefox's address bar.

Then in the profile page select the option up top Create new profile > then select next > and in the profile setup page where it allows you to give it a name (Default User should show as the original name it gives go down to Choose folder > select the profile folder usually some odd string like mdhfh5674.default in the .mozilla/firefox folder. The click ok or yes and 
then when it finishes it'll reload the profiles page with the new profile listed amongst the list of profiles, you can now select it to be set as default, or optionally double check it first and run the launch profile in new browser.

hope it makes sense
it feels rambly.

---

### Post by Autodave on 2018-12-08
It does make sense.  I will give it a try when I get the other machine back.  It sure was a lot easier to do before!

Thank you!!!

---

### Post by kurt18947 on 2018-12-09
> **Autodave said:**
> Running Xubuntu 18.04 with Firefox 63.0.3.  I used to know where the files were that needed to be backed up for preserving bookmarks, passwords, etc.  However, they are no longer there.  Even a web search gave me nothing but bad info.  Anyone know how to do that now?

I don't know if this is something you want to do due to security considerations but Firefox Sync works pretty well. I am careful about which passwords I allow to be saved/synced.

---

