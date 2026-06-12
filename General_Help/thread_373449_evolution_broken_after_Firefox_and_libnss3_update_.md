---
title: "evolution broken after Firefox and libnss3 update (070301)"
date: 2007-03-01
forum: General Help
---

### Post by Stryker777 on 2007-03-01
Updated libnss3 and libnss-dev today with the update to 2.1.firefox.1.5.0.10

THis is causing a evolution to crash.

Any ideas?

> 
(evolution-2.6:11338): evolution-smime-WARNING **: Failed all methods for initializing NSS


---

### Post by frogotronic on 2007-03-01
SAME PROBLEM HERE

```

CalDAV Eplugin starting up ...

(evolution-2.6:6282): camel-WARNING **: Failed to initialize NSS
```



PLEASE TEST YOUR UPDATES **BEFORE** SENDING THEM OUT.

---

### Post by frogotronic on 2007-03-01
evolution is broken with the new firefox upgrade in dapper

lbnss is the culprit

here's the workaround:

1) open terminal

2)  ```
LD_LIBRARY_PATH=/usr/lib/firefox evolution &
```

3) minimise terminal and use evolution.

Developers, PLEASE FIX ASAP.

- CH

---

### Post by Porta on 2007-03-01
Hi there;

I received a couple of updates today for gnome and firefox (4 in total) and now i can't start Evolution mail annymore, this is the case on both of my machines, maybe it has something to do with it, i don't know
Is there a way out of this nasty bussines.

Greetings
Porta

---

