---
title: "Do you know what the HTTP Cache Cleaner is?"
date: 2005-09-07
forum: General Help
---

### Post by GreyFox503 on 2005-09-07
I've been using my Ubuntu system for a couple months now, and recently I've noticed that several times a day, a new window appears in my task bar entitled "Launching HTTP Cache Cleaner".  It will stay for about 5-10 seconds, then disappear.  This did not used to happen.

Two questions:  Does anyone know what this program does/is doing?

And secondly, if I don't need it or it's undesirable, how can I stop it from being triggered?

---

### Post by arnieboy on 2005-09-07
[QUOTE=GreyFox503]I've been using my Ubuntu system for a couple months now, and recently I've noticed that several times a day, a new window appears in my task bar entitled "Launching HTTP Cache Cleaner".  It will stay for about 5-10 seconds, then disappear.  This did not used to happen.

Two questions:  Does anyone know what this program does/is doing?

And secondly, if I don't need it or it's undesirable, how can I stop it from being triggered?[/QUOTE]
happens when u try to launch a kde app in GNOME?

---

### Post by GreyFox503 on 2005-09-07
I probably should have included this kind of info  :roll: :

Most of the time I run firefox, gaim, azureus, and .... amarok in the background.  Occassionally K3b.

You might be on to something since I use amarok.  However, its playing almost all the time, and the http cleaner window seems to appear without warning.  I might try not running that program for a while to see if it is the cause.

---

### Post by madjo on 2005-09-07
I believe indeed that amaroK is the culprit here... it only appears when I run that program in Gnome.

---

### Post by fat_larry on 2005-10-17
I also get this and it's becoming annoying... It's bad enough that the taskbar objects tend to change size almost randomly in Gnome anyway, let alone having mysterious and pointless (in the eyes of the user) taskbar items popping up... Anyone know how to banish this beast?

---

### Post by `GooZ´ on 2005-11-05
I guess it's AmaroK related too, since I'm using AmaroK in gnome and I'm also getting this frequently :/

---

### Post by Ricapar on 2005-11-08
I get that HTTP Cache Cleaner every once in a while too. I'm running amaroK in Gnome as well.

It's annoying =(
Hopefully someone knows how to get rid of it..

---

### Post by AlexMartinius on 2005-11-10
I've got the same problem. Also running amaroK and also using Gnome. I hope there's a way to stop this, it's really annoying, but amaroK is great, so is Gnome and I want to keep using both of 'm.

---

### Post by ssam on 2005-11-10
i have seen it when running kde (i usually use gnome, but i thought i should give kde a go.). i am not running amarok, so its not exclusivly that.

i imagine it is a background process to stop kdes http cache growing to big. i assume it is harmless and useful.

it probably should be allowed to run, but it would be nice if it did so invisiby in the background like updatedb does.

---

### Post by Oxygene on 2005-11-12
I'm experiencing this problem, too. In my case I'm quite sure that it is caused by amarok, since it is the only kde application I use frequently. And this makes sense, because amarok does a lot of http-stuff like sending song information to last.fm, searching for lyrics etc.

Would be great if someone knew an answer

---

### Post by Toba on 2006-04-23
I'm having the exact same problem - I just started using amaroK today and this is the first time I've seen it.  I don't use any other KDE apps - just GNOME.

If somebody can find a way to make it invisible, it would be much appreciated.

---

### Post by paulyche on 2006-04-25
bump

---

### Post by transducer on 2006-04-28
From the kio_http_cache_cleaner man page

"[FONT="Lucida Console"]kio_http_cache_cleaner is a KDE HTTP cache maintenance tool.[/FONT]"

So I guess the kde framework launch this app on a regular basis.  

In its desktop file (/usr/share/services/http_cache_cleaner.desktop) there is the line 

[FONT="Lucida Console"]X-KDE-StartupNotify=false[/FONT]

I'm not an expert in .desktop files, but I guess that's a specific kde tags that specifies the application should run in background and that gnome does not support it.

---

### Post by ubunlilluz on 2006-05-16
i don' have amarok but i installed only the necessary of kde for lounching kcopy, not all kde. I've the problem of cache cleaner too.

---

### Post by dmacdonald111 on 2006-05-18
I'm glad I'm not alone here! I thought I was going mad seeing that pop up all the time. I don't use amorak either, but I DO use ktorrent. So it's a kde cleaning thingie? Cool. :)

