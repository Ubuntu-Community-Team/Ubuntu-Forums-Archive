---
title: "Latest feisty update kills Opera...."
date: 2007-04-04
forum: General Help
---

### Post by floke on 2007-04-04
Just updated Feisty and Opera has broken.
Terminal gives me this...

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)


Anyone got any ideas?

---

### Post by lvanderree on 2007-04-04
I've got the same problem!

Also installing opera-static (weekly) doesn't help.

---

### Post by floke on 2007-04-04
Just downgraded to 9.10 (from 9.20)

Stgill noi joy...

---

### Post by hansheng on 2007-04-04
yes, me too (9.20), pls fast fix it, thanks!  :(

---

### Post by NRG88 on 2007-04-04
I can confirm it, I was using Opera 9.10.

---

### Post by hansheng on 2007-04-04
this is libx11-6 problem, for more:

[http://my.opera.com/community/forums/topic.dml?id=183923](http://my.opera.com/community/forums/topic.dml?id=183923)

---

### Post by floke on 2007-04-04
Oh well, 
Back in Firefox!

Can't complain really

:)

---

### Post by zvacet on 2007-04-04
Steve,it is from horse to donkey.

---

### Post by floke on 2007-04-04
Better a living donkey than a dead horse though :) 

(BTW: i do use Opera as my primary browser, but used FF extensively before that so am happy to revisit an old friend. If you set it up right the functionality is just as good).

---

### Post by downforce on 2007-04-05
I wrote about how to fix it [on my blog]("http://linuxn00b.wordpress.com/2007/04/05/fixing-dead-opera-on-704-feisty/")

Basically, the offending package is libx11-6.

Downgrade to the previous version of by ```
sudo dpkg -i /var/cache/apt/archives/libx11-6_2%3a1.1.1-1ubuntu2_i386.deb
```.
But that will only fix it until you update again. The easiest way to hold a package from updating/install is to use wajig:
```
 sudo apt-get install wajig
wajig hold libx11-6
```

Load Opera and you're away again!

I'm sure they'll fix it soon, so keep and eye out for version ```
libx11-6_2%3a1.1.1-1ubuntu2_i386.deb
``` during your next wajig update

---

### Post by Engnome on 2007-04-05
I didn't have that package in my cache so I just went to packages.ubuntu.com and downloaded the old edgy version. It works but I don't like my solution, it's a dirty hack IMO.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibx11%2Flibx11-6_1.0.3-0ubuntu4_i386.deb&md5sum=411eac6b95a3af50d230263049efea62&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibx11%2Flibx11-6_1.0.3-0ubuntu4_i386.deb&md5sum=411eac6b95a3af50d230263049efea62&arch=i386&type=main)

---

### Post by dannyboy79 on 2007-04-05
why install a new package to do something aptitude can do? doesn't this work without using another package

**sudo aptitude hold libx11-6**

according to man aptitude:

remove, purge, hold, keep, reinstall
              These commands are the same as ââinstallââ, but apply the named action to all packages given on  the  command  line  for which  it is not overridden. The difference between hold and keep is that hold will cause a package to be ignored by future upgrade commands, while keep merely cancels any scheduled actions on the package.

OR

**sudo aptitude forbid-version libx11-6=2:3a1.1.1-1ubuntu3**
(NOTE: i am unsure whether you should use the ":" or the "%" because when I show the version I have installed, it states,  2:1.0.0-0ubuntu9, but yet the link I posted below shows the .deb file with a "%". huh?)

