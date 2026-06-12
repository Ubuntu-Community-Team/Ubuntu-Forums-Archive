---
title: "I need help installing e17 in Xubuntu"
date: 2007-09-08
forum: General Help
---

### Post by RAV TUX on 2007-09-08
I followed the directive in this thread:

[http://ubuntuforums.org/showthread.php?t=97199](http://ubuntuforums.org/showthread.php?t=97199)

When trying to start the e17 session I get this message:

```
Xsession: unable to launch "/opt/e17/bin/enlightenment" X  Session ---"/opt/e17/bin/enlightenment" not found; falling back to default session.
```I would greatly appreciate any help I can get.

This is in my e17.desktop:

```

[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
```This is in my environment (/etc) -  gedit

```
 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```I just edited this to read like this:

```
 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin"
```I added " " I hope this helps, I will restart X and try to log into the e17 session again.

---

### Post by RAV TUX on 2007-09-08
> **RAV TUX said:**
> I followed the directive in this thread:

[http://ubuntuforums.org/showthread.php?t=97199](http://ubuntuforums.org/showthread.php?t=97199)

When trying to start the e17 session I get this message:

```
Xsession: unable to launch "/opt/e17/bin/enlightenment" X  Session ---"/opt/e17/bin/enlightenment" not found; falling back to default session.
```I would greatly appreciate any help I can get.

This is in my e17.desktop:

```

[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
```This is in my environment (/etc) -  gedit

```
 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```I just edited this to read like this:

```
 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin"
```I added " " I hope this helps, I will restart X and try to log into the e17 session again.


Adding " " gave me the same error message.

---

### Post by kvonb on 2007-09-08
Just a wild guess, but does the file /opt/e17/bin/enlightenment exist, and is it executable?

---

### Post by RAV TUX on 2007-09-08
> **kvonb said:**
> Just a wild guess, but does the file /opt/e17/bin/enlightenment exist, and is it executable?

Actually it doesn't exist:

```

  /opt/e17/bin/enlightenment
bash: /opt/e17/bin/enlightenment: No such file or directory
```


how do I create it? and make it executable?

---

### Post by bettlebrox on 2007-09-08
I'm using the packages from edevelop.org and they work fine. See this link to see how to iinstall them:


[http://ubuntuos.wordpress.com/2007/03/12/howto-ubuntu-feisty-install-e17-enlightenment-desktop/](http://ubuntuos.wordpress.com/2007/03/12/howto-ubuntu-feisty-install-e17-enlightenment-desktop/)

Or on my blog at:

[http://timony.com/mickzblog/2007/02/18/enlightement-e17-on-debian-ubuntu/](http://timony.com/mickzblog/2007/02/18/enlightement-e17-on-debian-ubuntu/)

---

### Post by Rui Pais on 2007-09-08
> **RAV TUX said:**
> Actually it doesn't exist:

```

  /opt/e17/bin/enlightenment
bash: /opt/e17/bin/enlightenment: No such file or directory
```


how do I create it? and make it executable?

This forum is change at high speed. Previous thread was closed on a bad time... 
we continue here then...

You don't read it all my [#481 post]("http://ubuntuforums.org/showpost.php?p=3082892&postcount=481") ;)


edit: 
About doing an updated how-to, I was thinking in dong that a long time ago, but then came the holiday and after that, this September my time has been so short...
I' ll try to do it tonight. Updated and with suggestions for safer ways of using the script. :)

---

### Post by RAV TUX on 2007-09-08
> **Rui Pais said:**
> This forum is change at high speed. Previous thread was closed on a bad time... 
we continue here then...

You don't read it all my [#481 post]("http://ubuntuforums.org/showpost.php?p=3082892&postcount=481") ;)


edit: 
About doing an updated how-to, I was thinking in dong that a long time ago, but then came the holiday and after that, this September my time has been so short...
I' ll try to do it tonight. Updated and with suggestions for safer ways of using the script. :)

Rui Pais I read your thread on post #481 and followed your directive, e17 is still not executable for me.

I look forward to your updated user guide on how to install e17 in Ubuntu,...what I have found most difficult finding is a concise up-to-date & easy-to-use guide.

Specifically I need to make e17 executable, it currently isn't executable. I can paste any info that will make it helpful for you or anybody else to trouble shoot.

I greatly appreciate any help I can get.

---

### Post by Rui Pais on 2007-09-08
I'll try to make it tonight (in 3 or 4 hours). At least i'll make a version updated :)

About your question, 
you need to change line on e17.desktop:
```
Exec=/opt/e17/bin/enlightenment
```
to
```
Exec=/opt/e17/bin/enlightenment_start
```

it don't need to be an executable file.

---

### Post by RAV TUX on 2007-09-08
> **Rui Pais said:**
> I'll try to make it tonight (in 3 or 4 hours). At least i'll make a version updated :)

About your question, 
you need to change line on e17.desktop:
```
Exec=/opt/e17/bin/enlightenment
```to
```
Exec=/opt/e17/bin/enlightenment_start
```it don't need to be an executable file.

Yeah I did that it still doesn't work.

---

### Post by Rui Pais on 2007-09-08
Sorry to hear that. :(

Did the script finished ok? or at least end successfully the compilation/installation of e?

Do you have am /opt/e17/bin/enlightenment_start file?

btw whats the optput of 
```
echo $PATH
```

---

### Post by RAV TUX on 2007-09-08
> **Rui Pais said:**
> Sorry to hear that. :(

Did the script finished ok? or at least end successfully the compilation/installation of e?

Do you have am /opt/e17/bin/enlightenment_start file?

btw whats the optput of 
```
echo $PATH
```

  here's the output: 
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```

---

### Post by TravMan63 on 2007-09-08
Rav Tux (nice avatar btw),

I was successful in getting e17 on ubuntu... although this could be 'dangerous'

-> add the elive repository(ies) to ubuntu's
(see links below)



I DID have problems with some dependency problems between 'enlightenment' (e16) and e17. - but it was fairly easy to fix..

I had this installed and it worked beautifully....(however, now I have elive installed in a dual boot config --- my tests show that videos/games (i.e. torus trooper) - play faster/better/smoother in elive (kernel latency?)...(2ghz 1GB...)

After you are successful in obtaining e17 - be SURE to remove the elive repositories from ubuntu's list.  (this is the dangerous part...) - I did a system update (to ubuntu) - and had a CRAZY time - (I think I experienced 'dependency hell' - it was impossible to recover - I ended up formatting and reinstalling) - I'm guessing the update used all of elives repos as well...do NOT do that! remove the repo info after your successful install of e17!)

it's good to be cautious about this! backups are ALWAYS a good idea...

on a 'related' issue - gvim - is the default text editor with elive - I've had some issues with it (corrupt caches and errors) - gedit is better imo.

[http://ubuntuforums.org/archive/index.php/t-231274.html](http://ubuntuforums.org/archive/index.php/t-231274.html)
[http://wiki.elivecd.org/index.php?title=Sources.list_of_Elive](http://wiki.elivecd.org/index.php?title=Sources.list_of_Elive)


I currently have no issues running the two OS's (ubuntu ce, elive gem) as dual boot.  (and also have the nice elive grub splash screen)

Good luck
TM

--edit
also have an xubuntu /elive dual boot.  this machine still lacks video performance, however (700 mhz, 256 MB intel 768? video)

---

### Post by RAV TUX on 2007-09-08
> **TravMan63 said:**
> Rav Tux (nice avatar btw),

I was successful in getting e17 on ubuntu... although this could be 'dangerous'

-> add the elive repository(ies) to ubuntu's
(see links below)



I DID have problems with some dependency problems between 'enlightenment' (e16) and e17. - but it was fairly easy to fix..

I had this installed and it worked beautifully....(however, now I have elive installed in a dual boot config --- my tests show that videos/games (i.e. torus trooper) - play faster/better/smoother in elive (kernel latency?)...(2ghz 1GB...)

After you are successful in obtaining e17 - be SURE to remove the elive repositories from ubuntu's list.  (this is the dangerous part...) - I did a system update (to ubuntu) - and had a CRAZY time - (I think I experienced 'dependency hell' - it was impossible to recover - I ended up formatting and reinstalling) - I'm guessing the update used all of elives repos as well...do NOT do that! remove the repo info after your successful install of e17!)

it's good to be cautious about this! backups are ALWAYS a good idea...

on a 'related' issue - gvim - is the default text editor with elive - I've had some issues with it (corrupt caches and errors) - gedit is better imo.

[http://ubuntuforums.org/archive/index.php/t-231274.html](http://ubuntuforums.org/archive/index.php/t-231274.html)
[http://wiki.elivecd.org/index.php?title=Sources.list_of_Elive](http://wiki.elivecd.org/index.php?title=Sources.list_of_Elive)


I currently have no issues running the two OS's (ubuntu ce, elive gem) as dual boot.  (and also have the nice elive grub splash screen)

Good luck
TM

--edit
also have an xubuntu /elive dual boot.  this machine still lacks video performance, however (700 mhz, 256 MB intel 768? video)

TravMan, Thanks for the insightful input, this is a great idea. I may actually install Elive Gem on a seperate partition and triple boot to Xubuntu/Elive/XP

I really wish it would work in Xubuntu also.

---

### Post by Rui Pais on 2007-09-09
Hi again RAV TUX, sorry the long delay. It was very late last night...

Your PATH seems to be ok, so there must be an error on installation. 
Whats the output of
```
ls /opt/e17/bin
```



About TravMan63 suggestion. That sounds a little too radical and dangerous.
Why mix elive and ubuntu? There are e17 repos available for ubuntu, that should be safe.

Check this thread here:
[http://ubuntuforums.org/showthread.php?t=319336](http://ubuntuforums.org/showthread.php?t=319336)

---

### Post by RAV TUX on 2007-09-09
> **Rui Pais said:**
> Hi again RAV TUX, sorry the long delay. It was very late last night...

Your PATH seems to be ok, so there must be an error on installation. 
Whats the output of
```
ls /opt/e17/bin
```



Thanks again for the response Rui Pais, here's the requested output:

```
ls /opt/e17/bin
eet
```

---

### Post by Rui Pais on 2007-09-09
> **RAV TUX said:**
> Thanks again for the response Rui Pais, 
No problem, i'm glad if i can help :)

> here's the requested output:
```
ls /opt/e17/bin
eet
```
Ah, then you don't have a complete e17 installed yet.

The best option would be reinstall again (run script with -i flag)
removing any previously stalled installation with
```
sudo rm -rf /tmp/easy_e17
```
That should do the trick. 

Remember that to get a functional enlightenment script must run and finish at least till e package (from that one all are optional).

Good luck.



PS. Btw. I already made a thread with an updated how-to but it's still waiting the approval of a mod :)

---

### Post by RAV TUX on 2007-09-09
> **Rui Pais said:**
> 
```
sudo rm -rf /tmp/easy_e17
```That should do the trick. 

I tried running this script but it did nothing?

---

### Post by Rui Pais on 2007-09-10
uhmm... maybe reinstall process is conflicting with the semi installed e17. 
Try to start from fresh:
```
sudo rm -rf /opt/e17
sudo rm -rf /tmp/easy_e17*
```

and then again
```
sudo ./easy_e17.sh -i
```

if it fails, take note of the error output, please, to make it easy track down the issue.

Good luck

---

### Post by RAV TUX on 2007-09-10
> **Rui Pais said:**
> uhmm... maybe reinstall process is conflicting with the semi installed e17. 
Try to start from fresh:
```
sudo rm -rf /opt/e17
sudo rm -rf /tmp/easy_e17*
```and then again
```
sudo ./easy_e17.sh -i
```if it fails, take note of the error output, please, to make it easy track down the issue.

Good luck

At this point I am starting with a fresh install of Xubuntu.

Did they publish your e17 guide yet?

---

### Post by Rui Pais on 2007-09-11
hi again,
sorry things didn't go well first time. Hope installation will run better now.

My how-to it's still awaiting, but it boils down to what you already know (the old thread was not that obsolete...) 
Use the correct list of dependencies, and the correct exec for start it, like i mention on #481 post of old thread.

My focus on the updated how-to is to get carefully on what install. 
Thats what makes an installation of e17 more or less stable. A minimal e17 with a few modules is very stable, although the status of pre-alpha, while some e apps are very unstable or even non functional or partially functional only (file manager, login manager, etc.) 

If one are installing with another DE, like your case with xfce4, theres no reason to install those apps. Use xfce ones that are finished, tested and stable. 
And you even save time, cpu, internet connection and disc space.

You can tweak installed apps with an .easy_e17.conf file with a line containing --skip=appname1,appname2,... or pass that option on command line.
A minimal e17 is:
```
sudo ./easy_e17.sh -i --skip=emotion,entrance,eclair,evfs,edje_viewer,edje_editor,elicit,elitaire,emphasis,empower,engycad,entrance_edit_gui,entropy,ephoto,estickies,exhibit,expedite,extrackt,engage,enthrall,rage,scrot,alarm,bling,cpu,deskshow,emu,flame,forecasts,language,mail,mem,mixer,moon,net,news,photo,rain,screenshot,slideshow,snow,taskbar,tclock,uptime,weather,winselector,wlan

```
An e17 with extra modules could be:```

sudo ./easy_e17.sh -i --skip=emotion,entrance,eclair,evfs,edje_viewer,edje_editor,elicit,elitaire,emphasis,empower,engycad,entrance_edit_gui,entropy,ephoto,estickies,exhibit,expedite,extrackt,engage,enthrall,rage,emu,flame,moon,rain,snow
```

One can add after installed with one of those above, any other app or module later on, from an already running e17, keeping unstable stuff installation separated from main installation.

hth in someway.

---

### Post by Rui Pais on 2007-09-14
Hi RAV TUX, 
Sorry the double posting (and in a way the hijacking of your threads, since the old thread on cvs e17was closed and your last post there links here, people will most likely check it... i take the liberty of announce the new here, hoping you don't mind)

So how it goes. Did it run ok this time?

I have finally the updated thread, it's here:
[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

hope you find it useful.
Rui

---

### Post by RAV TUX on 2007-09-14
> **Rui Pais said:**
> Hi RAV TUX, 
Sorry the double posting (and in a way the hijacking of your threads, since the old thread on cvs e17was closed and your last post there links here, people will most likely check it... i take the liberty of announce the new here, hoping you don't mind)

So how it goes. Did it run ok this time?

I have finally the updated thread, it's here:
[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

hope you find it useful.
Rui

Thanks Rui Pais this will be very helpful for many people, I have made the choice to reinstall Elive Gem 1.0 with e17 by default and am quite happy overall with it. Again think you for all your help.

If anybody wants to try e17 in Elive Gem 1.0 you can download the live disk free at LinuxTracker [here]("http://linuxtracker.org/torrents-details.php?id=4333").

If you like e17 and/or Elive Gem 1.0 don't forget to donate to the project.

---

### Post by sweeney276 on 2008-03-15
Can someone help me before i throw caution to the winds and try a Kubuntu Gutsy amd64 installation?

I've always liked the Enlightenment window manager since I first discovered it (about 2000) and E17 looks quite stable, so has anyone got any information about using it with Kubuntu?

There is a distro, Granular Linux, which appears to bring together KDE and Enlightenment, if nothing seems to work, but I have lots of data backed up that's in my /home/graham/ directory, so how easy is it to install and retain my data?  Anyone know?  If not, I guess I'll have to reinstall data rather than directories :-(

Grateful for any help out there.....

---

### Post by Rui Pais on 2008-03-15
> **sweeney276 said:**
> Can someone help me before i throw caution to the winds and try a Kubuntu Gutsy amd64 installation?

I've always liked the Enlightenment window manager since I first discovered it (about 2000) and E17 looks quite stable, so has anyone got any information about using it with Kubuntu?

There is a distro, Granular Linux, which appears to bring together KDE and Enlightenment, if nothing seems to work, but I have lots of data backed up that's in my /home/graham/ directory, so how easy is it to install and retain my data?  Anyone know?  If not, I guess I'll have to reinstall data rather than directories :-(

Grateful for any help out there.....

Well most people simple use this method here:
[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

It usually works with any debian based distro, kubuntu included. Post there on any problem.

:)

Edit: 
and of course you have OzOS too, for an install from zero.

---

### Post by Rui Pais on 2008-03-15
Thanks too for the reference to Granular Linux. I didn't know that one.
Note that they don't "merge" KDE with E17. They simply offer both on same CD/DVD.


@RAV TUX
Well, I think we may need to add that one to distropedia and a reference on UEOSC page of cafelinux. :)

Rui

---

