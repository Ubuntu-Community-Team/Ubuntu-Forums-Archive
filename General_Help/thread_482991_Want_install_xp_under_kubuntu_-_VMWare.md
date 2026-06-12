---
title: "Want install xp under kubuntu - VMWare ?"
date: 2007-06-24
forum: General Help
---

### Post by AflingZ on 2007-06-24
Hey.

Just installed kubuntu (7.04), and now I want XP under.

But how? Should I use VMWare Server? Read something about it, but I'm pretty lost..

My needs:
To have a computer with linux and have xp under it, and should have access to each other, so I can move files to the fake "xp harddrive" in linux, and have network to my other computer over network.

I have 2 netcards in my computer, one for internet, one for home network, so I would also like to move files to my other computer.. 

I'm pretty lost in all these things.. Can somebody help?

Ask, if U need more info :)

---

### Post by aktiwers on 2007-06-24
Hi AflingZ ;)
>  My needs:
To have a computer with linux and have xp under it, and should have access to each other, so I can move files to the fake "xp harddrive" in linux, and have network to my other computer over network.


This can be done in many ways.. but its true that Vmware is a good solution.
Here is a quick and easy guide on howto set up Vmware with Windows XP:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

To share files between Ubuntu and your Virtual Hard drive you simply do as you normally would. Create a network share between Ubuntu and WindowsXP. With Samba.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

Sorry I didn't reply on your PM, I have been away for some days (i Sommerhus ;) )

Let me know how it goes :)

---

### Post by juanvicfer on 2007-06-24
You are right, VMWare is a good solution, I think that you will need to install VMWare Server and all the dependencies (it's done automatically with the "Add programs" application). I did so and everything worked ok.
However, you should know that there are some other free alternatives to VMWare, as an example, Virtual Box.
If you have trouble, post a reply

Good Luck!

---

### Post by mdurham on 2007-06-24
VirtualBox seemed easier than Vmware for me, give it a try.
Cheers, Mike

---

### Post by AflingZ on 2007-06-26
okay, thx for answers ! I will check it out later :) and write back ;)

---

### Post by AflingZ on 2007-07-06
So.. I have checked the guide, but it is not for Feisty Fawn? Can I still use it then? As Edgy, Dapper or Breezy?

---

### Post by dabl on 2007-07-06
To run a Win XP window and apps within (K)Ubuntu, you only need VMWare Player.  The current version is 2.0 (free as in beer).  Once you have it installed, you can get a decent pre-built XP "machine" here:

[http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model](http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model)

There are instructions for installing it there.  You will need a real Win XP installation CD and key to install it.  You might have to fiddle around with the CD ROM device number, and turn on USB -- but any noob can figure it out.

:)

---

### Post by AflingZ on 2007-07-06
hmm looks complicated, and I also got some errors "mkdir /faked_windoze && chmod 777 /faked_windoze"

Just want answer on my question please :):

I have checked the guide, but it is not for Feisty Fawn? Can I still use it then? As Edgy, Dapper or Breezy?

---

### Post by mysticrider92 on 2007-07-06
The mkdir error will occur because you need root access to make that folder.

Typically, Edgy or older programs must be ported to Feisty, and most often the package won't work. The guide should work fine, but the program itself has to be made for Feisty. 

Also, vmware-player is listed in my Synaptic, maybe you just need to enable the other repos?

---

### Post by dabl on 2007-07-06
Mystic is correct, the command needs to be _sudo_ mkdir ....

YES -- any instruction regarding VMWare that works on Edgy will also work on Feisty.  :)

---

### Post by AflingZ on 2007-07-07
well, I did use sudo the first time, and if I try the command "sudo mkdir /faked_windoze && chmod 777 /faked_windoze" again, it says it already exists :)

but now, when I write "tar -zxf WinXPpro.tar -C /faked_windoze", it says:
gzip: stdin: not in gzip format
tar: Child returned status 1
and a danish line (because I'm danish ;)):
tar: Udsat fejll-afslutning som resultat af tidligere fejl

and yes, I downloaded the file WinXPPro.tar from the site, as the guide says I should..

and the other app, VmWare Server, its like Edgy, well can I use that guide then, or should I continue with VmPlayer? I see that VmWare Server before was shareware, but now free? So it should be better than VmPlayer or what? :)

---

### Post by aktiwers on 2007-07-08
Hi AflingZ,

Im not familiar with those steps? Why are you trying to make a folder called Faked_windoze ?

Simply follow this guide:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

And XP should be running on your Vmware server fast! I have used it many times and it works great!

You can  then also install other OS's like Vista or whatever you like.

Just remember to install the Vmware tools like the end of the guide explains.. Really, it does speed up the whole thing!

Good luck :)

---

### Post by AflingZ on 2007-07-09
hehe well, it was because some others said I should use VM Player thing.. hmm.. I will try UR guide tomorrow again then .. :)

Also remember to read my older posts in this thread, aktiwers! ;)

---

### Post by AflingZ on 2007-07-10
now, I get this error, when I try to install VMWare Server:
"A previous installation of VMware software has been detected.

Failure

Execution aborted."

Maybe because I before tried to install vmware player thing? anyways I think I uninstalled it, in adept_installer . Hmm..

Also I tried the samba to connect to other computer on the network, but no success.. Windows just says it couldn't find the place.. Also the guide just say "\\Dapper\Myfiles", and I don't understand why it should be myfiles? Aktiwers forklar.. ;)

---

### Post by aktiwers on 2007-07-10
Hi again,

Okay, this shouldn't be much hassle really.. I think we need to uninstall the installation of the Vmware player.

Try this command:
```

sudo apt-get remove vmware-player

```Also remember to delete that folder you created:
```
sudo rm -rf /faked_windoze
```Then try to follow that guide again :)
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

Then we do the network afterwords..  but keep in mind I dont have 
any experience making network between Windows and Ubuntu, as I dont 
use Windows.

But I guess we can get it to work anyways :)

Let me know how it goes ;)

---

