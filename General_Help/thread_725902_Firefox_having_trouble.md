---
title: "Firefox having trouble"
date: 2008-03-16
forum: General Help
---

### Post by bigfoot1979 on 2008-03-16
Hi, 

Everytime i try to start firefox the programme doesn't does load. 

I have tried starting the program from terminal but get his error message. I'm not sure what to do about it....any ideas?

(gecko:6465): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Serif 12'
Segmentation fault (core dumped)


Many thanks

---

### Post by thiebaude on 2008-03-16
Can you delete Firefox from Synaptic and then try to re-install it to see if that problem still occurs?

---

### Post by bigfoot1979 on 2008-03-16
yep tried that twice, but the same problem occurs.... Thanks for the help. 

I know this is a terrible thing to say, but I'm tempted to go back to microsoft as I spend half the time with ubuntu gutsy trying to figure out how to fix things...

---

### Post by hbbk on 2008-03-20
hi

I've the same problem since few days (see this thread: [http://ubuntuforums.org/showthread.php?t=729044](http://ubuntuforums.org/showthread.php?t=729044))

Could not find any answer except using the tar.gz package with the latest firefox version from the mozilla.org website. 

good luck

---

### Post by Ck.asdf on 2008-03-20
try deleting your firefox profile from /home/[user]/.mozilla
you may have tried using some custom font or something.
I know sometimes, in both Windows & Linux, I have weird problems with Firefox, and the resolution is usually to delete the profile and try again.

---

### Post by dnairb on 2008-03-20
> **Ck.asdf said:**
> try deleting your firefox profile from /home/[user]/.mozilla
you may have tried using some custom font or something.
I know sometimes, in both Windows & Linux, I have weird problems with Firefox, and the resolution is usually to delete the profile and try again.

Warning - if you delete your profile folder, you will lose all settings and emails!

---

### Post by hbbk on 2008-03-20
Instead of deleting the profile you can make a backup of it:

From command line in a console
```

> cd ~
> mv .mozilla .mozilla.backup
> firefox

```

If firefox run ok from there your only way is to run it with a brand new profile, if it still crashes the pb come from elsewhere... so you can restaure your profile
```

> cd ~
> rm -rf .mozilla
> mv .mozilla.backup .mozilla

```

For my own problem the profile was ok, the the pb came from elsewhere.

good luck

---

### Post by Ck.asdf on 2008-03-20
both the previous people are right ... you'll lose whatever stuff you have as far as plugins, extensions, themes, bookmarks, etc. I'm not sure what they mean by emails, since firefox isn't an email app, but the poster immediately before me has the idea, as far as backing up the profile before deleting it.

I suppose the reason I didn't suggest backing it up is that I've always found that if reinstalling firefox itself doesn't work, then the problem is most likely in the profile, as I can't even begin to think where else a problem could reside.

---

### Post by forrestcupp on 2008-03-20
Well, since it is a problem with the dejavu serif font, you could try removing it and reinstalling it.

```
sudo apt-get --purge remove ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
sudo apt-get update
sudo apt-get install ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
```

---

### Post by Oreo on 2008-03-23
All of the above didn't work for me.

I found a temporary work-around at this post: [http://ubuntuforums.org/showthread.php?t=610488&highlight=firefox+segmentation](http://ubuntuforums.org/showthread.php?t=610488&highlight=firefox+segmentation)
The post is by Ellioo.

[INDENT]To accomplish the same in firefox on any ubuntu-family installation (for the record, I am currently on xubuntu-gutsy)

01. Launch Firefox.
02. Go to the Edit menu and select Preferences.
03. Select the Content tab.
04. In the "Fonts & colors" section, click on the Advanced button.
05. Specify the fonts you would like to use as the defaults, as well as their size.
06. Uncheck the checkbox "Allow pages to use their own fonts, instead of my selections above."
07. Restart Firefox

You should be free of the ubuntu.com/ubuntuforums.org crashes, however you won't be seeing any of the cool fonts the web designers used.[/INDENT]

This worked for me. I have tried reinstalling Firefox, deleting my old profile, reinstalling mscorefonts, checking the chmod of the corefonts, etc. So far the above is the only thing I have found that allows me to use Firefox. I sure hope someone comes up with something that allows me to use the designer's fonts.

Oreo

---