### Post by bapoumba on 2007-03-01
[https://launchpad.net/ubuntu/+source/evolution/+bug/56118]("https://launchpad.net/ubuntu/+source/evolution/+bug/56118")
Please look if your reports are related to this fixed bug. And may be comment in it if applicable.

---

### Post by Stemp on 2007-03-01
Try to start evolution from a Terminal to see if you have any error messages

NB : [http://www.ubuntuforums.org/showthread.php?t=373449](http://www.ubuntuforums.org/showthread.php?t=373449)

---

### Post by frogotronic on 2007-03-01
> **bapoumba said:**
> [https://launchpad.net/ubuntu/+source/evolution/+bug/56118]("https://launchpad.net/ubuntu/+source/evolution/+bug/56118")
Please look if your reports are related to this fixed bug. And may be comment in it if applicable.

yep, looks similar

here's the workaround

from terminal:

 LD_LIBRARY_PATH=/usr/lib/firefox evolution &

but it's not permenent - is there a fix on the way?

---

### Post by Stemp on 2007-03-01
You should fill a bug (if it's not already done)

[Bugs Launchpad]("https://bugs.launchpad.net/")

---

### Post by Porta on 2007-03-01
That did the trick (for now), thanks for the assistance Stemp :) 
I hope they'll fix it soon.

regards
Porta

---

### Post by cookfromfrozen on 2007-03-01
Those who are having this problem must file bug reports or confirm the problem if there is already a bugrep open, otherwise the chances of this being fixed are low.

---

### Post by cbhargava on 2007-03-01
Today I installed two upgrades (below) on my Ubuntu 6.06LTS installation.

libnspr4 (2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1) to
2:1.firefox1.5.dfsg+1.5.0.10-0ubuntu0.6.06.1
libnss3 (2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1) to
2:1.firefox1.5.dfsg+1.5.0.10-0ubuntu0.6.06.1

After the upgrade, Evolution 2.6 crashed. I restarted the machine and started evolution, it crashed every time. Cannot start evolution at all.

Anyone else experiencing this issue?

---

### Post by Stemp on 2007-03-01
[http://www.ubuntuforums.org/showthread.php?t=373449]("http://www.ubuntuforums.org/showthread.php?t=373449")

---

### Post by Scunizi on 2007-03-01
I just filed a bug # 413532.  A previous bug was filed by a RedHat user that was solved. That bug was 412537.  After chatting on Gimpnet #evolution they had recommended filing another bug against Ubuntu on launchpad.  Couldn't do it there so I went to bugzilla.  Hopefully this will be fixed soon so I can retrieve my data and move on (thunderbird/sunbird?).  I wish there was a way to have Evo update my gmail account for addresses & calendar when entered.

---

### Post by cbhargava on 2007-03-01
Thanks, got it and added a comment to Bug 88990

[https://launchpad.net/ubuntu/+source/firefox/+bug/88990](https://launchpad.net/ubuntu/+source/firefox/+bug/88990)

Hope that they fix it pretty soon.

---

### Post by kline on 2007-03-01
As of this morning evolution fails to init.  I <I>did</I> download and install some new firefox upgrade just before trying evoultion; noy sure if that caused the troubles.  I'm running 6.06 and waiting for 7.04, but would appreciate some clues.

I use this server for all the bells/whistles: graphics, sound.  I can make-do with mutt if no other choice.  Feedback, suggestions appreciated!

---

### Post by cbhargava on 2007-03-01
Evolution has caused lot of trouble today 

> **Stemp said:**
> [http://www.ubuntuforums.org/showthread.php?t=373449]("http://www.ubuntuforums.org/showthread.php?t=373449")

---

### Post by kline on 2007-03-01
Thanks lots.  This is really a bizarre bug.  (( Not only that, but both firefox and evo are *huge* ; i.e., a not-trivial fix.  [[OMG]] ))

---

### Post by laidback on 2007-03-01
cement_head
You're brilliant. I'd just hit the problem after the upgrade, tried a reboot, no good. So off to the forum and there's your message. Tried it out and bingo it worked.

Thank you so much, thought I'd lost my emails.

---

### Post by ardchoille42 on 2007-03-01
First of all I'd like to say that I never install anything except from the official repos and I never compile software.. the repos are there for a reason.

Today I was using Firefox and noticied the update notifier telling me there were updates. So, I opened a terminal, ran "sudo aptitude update && sudo aptitude upgrade" and found there were the following updates:

this is from /var/log/aptitude
> 
===========================================================
[UPGRADE] firefox 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 -> 1.5.dfsg+1.5.0.10-0ubuntu0.6.06.1
[UPGRADE] firefox-gnome-support 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 -> 1.5.dfsg+1.5.0.10-0ubuntu0.6.06.1
[UPGRADE] libnspr4 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 -> 2:1.firefox1.5.dfsg+1.5.0.10-0ubuntu0.6.06.1
[UPGRADE] libnss3 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 -> 2:1.firefox1.5.dfsg+1.5.0.10-0ubuntu0.6.06.1
===========================================================


I closed Firefox and updated. After that I found that Evolution crashes when it's run. To make sure this was the cause, I restored my /dev/hda1 from an image I made yesterday - yay for PartImage - which took all of 3 minutes. This restored my hard drive to the exact condition it was in yesterday without any problems. Then the first thing I did was ran Evolution to check my email. All was well. Then I ran "sudo aptitude update && sudo aptitude upgrade" to install all updates and Evolution crashed again. I can restore my /dev/hda1 from the image again, since it only takes 3 minutes.

Anyone else having this problem with today's updates?

EDIT: I see others are having this problem too. Whew, it's not just me. I also see a bug report filed. This community ROCKS :)

---

### Post by cbhargava on 2007-03-01
Yes there are problems with evolution today. Please search the forums for evolution and you will find a temporary solution. Bug report is already filed.

---

### Post by paddyg on 2007-03-01
You can also include cement_head's workaround in a script in

/home/yourself/.gnome2/nautilus-scripts

so you can just rightclick and start Evolution by selecting your script without having to always use the terminal. The script can be as simple as that and chmod 700

#!/bin/sh
LD_LIBRARY_PATH=/usr/lib/firefox evolution &

---

### Post by jazzeymike on 2007-03-01
Saw updates available so installed them, using the gnome interface. Then Evolution wouldn't start. After a couple of goes, I opened a terminal and typed evolution as a command, which elicited this response:

```
(evolution-2.6:5386): camel-WARNING **: Failed to initialize NSS
```
 Has this happened to anyone else? Does anyone have a fix?

Many thanks, in anticipation,

Mike

---

### Post by Stemp on 2007-03-01
[http://www.ubuntuforums.org/showthread.php?t=373449](http://www.ubuntuforums.org/showthread.php?t=373449) ?

---

### Post by cookfromfrozen on 2007-03-01
This is happening to quite a number of people.  It has been filed as a bug (#413532) and should be fixed in another update, I hope.

A temporary workaround is to go into a terminal and type

```
LD_LIBRARY_PATH=/usr/lib/firefox evolution &
```
then type "evolution" to start it.

---

### Post by paperclip on 2007-03-01
Thank you so much.. This is why I love Ubuntu and the forums..

---

### Post by Robhogg on 2007-03-01
I have been using gnome, and evolution, on Dapper Drake for some time now, with no problems up until a short while ago. 

I launched evolution to check my email when I got home this evening, and it worked fine. However, a little later it failed to launch. Using a panel button, "Starting Evolution Mail" appears in the bottom panel, and then disappears. No error message is displayed. Launching it with *strace evolution*, the output contains many lines like the following:

```
open("/usr/lib/i486-linux-gnu/tls/i686/cmov/libfreebl3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/cmov", 0xbf947824) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/libfreebl3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686", 0xbf947824) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/cmov/libfreebl3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
```

Before the failure, I had installed five updates to: firefox, the Firefox DOM inspector, firefox-gnome-support, libnspr4 and libnss3 (both of which appear to be part of firefox). I had also recently modified xorg.conf for a newly installed wacom graphics tablet (though evolution has been working since I installed the wacom-tools).

Can anyone suggest how to sort this out (short of re-installing each file seperately - the output of strace contains more than 1200 lines referring to missing files). I've tried re-installing evolution, but that did not solve the problem. 

Thanks,
Rob

---

### Post by Stemp on 2007-03-01
[http://www.ubuntuforums.org/showthread.php?t=373449](http://www.ubuntuforums.org/showthread.php?t=373449)

---

### Post by jazzeymike on 2007-03-01
Zounds, thanks, folks, and so quick too.

I used the LD_LIBR . . . command and didn't have to type in evolution, it just came up.

So I can communicate again. I hate those long silences. :) 

Thanks again and best rgards,

Mike

---

### Post by SLOSue on 2007-03-01
Thanks from me too, you're a doll!

---

### Post by Robhogg on 2007-03-01
Je vous remercie pour votre aide.

Rob

---

### Post by bapoumba on 2007-03-01
I have merged several similar threads in here.

---

### Post by Scunizi on 2007-03-01
For those of us who want to learn .... what does "LD_LIBRARY_PATH=/usr/lib/firefox evolution &" actually do? and why does it work.  Also will I have to enter this command every time I reboot until the issue is fixed? or will I have to "undo" the command somehow after the fix is applied?  Inquiring mind wants to know!

---

### Post by bapoumba on 2007-03-01
Here is the new bug report:
[https://launchpad.net/ubuntu/+source/firefox/+bug/88990]("https://launchpad.net/ubuntu/+source/firefox/+bug/88990")

---

### Post by D10 on 2007-03-01
Cement Head 

Thanks for the workaround.

---

### Post by AlanRogers on 2007-03-01
> **paddyg said:**
> The script can be as simple as that and chmod 700
```
 #!/bin/sh
LD_LIBRARY_PATH=/usr/lib/firefox evolution &
```This worked for me. Just sitting waiting for the real fix now. For those that are unsure how to do this:[LIST=1]
[*]Open your Home folder
[*]Click on View > Show Hidden Files
[*]Navigate to \...\.gnome2\nautilus-scripts\
[*]Right-click and choose Create Document > Empty File
[*]Call it Evolution
[*]Open the file by double-clicking on it
[*]Paste the above code into the file
[*]Save & Close
[*]Right-click and choose Properties
[*]Select Permissions tab
[*]Check Execute
[*]Click [Ok] to close[/LIST]If you want a desktop launcher for convenience:[LIST=1]
[*]Return to your desktop
[*]Right-click and choose Create Launcher
[*]In Command, paste home\<user>\.gnome2\nautilus-scripts\Evolution
[*]Add Comment and Description if required[/LIST]When the fix comes through, just delete the launcher and return to launching Evolution in the normal way.

And Robert is your mother's brother!

---

### Post by smokeslikeapoet on 2007-03-01
I fixed by 
```

cd /usr/lib
sudo ln -s firefox/libfreebl3.so .

```
Found the fix on the Redhat Bugzilla.

---

### Post by potterpoole on 2007-03-01
This morning I started to write a mesage in evolution and realised I didnt have time so I hit the x closed it down and went to work. This afternoon it wont open for me I tried restarting the computer reloading evolution and runing it from a terminal using (sudo evolution )as a comand. all I got back was failed to initalise NSS  can anyone help.

---

### Post by bapoumba on 2007-03-01
@ potterpoole: please read the thread I just merged yours in.

---

### Post by AklBlue on 2007-03-01
> **smokeslikeapoet said:**
> I fixed by 
```

cd /usr/lib
sudo ln -s firefox/libfreebl3.so .

```
Found the fix on the Redhat Bugzilla.

Thanks.  Works on my Dapper.
Easier option than the new launcher option also suggested in this thread.

---

### Post by sleepytom on 2007-03-01
Tonight I updated my Dapper system with the packages recommended by the update manager, but now Evolution will not run. I get the following error:

```
evolution-smime-WARNING **: Failed all methods for initializing NSS
```

What kind of an update breaks things that were working just fine!? Can I undo the last update, or fix it somehow?

---

### Post by nrayever on 2007-03-01
the same happend to me!! and i need it to check some mails! damn....

---

### Post by HereInOz on 2007-03-01
Likewise here, good people.

Ran the upgrade this morning and bingo - no Evolution.

What kind of update breaks things that were working just fine????  You clearly have never used a Windows operating system have you ?? :-)

Lets see what happens.

---

### Post by thomasaaron on 2007-03-01
Whoever the genius was that came up with the workaround...

Muchos Gracias!

Tom

---

### Post by thomasaaron on 2007-03-01
Oh yeah, and one more thing.

Forums like this are the reason I'll be staying with Ubuntu.
When the forum goes, I go.

Best,
Tom

---

### Post by zzatz on 2007-03-01
Yes, same issue, on Ubuntu 6.06 LTS:

Upgrade Firefox, and on reboot (for other reasons), evolution fails with the following:

Failed to initialize NSS

Note that libnss was one of the packages upgraded.

---

### Post by HereInOz on 2007-03-01
I tried a re-install, a removal and re-install and a complete removal and re-install.  No joy.  Still not working.

Looks like an issue in the NSS upgrade.

---

### Post by davarino on 2007-03-01
> **smokeslikeapoet said:**
> I fixed by 
```

cd /usr/lib
sudo ln -s firefox/libfreebl3.so .

```
Found the fix on the Redhat Bugzilla.

Thank you! Thank you! Thank you!

Nice thing about this is that it works for all users... which means I don't have to change a lot of launchers or explain anything to anyone.

---

### Post by davarino on 2007-03-01
Enter this code and you will eliminate this problem:

> cd /usr/lib
sudo ln -s firefox/libfreebl3.so

There is another thread running on this same issue... "evolution broken after Firefox and libnss3 update (070301)". Check it out... but the bottom line is: run the "ln" stuff and that ought to fix it. (Courtesy of **smokeslikeapoet**)

---

### Post by malel on 2007-03-01
There was some updates came out today and ever since I updated my Evolution mail will not start from the shortcut icon on the desktop . I can use it through the Firefox browser but what can I do to get functionality back from the desktop . It also crashes when I go through Applications > Internet > Evolution
Thank you

---

### Post by sleepytom on 2007-03-01
Yes! Very nice. Thank you!

---

### Post by malel on 2007-03-01
Problem now sorted . Followed instructions "sudo ln -s firefox/libfreeble.so" and the problem has been fixed . 
Cheers

---

### Post by edu65 on 2007-03-01
> **malel said:**
> Problem now sorted . Followed instructions "sudo ln -s firefox/libfreeble.so" and the problem has been fixed . 
Cheers

It works, but you must "cd /usr/lib"  first.

---

### Post by crudolphy on 2007-03-01
Creating the link worked for me and seems to be more simple than a script here is what I did:

cd /usr/lib
sudo ln -s firefox/libfreebl3.so libfreebl3.so

then just to make sure:
ls -l libfreebl3.so

result should be
libfreebl3.so ---> firefox/libfreebl3.so

Then start Evolution.

Hope this helps.

Chuck

---

### Post by FaceLeg on 2007-03-01
Yes this fix works for me as well.

Thanks! I had installed quite a few programs, and thought I had inadvertantly broken something.

Off to fill a bug report out now.

---

### Post by twoeyedhuman on 2007-03-01
I installed the latest firefox security advisory on March 1 2007 and now I can't connect to secure servers.

I'm running ubuntu edgy i386 with firefox version 1.5.0.10.

---

### Post by Buzzygirl on 2007-03-01
Whew... glad to see at least a temporary fix. I had the exact same problem as all of you after I download the most recent updates this afternoon. Hopefully this will be solved soon.

---

### Post by stimpyaw on 2007-03-02
> **smokeslikeapoet said:**
> I fixed by 
```

cd /usr/lib
sudo ln -s firefox/libfreebl3.so .

```Found the fix on the Redhat Bugzilla.

this worked for me.

I just recently had this issue to, thanks for adding this!!

---

### Post by ardchoille42 on 2007-03-02
> **Scunizi said:**
> For those of us who want to learn .... what does "LD_LIBRARY_PATH=/usr/lib/firefox evolution &" actually do? and why does it work.  Also will I have to enter this command every time I reboot until the issue is fixed? or will I have to "undo" the command somehow after the fix is applied?  Inquiring mind wants to know!

My question is why does evolution depend on firefox or vice versa? These are two completely different apps and shouldn't depend on each other. If evolution didn't depend on firefox stuff, then evolution wouldn't have broke with a firefox update. OR am I wrong about this?

---

### Post by nrayever on 2007-03-02
> **smokeslikeapoet said:**
> I fixed by 
```

cd /usr/lib
sudo ln -s firefox/libfreebl3.so .

```
Found the fix on the Redhat Bugzilla.

thanks smokeslikeapoet. finally redhat was useful for something :lolflag: :lolflag:

---

### Post by pgabriel on 2007-03-02
I can confirm that for Ubuntu Dapper, it is a problem with nss library. Someone from packaging take notice.
The description of the problem and a workaround is available on [RedHat Bugzilla]("http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=229987").
For me it broke Evolution which no longer starts:
```
$ evolution-2.6
CalDAV Eplugin starting up ...

(evolution-2.6:5448): camel-WARNING **: Failed to initialize NSS
```

Suggested workaround:
```
cd /usr/lib
sudo ln -s firefox/libfreebl3.so .

```

---

### Post by bapoumba on 2007-03-02
Merged a couple more thread in here. From USN maling list:
> 
[USN-428-2] Firefox regression 

Ubuntu 6.06 LTS:
 firefox                                  1.5.dfsg+1.5.0.10-0ubuntu0.6.06.2
 libnspr4                                 1.5.dfsg+1.5.0.10-0ubuntu0.6.06.2
 libnss3                                  1.5.dfsg+1.5.0.10-0ubuntu0.6.06.2

USN-428-1 fixed vulnerabilities in Firefox 1.5.  However, changes to
library paths caused applications depending on libnss3 to fail to start
up.  This update fixes the problem.

---

### Post by cookfromfrozen on 2007-03-02
Fixes have been commited for Dapper and released for Edgy, so I'd expect another update fixing the problem  soon.

I would recommend you use the LD_LIBRARY_PATH workaround rather than permanently modifying your system, as it will eventually be fixed by an update anyway.

---

### Post by Robhogg on 2007-03-02
Just installed the newly released firefox updates in Dapper. This has fixed the problem. Evolution starts as normal with no work-around needed.

Thanks, all

---

### Post by hobo on 2007-03-02
New update fixed my problem also. dapper 6.06 =D>

---

### Post by frogotronic on 2007-03-02
Kudos to the developers and Ubuntu personnel

The fix worked - good work & thanks.

- CH

---

### Post by WW on 2007-03-02
Arghhh... my Firefox is now broken after the last update.  Edit->Preferences does nothing, and Tools->Extensions gives me an error (see [http://ubuntuforums.org/showthread.php?t=374232](http://ubuntuforums.org/showthread.php?t=374232) ).

---

### Post by bapoumba on 2007-03-02
As the evolution problem is solved now, I am closing this thread.

---

