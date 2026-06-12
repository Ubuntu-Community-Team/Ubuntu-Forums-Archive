---
title: "Black Screen -  no response"
date: 2008-06-18
forum: General Help
---

### Post by NNNDaddy on 2008-06-18
I successfully installed Ubuntu on my old computer today. Everything setup just fine. I configured everything. It works great, but if i leave my computer alone for more than 2 minutes, the screen goes black,my fans start to spin faster, and the processor light lights up continuously. The only way to get out of this is to pull the plug - nothing else will get it out of this weird state. I tried turning of the screen saver and setting my power options to NEVER go into any other state and continuously stay on - this did NOT work.

I have a Nvidia TNT2 in this old computer - this integrated chip is about 7 years old. Could it be a driver?

---

### Post by bijeeshvs on 2008-06-18
open the system monitor and watch it u can see which program is screwing up check for cpu usage and mem usage.....................

---

### Post by NNNDaddy on 2008-06-18
> **bijeeshvs said:**
> open the system monitor and watch it u can see which program is screwing up check for cpu usage and mem usage.....................

Okay...

Uhh, how do I do that?

I'm really new to this. Sorry.

---

### Post by bijeeshvs on 2008-06-18
Go to system->administration->system monitor
 in the process tab you can see all process running and sort processes based on name, cpu usage, memory by the way you can see which program is eating the cpu or memmory observe it until the system hangs and u can find which program is going nuts

and in the resources tab u can see the total memory usage and swap usage and check if anything wrong there.....................

---

### Post by NNNDaddy on 2008-06-18
> **bijeeshvs said:**
> Go to system->administration->system monitor
 in the process tab you can see all process running and sort processes based on name, cpu usage, memory by the way you can see which program is eating the cpu or memmory observe it until the system hangs and u can find which program is going nuts

and in the resources tab u can see the total memory usage and swap usage and check if anything wrong there.....................

That would work nice, but when the system hangs, I no longer can see what is going on.

I think I do have some further info, though:

I just booted it up and two things happened:

1. I have like 26 important updates to install, and
2. Apparently, I wasn't running the best video driver.

I changed my driver and reboot. Everything was working fine, when in the middle of the update.

BLANK!

What do I do?

---

### Post by bijeeshvs on 2008-06-18
i agree that u cannot see whats happening when the system hangs but just before the system hangs u can check is there anything wrong (i mean just before it hangs ) and was that system not being used for a long time ?????????
check for the cpu temp as u mentioned abt the fan speed 

u can run a mem test before booting and find anything is wrong (ie from the boot menu select memtest) and run it and run it long enough to see if the system hangs 

if it doesnt hangs possibly u crashed an update...................

---

### Post by NNNDaddy on 2008-06-18
> **bijeeshvs said:**
> i agree that u cannot see whats happening when the system hangs but just before the system hangs u can check is there anything wrong (i mean just before it hangs ) and was that system not being used for a long time ?????????
check for the cpu temp as u mentioned abt the fan speed 

u can run a mem test before booting and find anything is wrong (ie from the boot menu select memtest) and run it and run it long enough to see if the system hangs 

if it doesnt hangs possibly u crashed an update...................

Thank you soo much. I got it to work. I was watching the monitor and that STUPID email app that comes with ubuntu suddenly went to 100% cpu usage and the whole thing fries then.

THANKS!!!!!!

But I have one last problem - I have a Netgear WG111v2 USB router hooked up. It doesn't even connect if I have WEP protection, so I turned it off. It connects, Ubuntu tells me I need to update, I start the update and within 1 minute the connection gets lost...

Any help, please?

---

### Post by linux6994 on 2008-06-18
Getting the internet connection stable is next, hold of on updates until its stable. Can you browse to your router usually 192.168.1.1 or 15.1 Are you running dhcp or static ip? You need to open a terminal window and do a ifconfig and see what ip address is assigned. You can also go to System > Administration > Network to check the settings. Normally your GW and DNS will be provided if running dhcp. If you are running a static ip then you should have your GW and DNS set to the router's ip address.

Once you can maintain the connection then do the updates.

---

### Post by NNNDaddy on 2008-06-18
> **linux6994 said:**
> Getting the internet connection stable is next, hold of on updates until its stable. Can you browse to your router usually 192.168.1.1 or 15.1 Are you running dhcp or static ip? You need to open a terminal window and do a ifconfig and see what ip address is assigned. You can also go to System > Administration > Network to check the settings. Normally your GW and DNS will be provided if running dhcp. If you are running a static ip then you should have your GW and DNS set to the router's ip address.

Once you can maintain the connection then do the updates.

Well, my IP does NOT change, so I guess it is static. 

How do you get to the terminal window?

---

### Post by NNNDaddy on 2008-06-18
Okay... I just learned SOO much about Linux in the last 5 minutes.

Here is what is going on:

I have the NETGEAR WG111v2 USB router. I apparently need to install ndiswrapper 1.49 to get the right drivers on. I got the drivers, got ndiswrapper, and put them on a CD. When installing ndiswrapper, I got errors. I read the install file in the ndiswrapper and my kernal headers are NOT up to date. I need to connect to the internet to get updated. But, I have no stable connection. What do I do?

---

### Post by NNNDaddy on 2008-06-18
Is there any way I can get all the updates and burn them to a disk and run them? Because without the latest kernal , I cant run ndiswrapper, and therefore I cannot get internet.

Please. All responses are appriciated.

---

