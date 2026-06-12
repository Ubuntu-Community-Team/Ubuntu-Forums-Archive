---
title: "Ubuntu's Firewall"
date: 2007-07-13
forum: General Help
---

### Post by Graham1 on 2007-07-13
Hi Guys

Just wanted to check :). Does Ubuntu come with a built-in firewall by default? I couldn't find a firewall option within the menu's so wasn't sure. I've installed Firestarter (just in case) but if a firewall (i.e iptables) is already installed, do I just use Firestarter to create rules?

:)

---

### Post by disturbedite on 2007-07-13
the linux kernel has a built-in network framework called netfilter.  part of it contains the [firewall]("http://en.wikipedia.org/wiki/Iptables"), so a frontend isn't necessarily needed, unless you want one.

---

### Post by Graham1 on 2007-07-13
So if I needed to add some rules, I would need a frontend or could this be done with the existing setup?

:)

---

### Post by sam0t on 2007-07-13
If you want add firewall rules easily I would suggest you install Firestarter. Its a easy GUI firewall and from what I have gathered, pretty good also. Either install it through synaptic packet manager or with a command to terminal:

$ sudo apt-get firestarter

Not using Ubuntu right now, but Iam pretty sure thats how the terminal command went, anyways firestarter is recomended firewall for Ubuntu and seems to be pretty solid. I have one question how do I make Firestarter load as default when I reboot my machine?

edit:

Sorry for reading your post so hastily, I see you have alrdy installed firestarter. I have just added needed rules to Firestarter and everything seems to be working ok, but then again Iam a Linux newbie also :)

---

### Post by Elijah on 2007-07-13
> **sam0t said:**
> If you want add firewall rules easily I would suggest you install Firestarter. Its a easy GUI firewall and from what I have gathered, pretty good also. Either install it through synaptic packet manager or with a command to terminal:

$ sudo apt-get firestarter

Not using Ubuntu right now, but Iam pretty sure thats how the terminal command went, anyways firestarter is recomended firewall for Ubuntu and seems to be pretty solid. I have one question how do I make Firestarter load as default when I reboot my machine?

edit:

Sorry for reading your post so hastily, I see you have alrdy installed firestarter. I have just added needed rules to Firestarter and everything seems to be working ok, but then again Iam a Linux newbie also :)

That one is answered in the faq's
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

as for Graham1's question, yes you can set one up manually by making your own script and iptables ... but it'll be easier with a frontend if you don't have the time.

---

### Post by deepclutch on 2007-07-13
make sure you installed lokkit.that is enough.dont go for colors(aka firestarter etc)

---

### Post by sam0t on 2007-07-13
> **Elijah said:**
> That one is answered in the faq's
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)


Thanks for that, sometimes the answer is too obvious :D

---

### Post by mcduck on 2007-07-13
> **sam0t said:**
> Thanks for that, sometimes the answer is too obvious :D

Keep in mind that Firestarter is just a tool for configuring the firewall, so you don't need to have it running all the time to have a working firewall..

---

### Post by disturbedite on 2007-07-13
yeah, to clarify, you can configure the "firewall" by command line, with scripts, or a frontend.

---

### Post by sam0t on 2007-07-14
Thats good info, Iam pretty intrested in learning the terminal way of doing things in ubuntu/linux. I would be most thankfull if you could post a link to a site which explains how to  configure the linux firewall from terminal, assuming a site like that exists :)

> Keep in mind that Firestarter is just a tool for configuring the firewall, so you don't need to have it running all the time to have a working firewall..

Thanks for the info! I have been starting firestarter on every reboot in fear of invasion. Like I said above, Iam very intrested in terminal way of doing things, could you guys tell me where I can check my new firestarter rules in terminal view?

---

### Post by marsbt on 2007-07-14
To see all your IP packet filter rules you can use the following command:
> iptables -nvL

---

### Post by Bloke on 2007-07-14
Ubuntu's firewall is OFF by default which allows all traffic. This is BAD.

You'll want to install a frontend, or certainly manually configure iptables. I use Firestarter. Launching Firestarter for the first time enables the firewall (for the current session). I tested if rules stuck by using "sudo iptables -nvL" prior to reboot, and again when the system was back up, and they do not. I think scripts can be created to ensure rules are restarted after a power cycle. 

Read something about it all:

