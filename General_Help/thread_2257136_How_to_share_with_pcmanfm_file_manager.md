---
title: "How to share with pcmanfm file manager"
date: 2014-12-17
forum: General Help
---

### Post by fkervin on 2014-12-17
Hi all,

I have just install lubuntu in one computer and I've notice that I cant share folders with pcmanfm (lubuntu's default file manager) as I can do with kubuntu (dolphin) or Ubuntu (Nautilus).

I mean, I've install samba and all needed packets, but using pcmanfm I have no option to share when I go to properties of a folder. I've even install nautilus manager (nautilus-share) and using it I have a tab to share in the properties of the folders.

I would prefer leaving pcmanfm if possible, since I don't know if replacing it with Nautilus or Dolphin is a good idea (I want an stable system with less possible problems), so I have 2 options that I don't know how to do:

OPTION 1: keep pcmanfm. The problem is: How to share folders in the way can be done with Nautilus or Dolphin?
OPTION 2: Replace pcmanfm: For do this, I need to completely replace it in way that lubuntu uses always Dolphin (or Nautilus, but I'd prefer Dolphin unless you advice me Nautilus for some reason). How could I do this, and more important... is this a problem in some way?+

I hope someone can lend me a hand.

Many thanks in advance

---

### Post by Morbius1 on 2014-12-18
I just downloaded Lubuntu 14.10 to see if I could adapt my thunar custom actions for samba in pcmanfm. It's not quite there but give this a shot:

[1] Create a path in your home directory:
```
mkdir -p ~/.local/share/file-manager/actions
```
[2] Then create a file called SambaGuestReadOnly.desktop:
```
leafpad ~/.local/share/file-manager/actions/SambaGuestReadOnly.desktop
```
[3] Then copy this to that file:
```
[Desktop Entry]
Type=Action
Name=SambaGuestReadOnly
Profiles=profile-zero;

[X-Action-Profile profile-zero]
Exec=/usr/bin/net usershare add %w %f "" Everyone:R guest_ok=y
Name=Default profile
```
[4] Save the file.
[5] Logoff and Log on again

Now go to your home folder, right click a folder, and you should see a context item called: SambaGuestReadOnly. Selecting that should create the samba usershare. To verify run this command:
```
net usershare info --long
```

I created another one called SambaGuestWite.desktop with this exec:
```
Exec=/usr/bin/net usershare add %w %f "" Everyone:F guest_ok=y
```

[COLOR=#0000cd] Note: Nautilus-share in gnome does something that this approach won't do. It changes the permissions of the shared folder allowing the guest to actually write. In thunar in XFCE I can write this as a thunar custom action and it will replicate that:[/COLOR]
```
net usershare add %w %f "" Everyone:F guest_ok=y && chmod = 777 %f
```
I can't quite get that to work in pcmanfm.

[COLOR=#0000cd]Note2: The possible values in usershare are:[/COLOR]
Everyone:R - Read only
Everyone:F - Writeable
guest_ok=y - Allow guest access
guest_ok=n - Do no allow guest access

---

### Post by fkervin on 2014-12-19
Hi Morbius1,

Your answer is incredible! I've still not try but I think it could meet my needs (for me it's ok if I have 2 options in the folders, one to read-share and other to write-share :D).

Despite this, in other forum I've been adviced to change file manager with Nautilus since pcmanfm lacks many features that samba or nautilus have. I think it could be a great solution if it have no secondary effects like losing system stability or losing system speed. What can you reccomend me in this sense?

If I could replace pcmanfm with samba (my prefer since it's the one I know) or Nautilus perhaps it saves me from having other problems with pcmanfm in the future. The problem is that I don't know how to do it in the way the new file manager becomes the default one in the system.

Many many thanks!!

---

### Post by Bucky Ball on 2014-12-19
Thunar is lighter and from memory now has what you're looking for. Simply a matter of installing it from Synaptic Package Manager (or Software Centre) and making that your default file manager. Don't use Lubuntu so can't instruct you on how to do that, but might be something like 'Preferred Applications'. 

Good luck. ;)

---

### Post by fkervin on 2014-12-19
Thank you very much, Bucky Ball, it's a real pleasure coming to a forum and find people who has the aim of helping.

I'm making a change from kubuntu to lubunbu since kde made me had some problems with XBMC, so that I want the lighter possible system (window manager mainly), if replacing pcmanfm with other file manager means having problems with XBMC then I don't want this.

According to what you say, Thunar can be a good option, I will research how to effectively install it and replace pcmanfm, I need pcmanfm to dissapear from system and new one replace it in all senses (in simple words: made the new windows manager be the default one).

Regards and MANY thanks again

---

### Post by Morbius1 on 2014-12-19
I test out Lubuntu every 2 years or so just to see how things are progressing and these a just some random thoughts I have regarding how it deals with Samba:

*** For reasons unknown Lubuntu is missing the following packages:
```
smbclient
avahi-daemon
```
I don't know why that is but it's unique in that regard since most modern distros have both installed by default. You can easily install them youself but it always surprises me that they are not installed by  default.

*** Another peculiarity is that there is no "Browse Network" available in PCManFM. That one is easy to fix:

Just edit the following file:
```
leafpad ~/.config/gtk-3.0/bookmarks
```
And add the following line to the bottom of the file:
```
network:/// Browse Network
```

*** As for Thunar I'm afraid you will have the same problem as you had with PCManFM. There is no default way to create samba shares from Thunar. It is easier to create a "thunar custom action" to replace it than it was figuring out how to do it in PCManFM but it's still missing by default.

---

### Post by fkervin on 2014-12-19
Many thanks, Morbius1

To be honest, the most important for me is having a system that gives the less possible problems when working with XBMC, but in the other hand I need the system to look modern and have a minimun functionalities. Perhaps the best solution is the first you gave me, it allows me to leave pcmanfm, my doubt is, what other features does pcmanfm lacks?

I've read something about spaceFM as pcmanfm evolution, could it be a good solution? does it support samba shares management?

I noticed the lack of those packages, I had to install them to be able to share with lubuntu (using nautilus). I also noticed that after sharing a folder I was not able to write on it from other computer, even when I set write permissions to any user and took ownershit of this folder (sudo chown -R user folder) and gave total permissions (sudo chmod -R 777 folder). I suppose I'll have this problem again. I remember having a problem with shares in kubuntu and I had to edit some system file but I don't remember :(

I really want to help you for your help, I have some experience with linux but nothing compares with you, sometimes I want to do things that at last result easy but make me have lots of headaches

Regards

---

### Post by fkervin on 2014-12-19
Hi Again,

Morbius1, I've test yout way to share under pcmanfm and i can share for read, but write permissions does not work.

I've been reading and I think that althought I could fix it, at last I would replace this file manager due to its lacks (lacks further than share with samba).

So... I think that best is going to be replacing it, but I don't know if Dolphin or Nautilus, I want the one that will procuce less possible problems with XBMC, the lighter one, but also the one that can replace pcmanfm best and give no problems. I've read that Dolphin needs no many dependencies from KDE...

What can you advice me?

Regards

---

### Post by Bucky Ball on 2014-12-19
Yea, avoid Dolphin. That will drag in a heap of stuff. Nautilus will drag in some things, too, but not as many unrelated to your current install.

---

### Post by fkervin on 2014-12-19
Thanks a lot,

I've been reading a lot and I've get the same conclussion: Nautilus better than Dolphin.

My problem is that althought have googled a lot and read many many info, I can't get a place where explain how to replace pcmanfm with Nautilus in a good and efficient way (important that Nautilus will be the default mananger everywhere).

I've read this, that I think is very important:

**Just make sure to use "nautilus --no-desktop" as the command, as Nautilus also handles the desktop background, menus etc. in Gnome. The "--no-desktop". option tels it to just open the fie manager window instead of starting to draw the desktop for you. **

How to apply this **--no-desktop** option in way that works always, no matter where Nautilus will be called from?

Regards and many thanks

---

### Post by Bucky Ball on 2014-12-19
Would that be when you install Nautilus? As in:

```
sudo apt-get install nautilus --no desktop
```

? Could you provide a link to where you saw that command?

I don't know about Lubuntu, but in xfce there is 'Preferred Applications'. You'll probably find something similar under Preferences in Lubuntu. Once Nautilus is installed go to the 'Utilities' tab and set Nautilus as the default browser. Once that's working, use Synaptics or a terminal to uninstall pcmanfm, if you really don't want it on the system. I wouldn't bother, though, if Nautilus is working fine.

---

### Post by vasa1 on 2014-12-20
> **Bucky Ball said:**
> Would that be when you install Nautilus? As in:

```
sudo apt-get install nautilus --no desktop
```

? Could you provide a link to where you saw that command?

I don't know about Lubuntu, but in xfce there is 'Preferred Applications'. You'll probably find something similar under Preferences in Lubuntu. Once Nautilus is installed go to the 'Utilities' tab and set Nautilus as the default browser. Once that's working, use Synaptics or a terminal to uninstall pcmanfm, if you really don't want it on the system. I wouldn't bother, though, if Nautilus is working fine.
That may just be the way to run nautilus:```
--no-desktop
              Do not manage the desktop &#8212; ignore the  preference  set  in  the
              preferences dialog.

```from [http://manpages.ubuntu.com/manpages/trusty/en/man1/nautilus.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/nautilus.1.html)

Edit: and I suppose the Exec= line in nautilus.desktop should be modified though I don't have recent experience with nautilus.

---

### Post by Bucky Ball on 2014-12-20
> **vasa1 said:**
> That may just be the way to run nautilus:```
--no-desktop
              Do not manage the desktop &#8212; ignore the  preference  set  in  the
              preferences dialog.

```from [http://manpages.ubuntu.com/manpages/trusty/en/man1/nautilus.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/nautilus.1.html)

Edit: and I suppose the Exec= line in nautilus.desktop should be modified though I don't have recent experience with nautilus.

I don't use it either, but yea, I see what you mean with the other bit. In light of what you're saying, I guess it would be possible to make a launcher with the command 'nautilus --no desktop' and stick that in the top panel. Guess you could even select the nautilus icon for it, if there is one. 

Clumsy, but might just work. I'm not really familiar with Lubuntu but I imagine it would be easy enough to make a launcher. In xfce, right click the desktop and 'Create Launcher' is in the drop-down menu. :p

---

### Post by Morbius1 on 2014-12-20
>  Morbius1, I've test yout way to share under pcmanfm and i can share for read, but write permissions does not work.
[1] First post the output of this command please:
```
net usershare info --long
```
[COLOR=#0000cd]* It may not be that the share wasn't created correctly. It may be what you are sharing and/or where it is located.*[/COLOR] [COLOR=#0000cd]*The output of the command above will tell us that*[/COLOR].

[2] And remember unlike nautilus-share write access is a 2 step process with PCManFM:
*** Create the share
*** Change permissions on the shared folder to allow "others" to write to the folder:
```
chmod 777 /path/to/shared/folder
```
[COLOR=#0000cd]* In this respect dolphin won't help you. Dolphin creates the usershare but doesn't modify linux permissions of the folder. Only Nautilus and derivations of Nautilus does that.*[/COLOR]

[3] And just in case there is an issue with the desktop script you might want to post that as well:
```
 cat ~/.local/share/file-manager/actions/SambaGuestWrite.desktop
```

---

### Post by fkervin on 2014-12-20
> **Bucky Ball said:**
> Would that be when you install Nautilus? As in:

```
sudo apt-get install nautilus --no desktop
```

? Could you provide a link to where you saw that command?


Sorry, I forgor to menction where i saw:
[http://ubuntuforums.org/showthread.php?t=1527468&p=9567984#post9567984](http://ubuntuforums.org/showthread.php?t=1527468&p=9567984#post9567984)

> **Bucky Ball said:**
> I don't use it either, but yea, I see what you mean with the other bit. In light of what you're saying, I guess it would be possible to make a launcher with the command 'nautilus --no desktop' and stick that in the top panel. Guess you could even select the nautilus icon for it, if there is one. 

Clumsy, but might just work. I'm not really familiar with Lubuntu but I imagine it would be easy enough to make a launcher. In xfce, right click the desktop and 'Create Launcher' is in the drop-down menu. :p

Perhaps it should be this way, opening nautilus always with this modifier, the issue here is that by right click on desktop I have only "create file" and "create folder", hehe, I will have to look for info about "creating launcher".

> **Morbius1 said:**
> [1] First post the output of this command please:
```
net usershare info --long
```
[COLOR=#0000cd]* It may not be that the share wasn't created correctly. It may be what you are sharing and/or where it is located.*[/COLOR] [COLOR=#0000cd]*The output of the command above will tell us that*[/COLOR].

[2] And remember unlike nautilus-share write access is a 2 step process with PCManFM:
*** Create the share
*** Change permissions on the shared folder to allow "others" to write to the folder:
```
chmod 777 /path/to/shared/folder
```
[COLOR=#0000cd]* In this respect dolphin won't help you. Dolphin creates the usershare but doesn't modify linux permissions of the folder. Only Nautilus and derivations of Nautilus does that.*[/COLOR]

[3] And just in case there is an issue with the desktop script you might want to post that as well:
```
 cat ~/.local/share/file-manager/actions/SambaGuestWrite.desktop
```

It didn't work since I was doing it as you told with shmod option and it make the script not to work at all, hehe

I've fix it and create another option to "un-share":

```
[Desktop Entry]
Type=Action
Name=No compartir
Profiles=profile-zero;

[X-Action-Profile profile-zero]
Exec=/usr/bin/net usershare delete %w
Name=Default profile
```

The issue is that I've to use chmod as you told, but if there is no way to do it automatically with pcmanfm I think I could live with it (at last I used Dolphin that lacks this feature too).

With this working I can think in leaving pcmanfm and not to install Nautilus. I don't need a light system but XBMC suffer problems with most linux just becouse they interfere in its work, so having everything as simple as possible is a good idea. In in some days I see that pcmanfm lacks other features I can't live without I'll think again in Nautilus.

Morbius1, I've another question regarding the awesome scrips I've create thanks to you: Now I've three options in the menu (Read Share, Write Share, Un-share). Is it possible to put them in one menu? I mean, not three options in the menu when I right click a folder but only one Option that when I go to it opens a Submenu with the three options (It would be really GREAT).

Many thanks :)

---

### Post by Morbius1 on 2014-12-20
I'm glad you got that to work.
> The issue is that I've to use chmod as you told, but if there is no way to do it automatically with pcmanfm
There may be a way I'm just not smart enough to figure out how yet.

In thunar I can write:
```
net usershare add %w %f "" Everyone:F guest_ok=y && chmod = 777 %f
```
It creates the share then modifies permissions. In Lubuntu it fails - in fact it even fails to create the share. Don't know why.
> Morbius1, I've another question regarding the awesome scrips I've create  thanks to you: Now I've three options in the menu (Read Share, Write  Share, Un-share). Is it possible to put them in one menu? I mean, not  three options in the menu when I right click a folder but only one  Option that when I go to it opens a Submenu with the three options (It  would be really GREAT).
That I do not know. Zenity maybe? I don't know if Lubuntu can handle submenus by itself. Not a regular Lubuntu user I'm afraid.

---

### Post by fkervin on 2014-12-21
Many Thanks, Morbius1, your help is very valuable.

For now I'll try to stay on pcmanfm using those three links to "share read" "share full" and "unshare" :)

Regards

---

### Post by fkervin on 2014-12-25
Hi again Morbius1,

Don't ask me why, but at last I've move from lubuntu ro xubuntu, and now I don't know how to create the shares. I've try with the same method that you teached me for lubuntu/pcmanfm and here in thunar doesn't work.

I mean, I've create those files .desktop but after creating them and restarting the options to share doesn't appear on menu.

Can you help me?

Regards and many thanks

---

### Post by Morbius1 on 2014-12-25
Different mechanism and much easier in XFCE.

**[1]** Open Thunar and Select [B]Edit > Configure Custom Actions > +

[2] [/B]Then give it the name you want to see in the context menu and add the expressions:

SambaGuestRead: ```

net usershare add %n %f "" Everyone:R guest_ok=y
```
SambaGuestWrite:```

net usershare add %n %f "" Everyone:F guest_ok=y && chmod 777 %f
```
SambaUnShare:```

net usershare delete %n && chmod 755 %f
```

In all cases make sure that in the **Appearance Conditions Tab**:
only Directories is enabled.

[COLOR=#0000cd]EDIT[/COLOR]: You will need to close thunar and reopen it.

---

### Post by fkervin on 2014-12-31
> **Morbius1 said:**
> Different mechanism and much easier in XFCE.

**[1]** Open Thunar and Select [B]Edit > Configure Custom Actions > +

[2] [/B]Then give it the name you want to see in the context menu and add the expressions:

SambaGuestRead: ```

net usershare add %n %f "" Everyone:R guest_ok=y
```
SambaGuestWrite:```

net usershare add %n %f "" Everyone:F guest_ok=y && chmod 777 %f
```
SambaUnShare:```

net usershare delete %n && chmod 755 %f
```

In all cases make sure that in the **Appearance Conditions Tab**:
only Directories is enabled.

[COLOR=#0000cd]EDIT[/COLOR]: You will need to close thunar and reopen it.

Sorry for my delay, I've been busy those days. I've just try and works great.

Many thanks :D

---

