---
title: "contents of Unity Video Lens in 12.04"
date: 2012-10-17
forum: General Help
---

### Post by J. Random User on 2012-10-17
I am running 12.04.  When I go to the Video Lens, it shows some items that appear to be advertisements.  How does Ubuntu know to display those items, and not others?  How does it know which advertisements to display?  Are they chosen randomly?  Is Ubuntu sending information through the Internet which results in those items being displayed?   I cannot find anything on this system that might allow me to configure this behavior.

---

### Post by stinkeye on 2012-10-17
Remove the package **unity-scope-video-remote** if you don't want the online searches.
```
sudo apt-get remove unity-scope-video-remote
```
Have a browse [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2060764") to see what's coming in Quantal.

---

### Post by J. Random User on 2012-10-17
How did this package get installed?  I don't think I installed that.  Shouldn't this be opt-in?


(I don't need to follow that link and have a look at Quantal.  No way I'm upgrading to that.)

---

### Post by stinkeye on 2012-10-17
> **J. Random User said:**
> How did this package get installed?  I don't think I installed that.  Shouldn't this be opt-in?


(I don't need to follow that link and have a look at Quantal.  No way I'm upgrading to that.)
It's a default package and before you get all huffy, in Quantal you can turn off all remote searches in Privacy settings.

---

### Post by J. Random User on 2012-10-17
Huffy?  I think this is a valid question.  Shouldn't this be opt-in?

We're not talking about Quantal now.  This is 12.04, the LTS.


(I did look at that link after all.  It led me to the discovery that I had to remove **unity-scope-musicstores** as well.  Thanks.)

(Are there any other packages like this in 12.04?  Should these all be explicitly listed in Ubuntu's Privacy Policy?)

---

### Post by stinkeye on 2012-10-17
Huffy might have been a bit strong.
It's just that there have been numerous posts and discussion on this and 
the applications are new and the implementation is still under development.
Quantal has a privacy link in the dash which tells you how to turn off,  which will probably also come to Precise.
Many would prefer opt-in but turning off is very simple and not hidden.

---