Ubuntu: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Firestarter: [http://www.fs-security.com/](http://www.fs-security.com/)

iptables: [http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html](http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html)

---

### Post by deepclutch on 2007-07-15
why the pain?Like fedora,install and enable[COLOR=Indigo]** lokkit**[/COLOR] by default.simple

---

### Post by eentonig on 2007-07-15
> **Bloke said:**
> Ubuntu's firewall is OFF by default which allows all traffic. This is BAD.

...]

I fail to see why. By default, there is nothing to connect to. So your Firewall will be a redundant ressource consumer.

As soon as you start to open services on your computer (ssh, http, samba, ...) I can only see a justifiable reason to use it, if you use it in conjunction with an IDS system that can manage it.

Why?
- If you open a service, you want it to be reachable. so you're not going to configure your firwall to block connections. Unless you know from which ip address you'll always connect, you'll leave it open to the world.
- If you only want local access. Chances are big you're behind a router with NAT. so internet wont be able to connect by default.
- IDS will monitor traffic and detect if someone is trying to breach you server. In that case, it will create dynamically a new rule to block connections from that IP. No way you can manually keep up with that.
- In the mean time, all other unused service ports are still dead, so nobody can use them to hack your system.

Personal conclusion:
For home linux use, a firewall and virusscanner are redundant unless you have a specific setup (ie. ssh server running on the internet that you want to protect against hacking).

PS. As soon as you start opening services on your systems, One must assume to be aware of security concerns and usefull protective measures.

---

### Post by mcduck on 2007-07-15
> **sam0t said:**
> Thanks for the info! I have been starting firestarter on every reboot in fear of invasion. Like I said above, Iam very intrested in terminal way of doing things, could you guys tell me where I can check my new firestarter rules in terminal view?
If you go to System/Help and Support, and search for "iptables" you'll find "Linux Packet Fitering HOWTO".

While not really suitable for those scared of technical stuff and using command line, it's a great read if you want to build your own firewall by hand.

---

### Post by SuSUntu on 2007-07-15
> **Bloke said:**
> 
You'll want to install a frontend, or certainly manually configure iptables. I use Firestarter. Launching Firestarter for the first time enables the firewall (for the current session). I tested if rules stuck by using "sudo iptables -nvL" prior to reboot, and again when the system was back up, and they do not. I think scripts can be created to ensure rules are restarted after a power cycle. 


Are you saying that if you set rules with Firestarter (in effect, editing iptables), that when you reboot, the rules you added / edited are no longer in iptables?

This is not my experience, nor is it my understanding of how Firestarter's relationship with iptables works. I actually don't even keep Firestarter running (not in the background or otherwise) ... I only start it up to edit rules when necessary, and the rules I create / edit are there even after reboots.

Maybe I'm misunderstanding you.

---

### Post by sam0t on 2007-07-16
I too tested "sudo iptables -nvL" after a reboot and indeed the output is quite different before and after you start firestarter, so maybe somebody could clear that up.

One other thing, I followed this FAQ: [http://www.fs-security.com/docs/faq.php]("http://www.fs-security.com/docs/faq.php")

And succesfully edited my sudoers list with visudo commane and overwrited the file. With just the problem that, when I do actually start firestarter it still asks for the password. Note I did notice that firestarter tryes to launch itself from /etc/sbin location and changed it to the sudoers list. Has anything changed in Feisty so that the FAQ tip no longer works?

---

### Post by mcduck on 2007-07-16
> **SuSUntu said:**
> Are you saying that if you set rules with Firestarter (in effect, editing iptables), that when you reboot, the rules you added / edited are no longer in iptables?

This is not my experience, nor is it my understanding of how Firestarter's relationship with iptables works. I actually don't even keep Firestarter running (not in the background or otherwise) ... I only start it up to edit rules when necessary, and the rules I create / edit are there even after reboots.

Maybe I'm misunderstanding you.

All iptables rules are lost on boot. You need some script that loads the rules on every boot.

Firesarter is actually divided in 2 parts, the firewall script that loads on boot and activates the firewall, and the graphical tool for configuring the firewall.

So when people say that you don't need to run Firestarter all the time they are talking about the GUI. The actual firestarter script _will_ start on boot and run all the time.

---

### Post by SuSUntu on 2007-07-16
> **mcduck said:**
> All iptables rules are lost on boot. You need some script that loads the rules on every boot.


Correct. Iptables rules are lost if you apply them from the command line without taking some additional action to maintain them after a reboot, i.e., saving them to file with "iptables-save" and then calling that file from a startup script.

> **mcduck said:**
>  
Firesarter is actually divided in 2 parts, the firewall script that loads on boot and activates the firewall, and the graphical tool for configuring the firewall.

So when people say that you don't need to run Firestarter all the time they are talking about the GUI. The actual firestarter script _will_ start on boot and run all the time.

Correct. You can confirm that the Firestarter scripts are set to launch at run levels 2. 3, 4, and 5 by running:

```

sudo sysv-rc-conf

``` 

However, it seemed to me that when Bloke said this:

> 
**I use Firestarter. Launching Firestarter for the first time enables the firewall (for the current session).** I tested if rules stuck by using "sudo iptables -nvL" prior to reboot, and again when the system was back up, and they do not. I think scripts can be created to ensure rules are restarted after a power cycle.


he was stating that:

1) the rules created in Firestarter only apply for the "current session"
2) the rules created by Firestarter are lost on reboot
3) the user has to manually create scripts to get the rules created in Firestarter to apply after reboot

