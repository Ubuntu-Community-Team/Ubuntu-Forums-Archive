---
title: "GeForce GTX 750: Trying to raise screen resolution past 1024x768"
date: 2015-01-20
forum: General Help
---

### Post by kade2 on 2015-01-20
So I've asked around superuser if there was a way to do it. I've seen threads that don't offer any help. I really want to get into linux for school because in less than 6 months I'm going into networking and I want the experience. So I removed my windows HDD and am going to muscle through the process of never using unbuntu besides for basic game servers. I want to use it every day until I start schooling.

So when I go into display settings it will not let me raise the res past 1024x768. I've had the problem before but I've never really cared to look into it. I hate how slim the screen is and it will kill me to use it like this. My monitor goes to 1680x1024 which is what I want to get it into if possible. Currently I'm running the latest version (14.4?) with nothing but flash installed. I tried to install nvidia drivers last night but I got stuck in a no gui login so I just decided to get a fresh install and ask a community that specializes in linux instead of just a general computer community.
This may be a very stupid question to some of you but any help is appreciated!

Edit: to anyone else looking for a fix for nvidia cards, all I had to do was update my kernel version to one supporting the build of my gpu. That's all I had to do!

---

### Post by mooreted on 2015-01-20
How did you install the Nvidia drivers?

Tap the Windows key on your keyboard and type the word "drivers". You will see "Additional Drivers" listed. This will allow you to install the Nvidia drivers the easy way.

---

### Post by kade2 on 2015-01-20
When I open additional drivers "No additional drivers avalable"

---

### Post by kade2 on 2015-01-20
When I open additional drivers "No additional drivers avalable" I've been installing it through apt-get before.
sorry for the double post.

---

### Post by Bashing-om on 2015-01-20
kade2; Hi ! Welcome to the forum .

Be aware here :
> 
This may be a very stupid question to some of you but any help is appreciated!

The only stupid question is the one that you do not ask !

To further our aid we need to know that hardware we are working with; to that end post the outputs - Between Code Tags - of terminal commands:
To get a terminal (Command Line Interface ) at your desktop key combo ctl+alt+t is the shortcut .
Provide:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
To even list (ls) the (h)ard(w)are (lshw) at the level we want to see it your user privileges need to be elevated - sudo == Super User DO . You will be asked for your password, enter the pass word you made when you installed the system - there will be no response to the screen when the pass word is entered - security measure - . Enter your password blindly and hit the enter key .
It will take a bit of time for the system to look up your hardware so be patient for the lshw command to complete and return to prompt .

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

With those commands:

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by kade2 on 2015-01-20
Thank you! Here are is the output of the first command
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750] [10de:1381] (rev a2)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3104]
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3104]


```
And the second:
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fd000000-fdffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:dc00(size=128) memory:fea00000-fea7ffff


```
I'm assuming since it says nvidia that the driver is present?

---

### Post by oldfred on 2015-01-20
The new Maxwell need newer kernels, support software & nVidia drivers than are in repository. 
Best to use ppa.

 Maxwell 750 - kernel 3.15 required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)
 open-source driver support for Maxwell, there's none right now, at least not mainline.  Feb 2014

   The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)

---

### Post by kade2 on 2015-01-20
I'm lost on how to follow this but I'll try to work it out. Thanks for helping!

---

### Post by Bashing-om on 2015-01-20
kade2; Well; well ...

Confirmed that your graphics card is the Nvidia GTX 750.
And no:
> 
I'm assuming since it says nvidia that the driver is present?

No driver is loaded per :
> 
configuration: latency=0

That line would have listed the driver also.

OK. the bad news (maybe); I am aware that there is no driver yet available for the Nvidia GTX 750ti - in our repository. Which would be a good reason that "Additional Drivers" can not find a driver. Your card may be in the same boat.

The good news :
a) A driver is available from  trusted PPAs :
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)

b) obtain the driver direct from Nvidia, with this caveat:
> 
As a GTX 750 owner myself, I prefer to trust the PPA. Why?

Well, using NVIDIA's excellent scripts is fine but you need to re-do things every time a new kernel comes down the pipe at you. With the PPA, no such problem.

Of course YMMV!


For instruction of installation ->
To cut to the heart of the matter, oldfred says it better than I can, and there is no point in reinventing his wheel; see:
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)


[INDENT][INDENT]bet ya come out
[INDENT][INDENT][INDENT]smelling like a rose
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kade2 on 2015-01-20
Ok so I got my kernel updated perfectly and the resolution is perfect I thank you both so much for the help. But with this upgrade my network says it's connected but there Is no connection. Is this a problem introduced through the update or my own network? Currently typing this from my laptop on the same network
also after the restart I noticed my static was set to my default gateway(whoops). I changed that before the update and forgot to validate so it bit me on the reboot and kicked everyone off the internet. Any ideas?
Edit:
The error it throws out is "connection actiactivation failed" "creating object path org/freedesktop/networkmanager/activeconnection/11 failed in libnm-glib"
So I'm assuming this is stemming from the update and not my own network.

edit: this was fixed by removing all the saved connection information through network manager Thanks for the help with getting my kernel updated guys! I really appreciate it

---

### Post by Bashing-om on 2015-01-20
kade2; Hoo Boy;

OK, glad ya got the resolution you desire .. For others benefit, please advise on your actions to reach resolution of the resolution.

Now, as to forum administration. Threads are like dead men, one to the box -> one problem 1 thread.
When this thread is 'solved' over and done with the originating situation, mark this thread 'solved'.
When you mark a thread solved it;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

 Any other condition open a new thread for that situation. This will give greater focus to those qualified in the area of your problem.
I will join you in that new thread. See what we can work out.

It is no big deal
[INDENT][INDENT][INDENT]it just helps to keep things simple
[/INDENT][/INDENT][/INDENT]

---

