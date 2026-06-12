---
title: "USB drive, change default group?"
date: 2007-03-07
forum: General Help
---

### Post by guice on 2007-03-07
So, I figured out how to change the default umask of a mounted USB drive from 0077 to 0027. Now, I need to change the default group, but it's not working.

I've edited the file: /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi
and added the lines:
<merge key="volume.policy.mount_option.umask" type="string">0027</merge>
<merge key="volume.policy.mount_option.gid" type="string">www-data</merge>

To the volume.fstype of vfat section.

The umask works just fine, but the gid part isn't working. I tried using type int and using 33. I've also tried using type of string and value 33. And any ol' combo I could find within Google.

Nothing's working. Anybody care to shed some line on this for me? Thanks

---

### Post by po0f on 2007-03-07
guice,

[Create your own udev rules to control removable devices](http://ubuntuforums.org/showthread.php?t=168221).

[Writing udev rules](http://reactivated.net/writing_udev_rules.html#ownership).

[EDIT]

The second link is probably more relevant to your situation.

---

### Post by guice on 2007-03-17
I tried what they said, but it didn't work ... I don't get it. Is udev what mounts a USB drive upon login? Or is it something else? What ever it is, I added a 50-external.rules of the proper format and it still does not set the group to www-data.

---

