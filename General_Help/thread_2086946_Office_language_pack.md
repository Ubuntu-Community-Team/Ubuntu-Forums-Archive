---
title: "Office language pack"
date: 2012-11-22
forum: General Help
---

### Post by googleye on 2012-11-22
I've installed Office 2010 through PlayOnLinux and now I want to install a language pack for spellcorrection. The problem is it looks like the installer isn't looking in
~/user/.wine/drive_c/Program Files 
for Office, shouldn't it do just that when I run it through wine? Is there a way to make it look in that folder?

Ps. So the problem is that I can't install the lang pack because the installer can't find an Office installation

---

### Post by googleye on 2012-11-24
Anyone?

---

### Post by aharonl on 2012-11-27
I've just had exactly this issue, luckily the fix is quite simple:
You can't add any language packs to office after installation, rather the language pack must be merged with the office cd before installation. First remove your office instalation.

Instructions for this can be found at:
[http://technet.microsoft.com/en-us/library/dd162397.aspx](http://technet.microsoft.com/en-us/library/dd162397.aspx)

I'll summarize here exactly what to do:

1)Copy the whole ms office cd to a directory on your hard disk
2)Copy the whole language pack cd to the same directory.DON'T overwrite duplicate files.
3)inside the directory (just copied) there should be a dir called either "SingleImage.WW" or "Proplus.WW" or something similar depending on your office version. Inside that dir is a file called config.xml. You need to add the following text to that file:

```
<AddLanguage Id="en-us" ShellTransform="yes"/> <AddLanguage Id="he-il" />
```

Exact text depends on your language , the text I've put here tells office to use english as the main language (for the interface) and also to include hebrew as an extra language.

4)Install Office normaly using PlayOnLiux. When The office installation asks you what to install ("office" or "language pack") choose "office".

Done!

---

### Post by googleye on 2012-11-27
> **aharonl said:**
> I've just had exactly this issue, luckily the fix is quite simple:
You can't add any language packs to office after installation, rather the language pack must be merged with the office cd before installation. First remove your office instalation.

Instructions for this can be found at:
[http://technet.microsoft.com/en-us/library/dd162397.aspx](http://technet.microsoft.com/en-us/library/dd162397.aspx)

I'll summarize here exactly what to do:

1)Copy the whole ms office cd to a directory on your hard disk
2)Copy the whole language pack cd to the same directory.DON'T overwrite duplicate files.
3)inside the directory (just copied) there should be a dir called either "SingleImage.WW" or "Proplus.WW" or something similar depending on your office version. Inside that dir is a file called config.xml. You need to add the following text to that file:

```
<AddLanguage Id="en-us" ShellTransform="yes"/> <AddLanguage Id="he-il" />
```

Exact text depends on your language , the text I've put here tells office to use english as the main language (for the interface) and also to include hebrew as an extra language.

4)Install Office normaly using PlayOnLiux. When The office installation asks you what to install ("office" or "language pack") choose "office".

Done!

Okay so I made a new directory with all the files as you described, however, I can't install office anymore. The installer fails on several points and even though I can actually run everything but powerpoint without spell correction I can't uninstall them since they don't show up in the Playonlinux list??

---

### Post by aharonl on 2012-11-27
Strange, for me it worked flawlessly.

Did you make sure to first un-install everything?
When you re-installed did you point Playonlinux to your new dir (instead of to the DVD)?
The DVD should have 2 main dirs : x86 and x64 did you edit the config.xml in the correct one (or both to be sure)?

I'm running office 2010 on Linux Mint 13 (which is essentially ubuntu 12.04)

---

### Post by googleye on 2012-11-27
> **aharonl said:**
> Strange, for me it worked flawlessly.

Did you make sure to first un-install everything?
When you re-installed did you point Playonlinux to your new dir (instead of to the DVD)?
The DVD should have 2 main dirs : x86 and x64 did you edit the config.xml in the correct one (or both to be sure)?

I'm running office 2010 on Linux Mint 13 (which is essentially ubuntu 12.04)

Yep I chose the exe in the new folder, and I got the correct version. I uninstalled all of the office programs using playonlinux

---

### Post by aharonl on 2012-11-27
so you used the "install from exe" option. I chose "Install from cd/dvd" > "other location" and chose my new dir as if it was a dvd.
Don't know if this makes a difference or not

---

### Post by googleye on 2012-11-28
> **aharonl said:**
> so you used the "install from exe" option. I chose "Install from cd/dvd" > "other location" and chose my new dir as if it was a dvd.
Don't know if this makes a difference or not

Ah, didn't know that was possible, I'll try again.

---

### Post by E@zyVG on 2013-07-20
Just to let you know, did the above instructions on my openSUSE distro and made the modifications to the config.xml file and installed via PlayOnLinus selecting the setup.exe file. All worked flawlessly, now apart from US English I also have proofing tools for Russian and French.

---

### Post by kwameleisje on 2014-07-02
Hi for everybody who has their language pack as 1 single exe file the method above doesnt work since you dont have a content cd to copy from.
I just managed to install a language pack trough trough Play On Linux.
This is how I did it:
[LIST=1]
[*]Install Office (I installed the standard edition)
[*]Go to Configure and select the office 2010 prefix then go to Wine->Configure Wine
[*]Select windows version Windows 7
[*]Go to miscellaneous->Run a .exe file in this virtual drive
[*]select the setup file
[*]Install language pack and then do a software reboot.
(I dissabled all options other than the proofing tools since i only wanted to install those but it should also work for the GUI translations.)
[*]Select windows version windows xp (step 2-3)
[*]Open SETLANG.exe in the office installation folder
[*]AFTER COMPLETING ALL steps open your office application
[/LIST]
Do not attempt to open office before completing all steps for it WILL break the entire installation.

---

### Post by slickymaster on 2014-07-02
Necromancy. 
I'm closing this thread.

@kwameleisje:
From the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

