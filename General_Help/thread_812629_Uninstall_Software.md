---
title: "Uninstall Software"
date: 2008-05-30
forum: General Help
---

### Post by abbasali31 on 2008-05-30
I am a newbie ubuntu user, and installed few software such as

Wine
DVD Shrink/DVD Decrypter

These apps are not working smoothly, and I wanted to uninstall, but I couldn't.  Under GUI, there is an option to uninstall through windows, but it didn't work.  Thru Terminal Mode,

Sudo apt-get remove DVD Shrink or DVD Dycrepter or Wine, the message would appear, "Couldn't find Package".

How do I remove those application completely.

Thanks,

---

### Post by kpkeerthi on 2008-05-30
To uninstall wine, run this command
```
sudo aptitude purge wine
```

To completely remove applications installed on wine, run this command
```
rm -rf ~/.wine
```
(Or simply delete the **.wine** folder in your HOME directory)

---

### Post by gdzsi on 2008-05-30
you can run the uninstaller with wine, as you would do in windows. there is a Wine menu in the applications menu, check if you have an uninstall entry in the wine/Programs/DVD Shrink or wherever it is.
if you have not, pop up a terminal, cd into the directory you installed the program (the wine 'c:' drive is in /home/<you>/.wine/drive_c) and search for a uninstall.exe file, or something like that. if you find it, you can run it with a 'wine ./uninstall.exe' command.
if you want to uninstall wine, you can use synaptic or any apt software (I assume you installed it from the repositories.)

instead of DVD Shrink or DVD decrypter, there are cool apps in the repo which do the same.
Check: dvdrip, k9copy (which is my favourite), ......

---

### Post by abbasali31 on 2008-05-30
Thanks guys,

It worked.

One more question,  Is there any command in Ubuntu to remove unnecessary file such as cookies, tmp files etc.  Like in Windows where we use disk cleanup built in utility.

Regards,

---

### Post by kpkeerthi on 2008-05-30
> **azhar-teza said:**
> Thanks guys,

It worked.

One more question,  Is there any command in Ubuntu to remove unnecessary file such as cookies, tmp files etc.  Like in Windows where we use disk cleanup built in utility.

Regards,

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

