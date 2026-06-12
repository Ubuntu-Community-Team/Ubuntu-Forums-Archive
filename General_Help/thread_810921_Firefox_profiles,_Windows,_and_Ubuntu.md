---
title: "Firefox profiles, Windows, and Ubuntu"
date: 2008-05-28
forum: General Help
---

### Post by Ramzy on 2008-05-28
I would like to dual boot Ubuntu. I know that it has Firefox by default, which is great, however, my (Windows) Firefox profile is VERY customised. I have more than 300 passwords saved, hundreds of bookmarks, tons of addons, themes, and dozens of custom written chrome hacks.

In Windows, all this information is located in C:\Documents and Settings\Ramzy\Application Data\Mozilla\Firefox\Profiles.

I have two questions,

1) Is my Windows Firefox profile compatible with Firefox in Ubuntu?

If yes,

2) Where is the profile folder located in Ubuntu? (Please be very specific, as i've only ever used Linux / Ubuntu about 3 or 4 times).

Thanks!

---

### Post by geo909 on 2008-05-28
Hi,

I'm not sure about compatibility. I know that you can export your bookmarks as an html file easily (and import it again from another firefox) but I guess you have more important thinks to preserve.

In my SUSE machine I can find firefox here:
```
/home/<myusername>/.mozilla/
```

So, here's what you can actually do:

Check your "C:\Documents and Settings\Ramzy\Application Data\Mozilla" file.
Does it look like the one mentioned above? If yes, then do
```
mv /home/<yourusername>/.mozilla /home/<yourusername>/mozilla_BACKUP
```

Copy your windows folder as "/home/<yourusername>/.mozilla/"

Now, re-log in (not sure if you need to reboot, maybe that's the case) and try to run firefox.
If you have problems, then remove the Windows folder from there and restore your previous settings:

```
mv /home/<yourusername>/mozilla_BACKUP /home/<yourusername>/.mozilla
```

---

