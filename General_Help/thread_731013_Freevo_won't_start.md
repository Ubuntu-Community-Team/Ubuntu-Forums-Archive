---
title: "Freevo won't start"
date: 2008-03-21
forum: General Help
---

### Post by austin on 2008-03-21
Hi,

installed freevo from repositories (gutsy, no backports, so this 1.8.0-rc2). While configuring I told it to not start any services and to use x11. I have no tvcard but I thought the prog would start nevertheless so I can have a look at the music functions ...

Freevo stup seems to work

When I type freevo is says "Switching process to principal group 'freevo'." and nothing else happens . Nothing useful in the freevo-logs nore in dmesg.

What's up here? Do I need to use a specific user? Do I need a specifiv x11 setup?

---

### Post by Yellow_Panther on 2008-03-22
Hi,
Till now I used freevo 1.7.6 and it worked fine, next I updated it via synaptic to 1.8.0-rc2 and now I have the same message. Anybody knows what password should I use ?:confused:

I found this link, but I don't understand the code : [http://lists.alioth.debian.org/pipermail/pkg-freevo-maint/2008-January/000042.html]("http://lists.alioth.debian.org/pipermail/pkg-freevo-maint/2008-January/000042.html")

Yellow_Panther

---
I'm sorry if my English isn't very good, I'm a SwissFrench people.

---

### Post by littlebattler on 2008-03-22
The same problem here on a fresh install of fluxuntu. I put it down to the latest update (i think done yesterday) which bumped the version to 1.8rc3, or smething like from the 1.7 which worked perfectly well. 

no fixes as yet that ive come across. 

please shaer what you discover

---

### Post by littlebattler on 2008-03-22
Maintainer: Freevo Debian Dream Team <pkg-freevo-maint@lists.alioth.debian.org>
Maintainer: Georg W. Leonhardt <repo@geole.info>

we need to mail these guys and tell them that in their zeal to force upon us security they've broken freevo

---

### Post by segalion on 2008-03-29
Same problem.

Maybe here could be reported... 

