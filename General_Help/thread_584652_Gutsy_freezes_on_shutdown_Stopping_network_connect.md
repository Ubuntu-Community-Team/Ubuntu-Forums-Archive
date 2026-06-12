---
title: "Gutsy freezes on shutdown: Stopping network connection manager NetworkManager"
date: 2007-10-21
forum: General Help
---

### Post by mchnhed on 2007-10-21
Ever since I upgraded to Gutsy Gibbon, every time I shut down now I keep getting this weird error message that holds the entire system:

"Stopping network connection manager NetworkManager"

This message comes up after x shuts down and it's just showing the console messages...

 :confused:    Any ideas?

---

### Post by Difushion on 2007-10-22
The same is happening here. I'm using a 3com usb wireless connection.

---

### Post by Dimitriid on 2007-10-23
Saw it too. I saw it posts from 2 weeks ago so apparently it was not important enough to get it fixed :mad:

---

### Post by Dimitriid on 2007-10-23
bump

This is serious and if systems cannot shut down it can eventually damage hard drives why nobody has a clue?

---

### Post by mchnhed on 2007-10-23
Yeah this is definitely a serious problem. It freezes even when I have the network cable plugged in! :confused:  :(

---

### Post by DavyDuke17 on 2007-10-23
I get messages about network manager and it freezes when I shutdown as well. The messages are not always the same, but they always relate to network manager.

---

### Post by Dimitriid on 2007-10-23
Its  wicd in Gutsy repositories? A temporal solution ( i imagine ) would be to just outright remove network manager and use wicd.

---

### Post by funkythumb on 2007-10-23
Same problem on my Dell laptops. I have D600 and D400 laptops, and they all do the same thing. One of my D600 was a Gutsy Tribe 5 install that I've been upgrading through the final release. There was a period between updates where it was an issue, then fixed, then came back again.

The final release has this problem on my systems. I have a fresh install of Gutsy on another laptop, and a fresh install of Ubuntu Studio 7.10 on yet another, and they all hang at the same place - just as described by previous posters.

I just downloaded Xubuntu, and going to install it on a Dell L400 laptop. It'll be interesting to see if the same thing happens. I might also install Kubuntu on one of the other laptops to see if it happens there...

:guitar:

---

### Post by rfaull on 2007-10-24
I have a similar problem on a Dell 6400, but it eventually shutdown after a minute or two delay (sometimes it shutsdown without delay, I can't pick a pattern). 

My Dell M1210 works flawlessly.

---

### Post by fedleo on 2007-10-25
Up.
Same here with my old C400 but just if I use a wired connection: wifi work fine on shutdown sequence.

---

### Post by yonexFactory on 2007-10-25
I have this problem too... I tried logging out and then shutting down from the log-out screen and that seemed to work. But hopefully that can just be a temporary solution.

---

### Post by sgornick on 2007-10-25
**This post could be related to an Ubuntu bug filed at**: 156490 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				May be related to Bug #156490.

---

### Post by rfaull on 2007-10-26
Try using wicd -- works for me

---

### Post by rfaull on 2007-10-26
Try using wicd -- works for me

---

### Post by mchnhed on 2007-10-26
> **sgornick said:**
> **This post could be related to an Ubuntu bug filed at**: 156490 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				May be related to Bug #156490.



Yes, that is exactly the problem. I would much rather just do what yonexFactory suggested, rather than have to install a new network manager (wicd), as suggested by rfaull. We shouldn't run away from the problem, but rather, search for a way to solve it. The only thing is that I am a relatively new Linux user, and wouldn't even know where to start in solving this one...

Hopefully the developers/hackers figure something out soon!

---

### Post by GoodPanos on 2007-10-26
> I would much rather just do what yonexFactory suggested, rather than have to install a new network manager (wicd), as suggested by rfaull. We shouldn't run away from the problem, but rather, search for a way to solve it.
I agree with mchnhed too.

But, I am curious what is wicd?  How does it work?  Does it work better than NetworkManager?

---

### Post by Dimitriid on 2007-10-26
wicd its another network manager, it actually replaces network manager and gnome network manager ( the gnome frontend ubuntu uses by default ). For me in gutsy, synaptic automatically prompted for removal of network manager after installation so its a fairly simple process: use wicd gutsy repository, add it to session start up and restart. 

Many people have reported better functionality for wireless connections than network manager. I think it also supports more wireless features by default. On the other hand, it seems to take an awfully long time to start when I boot my system, and its icon keeps saying "not connected" even long after its successfully connected and then the Icon decided to cooperate on its own after 10 minutes. I suspect integration with the gnome panels its whats causing the behavior but not sure.

---

### Post by zeddock on 2007-10-26
> **mchnhed said:**
> Yes, that is exactly the problem. I would much rather just do what yonexFactory suggested, rather than have to install a new network manager (wicd), as suggested by rfaull. We shouldn't run away from the problem, but rather, search for a way to solve it. The only thing is that I am a relatively new Linux user, and wouldn't even know where to start in solving this one...

Hopefully the developers/hackers figure something out soon!

~~~
EDIT: Note!  I tried the install right after the post and Gnome network-manager is so screwed up, that the install failed because the uninstall of n-m hung.  The good thing is that I did a reboot then attempted again and all went well.  Even with this install glitch I still am going to encourage the use of wicd.   Once n-m was out of the way wicd was was very stable... and usable!

One other thing... in the time since I left wicd on Feisty to do beta tests of Gusty, wicd has had even more updates! I am even more impressed.  Good luck to you all.
~~~

You know... I would like to have networking issues through n-m solved too, but they are NOT getting solved.

n-m acts intermittently to do its job and often reports status in error.  I tried wicd and it seems to do a better job.

I am becoming less new than I once was on Linux and have great news for you...
Changing out the networking manager under Ubuntu is so simple a caveman could ... Well, you get the idea.
Use Synaptic Package Manager or Add/Remove.
Do a search on wicd.  If it is not there it is because it is not yet in the repositories which you have enabled.  No problem, just go to the wicd page... 
[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")
Wow! That page really tells how to do it better than I ever could. Just follow the directions.

zeddock

---

### Post by Dimitriid on 2007-10-26
So simple network manager wont uninstall correctly? I had the exact same problem. 

Besides we all know cavemen use Apple  :lolflag:

---

### Post by unebaguettesvp on 2007-10-26
i'm having the same problem!!!!

---

### Post by GoodPanos on 2007-10-27
I don't like this wishy washy stuff [-X

Does it install smoothly or not?  If I decide to go back to NetworkManager, is it possible and how?

---

### Post by Dimitriid on 2007-10-27
> **GoodPanos said:**
> I don't like this wishy washy stuff [-X

Does it install smoothly or not?  If I decide to go back to NetworkManager, is it possible and how?

wicd installs smoothly. Network Manager might not uninstall smoothly. Cant comment on going back to network manager but installing the whole os would put it back in its place.

And i definitely think that network manager is a lot more "wishy washy" right now than wicd.

---

### Post by rfaull on 2007-10-27
I agree that it would be great to have NM work without issues (it did in Feisty). Until this issue is resolved, I'm going with wicd -- it's stable and just WORKS. wicd now working on my Dell 6400 and M1210. BTW 

The Ubuntu team have done a great job, everything else works, out of the box.

---

### Post by DavyDuke17 on 2007-10-29
I simply cannot run network-manager if it cannot shutdown correctly and I see no solutions so I tried to switch to wicd, however, like other people have noted I am having problems uninstalling network-manager. Everytime I try to uninstall it through synaptic it says that it is stopping network-manager and it just freezes there. However, it doesn't even seem like network-manager is even running anymore. Any advice on how to uninstall it?

---

### Post by Rob2687 on 2007-10-31
This started happening for me ever since I installed Madwifi SVN. The problem went away when I went back to the driver from the restricted drivers package.
It sucks because I have problems connecting to my home network with the version from the repos.

---

### Post by DavyDuke17 on 2007-11-01
Any help at uninstalling network-manager? Synaptic uninstalled network-manager-gnome fine but it still cannot uninstall network-manager, it just hangs up when it says stopping network-manager. Can't install wicd because it tries to uninstall network-manager first.

---

### Post by zeddock on 2007-11-01
> **DavyDuke17 said:**
> Any help at uninstalling network-manager? Synaptic uninstalled network-manager-gnome fine but it still cannot uninstall network-manager, it just hangs up when it says stopping network-manager. Can't install wicd because it tries to uninstall network-manager first.

I am still considered a noob so take this with salt!

Try to boot into a "safe" mode by way of the login screen.  You will see options down to the left of where you login.

... You know what... Let me test this first. be right back...

zeddock

Here are the steps:

First... 
===if it is just hanging as you descibe above, try to go into the Monitor, (System / Administration / System Monitor) Sort by CPU%, and try to find the process for anything network manager, or gnome network manager related.  AND KILL IT, by right clicking on the process and selecting Kill.

Now try the install again of wicd. (I tried to install via just clicking on the .deb file.  If you are in Synaptic doing this install, I am unsure of those steps.)
Now try steps 1, 2, and 3. Reboot, and if it is not working, go down through the remainder of this post.

  Open Terminal:
  Applications / Accessories / Terminal

One line at a time enter these, excluding the number, and hit Enter:
1.  sudo apt-get update
2.  sudo apt-get install ubuntu-desktop gdm
3.  sudo /etc/init.d/gdm start
(This is supposed to make sure that your Gnome Desktop is not hosed from the partial uninstall.)
===

Second...

Reboot
At login screen look to lower left
Click Options / Select Sessions / Failsafe Gnome
Click Change Sessions button
give username
give password
Enter and OK to the notice of Failsafe

Allow the OS to fully boot... go get some tea and a cookie, but let it go....

Click:
System / Administration / Synaptic
At lower left click:
Custom Filters
Click "Broken" at top left
If you see any entries, try to resolve them.  If n-m is there, completely remove it, if possible.

Now, Close Synaptic and try to install wicd.

Open Terminal:
  Applications / Accessories / Terminal

One line at a time enter these and hit Enter:
1.
sudo apt-get update
2.
sudo apt-get install ubuntu-desktop gdm
3.
sudo /etc/init.d/gdm start

This is supposed to make sure that your Gnome Desktop is not hosed from the partial uninstall.

Hope these things help you until some other, much more knowledgeable person tries to help you.

zeddock

---

### Post by GoodPanos on 2007-11-04
Well, I got news for all of you.

Maybe the NM shutdown issue is somehow related with the graphics card?

I have a Dell Inspiron 8500 with an nVidia card.  I made some changes to get suspend to work see [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend"), and since then my notebook shuts normal!

Now, there have been a few updates for Ubuntu since then, so I am not 100% sure that is what fixed it.

But anyways I am a happy camper now and I don't have to remove NetworkManager.  :)

---

### Post by #Reistlehr- on 2007-11-04
GoodPanos: Are you using the restricted nvidia drivers?

---

### Post by cegpope on 2007-11-05
I just made the switch to Ubuntu ~5 days ago and was having this same problem, the solution I found while googling the issue resulted in the following temp fix for an older version of Ubuntu, but it worked for me with Gutsy, so you could always give it a try.


> Run the following to open the file with read/write permissions: gksudo gedit /boot/grub/menu.lst
Look for the kernel you're running. Mine looks something like this (on Dapper):

title Ubuntu, kernel 2.6.15-27-k7
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-k7
savedefault
boot

Add acpi=force to the kernel line, so it looks like this:
kernel /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda5 ro quiet splash acpi=force


---

### Post by GoodPanos on 2007-11-06
> GoodPanos: Are you using the restricted nvidia drivers?
Yes I am.

I want to add that I set up another notebook with Gutsy and this one with an Intel card and I am not having this issue.  So maybe the updates have corrected this problem?  In any case if you try my solution you will at least make your notebook suspend properly (assuming it never worked :mrgreen:).

---

### Post by markdjones82 on 2007-11-06
I am having the same issue.  It only happened after I installed the restricted wireless drivers.  After I uninstalled the drivers, I still receive the same error.  So, I take it there is no solution other than changing network manager?  You'd think they would have a security update by now.

---

### Post by AKoine on 2007-11-09
Hi all,

This did not solve my problem : when I do this, just like when I install wicd and remove nm, I get a blinking underscore at the end of the shutdown sequence instead of the errors messages ... And my pc won't shutdown ...

Any idea ? This is becoming to be REALLY annoying ... :)

Cheers

---

### Post by ThinkDave on 2007-11-10
I agree i had the same experience it may be another process stalling the shutdown but not ouputting any error messages. When i first updated to gutsy it didn't do this it seems to be from an update or a program i have installed afterwards. Any way to see what happened in the last shutdown?
-Dave

---

### Post by dingansich on 2007-11-13
Just to throw my 2 cents in.  I am having the same problem, but it has persisted even after dumping NM in favour of Wicd!  Originally I had problems getting my networking to work (Linksys WUSB54Gv4) and had to use ndiswrapper to load windows drivers.  I also switched over to Wicd.  Now the networking works more-or-less but hangs occassionally.  When this happens GDM seems to become unresponsive, and I can't reboot the machine.  I've been looking for days, but can't find a fix.

---

### Post by dangermouse28 on 2007-11-13
Dunno if this will help anyone but here's my experience with Gutsy.

I have a laptop so I fresh installed from the Alternative CD as I wanted encryption - seems like a good idea for a laptop. I had so many problems (very slow boot, sluggish performance, wouldn't shut down) in desperation I tried another fresh install using the live CD. No encryption but all my other problems have gone away!

There are BIG differences in the two installations - the installation from the Alternative CD immediately wanted loads of updates but the live CD didn't need any. It's like a Beta release. The only thing which worked with the alternative installation but not with the live CD are the Suspend and Hibernate functions. Worked perfectly with the crap installation but not at all with the good one](*,)

---

### Post by ThinkDave on 2007-11-13
> **dangermouse28 said:**
> Dunno if this will help anyone but here's my experience with Gutsy.

I have a laptop so I fresh installed from the Alternative CD as I wanted encryption - seems like a good idea for a laptop. I had so many problems (very slow boot, sluggish performance, wouldn't shut down) in desperation I tried another fresh install using the live CD. No encryption but all my other problems have gone away!

There are BIG differences in the two installations - the installation from the Alternative CD immediately wanted loads of updates but the live CD didn't need any. It's like a Beta release. The only thing which worked with the alternative installation but not with the live CD are the Suspend and Hibernate functions. Worked perfectly with the crap installation but not at all with the good one](*,)

Hmm well i was forced to use the alternate install as the live cd would not work... you may be correct with that one.

---

### Post by AKoine on 2007-11-14
Here is a workaround I found on launchpad, i worked for me :

> Released Gutsy Ubuntu 7.10 still hangs on shutdown on this computer. Here's the old workaround from Feisty from 6 months ago:

Do ```
 sudo gedit /etc/modules 
``` Add the following line, then save:
apm power_off=1
do ```
sudo gedit /boot/grub/menu.lst 
``` (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Restart. 

It worked for me. My computer is a Desktop. I don't know precisely what ACPI and APM are about (only that they deal with power management). Since I've done the thing written above, I haven't noticed any side effect. But that might be a bit different on a laptop, with the "standby", "hibernate", etc. options ...

Hope this'll help,

Cheers

---

### Post by mchnhed on 2007-11-20
OK that sounds alright... except that you don't exactly know exactly what ACPI and APM are for! At this point I'm rather apprehensive to try it out cause I have a laptop... anyone else wanna try and then test the hibernate/standby/shutdown functions? Or, anyone know of a solid fix for this? The problem is still persistent. I have submitted as a bug, but nothing has been released yet to fix it... :(

---

### Post by zemitras on 2007-11-26
No news about this?

It would be great to have this annoying bug solved..I I love having ubuntu in my laptop, but seems to me that in the meantime I'm going back to 7.04 :S

Best Regards

---

### Post by funkythumb on 2007-11-30
It does seem to be related to wireless... I disabled the wireless MiniPCI card in the BIOS on two different Dell laptops (but with the same wireless cards) and both Gutsy systems shutdown clean.

---

### Post by ladube on 2007-12-02
Same here on my Dell 5100 with a 3Com PCMCIA Wi-fi card.

Was working fine on Feisty. I should have stayed on this version instead of moving to Gusty. Hope it will get solved in the next updates...

---

### Post by thegrimgod on 2007-12-04
Well i kinda fixed suspend with the beta drivers from Nvidia for my 8600GT , now it does wake up , and sleep , but when it does wake up, wireless falls apart , i dont even have wlan0 listed anymore in n-m, the only solution is a reboot , so suspend is so far useless, im better off shutting down

---

### Post by drum on 2007-12-05
Same shutdown problem with 7.10 on my IBM T43 but NOT on my Lenovo 3000 N100
Both using wireless.
I have to do a hard shutdown every time.
Any news on this problem yet?
Thanks

:confused:

Edit: Both using same settings in composite

---

### Post by tiepolo on 2007-12-09
exactly the same problem

not using network manager (purged)

using wi-fi with rt2500 with driver compiled 

same configuration work on feisty, dapper, etc.

---

### Post by pd77 on 2007-12-10
I can reproduce this on a Debian Lenny system that is connected to the network via a Longshine USB adapter (Zydas 1211 chip). The system hangs on shutdown at "stopping network manager", then continues after about ~2 minutes and displaying a timeout message, only to hang again (and forever) at "shutting down network interfaces".

This machine ran fine for about 10 weeks since it was installed. I think, the troubles started about the time when kernel was updated to 2.6.22 (was 2.6.21 before). I'm back on 2.6.21 now since last weekend and so far I had no freezes on shutdown anymore.

---

### Post by onyxrev on 2007-12-20
I'm having the same problem with Gutsy on my 2nd Gen.  Macbook.  It really looks like it's madwifi related.  Going to try the ACPI/APM fix.

---

### Post by Lhorz on 2008-01-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having this problem too.

The workarounds having to do with editing /boot/grub/menu.lst
didn't work for me.

The workaround suggested by Dimitriid (uninstall network manager, install wicd)
solved the power down problem.  (Thanks Dimitriid)

Unfortunately, wicd is sub-optimal for me as I am using a wired network &
wicd appears to be optimized for wireless.

I've submitted this problem as an ubuntu bug report here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568)

with luck, they'll patch network-manager.

---

### Post by maddentim on 2008-01-16
So, I was having this problem too.  I had upgraded from 7.04 to Gutsy.  It didn't happen right away following the upgrade but started later.  Recently I saw a blog post from Russell Beattie ([http://www.russellbeattie.com/blog/cleaned-out-my-linux-home-directory]("http://www.russellbeattie.com/blog/cleaned-out-my-linux-home-directory")) which suggested I recreate my home directory fresh and I would clear up problems.  I have to say, it fix a bunch of idiosyncrasies in my system.  I had upgraded it and tweaked it to no end.  Many things were just not right.  Basically, I just did:

```

$ mv homedir homedirold
$ mkdir home
``` 

I then logged out and back in, and ubuntu rebuilt me a fresh desktop.  I could then just copy over the files I wanted from the old directory.  I purposely left most of the old hidden configuration directories in the old directory, let ubuntu recreate them.  For stuff that worked well and would have been a pain  to recreate, I copied them over.  It took a little longer than I expected, but in the end, very much worth it.

The short of it is, this particular network shutdown problem is gone! (knock on wood)  So, give it a try.  If you just leave your old home directory intact, it is a snap to back.  Just do the opposite (basically).

---

### Post by stream303 on 2008-01-22
Not only did I have this same problem on shutdown with my G4 iBook, but NM was tying up 100% of my resources as shown by top.

At first I just removed the package with synaptic, but since learned that is not the way to do it.

I followed these instructions on just disabling it, rather than removing it, and no problems so far.  I'm not using wireless anyway...

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by freeatlast on 2008-01-24
I have the same problem, ubuntu gutsy 7.1 hangs on shut down/restart.  if i reboot from the terminal sometimes it works, sometimes i get the similar error messages pointing to network manager.  I have a hunch, but dont know how to fix it (i've only been at this 4 days)  

when i run iwconfig, my wireless shows up as eth1.  could it be somewhere it is looking for it to be called wlan0, and this is the source of the hangup?

i was fiddling with ndiswrapper trying to get my broadcom to work, then finally installed the firmware and it works fine now.  i tried the fix about uninstalling nm and reinstalling it.  this worked, but disabled my wireless, when i reenabled my wireless (i had to remove and reinstall the firmware) the problem showed up again.  so it could be firmware related, but also the wlan0 vs eth1 pops to mind.

---

### Post by Lhorz on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ubuntu has confirmed this problem as a bug.  The URL to the bug report is here
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568)

Note that this bug has been marked a duplicate of another bug here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/156490](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/156490)

I've referenced but 183568 first because I lodged it, and because the thread for that bug supplies a workaround.  Here's the workaround supplied by Martin Fuzzey on 11.2.08
>>>>>>>>>>>>>>>>>>>>>>>>>



The problem appears to be caused when network manager catches the SIGTERM (15) signal
I have a workaround involving hard killing network manager with SIGKILL:

Modify /etc/dbus-1/event.d/25NetworkManager as follows (just add the --signal 9 option)

d_stop() {
        # Modified MF 11 Feb 2008 To avoid NM hang
        #start-stop-daemon --stop --retry 60 --quiet --pidfile $PIDFILE \
        # --oknodo --user $USER --exec $DAEMON

        start-stop-daemon --stop --signal 9 --retry 60 --quiet --pidfile $PIDFILE \
                 --oknodo --user $USER --exec $DAEMON
}

Modify /etc/init.d/sendsigs as follows
...
        # Kill all processes.
        log_action_begin_msg "Terminating all remaining processes"

        # Added MF 11 Feb 2008 To avoid shutdown hang
        OMITNM=
        if [ -f /var/run/NetworkManager/NetworkManager.pid ]; then
                OMITNM=$(cat /var/run/NetworkManager/NetworkManager.pid)
                OMITNM="-o $OMITNM"
        fi
        echo "Not killing $OMITNM"

        killall5 -15 $OMITPIDS $OMITNM

        # END MF mods
        log_action_end_msg 0
...

>>>>>>>>>>>>>>>>>>>>>>>>>>>>

I have implemented the workaround on my machine and confirmed that it is effective in eliminating the OS hang on restart.

-Larry

---

