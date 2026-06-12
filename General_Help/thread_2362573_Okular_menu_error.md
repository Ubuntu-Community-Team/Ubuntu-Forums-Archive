---
title: "Okular menu error"
date: 2017-05-30
forum: General Help
---

### Post by joseph123321123 on 2017-05-30
Hi guys,

So I have Okular installed, I was changing some of the settings and now some of the menu is missing.

[https://ibb.co/k1m2Av](https://ibb.co/k1m2Av)

Some of it says 'no text' and items are missing from those menus. 'Settings' appears as 'no text' and some menu items are there, such as 'Configure Okular'. However some, such as 'Configure shortcuts', are now missing from 'settings'.

I tried '[COLOR=#111111][FONT=Consolas]sudo apt-get remove --purge Okular' [/FONT][/COLOR]and then reinstalled. I guessed that it wouldn't work though I thought i'd try it and see, it didn't fix it.

I tried 'Ctrl M' that didn't fix it. 

 Might there be another way to remove the conifg and then reinstall?

Thanks.

---

### Post by howefield on 2017-05-30
If the problem is confined to Okular, you could try deleting (or renaming)..

```
~/.config/okularrc
```

Purging doesn't remove that file.

---

### Post by joseph123321123 on 2017-05-30
Ok great!

What should I type into terminal to delete the config file?

And should I uninstall it before doing so?

EDIT I tried with Synaptic Package Manager and marked for complete removal 

[https://docs.oseems.com/general/operatingsystem/ubuntu/completely-remove-program-and-settings](https://docs.oseems.com/general/operatingsystem/ubuntu/completely-remove-program-and-settings)

I then reinstalled, however it's still as it was before.

---

### Post by ajgreeny on 2017-05-30
The file you need to remove is now at **~/.kde/share/config/okularrc** on my system so have a look there and either delete it or rename it so it is not used by okular when you open it.

Then restart okular again and you may have it back to the normal expected GUI.

---

### Post by howefield on 2017-05-30
> **joseph123321123 said:**
> What should I type into terminal to delete the config file?

```
mv ~/.config/okularrc ~/Documents/
```

will move the file to your Documents folder in case you want to retrieve it later.

Or open the Files manager which should open in your /home folder, press the Ctrl + H keys to show hidden files and navigate to .config/okularrc and move/rename/delete.

---

### Post by joseph123321123 on 2017-05-30
Ok guys, thanks for the suggestions. 

I moved and renamed the 'okularrc' file however the GUI was still as it was before. I then deleted it, still the same though.

---

### Post by joseph123321123 on 2017-05-30
I think I might have found something.

These files 

gssettings.kcfg
okular.kcfg
okular_core.kcfg
pdfsettings.kcfg'

They are in '/usr/share/config.kcfg'

Should I delete those files?
They are root permission

I tried moving one of them with 'mv ~/usr/share/config.kcfg/gssettings.kcfg ~/Documents/'

and terminal gave this output
'mv: cannot stat '/home/joe/usr/share/config.kcfg/gssettings.kcfg': No such file or directory'

---

### Post by ajgreeny on 2017-05-30
Have you made some changes to system settings that might change the way all KDE applications are shown; what DE do you run and which of the *ubuntu family of OSs do you use?

In a similar manner there was a problem with the standard version of kmymoney2 for 16.04, where some elements of the GUI were missing; icons IIRC, but I wonder if this is a similar type of problem that might be overcome by using a PPA for a newer version of okular.
Unfortunately I can't find a newer version from a ppa for you to try; other forum users may know more.

---

### Post by joseph123321123 on 2017-05-30
I'm on 17.04 and the DE is Unity. It's a clean install from about a week ago so I guess it probably isn't to do with system settings changes. Should I try installing an older package?

---

### Post by ajgreeny on 2017-05-30
> **joseph123321123 said:**
> I think I might have found something.

These files 

gssettings.kcfg
okular.kcfg
okular_core.kcfg
pdfsettings.kcfg'

They are in '/usr/share/config.kcfg'

Should I delete those files?
They are root permission

I tried moving one of them with 'mv ~/usr/share/config.kcfg/gssettings.kcfg ~/Documents/'

and terminal gave this output
'mv: cannot stat '/home/joe/usr/share/config.kcfg/gssettings.kcfg': No such file or directory'

No, do not delete those files but if you wish to test things, just rename them temporarily with commands such as ```
sudo mv /usr/share/kde4/config.kcfg/okular.kcfg /usr/share/kde4/config.kcfg/okular.kcfg-backup
```repeated for each file.  You can always then restore them back to the original names if necessary; I have no idea how necessary or important they are.

NB: If my system (Xubuntu 16.04) is anything to go by you missed **kde4** from the pathway to those files, so check that before running the commands.  Note you must use sudo to make any changes to root owned system files such as these.

---

### Post by joseph123321123 on 2017-05-30
Ah Ok before I try that I should say there is a kde4 folder in '/usr/share'.
 However there is only one folder in the kde4 folder, 'Services'. When I open that there is 'ServiceMenus', an 'apt.protocol' file and an 'apt+http.protocol' file. When I open 'ServiceMenus' there is a 'cabextract.desktop' folder and if I click on 'cabextract.desktop' then I get a message saying 'there was an error launching the application'.

I thought that could be relevant.

There is also an okular folder in '/usr/share'.

---

### Post by joseph123321123 on 2017-05-30
> [COLOR=#000000]No, do not delete those files but if you wish to test things, just rename them temporarily with commands such as
[/COLOR][COLOR=#000000]Code: sudo mv /usr/share/kde4/config.kcfg/okular.kcfg /usr/share/kde4/config.kcfg/okular.kcfg-backup[/COLOR]


The thing is if I remove Okular in software centre then the 'config.kcfg' folder is also removed.

Should I still try renaming the files?

EDIT: I renamed the files; it's still the same as before though.

---

### Post by marcel-isolt on 2017-07-28
I've had the same problem. I solved it by reset the toolbars, choose "Configure Toolbars", then click the "Default" button. Hopefully this will solve your problem.

---

### Post by sansoo2 on 2017-12-31
just registered to post my fix, although i'm not on ubuntu. i could not configure toolbars and so i couldn't reset them. i had to go into ~/.local/share/kxmlgui5/okular and delete the rc files there, which fixed it.

btw i believe configuring Main Toolbar <okular_shell> as opposed to Main Toolbar <okular_part> is what caused my problems

---

### Post by lizajane999 on 2018-04-02
This last one worked for me. Thank you sansoo2
> **sansoo2 said:**
> just registered to post my fix, although i'm not on ubuntu. i could not configure toolbars and so i couldn't reset them. i had to go into ~/.local/share/kxmlgui5/okular and delete the rc files there, which fixed it.

btw i believe configuring Main Toolbar <okular_shell> as opposed to Main Toolbar <okular_part> is what caused my problems

---

### Post by oldos2er on 2018-04-03
Old thread closed.

---