this way, when the new package does get released (.......ubuntu4 or whatever) an upgrade will just go to that one and skip the bad one which is 2%3a1.1.1-1ubuntu3. (according to [http://linuxn00b.wordpress.com/2007/04/05/fixing-dead-opera-on-704-feisty/](http://linuxn00b.wordpress.com/2007/04/05/fixing-dead-opera-on-704-feisty/))

per man:
forbid-version
              Forbid a package from being upgraded to a particular version. This will prevent aptitude from automatically upgrading to this version, but will allow automatic upgrades to future versions. By default, aptitude  will  select  the  version  to which the package would normally be upgraded; you may override this selection by appending ââ=<version>ââ to the package name: for instance, ââaptitude forbid-version vim=1.2.3.broken-4ââ.

              This command is useful for avoiding broken versions of packages without having to set and clear manual holds. If you deâcide you really want the forbidden version after all, the ââinstallââ command will remove the ban.


hope this works for some1 instead of installing an extra package.

---

### Post by rei_t_ex on 2007-04-05
Engnome,

libx11-6_1.1.1-1ubuntu2_i386.deb is still available here:

[http://altruistic.lbl.gov/mirrors/ubuntu/pool/main/libx/libx11/](http://altruistic.lbl.gov/mirrors/ubuntu/pool/main/libx/libx11/)

I tend to delete my cached packages as well...

---

### Post by Engnome on 2007-04-05
> **rei_t_ex said:**
> Engnome,

libx11-6_1.1.1-1ubuntu2_i386.deb is still available here:

[http://altruistic.lbl.gov/mirrors/ubuntu/pool/main/libx/libx11/](http://altruistic.lbl.gov/mirrors/ubuntu/pool/main/libx/libx11/)

I tend to delete my cached packages as well...

Ok, thx. Actually I dont delete my cache on this machine (hdd space is cheap :D) but I didn't have it anyway. Deleting it is a good idea I'm gonna do it on my laptop as there isn't as much space on it and on this machine that cache was >750mb. :confused: That's a whole ubuntu install. :shock:

Edit: If anyone wonders settings for cache and cleaning the cache can be done in Synaptic -> Settings -> Preferences -> Files.

---

### Post by Colonel Kilkenny on 2007-04-06
Opera just released a weekly build which should work with newest X libs.
Available from [http://my.opera.com/desktopteam](http://my.opera.com/desktopteam)

Notice that it is weekly build based on Opera 9.20 beta 1. Not a official release!
Usually weekly builds are quite stable.

---

### Post by inphektion on 2007-04-06
yea I had this problem and this package:
[http://snapshot.opera.com/unix/Weekly-633/intel-linux/opera_9.20-20070405.6-shared-qt_en_i386.deb](http://snapshot.opera.com/unix/Weekly-633/intel-linux/opera_9.20-20070405.6-shared-qt_en_i386.deb)

fixed it.  I didn't change the libx11 either.

---

### Post by stenka on 2007-04-06
There is a fix :
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by gmiller01 on 2007-04-06
Thx, Thx, Thx :-)

---

### Post by obscur156 on 2007-04-06
i confirm that link is working for me
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

\\:D/

---

### Post by macogw on 2007-04-06
> **downforce said:**
> I wrote about how to fix it [on my blog]("http://linuxn00b.wordpress.com/2007/04/05/fixing-dead-opera-on-704-feisty/")

Basically, the offending package is libx11-6.

Downgrade to the previous version of by ```
sudo dpkg -i /var/cache/apt/archives/libx11-6_2%3a1.1.1-1ubuntu2_i386.deb
```.
But that will only fix it until you update again. The easiest way to hold a package from updating/install is to use wajig:
```
 sudo apt-get install wajig
wajig hold libx11-6
```

Load Opera and you're away again!

I'm sure they'll fix it soon, so keep and eye out for version ```
libx11-6_2%3a1.1.1-1ubuntu2_i386.deb
``` during your next wajig update

To make it stay, you can use dpkg -i --force-overwrite or dpkg -i --force-downgrade

---

### Post by Engnome on 2007-04-06
> **obscur156 said:**
> i confirm that link is working for me
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

\\:D/

Getting Segmentation faults :( But it's ~10 seconds after Opera started so I guess it's something else, like using beta software... Using FF now but I miss Opera, gonna downgrade libx11 again. : /

---

### Post by zvacet on 2007-04-06
It works for me.I´m runing Opera again.

---

### Post by Engnome on 2007-04-06
Downgraded libx11 but not Opera, everything is working again... I guess libx11 had something to do with it and the hotfix build didn't work on my system.

Whatever. Works now :)

---

### Post by stenka on 2007-04-06
Very weired... Have you tried restarting the X session ?

---

### Post by lvanderree on 2007-04-07
There is a hot fix released at the opera weeklies blog:
[http://my.opera.com/desktopteam/blog/2007/04/07/hotfix-2](http://my.opera.com/desktopteam/blog/2007/04/07/hotfix-2)

Weeklies can be less stable then the normal builds, but in this case I think it is a better solution then downgrading you xlibs.
But actually, the weeklies have lots of improvements, like better flash support and the new speed dial window is also great!

---

### Post by desicratn on 2007-04-08
According to the web blog:
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

They have a new Unix .deb that fixes the issue. I downloaded it ( the  opera_9.20-20070407.6-shared-qt_en_i386.deb )and opera is working again with the newest Libx6 installed.

[http://snapshot.opera.com/unix/Weekly-636/intel-linux/](http://snapshot.opera.com/unix/Weekly-636/intel-linux/)

---

### Post by JGJones on 2007-04-09
I've got the latest Opera myself - it does run...

But I cannot access any websites whatsoever with it. All other tools that connect to the internet such as ssh, ping, telnet, Firefox, Thunderbird, Epiphany etc etc are fine. Opera doesn't connect and I can't figure out why.

I'm a die-hard Opera user and Firefox just isn't up to par.

---

### Post by lvanderree on 2007-04-09
I haven't got any problems with any of the 3 hotfixes (now of course running the latest, but all worked out fine).

Are you sure it isn't a firewall issue?

---

### Post by nanog on 2007-04-09
The 636 hotfix worked but the earlier one did not. 
Is Opera the package maintainer for Ubuntu? 


**Gratuitous FF rant warning! Please do not read if this will offend you.**


Having to tweak FF with plugins to obtain funtionality that is there by default in Opera (and IE7) is so boring. I have wasted too much time figuring out which plug-ins *BREAK* FF after an upgrade.

---

### Post by floke on 2007-04-09
> **obscur156 said:**
> i confirm that link is working for me
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

\\:D/


Works for me too.
Now I have a dilemma - stick with Firefox (have grown to re-love it), or switch back to Opera???

---

### Post by zvacet on 2007-04-09
Steve did you saw speed dial option in latest Opera?I think it is enough to solve your dilema.

---

### Post by floke on 2007-04-09
Ah - but Opera doesn't have GoogleBrowserSync, which is faaaaar better since you can sync your bookmarks between PCs! What use is speed dial at home if I need to set it all up the same way at work or elsewhere? With the GoogleBrowserSync I can have exactly the same Firefox wherever I am. It's great. Also, have discovered the prefetch option in the fasterfox extension, which speeds things up mightily.

As it stands, I think I am now preferring Firefox.

Sorry Opera.

---