Edit: Just realised which forum this is in. Strange, I am running dapper (from breezy). Hmm.

---

### Post by jquintero on 2006-07-10
> **transducer said:**
> From the kio_http_cache_cleaner man page

"[FONT="Lucida Console"]kio_http_cache_cleaner is a KDE HTTP cache maintenance tool.[/FONT]"

So I guess the kde framework launch this app on a regular basis.  

In its desktop file (/usr/share/services/http_cache_cleaner.desktop) there is the line 

[FONT="Lucida Console"]X-KDE-StartupNotify=false[/FONT]

I'm not an expert in .desktop files, but I guess that's a specific kde tags that specifies the application should run in background and that gnome does not support it.


thanks for pointing out that .desktop file. just out of curiosity i tried adding this:
```
StartupNotify=false
X-GNOME-StartupNotify=false

```

to the end of that file. I don't know whether the X-GNOME tag is a real tag, but so far it seems to work for me. anyone else wanna try and let us know if it works for you?

---

### Post by Avian00 on 2006-08-24
Uhh... has nobody come upon a solution to this?  If you have, please share it.  I'm sure I'm not the only one who would appreciate a solution.

---

### Post by John64 on 2006-08-26
I just disabled Cache in the Konqueror settings.  Will let you know if this changes anything

---

### Post by Sionide on 2006-08-28
Any luck?

---

### Post by celisyn on 2006-09-05
I've also disabled cache under konqueror settings using kcontrol and it seems to be working--have not had any instances of the http cache cleaner again.

---

### Post by Turtle.net on 2006-09-09
I had the same problem in kubuntu ... but just to let you know : I never used amarok.
The problem appeared only when I used konqueror.

---

### Post by dolphinsonar on 2006-10-13
Still no soultion, thats crazy.  I might be able to provide some insight.  I just loaded Ktorrent, and I never had this happen before today.

I have never run any KDE programs on my Gnombe dapper before, so I am guessing that is indeed the case.  I have no idea how to make it bugger off however.

---

### Post by guyvdb on 2006-10-17
i'm having the exact same problem running amarok on gnome

a solution would be nice

---

### Post by paulyche on 2006-10-17
```
sudo apt-get install kcontrol
```

and then running kcontrol and disabling the cache in the konqueror section seemed to work for me.

Please reply if anyone needs help with this.

---

### Post by ASUmusicMAN on 2006-10-23
I had this problem using amaroK in gnome and taking the instructions in this thread have made it disappear so far ;)