[http://sourceforge.net/mailarchive/forum.php?forum_name=freevo-users](http://sourceforge.net/mailarchive/forum.php?forum_name=freevo-users)

---

### Post by shwan on 2008-03-30
Same, fresh install of 8.04 beta, and Freevo from the gutsy repositories, I've added my user account to the freevo group as it says - but just doesn't start.
Thought it was something I did wrong until I found this thread...
Nothing useful from google, so I'll just keep checking back here. =)
Shwan

---

### Post by pk386 on 2008-03-30
I'm having the same problem... (using 7.10 following the install guide [HERE]("http://doc.freevo.org/FreevoAptUbuntu"))

I've added the user to the freevo group but I get the folloing error

```
tvpc@TVPC:/etc/freevo$ freevo
You are not part of the group 'freevo', you cannot exploit 
shared resources (such as the cache). Your data will be saved in /home/tvpc/.freevo 

```

any ideas?

---

### Post by BootROM on 2008-03-31
It appears as though it has been updated to 1.8.0-rc2 which seems to be broken in some form. I'm going to attempt building from the source packages at freevo.sf.net

---

### Post by finster on 2008-03-31
Same problem here on a fresh install of Ubuntu 7.10. Anybody have any success yet?

---

### Post by BootROM on 2008-03-31
Just woke up, so I'm about to try install from source again on 8.04

Apparently this trick worked for installing a slightly older version on the freevo-users mailing list:
[http://sourceforge.net/mailarchive/forum.php?thread_name=766803B4-4386-4CF8-8D25-5ACE64406CFF%40sentex.net&forum_name=freevo-users]("http://sourceforge.net/mailarchive/forum.php?thread_name=766803B4-4386-4CF8-8D25-5ACE64406CFF%40sentex.net&forum_name=freevo-users")

I'll try this method next if I can't get version 1.8.0 working from source.


EDIT: Also discovered that Freevo 1.8.0 requires kaa base 0.4 according to the Freevo front page whereas the geole repository only has kaa base 0.2
So it could be that the dependencies simply aren't met on the repo :S

---

### Post by samuraix51 on 2008-04-02
> **BootROM said:**
> 

Apparently this trick worked for installing a slightly older version on the freevo-users mailing list:
[http://sourceforge.net/mailarchive/forum.php?thread_name=766803B4-4386-4CF8-8D25-5ACE64406CFF%40sentex.net&forum_name=freevo-users]("http://sourceforge.net/mailarchive/forum.php?thread_name=766803B4-4386-4CF8-8D25-5ACE64406CFF%40sentex.net&forum_name=freevo-users")


This worked for me, I just tried it and Freevo is working just fine now

---

### Post by finster on 2008-04-02
> **samuraix51 said:**
> This worked for me, I just tried it and Freevo is working just fine now

Many thanks for this link. Worked for me too. For anybody else, here's a summary of what I did: -

Remove broken version of freevo
```
sudo apt-get remove freevo freevo-data python-freevo
```

Then remove the ubuntu.geole.info sources from your /etc/apt/sources.list and add the following instead: -
```
deb http://debian.geole.info/ etch main contrib non-free
```

Then do : -

```
sudo apt-get update
sudo apt-get install freevo
```

Which should hopefully then install a working version. As the post says, it might be worth removing the geole.info repository after everything is working to make sure that an automatic upgrade doesn't break things again!

Hope this helps!

---

### Post by BootROM on 2008-04-03
Awesome to hear it's working.

Just wondering if anyone has been able to get Freevo version 1.8.0 working on Ubuntu 7.10 or 8.04 beta? I'm on the verge of giving up and just using the older version.

---

### Post by thib on 2008-04-06
This method doesn't work under hardy

---

### Post by hulluPeruna on 2008-04-11
I played around a little bit to find out that the only thing missing is the KAA libs. 

I started with the non working version after the update from 1.7.x to  Freevo 1.8.0rc2.

I uninstalled freevo using 
> apt-get remove freevo
Than I followed the instructions to do a [_[COLOR="Blue"]SourceInstallation[/COLOR]_]("http://doc.freevo.org/SourceInstallation") for the missing libs. So I downloaded and installed the latest version of kaa-base, kaa-imlib2 and  kaa-metadata from sourceforge. 
After that I installed Freevo 1.8.0rc2 from the "deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) gutsy universe multiverse" mirror.Couple modification on the Configuration and the system was up and running again.

HP

---

### Post by psavva on 2008-04-14
You guys do realise that the RC version is a release candidate.  It is still a beta version...  Rather get the Stable release and dl the the next update as stable rather than RC.  Just wait a little while longer :D It's worth it

---

### Post by finster on 2008-04-14
> **psavva said:**
> You guys do realise that the RC version is a release candidate.  It is still a beta version...  Rather get the Stable release and dl the the next update as stable rather than RC.  Just wait a little while longer :D It's worth it
That's the problem - the version in the repositories is the RC version so an upgrade installs the non-working version :( The instructions above are to roll-back to the working version.

---

### Post by amr2205 on 2008-04-26
> **finster said:**
> Many thanks for this link. Worked for me too. For anybody else, here's a summary of what I did: -

Remove broken version of freevo
```
sudo apt-get remove freevo freevo-data python-freevo
```

Then remove the ubuntu.geole.info sources from your /etc/apt/sources.list and add the following instead: -
```
deb http://debian.geole.info/ etch main contrib non-free
```

Then do : -

```
sudo apt-get update
sudo apt-get install freevo
```

Which should hopefully then install a working version. As the post says, it might be worth removing the geole.info repository after everything is working to make sure that an automatic upgrade doesn't break things again!

Hope this helps!

It did the trick, thanks!

---

### Post by hom on 2008-04-30
hi,

i install new xubuntu 8.04 and i hope for freevo, but if i can install it (rc2) dont start , user freevo can,t write on /home freevo/...

someone can give me all step for install old freevo version??

tk

---

### Post by oscaruc on 2008-04-30
I've managed to run Freevo 1.8.0 in Hardy (8.04). It's a quite dirty workaround, but works for me. These are the steps I've followed:

1) Add the broken geole repository (Yes, add it!)
```
deb http://ubuntu.geole.info/ gutsy universe multiverse
```
2) Install freevo: ```
aptitude install freevo
```

3) It will download all dependencies and try to install and configure the freevo package.

4) It will fail when trying to configure it. Well, then ```
cd /var/lib/dpkg/info/
``` and delete the file of postinstallation script ```
rm freevo.postinst
```  The package won't be correctly configured but doesn't matter because we won't use it. 

5) Execute ```
aptitude -f install
``` to allow the installation of remaining dependecies packages. At this point we have installed a broken freevo with all its dependencies.

6) Download from freevo.sourceforge.net the .tgz file with version 1.8.0, and uncompress it into a directory. If we execute the freevo binary it will return the following error: 

```
Can't find all Python dependencies:
No module named utils
```

