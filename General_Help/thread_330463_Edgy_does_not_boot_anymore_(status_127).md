---
title: "Edgy does not boot anymore (status 127)"
date: 2007-01-03
forum: General Help
---

### Post by erdalronahi on 2007-01-03
Hi,

since today my edgy does not boot anymore. It stops after the filecheck (which is ok) with

```
init: rc-default process (####) terminated with status 127
```

with #### being something between 3800 and 4100.

The only change I made to the system was the installation of compiz 0.3.6 yesterday. So this may have caused the error.


How can I rescue my system? Single user boot does not help. I have an alternate CD, but do not exactly know what to do with it. 

Any help appreciated.

---

### Post by kthxbai2u on 2007-11-27
I have the exact same problem on my webserver!

It's not releated to compiz. Do you have a webserver on that box? I was looking in my active connections before it screwed up, and there was one on port 59003. I added that to block list, and tried to reboot/halt. It said reboot/halt commands were not found or whatever so I had to unplug it and plug it in again (my servers dont have power switches). When I did reboot it, I got that error message. I need ***URGENT*** help I have a site not being served!

Im going to try to reinstall just KDE and Gnome, see what happens.

I was going to write this fags IP down and hack his *** and make *HIS* life a living hell, but i forgot to write the IP and it coulda been a proxy anyways. Ill look for whatever program he installed and reverse engineer it :D

I did that with one other attacker, he tried to install a shell bot on my server through the PHP coding that he *thought* was buggy. When you mess with codinggroundz.com you mess with x-hacker kthxbai2u :) Well, not x-hacker, just a hacker for good purposes :) So anyways, I showed up in the muther ******* IRC channel. He banned my IP but I'm dynamic, as well as loaded with proxies and brainz :D I found a work around in his shellbot. It uses name based authentication, as well as when you query the bot its dumped into a terminal and the response is spit out to you. Nickserv on that server doesnt force you to identify, so you just ignore the messages asking you to identify.  and 
I still have to go back remove all his bots but thats for another day :D

---

### Post by kthxbai2u on 2008-01-16
Ok, no one has posted since I last posted? LOL thanks for the help :P


Since that post I have reinstalled and had another working server, and had the same issue occur using different steps to reproduce it. I didnt intentionally reproduce it, but whatever. It's still useful info.

Basically, the other day I reconfigured SSH and was wanting to restart the service. 

As of one of the ubuntu releases (possibly 7) they changed the way services are managed, started, and stopped. The switch was from the SysVInit to UpStart which is supposedly better. 

When I typed "sysvinit" in console to restart the SSH service, it said sysvinit was not installed. So, naturally I typed "apt-get install sysvinit".

Because of the facts that apt-get will resolve dependancies automatically, and alsp your system runs with UpStart (like mine if your > 7.10) it will automatically uninstall UpStart and start installing SysVInit.

Now, I saw this happening and thought "oh yeah I want to keep upstart" so I pressed CTRL + c. What can I say, I did this at the ***wrong*** time. I must have cancelled half way between the switch from UpStart to SysVInit. 

Now, I get that rc-default terminated message again. Same status code, different process number (obviously).

I havent tried yet, but there may be a simple fix. Im going to try to boot the live CD and reinstall upstart. Hopefully this will work. I cant get a shell even on the server and this is my main webserver. None of the services are being loaded because of this.


How I think this may be related to the initial post:

SysVInit could have been a requirement for compiz. Check compiz's dependancies. If it includes SysVInit, try either switching to SysVInit again after restoring the server or also try "beryl" i believe it does the same thing as compiz, but it may have UpStart as a requirement.

You can figure that out because I'm not needing the 3D desktop just yet. Ill keep you posted on my progress repairing this problem.

---

### Post by Comhra on 2008-01-16
Sounds to me like you're doing ok there, you don't need any help. ;)

---

### Post by kthxbai2u on 2008-01-16
nope, actually im doing horrible... Booting off the live CD and then reinstalling the packages doesnt work because its running of the RAMFS or w.e so your installing packages to the live cd kind of... they all will be lost when you reboot.

I got into a maintenance shell once as mentioned in [this thread]("http://ubuntuforums.org/showthread.php?p=4149008"), by accident, and i was able to start the apache2 and ssh process, but I rebooted (stupidly) and now I cant get back into the maintenance shell... Both grub menu options (normal boot and recovery) do not work, they give me the status 127 error mentioned above.

When I did get into maintenance shell, after starting those processes, I tried to reinstall UpStart. This did not solve the issue :(

---

### Post by kthxbai2u on 2008-01-16
OMFG OMFG OMFG OMFG THANK YOU SOOO MUCH !! Now I dont have to reinstall!

If the owner of the thread wants to try this fix (boot off live cd, and look for telinit - you can get copy from the live cd) and change the name of the thread to [SOLVED] that would be great!

I dont know how that file dissapeared... Would stopping half way through switching from upstart to sysvinit cause that? I dont know, but this solved my problem, good day to you sir!

---

