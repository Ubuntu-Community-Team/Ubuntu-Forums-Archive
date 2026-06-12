---
title: "firefox stuck on 1.0.2?"
date: 2005-07-20
forum: General Help
---

### Post by gammyhand on 2005-07-20
I have just re-installed ubuntu and am trying to upgrade firefox to 1.0.4 (worked last time I am sure). I made sure I had the latest version in synaptic, and then I went to about:config and changed the version number to 1.0.4 but still FF reports as version 1.0.2 and I can't upgrade it to 1.0.4 in upgrade manager and I definitely got round that problem last time. Also when I try to get extensions it says I need 1.0.4 or higher and points me in the direction on 1.0.6... help :)

---

### Post by Juergen on 2005-07-20
The versions of packages are fixed when a release comes out.
All security related changes in the new versions are included in the bugfixes you download though, but the version stays until Breezy comes out.

You can get a newer version of Firefox if you enable the 'Backports'-repository.
Go here:[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) ,read, and remember that you had (most probably) done it before ;-)

---

### Post by gammyhand on 2005-07-20
[QUOTE=Juergen]The versions of packages are fixed when a release comes out.
All security related changes in the new versions are included in the bugfixes you download though, but the version stays until Breezy comes out.

You can get a newer version of Firefox if you enable the 'Backports'-repository.
Go here:[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) ,read, and remember that you had (most probably) done it before ;-)[/QUOTE]
 I have backports enabled though, it was the first thing I did. And I still can't get it working :S

---

### Post by george29 on 2005-07-21
the version in backports is 1.0.4 - if you use apt to upgrade it will still show as version 1.0.2 if you look under Help - about firefox. if you search the forums there are some posts about using the about:config file to update the version number. (set general.useragent.vendorSub to 1.0.4 - check that you changed the version number in the right section.)

I presume that the backports people are already working on 1.0.6.

george

---

### Post by gammyhand on 2005-07-21
[QUOTE=george29]the version in backports is 1.0.4 - if you use apt to upgrade it will still show as version 1.0.2 if you look under Help - about firefox. if you search the forums there are some posts about using the about:config file to update the version number. (set general.useragent.vendorSub to 1.0.4 - check that you changed the version number in the right section.)

I presume that the backports people are already working on 1.0.6.

george[/QUOTE]
 hey, I said in my first post I had already done that. Thanks though :)

I think I found the problem. Although it is a bit weird. Last night synaptic said I had the latest version of FF (1.0.4) but this morning it says I am on 1.0.2 and offers to let me upgrade....I am not sure why. I restarted X a few times last night and backports was definitely in the repositories  :???: Thanks for your help :)

---

