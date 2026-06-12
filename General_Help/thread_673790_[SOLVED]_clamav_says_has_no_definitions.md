---
title: "[SOLVED] clamav says has no definitions"
date: 2008-01-21
forum: General Help
---

### Post by mandrill on 2008-01-21
Not that I'm really worried about viruses, but tried clam - says no definitions installed - even thought the repos say they are (perhaps to incorrect directory?) - also tried from clam website, another error message about configuration files. - tried avg and the download link        gave me a full page of what I assume to be javascript, no happiness there.

Anyone know what's going on??

---

### Post by y-lee on 2008-01-21
I assume you tried typing **freshclam ** in the terminal to update the Virus definitions. If so then....Hmm, anytime I have a problem like that I uninstall and then reinstall. Don't know if that will help. 

Also you might wanna see this thread, [Clam AV nuts and bolts]("http://ubuntuforums.org/showthread.php?t=30060"). I quit using ClamAV because it fails to detect a well known trogan, see [Using Myspace For Evil]("http://www.terminally-incoherent.com/blog/2007/02/15/using-myspace-for-evil/") and because it is not supported in Dapper, [ClamAv Outdated on Ubuntu Dapper]("http://www.terminally-incoherent.com/blog/2007/02/16/clamav-outdated-on-ubuntu-dapper/").

---

### Post by y-lee on 2008-01-21
Oh btw I use AVG and BitDefender .

---

### Post by mandrill on 2008-01-21
y-lee, thank you for the info. No, I didn't invoke freshclam, as I was just kind of messing around and didn't want to get into a full-blown late-night quest. I have also heard that clam is not the most efficient finder of trojans and such.

Do you know of a problem with avg's download? tried that and got a page full of script.

---

### Post by y-lee on 2008-01-21
I don't know what link ya clicked but i would guess ya need to right click it and save to disk. Hmm, see[ AVG Linux Free Edition]("http://ubuntuforums.org/showthread.php?t=136064") or try[ AVG's web site]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl").

I forgot how i installed it but I don't remember any problems. I only use antivirus programs cause i share data with my windows partition and might use P2P but i ain't admitting anything.:lolflag:

---

### Post by mandrill on 2008-01-21
Same reasons here. I'll try avg again - I had it working on Feisty, but never bothered to install on Gutsy.....I also forgot how I installed it last time......

edit - tried avg website again, just script..... the other link is rather old, and somewhat confusing as it blares out at the top that avg linux doesn't exist anymore

---

### Post by y-lee on 2008-01-21
You must **Right click the link on AVG's web site and save the deb** to your hard drive. 
I don't know why firefox tries to open it instead of save it. (Using FF here)


Anyway The info on the forums here confused me too by blaring"out at the top that avg linux doesn't exist anymore". But ya need to use its launcher as AVG needs superuser privileges so it can update..

I uninstalled it and then reinstall it using the deb on AVGs web site and the launcher on the link i gave above. It worked fine no problems here. I scanned my home directory and it did ok, pretty quick too. There were 2 files in use it couldn't scan but I expected that. lol.

BTW it doesn't seem like BitDefender is updating its virus definitions any more they are very old. it is a command line tool anyway.

---

### Post by mandrill on 2008-01-21
Well, I installed from the deb, but cannot update as I don't have the permissions. (as you mentioned)....can you coach me a bit here on permissions while I try uninstall? I don't think I have the full picture in focus just yet - thanks a million!

---

### Post by y-lee on 2008-01-21
I take it you didn't create a launcher, so lets try that. 

Type the below into the terminal
```
sudo nano /usr/share/applications/avg.desktop
```

When nano opens add the following to the blank file we just created:

```
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
```

Save this file by hitting **CTRL O **and then exit nano by hitting **CTRL X**

now start AVG by going to ** Applications ** ---> **System Tools.**

BTW one could simply start AVG by typing

```
gksudo avggui
```

into the terminal but it is easier if ya had a menu item as above, that way ya don't need to remember the **gksudo avggui** part every time. :)

Hope this helps.

---

### Post by mandrill on 2008-01-21
y-lee - have made progress but the save file and close nano are not happening....

---

### Post by y-lee on 2008-01-21
maybe I wasn't clear enuff. Repeat the above steps.

To Save this file by hitting **CTRL O** This means hit the Control key and hold it down and then hit the **O** key. Now close to the bottom of the terminal window it will say

[INDENT]**File Name to Write: /usr/share/applications/avg.desktop**[/INDENT]

Hit Enter here to save the file.**DO NOT CHANGE the file location** Just hit enter.
See attached image for a picture of what this should look like.

Now hold the Control key down and hit x. This exits nano.

If this doesn't work give me details. Error messages in the terminal or something to go on.

**Bear in Mind I am new to Linux to.**

---

### Post by mandrill on 2008-01-21
that worked! thanks! still have 2 questions: should I have to give user/password to open from system tools location? and can I get rid of the original entry under Accessories by deleting it from the main menu config?


edit - removed accessories menu entry, can now use without "signing in" from the System Tools entry - thanks for your time and patience!

Peace....

---

### Post by y-lee on 2008-01-21
Well I'm glad that worked. :)  I'm tired and soon to be offa here.

Yes you will need to give password when opening from system tools.
And yeah go ahead and delete it from the menu in Accessories I didn't even notice that. lol.

Also I think ya need to set this as solve. I think ya can click on thread tools here and set it. I just noticed that yesterday.

---

### Post by keevee09 on 2008-01-22
ctrl-O, then >>>'Enter'<<<  will write out the text (save it).
ctrl-X exits the nano.
Worked for me and I haven't written a launcher since Mandrake 6.5 :-)
Thanks Y-Lee for your very informative and clear post.

---