Again, I have not found any of the above to be correct. In order for the Firestarter scripts **not to run**, the user would have to take extraordinary action, but not vice versa.

To test, I added a new rule to deny outbound traffic to a networked PC, then I ran: 

```

sudo iptables -nvL > ~/Desktop/iptablespreboot.txt

```

After that, I rebooted and ran:
```

sudo iptables -nvL > ~/Desktop/iptablesreboot.txt

```

then compared the files with 'meld'. In both output files (preboot and reboot), the new rule denying outbound traffic to the networked PC was present. Furthermore, the only difference between the two files was  (as expected) recorded packet and byte traffic information.

So, again, I have to say that I am mystified by Bloke's assessment  (and now sam0t's agreement with him) that Firestarter rules are lost after reboot. I cannot recreate the same behavior in Feisty nor have I ever experienced this behavior since I first used FS in Breezy.

I'll be interested in learning what's causing this reported anomaly in Firestarter's behavior. Maybe there's a glitch in the two described systems that is causing the Firestarter init script to fail on boot (maybe the network interface isn't available when the script tries to run initially). I don't know.

---

### Post by MRiGnS on 2007-07-16
> **Bloke said:**
> Ubuntu's firewall is OFF by default which allows all traffic. This is BAD.

sorry, but that's simply not true. 

to turn the firewall of you would have to blacklist the kernel module and that is not the default setup.

---

### Post by mcduck on 2007-07-16
> **MRiGnS said:**
> sorry, but that's simply not true. 

to turn the firewall of you would have to blacklist the kernel module and that is not the default setup.

It's off in the sense that there are no rules o restrict network traffic. (which is OK as there are no services that would respond to any incoming traffic).

I've seen Firestarter to fail starting on some achines when network connections are handled by Network Manager. So if you have that problem, and it's a desktop machine so you don't need to switch between many networks/interfaces, you could try removing Network manager and configuring the connection in the normal way.

---

### Post by az on 2007-07-16
A firewall is completely useless on a desktop machine.

You are never invisible on the network (if you think "stealthed" means anything, how do you think they know who to portscan?).  On Ubuntu, you will not be talking to the network unless you tell it to.  Unlike other operating systems.

---

### Post by sam0t on 2007-07-16
> **SuSUntu said:**
> 
So, again, I have to say that I am mystified by Bloke's assessment  (and now sam0t's agreement with him) that Firestarter rules are lost after reboot. I cannot recreate the same behavior in Feisty nor have I ever experienced this behavior since I first used FS in Breezy.