[http://www.ubuntuforums.org/showthread.php?t=241926&highlight=http+cache](http://www.ubuntuforums.org/showthread.php?t=241926&highlight=http+cache)

---

### Post by Ramses de Norre on 2006-10-31
Didn't help here..

---

### Post by motin on 2006-11-05
I remember finding and installing a package that allowed for setting actions on opened windows, such as moving, resizing, minimizing, closing, displaying on a set of virtual desktops and more based on application name, window title etc, but as of today i just cannot remember it's name and I have tried searching synaptic and google for an hour for it without luck. 

I think that program could help atm. 

> **transducer said:**
> From the kio_http_cache_cleaner man page

"[FONT="Lucida Console"]kio_http_cache_cleaner is a KDE HTTP cache maintenance tool.[/FONT]"

So I guess the kde framework launch this app on a regular basis.  

In its desktop file (/usr/share/services/http_cache_cleaner.desktop) there is the line 

[FONT="Lucida Console"]X-KDE-StartupNotify=false[/FONT]

I'm not an expert in .desktop files, but I guess that's a specific kde tags that specifies the application should run in background and that gnome does not support it.

I believe this is is the core issue here, though. Anyone filed a bugreport to GNOME on this? Is there one already maybe?

---

### Post by mrintegrity on 2006-11-23
the program you are looking for which starts programs with custom settings such as position, decoration and workspace is called devilspie. Download it from here:

[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

---

### Post by motin on 2006-12-01
> **mrintegrity said:**
> the program you are looking for which starts programs with custom settings such as position, decoration and workspace is called devilspie. Download it from here:

[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

COOL! THANKS! Been looking forever!

:)

Then, a reminder:
> **motin said:**
> 

>  Originally Posted by transducer  View Post
From the kio_http_cache_cleaner man page

"kio_http_cache_cleaner is a KDE HTTP cache maintenance tool."

So I guess the kde framework launch this app on a regular basis.

In its desktop file (/usr/share/services/http_cache_cleaner.desktop) there is the line

X-KDE-StartupNotify=false

I'm not an expert in .desktop files, but I guess that's a specific kde tags that specifies the application should run in background and that gnome does not support it.

I believe this is is the core issue here, though. Anyone filed a bugreport to GNOME on this? Is there one already maybe?

---

### Post by kelbizzle on 2006-12-16
Just curious wouldn't it be easier to find out who wrote it? and what amarok does when it's running? The only reason I ask is because no one seemed to have a clear cut answer. Where is all the documentation?

---

### Post by IpplyDip on 2007-03-05
The specification for .desktop files is available at

[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)

There is a directive StartupNotify, which I have set to false. I've only just tried this so it'll be a few hours I guess before I know for sure or not if it has helped.

Has anyone else taken a look at this option? 

There might also be some gnome-specific options -- might take a look in the gnome docs if it turns out not to have worked.

---

### Post by Baji on 2007-04-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/60315](https://bugs.launchpad.net/ubuntu/+bug/60315) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				here's the bug report on launchpad

---

### Post by rkrug on 2007-08-27
Change ```
X-KDE-StartupNotify=false
``` to ```
StartupNotify=False
``` in /usr/share/services/http_cache_cleaner.desktop

---

### Post by MGStreak on 2007-09-10
> **rkrug said:**
> Change ```
X-KDE-StartupNotify=false
``` to ```
StartupNotify=False
``` in /usr/share/services/http_cache_cleaner.desktop

I've tried this, and still no luck.  I've tried both changing the entry, and leaving both lines in the file... neither appears to solve the problem.  I still get the http cache cleaner periodically... and although I'm sure this is likely to be a subjective comment, the frequency with which it occurs also appears unchanged.

EDIT: I've just tried something new, however.  I noticed that in the /usr/share/services/http_cache_cleaner.desktop file, the word "false" in 
```
X-KDE-StartupNotify=false
```
appeared in the colour purple (indicating that the system understood it as a command, not simply text.

Conversely, the word "False" (note the capitalization), did not appear in purple, but rather in plain black... which would indicate (to my untrained eye) that the system does not recognize the word in the same way as it did "false" (small 'f')... so I have edited rkrug's 
```
StartupNotify=False
```
to
```
StartupNotify=false
```

Hopefully THIS will solve the problem once and for all.

---

### Post by MGStreak on 2007-09-12
And... having given it a few days, I can conclusively say that neither option was successful.

---

### Post by dberg on 2007-10-02
Has anyone found a solution for this yet?

---

### Post by KrIaXPaTaLa on 2007-10-12
I'm getting this too (running dapper), cause of ktorrent (good client btw). kcontrol does not give me any options regarding konqueror (cause i dont have it), and so, no options to disable this 'kde cache'. My problem isn't the window or the notification on the panel, I really dont want this running because it implies an insane amount of disk read/write and considerable slowdown of the system. I've just removed http_cache_cleaner.desktop from /usr/share/services and I'me ready to remove the actual process kio_http_cache_cleaner if necessary. My 'kde cache' cant be that big to the point this annoying thing runs once every hour.

Any more information on this is highly appreciated.

Best regards,

KrIaX, PT

EDIT: cache cleaner never started again. And no side effects aparently.

---

### Post by Bakon Jarser on 2007-10-27
I have just noticed this for the first time today.  I have been running Amarok for several days but just started running Ktorrent today.  I'm new to linux so I don't know if it can be done but has anyone tried making it run on a different desktop?  Seeing as how I have four desktops it wouldn't annoy me at all if it was running on desktop #4.

---

### Post by KrIaXPaTaLa on 2007-10-28
> **Bakon Jarser said:**
> I have just noticed this for the first time today.  I have been running Amarok for several days but just started running Ktorrent today.  I'm new to linux so I don't know if it can be done but has anyone tried making it run on a different desktop?  Seeing as how I have four desktops it wouldn't annoy me at all if it was running on desktop #4.

The app will start allways on the active desktop, I think.

Regards.

---

### Post by bred on 2008-07-17
I'm having the exact same problem with ktorrent on hardy deb

---