That's because Hardy uses python 2.5 and Freevo needs a package (PyXML) wich doesn't work directly on 2.5, and is not available.

7) Then, we need to install a similar package called python-xml: ```
aptitude install python-xml
``` The needed files are there, but in a different path that python and/or Freevo don't find.

8 ) Go to /usr/lib/python2.5/site-packages and link the installed package directory with the name Freevo expects:

```
cd /usr/lib/python2.5/site-packages
ln -s oldxml/_xmlplus/
```

After aaaaaall this, I finally can execute the binary file 'freevo' from the tgz.

---

### Post by Gras on 2008-05-01
I managed to get Freevo from the debian repository to work on hardy (ubuntu 8.04):

First install the broken freevo from the geole repositories, by entering into your sources.list

```
deb http://ubuntu.geole.info/ gutsy universe multiverse
deb-src http://ubuntu.geole.info/ gutsy universe multiverse
```

and running

```
apt-get install freevo
```

This will install the broken freevo and all it's dependencies. It's the dependencies we want :)

Now uninstall freevo, freevo-data and python-freevo:

```
apt-get remove freevo freevo-data python-freevo
```

...do NOT run apt-get autoremove afterwards, you need the other packages.

Now you remove or comment out the two lines from your sources.list:
```
#deb http://ubuntu.geole.info/ gutsy universe multiverse
#deb-src http://ubuntu.geole.info/ gutsy universe multiverse
```

... and insert

```
deb http://debian.geole.info/ etch main contrib non-free
```

afterwards you run:

```
apt-get install freevo
```

and you're have a working freevo on hardy heron!

PS. You also need to make the sneaky symbolic link fix, posted above:

```
cd /usr/lib/python2.5/site-packages/
ln -s oldxml/_xmlplus/
```

Kind regards, hoping this will help you. ;)

---

### Post by rdrgmth on 2008-05-04
Thanks, This work for me an the main app! (Xubuntu 8.04), Now i just have some problems of config  (user permissions, xmltv, full screen, Etc)

Thanks Again.

---

### Post by darthchaosofrspw on 2008-07-09
> **Gras said:**
> I managed to get Freevo from the debian repository to work on hardy (ubuntu 8.04):

Thanks. Got it installed, but I get the following even after I add my user to the freevo group:


```
WARNING: 'freevo' user cannot create files in cache directory  /home/freevo/cache , 
  freevo will malfunction  
WARNING: 'freevo' user cannot create files in log directory  /home/freevo/log , 
  freevo will malfunction  
WARNING: 'freevo' user cannot create files in static directory  /home/freevo/static , 
  freevo will malfunction  
WARNING: 'freevo' user cannot create files in video directory  /home/freevo/video , 
  freevo will malfunction  
WARNING: 'freevo' user cannot create files in audio directory  /home/freevo/audio , 
  freevo will malfunction  
WARNING: 'freevo' user cannot create files in image directory  /home/freevo/image , 
  freevo will malfunction  
WARNING: 'freevo' user cannot create files in recordings directory  /home/freevo/recordings , 
  freevo will malfunction  

```

Any solution to that?

EDIT: A reboot after I added my user to the freevo group didn't help.

---

### Post by amr2205 on 2008-07-12
> **Gras said:**
> I managed to get Freevo from the debian repository to work on hardy (ubuntu 8.04):

First install the broken freevo from the geole repositories, by entering into your sources.list

```
deb http://ubuntu.geole.info/ gutsy universe multiverse
deb-src http://ubuntu.geole.info/ gutsy universe multiverse
```

and running

```
apt-get install freevo
```

This will install the broken freevo and all it's dependencies. It's the dependencies we want :)

Now uninstall freevo, freevo-data and python-freevo:

```
apt-get remove freevo freevo-data python-freevo
```

...do NOT run apt-get autoremove afterwards, you need the other packages.

Now you remove or comment out the two lines from your sources.list:
```
#deb http://ubuntu.geole.info/ gutsy universe multiverse
#deb-src http://ubuntu.geole.info/ gutsy universe multiverse
```

... and insert

```
deb http://debian.geole.info/ etch main contrib non-free
```

afterwards you run:

```
apt-get install freevo
```

and you're have a working freevo on hardy heron!

PS. You also need to make the sneaky symbolic link fix, posted above:

```
cd /usr/lib/python2.5/site-packages/
ln -s oldxml/_xmlplus/
```

Kind regards, hoping this will help you. ;)

Thanks! Now it works on Hardy! =D

---