I'll be interested in learning what's causing this reported anomaly in Firestarter's behavior. Maybe there's a glitch in the two described systems that is causing the Firestarter init script to fail on boot (maybe the network interface isn't available when the script tries to run initially). I don't know.

Iam not sure that firestarter rules are forgotten after reboot at all, I lack the skill to do such conclusion. What I do know, is that I get very different  output from command "sudo iptables -nvL" after reboot and after I have launched firestarter GUI.

edit:

This is the stuff I get with command "sudo iptables -nvL" after reboot:

> Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

And here is the stuff after I have started up firestarter manually:

> Chain INPUT (policy DROP 3 packets, 148 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       195.197.54.100       0.0.0.0/0           tcp flags:!0x17/0x02 
    4  1071 ACCEPT     udp  --  *      *       195.197.54.100       0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       195.74.0.47          0.0.0.0/0           tcp flags:!0x17/0x02 

There is plenty more of those kinda firewall rules and the ones I have made with firestarter GUI, but they are lenghty so I edited it abit.

Also I booted up the recovery mode and when shutting down the system there is a clear text "shutting down firestarter", so there is one more weird thing added to the mix. I have absolutely no idea how to create a script that runs the firestarter rules at boot, I did try to make firestarter launch itself automaticly at reboot following the firestarter FAQ advice, but as described earlier, it&#347; not working as it should :(

---

### Post by juantovarm on 2007-07-16
I have the same results as sam0t, and this happens every time i reboot my pc. I have to start  firestarter manually so that my iptables rules are full again, process I think should be automatic and a total waste of time if done manually. I have opened port 631 to allow network printing at home and i don't know whether to configure or not my iptables. So if anyone can tell me how to keep the iptables values i would really appreciate it :D

By the way i am using feisty's network manager, does that influence the iptables/firestarter rules?


:):)

AZ, could you please explain a little bit more?

---

### Post by SuSUntu on 2007-07-16
> **sam0t said:**
> 
This is the stuff I get with command "sudo iptables -nvL" after reboot:

```

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination

```


The output you posted after reboot is definitely what you would see on a fresh Ubuntu install before adding any iptables policies (whether via Firestarter or command line).

Hopefully you guys understood that I wasn't denying your personal experiences, but trying to set the record straight that what Bloke, you and others are describing is not considered normal or intended behavior for Firestarter in Ubuntu. It is designed to populate iptables on boot automatically without any additional user intervention or script writing. That is the way it works and has worked for me. I think there are some expected issues with dial-up, but otherwise I think it should just work automatically.  

Your situation is that the init script is not launching or is launching and failing since you can manually launch Firestarter and have it populate iptables. Though technically different than "losing" or "forgetting" the rules, the result is the same, i.e., your iptables is not populated with your policies automatically on reboot leaving them empty as if no rules had ever been established.


> **sam0t said:**
> I have absolutely no idea how to create a script that runs the firestarter rules at boot, I did try to make firestarter launch itself automaticly at reboot following the firestarter FAQ advice, but as described earlier, it&#347; not working as it should :(

The point here is that you shouldn't expect to have to make a script yourself. One already exists and was installed when you installed Firestarter. The real issue is determining what is preventing it from launching as it was designed to do. Easier said than done, i suppose.

McDuck mentioned he's heard of some issues with Network Manager and Firestarter (NM has lots of issues doesn't it?). I don't use Network Manager and my FS works on reboot. Juantovarm says he uses Network Manager and his fails like yours and Bloke's do. Maybe that is a commonality.

---

### Post by juantovarm on 2007-07-16
Thanks for the reply, and i know you weren't denying our experiences :D . I uninstalled the network manager to see if i had any improvements, hahaha, none at all :guitar: so i went to the firstarter web page, i read a lot about what it should do, and i found out about the script you're talking about. I looked for it, i didn't find it, so i decided to load the firestarter, save the iptables to /home/juan/.iptables.up.rules and then modify:

/etc/network/interfaces

auto eth0 iface eth0 inet dhcp
  pre-up iptables-restore < /home/juan/.iptables.up.rules

ok, I know it's not the BEST way, if i were to change the iptables rules i would have to do it manually or do the same process again until i figure out where my firestarter init script is and why it doesn't run at startup :o:):o:):popcorn:

---

### Post by sam0t on 2007-07-17
Thanks for the lenghty and down to earth explanation on the situation SuSuntu!

As a matter of fact, I was messing with my xorg.conf file the other day and managed to trash it in such way that Gnome refused to load up. In that phase when text was flowing on screen and Ubuntu tried to start up I noticed a very clear "Firestarter load" or something like that and after it in red FAIL.

Hopefully this can be solved in the next version of ubuntu or by a patch, its not huge pain for me personally as I do not use Ubuntu daily, but atleast the issue is in the open now.

---

### Post by juantovarm on 2007-07-17
Thank you Sam0t for giving me an idea...
I deleted the quiet splash is /boot/grub/menu.list

