---
title: "Optimum, safest means to migrate one user/desktop to another?"
date: 2023-03-05
forum: General Help
---

### Post by gandsnut on 2023-03-05
20.04, effectively a kubuntu system.


User 'adam' (/home/adam) uses a KDE Plasma desktop.
User 'glen' (/home/glen) uses a Gnome MATE desktop.


I need to migrate daily use of 'adam' (settings, program data, etc.) to 'glen'. I think data stored outside /home/xxxx will require considerable "chown & chgrp" operations. For example, the files & subdirs on an external HD/partition '/extra' is entirely assigned to user 'adam' with owner 'adam'.


I'm not making 'adam' with its /home/adam go away. But I want to change which user is utilized daily, which will eventually be 'glen'.


Is there a guided or safe, comprehensive way to accomplish this? Thanks.

---

### Post by TheFu on 2023-03-06
User settings are stored in the user's HOME directory.
Back that up ... or directly transfer it from system A ---> system B using rsync.

For data that is stored outside the HOME directory, the answer is "it depends".  If it is well organized, perhaps under a single /media/{username}/ directory, then just rsync that directory just like you did with the HOME.

Obviously, settings for KDE programs won't exist if they had a pure Gnome DE and used that, but if they happened to run KDE programs, then those settings will be pulled over and should work for the same version of each program.  Newer versions of programs should upgrade the settings, but if there are older versions of KDE programs on the "system b", there could be issues if the newer settings aren't compatible with the older programs.  Some configs may need to be deleted, but this is might happen, perhaps for 2-3 programs out of 1000.

Going the other direction has the same caveats.

If it were me, I'd keep 2 separate user accounts on the new system and slowly migrate the data and settings under the single account you want.  If 2 different people will be sharing the same computer, I wouldn't merge any settings or data. In fact, you can run 2 different DEs, if you like, on the same computer. Prior to login, there's "gear" that allows selecting the DE to be used.

rsync is one of those tools that I feel every Unix/Linux user should know, at least a little.

---

