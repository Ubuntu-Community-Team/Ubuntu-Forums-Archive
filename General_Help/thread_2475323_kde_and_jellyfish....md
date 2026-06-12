---
title: "kde and jellyfish..."
date: 2022-05-22
forum: General Help
---

### Post by izakter-v22 on 2022-05-22
Hello! today i downloaded kde on ubuntu jellyfish with gnome, then icons changed , terminal stopped working , i can't use sudo... how can i fix this without reinstalling OS?:(

---

### Post by izakter-v22 on 2022-05-22
when i use sudo: [FONT=monospace][COLOR=#000000]sudo: /usr/bin/sudo &#1076;&#1086;&#1083;&#1078;&#1077;&#1085; &#1087;&#1088;&#1080;&#1085;&#1072;&#1076;&#1083;&#1077;&#1078;&#1072;&#1090;&#1100; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1102; &#1089; uid 0 &#1080; &#1080;&#1084;&#1077;&#1090;&#1100; &#1073;&#1080;&#1090; setuid[/COLOR]



[/FONT]

---

### Post by tea for one on 2022-05-22
Gnome (i.e Ubuntu 22.04) is a desktop environment
Kde (i.e. Kubuntu 22..04) is a desktop environment

It is _not_ advisable to have two desktop environments together with all the applications on one system.

Assuming that you have only recently installed Ubuntu, my advice is:-
Backup your data.
Install from scratch the flavour you like.
Restore your data.

If you are unsure about your flavour choice, then use live sessions to explore and evaluate.

---

### Post by Impavidus on 2022-05-22
> **izakter-v22 said:**
> when i use sudo: [FONT=monospace][COLOR=#000000]sudo: /usr/bin/sudo &#1076;&#1086;&#1083;&#1078;&#1077;&#1085; &#1087;&#1088;&#1080;&#1085;&#1072;&#1076;&#1083;&#1077;&#1078;&#1072;&#1090;&#1100; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1102; &#1089; uid 0 &#1080; &#1080;&#1084;&#1077;&#1090;&#1100; &#1073;&#1080;&#1090; setuid[/COLOR]



[/FONT]
Could you translate that? Hint: prepend LANG=C_LANG to the command to disable translations to your native language:```
LANG=C_LANG sudo some_command
```

---

### Post by izakter-v22 on 2022-05-23
/usr/bin/sudo must be owned by user with uid 0 and setuid bit

---

### Post by izakter-v22 on 2022-05-23
thanks

---

### Post by guiverc on 2022-05-23
Personally I'm a *lover* of having multiple desktops installed on my system(s), however I don't know how to respond as you've provided few specifics.

What package(s) did you install to get KDE?  `kubuntu-desktop` or something else?  

I tend to use the large *meta* packages like `kubuntu-desktop` as you can experience problems if you don't install all packages required by a DE; but I don't know what you installed.

Icons changed but no specific clues. A link to a picture may have helped here, but many things can change when using another DE to change configuration/settings, and you're new to how the interact with each other.

Terminal not working?  Are you talking about `gnome-terminal` or `konsole` or something else?  as adding another desktop means you normally have multiple terminals installed (one using KDE/Qt5 libraries; the other using your prior GTK libs) but no specifics.  Or do you just mean Ctrl+Alt+T doesn't work (*that is a different thing and can occur as it's not a KDE shortcut*).

Your later message however says "/usr/bin/sudo must be owned by user with uid 0 and setuid bit 				" which is a permissions issue; and unrelated to GNOME/KDE at all. That is a **more serious *permissions* issue** that confuses me as doesn't relate to desktops; thus I'll skip it.  That is more likely the result of a bad `chmod` command

---

### Post by Impavidus on 2022-05-23
> **izakter-v22 said:**
> /usr/bin/sudo must be owned by user with uid 0 and setuid bit

That is a serious error. It's unrelated to installing KDE.

This can be fixed, assuming it's the only thing wrong. You have to boot in recovery mode and fix the permissions. However, in my experience, this is rarely the only thing wrong. Broken permissions on /usr/bin/sudo usually result from applying chmod or chown on all files in /usr/bin, causing such severe damage that the only realistic way forward is reinstalling. Sometimes it's the result of filesystem damage, like a broken hard drive. Let's see...
```
ls -l /usr/bin/sudo
ls -l /usr/bin | grep -v '^lrwxrwxrwx\|^-rwxr-xr-x'
```
The first command will show the permissions of sudo, which should start with ```
-rwsr-xr-x  root  root
```and the second will show all files in /usr/bin that are not symlinks and don't have the most common set of permissions. It should list about 20 files.

---

### Post by izakter-v22 on 2022-05-23
kubuntu-desktop

---

### Post by izakter-v22 on 2022-05-23
i am talking about all terminals. I cant use sudo. Icons of all folders , disks , apps changed. I cant send screenshots now, sorry (

---