I looked for the firestarter load line it said OK
decided to comment out pre-up iptables-restore < /home/juan/.iptables.up.rules in /etc/network/interfaces 
rebooted: surprise firestarter load line FAIL, eliminated the comment in /etc/network/interfaces
rebooted: firestarter load line OK
decided to delete < /home/juan/.iptables.up.rules and only leave pre-up iptables-restore
rebooted: firestarter load line OK, 
checked iptables and it had all the rules, maybe i was missing that line in /etc/network/interfaces  :confused::confused:

any ideas?

---

### Post by noynac on 2007-07-17
> **SuSUntu said:**
> Are you saying that if you set rules with Firestarter (in effect, editing iptables), that when you reboot, the rules you added / edited are no longer in iptables?...

In my case, the rules do not appear to survive a reboot.

I installed Firestarter and put a check mark next to "enable ICMB Filtering" and removed check marks from all items under the ICMB-filtering option. Then, as a test, I went to the [www.grc.com](www.grc.com) site and ran the "common ports" section of the ShieldsUp test. The computer passed all of these tests.

I rebooted my computer and tried this test again. It failed this time because the computer was responding to certain items such as ping requests. Then, without doing anything else, I loaded Firestarter and ran the test once again. This time it passed. 

So, in my case, it would appear that Firestarter needs to be started whenever I run the computer.

---

### Post by SuSUntu on 2007-07-17
> **juantovarm said:**
> Thank you Sam0t for giving me an idea...
I deleted the quiet splash is /boot/grub/menu.list

I looked for the firestarter load line it said OK
decided to comment out pre-up iptables-restore < /home/juan/.iptables.up.rules in /etc/network/interfaces 
rebooted: surprise firestarter load line FAIL, eliminated the comment in /etc/network/interfaces
rebooted: firestarter load line OK
decided to delete < /home/juan/.iptables.up.rules and only leave pre-up iptables-restore
rebooted: firestarter load line OK, 
checked iptables and it had all the rules, maybe i was missing that line in /etc/network/interfaces  :confused::confused:

any ideas?

It seems to me from reading lots of other threads / bug reports (a few of which I linked below), the Network Manager is being identified as the culprit (as suggested earlier in this thread). Basically, since it seems to be a **timing** issue, i.e.,:

- boot > network down > network up > firestarter init attempt = firestarter start succeeds
- boot > network down > firestarter init attempt > network up = firestarter start fails

then I suppose anything that delays the network being brought up until after the firestarter init would cause firestarter to fail. Conversely, anything that might delay firestarter init until after the network is up or anything that might force the network to come up before firestarter init would resolve the issue. The latter may be the case for describing why adding the "pre-up" line allows firestarter to load properly. The "pre-up" line (in any form) may be "forcing" your network to be brought up prior to firestarter init. Just a theory. Otherwise, the line you are appending doesn't seem to have any real direct relationship and it is not a "normal" requirement.

See these posts and bug reports with possible work arounds; they focus on Network Manager, and I know you said you tested with NM installed and NM uninstalled with no difference in outcome, but it may provide additional food for thought:

[https://bugs.launchpad.net/debian/+source/firestarter/+bug/42759](https://bugs.launchpad.net/debian/+source/firestarter/+bug/42759)
[http://www.debian-administration.org/users/emeitner/weblog/2](http://www.debian-administration.org/users/emeitner/weblog/2)
[http://ubuntuforums.org/showthread.php?t=167411](http://ubuntuforums.org/showthread.php?t=167411)
[http://ubuntuforums.org/showthread.php?p=1581628](http://ubuntuforums.org/showthread.php?p=1581628)

Also, another thing that I see different in our system setups is that I use a static IP as opposed to DHCP (remember, I also don't use Network Manager). If you think about it, perhaps acquiring the DHCP stuff is causing a delay in network establishment that allows firestarter init to get ahead of the network being brought up ... thus firestarter fails. Again, just a theory, but it does try to stick to the logic of the timing issue.

---

### Post by sam0t on 2007-07-17
Susuntu your resoning sounds reasonable. 

ps. I did the same as juantovarm and disabled the quiet splash so I get more informative boot up. Too bad the text moves in such speed its impossible to make anything out of it. One thing is for sure, there is not Firestarter = (red) FAIL message on my Ubuntu reboot. But maybe thats because my machine boots up so fast that I cannot keep up with it :/

---

