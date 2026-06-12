---
title: "KDM Theme Manager"
date: 2008-04-13
forum: General Help
---

### Post by StephanG on 2008-04-13
I recently tweaked some login manager settings in KControl, and then my kdm theme was replaced by a default looking grey box with blue background.  How can I re-enable my kdm themes.  I have already tried to disable and re-enable "Enable KDM themes" button, but it made no difference.

Any help would be appreciated.
Thanks guys!

---

### Post by chritoph on 2008-04-21
I ran into the same problem lately.

According to [http://www.kde-apps.org/content/show.php?content=22120](http://www.kde-apps.org/content/show.php?content=22120) 
the version 1.2.2 of kdm theme manager fixes a bug addressing your/our problem. 
The Enable/Disable setting is just not saved in version 1.2 provided with Gutsy Gibbon 7.10.

BR,

Christoph

---

### Post by chritoph on 2008-04-21
Perhaps this info may help?

[http://ubuntuforums.org/showthread.php?t=34131](http://ubuntuforums.org/showthread.php?t=34131)

---

### Post by chritoph on 2008-04-21
OK,
the configs created by KDM Theme manager are written to /etc/default/kdm.d/??_kubuntu_default_settings .
The actual file seems to be the one with the highest number in place of ??.

USETHEME="false" and gone it is. :guitar:

---

