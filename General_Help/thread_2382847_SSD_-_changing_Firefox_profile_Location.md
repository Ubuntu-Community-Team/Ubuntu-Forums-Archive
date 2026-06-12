---
title: "SSD - changing Firefox profile Location"
date: 2018-01-18
forum: General Help
---

### Post by Quarkrad on 2018-01-18
Running 16.04 with gnome shell 3.20.   Just installed ssd and read it is worth putting browser profile on mechanical drive due to number of 'writes'.  I cannot find any info on how to do this - i.e. having moved said profile how does one point FF(57) to new position, and is this all one has to do?

---

### Post by oldfred on 2018-01-18
I move my  entireprofile to /mnt/data and use mozilla folder for both Firefox and Thunderbird.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I then create new profile with path to my Firefox (similar for Thunderbird) in .

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/mozilla/firefox/wojjex8t.default


```

---

