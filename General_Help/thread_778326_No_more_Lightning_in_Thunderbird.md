---
title: "No more Lightning in Thunderbird"
date: 2008-05-02
forum: General Help
---

### Post by notesetter on 2008-05-02
I've migrated my Mozilla Thunderbird files from a Windows XP system to Ubuntu Studio 8.04. I had the calendar add-on installed. When I started Thunderbird for the first time in Ubuntu, I got the message:

"The calendar data in your profile was updated by a newer version of Lightning, and continuing will probably cause the information to be lost or corrupted. Lightning will now be disabled and Thunderbird restarted"

How can I get the Lightning calendar add on to work? I've already uninstalled and reinstalled both Thunderbird and Lightning via >Add/Remove (it didn't work). Any insight is much appreciated.

Dave

---

### Post by komputes on 2008-05-26
Note: At this date, the version of lightning-extension in the Ubuntu repos in Gutsy is 0.5, in Hardy is 0.7 and the version from Mozilla is 0.8

Ok, this one has been on my list of bugs for a while now :-k and I finally got it :eek: . I can finally replace Evolution's calendar. For some reason Mozilla gives users the impression that the add-on that is used for Windows is the same one as for Linux (therefore will work on Ubuntu as well as others). This is NOT the case as of the date of me writing this. For at least 6 months the extension has been messed up not allowing me to view calendars properly.

If you use Ubuntu, **lightning-0.8-tb-linux.xpi** from the following sites **will not work well** with Mozilla Thunderbird:
```
http://www.mozilla.org/projects/calendar/lightning/
https://addons.mozilla.org/en-US/thunderbird/addon/2313
```If you have already installed it, I would recommend _**backing up** ~/.mozilla-thunderbird_ if you haven't done a backup already. Then, go into Thunderbird and remove the "defective" Lightning Add-On by going to:

[I]Tools > Add-Ons

[/I]and clicking "Uninstall" beside Lightning.


================================
[B]
[SIZE=4]To install Lightning into Thunderbird on Ubuntu 7.10/8.04 correctly:[/SIZE][/B]

1) Close Thunderbird. 

2) Go to: *Application > Accessories > Terminal *

3)In the terminal type:
```

$ sudo apt-get install lightning-extension

```

[SIZE=1][I][B][SIZE=3][SIZE=2]Note: This worked for me and I think it will work for you too. Since I had both versions of lightning (mozilla and the repository package) installed together, they were conflicting. I had to remove both, then reinstall lightning-extension, purge lightning-extension and reinstall lightning-extension again. It's been working flawlessly since.[/SIZE]

[/SIZE][/B][/I][/SIZE] ```

$ sudo apt-get install lightning-extension
 $ sudo apt-get purge lightning-extension
 $ sudo apt-get install lightning-extension

```
[SIZE=1][/SIZE] ================================
[B]
[SIZE=4]OR: Workarround for [/SIZE][/B]**lightning-0.8-tb-linux.xpi ****[SIZE=4]from Mozilla (seems to work for some people):[/SIZE]**
If you need the Add On from the web site (if you run windows and share the profile for example) I have heard that this helped solve the issue for some people and allow you to run the extention from mozilla's website. The bug seems to be that you need an older version of The GNU Standard C++ Library to use Lightning. To get it type the following in the terminal.

```
$ sudo apt-get install libstdc++5
```[SIZE=1][I]
I recommend the first method...cleaner, and uses libstdc++6
[/I][/SIZE]

---

### Post by JoWi on 2008-06-14
Thanx, the second advice worked great!

---

### Post by zekayi on 2008-06-16
Yep the second workaround worked fine for me too. Thanks a lot.

---

### Post by rage007 on 2008-06-24
Ditto the above statements, libstdc++5 made 0.8 work on Hardy like a charm.  Works better than 0.7.

---

### Post by Karl S. on 2008-06-29
> **notesetter said:**
> I've migrated my Mozilla Thunderbird files from a Windows XP system to Ubuntu Studio 8.04. I had the calendar add-on installed. When I started Thunderbird for the first time in Ubuntu, I got the message:

"The calendar data in your profile was updated by a newer version of Lightning, and continuing will probably cause the information to be lost or corrupted. Lightning will now be disabled and Thunderbird restarted"

How can I get the Lightning calendar add on to work? I've already uninstalled and reinstalled both Thunderbird and Lightning via >Add/Remove (it didn't work). Any insight is much appreciated.

Dave

It's a bit drastic, but I just deleted my profiles.ini file (under ./mozilla-thunderbird), and now everything's working fine.

---

### Post by pmla on 2009-07-05
* Remove calendar database "storage.sdb" from your profile 
.mozillathunderbird

---

### Post by jdn74 on 2009-11-16
Thanks for the good info.

I was using Thunderbird with the Lightning addon in Windows 7 RC1. I loved it. In Ubuntu, I got Thunderbird via Synaptic Packet Manager, but made the mistake of downloading the addon from the website. It didn't work. After installing Lightning using Synaptic Packet Manager, everything works great!

---

