---
title: "kubuntu 16,04.02 LTS and Resources"
date: 2017-04-02
forum: General Help
---

### Post by anon_private on 2017-04-02
I burned a live DVD for kubuntu 16.04.02 (for those reading my other post, I used a Windows laptop to prepare the DVD).

It took ages to boot up on my pc, and FF would not start.

I put this down to my machine (pc) only having 1 GB of RAM and an old processor (machine is 7 years old)..

Am I right in assuming that kubuntu 16.04.02 LTS will not run on a machine with only 1 GB of RAM. I can run kubuntu 14.04 without a problem.

I also noticed with version 16 that flashes occurred on the screen, I attributed this phenomenon to the fact that I would need to change the graphics card configuration from the default setting to NVIDEA (my graphics card).

I also observed that version 16 disconnected form the internet (of its own accord), a phenomenon I observed with version 15.

Overall, I will stay with 14.04.02.

Comments please

---

### Post by SeijiSensei on 2017-04-02
One problem with booting off the DVD into "live" mode on a memory-starved system is that there is no place to write any swap files.  

1 GB is pretty limited for modern operating systems with complex GUI interfaces like KDE.  If you're satisfied with 14.04, stick with it.  I'm still using it because my tests of 16.04 never convinced me it was worth the upgrade.  However the easiest and oftentimes cheapest performance improvement you can make on an older machine is to add memory.

You can move to 2 GB for as little as $16, or spend $58 to upgrade to 4 GB.  See [http://www.crucial.com/usa/en/compatible-upgrade-for/Dell/dimension-e520#memoryResults](http://www.crucial.com/usa/en/compatible-upgrade-for/Dell/dimension-e520#memoryResults)

It depends on how Dell installed the memory.  According to Crucial, the machine has two banks of two sticks each.  If it currently has two 512's in two of the slots, I'd buy the 2 GB kit at $32 to fill the other two slots and take the machine to 3 GB total.

---

### Post by anon_private on 2017-04-02
I found the kubuntu 16.04.02 OS an unsatisfactory experience on my pc. Out of interest, I downloaded UBUNTU 16.04.1 GNOME and found that it booted well from the live CD. The problem is that for some reason it will not connect to the wi-fi system. The router is fine. I did input the router password. Any suggestions to make it connect to the router.

The fact that Ubuntu-GNOME installs and runs so much easier than its equivalent kubuntu version on my machine tends to suggest that the kde interface require a lot more of the pc resources compared to GNOME.

Best wishes.

---

### Post by mastablasta on 2017-04-03
you can turn off various things in KDE bling to make it smoother on your PC. 

the GPU drivers will need to be proppely installed. KDE needs 3D acceleration to work. unless you turn off all of it's 3D features.

as for the wi-fi network - it KDE has same kernel (so drivers are the same) but the network manager is different. an option would be to trouble shoot the issue. or you can stay on 14.04 for now. it has 2 more years of support left.

---

### Post by Bucky Ball on 2017-04-03
> **anon_private said:**
> The fact that Ubuntu-GNOME installs and runs so much easier than its equivalent kubuntu version on my machine tends to suggest that the kde interface require a lot more of the pc resources compared to GNOME.

No suggestions. A known fact. Ubuntu-gnome lightweight all round and one of the lightest around. Lubuntu would also probably work fine (and perhaps Xubuntu). Ubuntu would struggle and that means Kubuntu would, too.

Wifi, along with other things that may need drivers, can be problematic on a live session. Plug in a cable and that should work fine (and you could check 'Additional drivers' when you're online and you may find a driver ready for your wifi card). 

It is a catch 22, but with some wifi cards, you need to be online to install the software to get the wifi working. Sometimes it is a matter of during your first update/upgrade of the new install the card will be picked up and drivers installed.

---

### Post by anon_private on 2017-04-03
This is quite frustrating. It looks like I can only use the flavour of ubuntu, or other Linux OS's, that connects with the wi-fi system.

The router belongs to another person, so I can't use a wired connection.

My current version of kubuntu 14.04 connects to the wi-fi system without any problem

PS. Why is UBUNTU GNOME light. I know that some favours are advertised as light, and have the lighter applications. I tend not to like the lighter applications - just not as good.

---

### Post by RobGoss on 2017-04-03
>  
PS. Why is UBUNTU GNOME light. I know that some favours are advertised as light, and have the lighter applications. I tend not to like the lighter applications - just not as good.  

They are made for those machines that have older hardware. Keep in mind those same old machines that most people use for Linux would not even be able to run any form of Windows

I think if you plan on running let's say 16.04.2 you might want to invest in upgrading your Ram so at least it will run a bit more efficient

---

### Post by anon_private on 2017-04-03
Yes, but remember the question.

My main problem is connecting the pc to the router using wi-fi. You are right, I don't have much RAM, but it has served 'well' so far

UPDATE on Ubuntu-GNOME 16.04.1 LTS

I find that I can connect the live DVD to the router via wi-fi, but it disconnects (say 5 mins). If I manually connect, It will re-connect, but again it will disconnect (say 5 mins). On the third occasion, it would not connect. Is there anything that I can do, at the live DVD stage, to ensure a stable wi-fi connection?

---

### Post by SeijiSensei on 2017-04-04
Some wifi adapters have power management circuitry which can cause this behavior.  Unfortunately I don't think you can fix this permanently using a live CD since you would have to edit some of the configuration files.  You can try this temporary fix to see if the problem is with power management:
```
sudo iwconfig wlan0 power off
```
assuming wlan0 is the name assigned to your wifi interface.

For some advice on fixing this permanently after you have installed from the CD, see [https://www.google.com/search?q=wifi+power+management+linux](https://www.google.com/search?q=wifi+power+management+linux)

---

