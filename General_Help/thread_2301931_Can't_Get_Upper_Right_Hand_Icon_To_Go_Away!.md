---
title: "Can't Get Upper Right Hand Icon To Go Away!"
date: 2015-11-06
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-11-06
In the upper right hand corner I have this red triangle warning icon!  This is what is says when I click on it. 

"The update information is outdated.  This may be caused by network problems or by repository that is no longer available.  Please update manually by selecting 'show updates' from the indicator menu, and watching for any failing repositories.

Show updates
Install all updates
Check for updates
Start package manager


Show notifications
Preferences  

I've clicked on everything on it and it's always there for the past three days!  How do I get rid of it?

---

### Post by QDR06VV9 on 2015-11-06
Normally that shows something miss-configured  in apt
IE: Duplicate PPAs or even Duplicate Stock(Factory) Repos.
That dose not mean apt is broken but it wont show updates there until you fix it.
What dose it show when you run in terminal.
```
sudo apt-get update
```
If there is a duplicate it will report that.

---

### Post by shane_faulkinbury2 on 2015-11-06
Hmmm, after I ran the sudo apt-get update it disappeared!  Thanks for your help, hopefully it stays gone!

Hmmm, after I ran sudo apt-get update the icon disappeared!  Hopefully it stays gone when I logon tomorrow.  Thanks for your help!

---

### Post by QDR06VV9 on 2015-11-06
If it dose re[COLOR=#000000]appear, you now know how to fix it.[/COLOR]:D
Cheers

---

