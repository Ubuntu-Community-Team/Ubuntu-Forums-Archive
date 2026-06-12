---
title: "How to uninstall the program installed from a .bin file?"
date: 2006-10-16
forum: General Help
---

### Post by yuliang on 2006-10-16
I installed RealPlayer 10 in my Xubuntu 6.06 from a .bin file. Then I decided to uninstall it. But I didn't find it in the package manager. Then how to uninstall the program?

---

### Post by az on 2006-10-16
> **yuliang said:**
> I installed RealPlayer 10 in my Xubuntu 6.06 from a .bin file. Then I decided to uninstall it. But I didn't find it in the package manager. Then how to uninstall the program?

Does the .bin file offer you an uninstall option?  Otherwise, you probably should delete the directory it created to put the installed files.

It is a good idea to avoid installing anything from outside of the repositories.

---

### Post by bettlebrox on 2006-10-16
Realplayer 10 is probably installed in /usr/local/Realplay10 . Look in the directory and see if there is an uninstall script. Otherwise just remove the directory.

If realplay10 isn't installed there do the following to try and find it:

*which realplay;*

Which may give:

*/usr/bin/realplay*

Then do a "ls -l" on the output of the *which* command:
 *ls -l /usr/bin/realplay*
lrwxrwxrwx 1 root root 35 2006-02-26 17:04 /usr/bin/realplay -> /usr/local/Realplay10/realplay

Which should point to where Realplayer is installed.

If you can't find it that way try the locate command:
*locate -i realplay |more*

---

### Post by yuliang on 2006-10-17
I found it was installed in /usr/lib/RealPlayer. I didn't find any uninstall scripts. But if I remove that folder, how about other changes it made during the installation?

---

### Post by kintsa on 2006-10-17
I found this link on helixcommunity website

> rm -rf /usr/local/RealPlayer will get most of it.
rm /usr/bin/realplay

... will get most of it, minus the mozilla plugin under 
/usr/lib/mozilla/plugins, loc files under 
/usr/share/locale/$LANGUAGE/LC_MESSAGES/{realplay.mo,libgtkhx.mo}, and 
realplayer icons under /usr/share/icons/hicolor/



Here is the link to source page
 [http://lists.helixcommunity.org/pipermail/player-users/2005-January/000249.html](http://lists.helixcommunity.org/pipermail/player-users/2005-January/000249.html)

---

