---
title: "Installing snaps via GUI?"
date: 2016-07-31
forum: General Help
---

### Post by Roasted on 2016-07-31
Hi friends. For the first time I decided to check out some snaps just to see what all of the development buzz is about. I hit a snag and figured I'd ask after I found limited info about this particular error (found some, but nothing that lead me to a resolution).

The act of installing snaps as of now... is that strictly limited to terminal usage? I only ask because I did successfully install the VLC snap through terminal, where the system remotely retrieved the VLC snap through the command line and installed it. This worked, with exception to the fact I think the VLC snap has some issues (no file/edit/view/etc menus, plus clicking on the VLC icon from the system tray up top was blank). 

I stumbled across the web UI for the snap store (uapp explorer, if I recall). I downloaded a few .snap files and figured, well, I would think I could double click them and install them. I hit a road block, though.

no file_to_app results to show

That's the error I get with each snap I double click. Software Center launches, it just yields that error immediately. It looked like the amount of snaps on uApp Explorer was larger than what I saw in the terminal output when running "snap find". 

Just curious if anybody else has seen this, or if perhaps I'm jumping the gun a bit with installing the snaps via GUI and it's not yet a completed project.

p.s. 16.04.1, fully updated. Thanks for any insight!

---

### Post by Roasted on 2016-08-10
Anybody have any idea in regard to this? Just trying to get the current jist as to what the process is for installing snaps on a 16.04 desktop. Looks (from what I've seen) easy enough for Ubuntu phones, but mobile devices aren't really what I'm focused on at the moment with these snaps. I assume in time it's intended to have a way to browse all available snaps in the Ubuntu Software program, though at the moment with it being unable to simply launch/install ones I downloaded from my browser, it raises an eyebrow a bit. Thanks for any insight!

---

### Post by grahammechanical on 2016-08-10
The command line is the only way at the moment and it does seem as if there is a special snap store that is accessed by the snap install command.

This will list the commands

```
man snap
```

If you know the name of the application then this will work without needing to download the application snap separately

```
sudo snap install <application name>
```

This command used to be useful but it was limited to listing 100 snaps and the developers stopped it working

```
snap find
```

This is the response we now get

> error: cannot list snaps: empty query

There is not very much useful information about on this subject. So, the Uapp exployer site is very useful in this regard

[https://uappexplorer.com/apps?type=snappy](https://uappexplorer.com/apps?type=snappy)

Regards

---

### Post by Roasted on 2016-08-10
Thanks for the information. Do you by chance know of a way within uapp explorer to filter the snaps based on what's installable on Ubuntu 16.04 desktop? I was finding snaps on uappexplorer and trying to snap install them via CLI on my laptop but nearly all of them were failing. I think VLC was the only one of the bunch I tried that worked. Just had me wondering if I was somehow hitting Ubuntu Phone specific snaps.

---

### Post by mc4man on 2016-08-10
There are some 16.04 installs that can search & install snaps from ubuntu-software, can clearly be seen here - 
[https://ubuntuforums.org/showthread.php?t=2331939&p=13529117&viewfull=1#post13529117](https://ubuntuforums.org/showthread.php?t=2331939&p=13529117&viewfull=1#post13529117)
Though I'd suspect most can't.

As far as the uapp site you could try the 16 filter though no guarantee it'll be suitable. Any app with unity7 in it's permissions would obviously be good for 16.04.
Just because a snap is available doesn't mean it'll work, apples & oranges there.

---

