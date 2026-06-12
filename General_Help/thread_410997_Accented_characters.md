---
title: "Accented characters"
date: 2007-04-16
forum: General Help
---

### Post by carpex on 2007-04-16
Hi, I am having issues with french accented characters under Feisty. Programs such as Picasa, lyx, sound juicer and others don't display accented characters. They are replaced with a series of odd characters. In other programs, such as Nautilus and OpenOffice, all is fine. Picasa is weird because accented characters in the menus are ok but the folder names are not. 

Any help would be appreciated. 

GL

---

### Post by dakhan on 2007-04-19
I had similar issues with Polish diacritical marks some time ago - in the LyX menus they were replaced by mystique code. :)
It was caused by the fact LyX 1.4.x does not support UTF-8 encoding. LyX 1.5 is to be converted totally to Unicode, so this fundamental issue will disappear soon.

However, as far as I remember, after my upgrade to Feisty the problem was solved automatically. Maybe somebody have included some corrections into LyX package present in Feisty repositories.

Earlier my method to have this corrected was to include ISO-8859-2 (native Polish LyX encoding) into locales to be generated.

Regards,

---

### Post by donmiguel on 2007-05-02
hi

there's a pretty simple solution for picasa2! all you have to do is uncomment 3 lines in the file **path_to_picasa/bin/wrapper**, et voilà

Taking a look at the lines 224-228 explains already everyting:

```

# FIXME - Only US English has been well tested to this point,
#         so we unset all LOCALE strings, causing us to default to Posix and hence US English
 for x in `locale 2>/dev/null | sed 's/=.*$//'` ; do 
    unset $x 
done


**comment out the three last lines**

```

don't be surprised if picasa discovers "new" folders.. it'll just rescan those folders which had special characters in the foldername.

Bonne chance et salutations

I took this information from [http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/39901bc7e6c8971d](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/39901bc7e6c8971d)

---

