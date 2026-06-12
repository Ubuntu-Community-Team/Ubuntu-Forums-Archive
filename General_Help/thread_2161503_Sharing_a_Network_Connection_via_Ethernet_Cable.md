---
title: "Sharing a Network Connection via Ethernet Cable?"
date: 2013-07-10
forum: General Help
---

### Post by unicornswag on 2013-07-10
Okay, so I have sort of a complicated situation, but bear with me. My main computer is an old G3 iMac with Debian 7.0 Wheezy PowerPC installed and running LXDE surprisingly well. My second computer is an old 600 mhz HP laptop with 256 mb ram running Xubuntu 12.04. Although it runs on this low spec machine, the gui is fairly useless for everyday use. Now to my problem... Since I am only 17 y/o, the only internet connection that I can afford is a 2g connection through t-mobile via my android phone. My hope was to "tether" this connection to both of my machines. Since my phone is not rooted, I opted to "buy" the app "Easytether" to accomplish this. If you're not familiar with this app, basically you just install it on your phone and then install the pc-side .deb file on your debian/*buntu machine. After th connecting the phone and pc via usb and running the app, you then have a working internet connection through the interface labeled "easytether0". So for my x86 Xubuntu laptop, setting this up was a breeze and I now have an internet connection. The only problem is that with such an old machine, I really cont do much with that connection as far as browsing or installing packages. For that I turn to my good old imac. The problem: Easytether does not have a PowerPC port of their linux package, so I figured my iMac would be stuck offline. Then an idea struck me, what if I could share the internet connection from my phone to my laptop via usb, and then from my laptop to iMac via crossover ethernet cable? I did some research on the subject of internet connection sharing in linux, and found quite a bit of info. The first method that I found was using iptables from the command line. It seemed simple enough as I almost always prefer command line methods and avoid the gui whenever possible. However, I am totally clueless when it comes to networking (Its riduculous how stupid I am). However I blindly followed the steps listed, hopefully changing the correct parameters to fit my setup, But after about a week of working on this, nothing worked. Finally, I decided to give in and follow the gui method suggested on the Ubuntu wiki here [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) . It says it that this method works in Network Manager for Ubuntu 9.10 and up. I assumed that the process should be the same for Xubuntu, but I Immediately ran into a problem. The wiki says:

"When the window opens, select 'Auto eth0'"

However when I open Network Manager in Xubuntu, it does not give me an option called "Auto eth0". Listed in tabs across the top of the window, I see "wired, wireless, Mobile Broadband, VPN, DSL". No Auto eth0. I dont know what the problem is here, is this somthing to do with XFCE? Could someone please explain to me what Auto eth0 actually is and possibly how to get this option in network manager? Also any suggestions for other ways to get this connection working would be great. I really just want to get this working so my old imac can have a new life!

---

### Post by unicornswag on 2013-07-11
By the way, is anyone sure whether all the *buntus use the same network manager? Or does xubuntu use a more lightweight alternstive?

---

### Post by silv3rm00n on 2013-07-11
It is simple. Setup internet connection sharing using Firestarter.

```

1. Setup your mobile phone internet on 1 linux machine.
2. Connect your 2nd machine to this first machine via ethernet cable or wifi or whatever suits.
3. Install Firestarter on the 1st machine with the internet.
4. Select internet connection sharing in Firestarter.
5. Your 2nd machine is now able to access internet through the 1st machine.

```

You may have to play with the settings a bit. I have put up some screenshots [here](http://www.binarytides.com/share-tata-photon-connection-lan-ubuntu/). 
I used this technique to share a cdma mobile based internet across entire LAN and it works quite well.

---

### Post by claracc on 2013-07-11
It is not recommended to use firestarter as it is abandonned software: see [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter) , for the same purposes it is recommended to config properly the inside built firewall: [https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)

---

### Post by unicornswag on 2013-07-11
Thanks guys. I installed firestarter (took over an hour with my slow connection & machine) However, after running through the wizard and enabling connection sharing, it gave me the error message:

Failed to start firewall
The device eth0 is not ready.
Please check your network device snd make sure your internet connection is active.

Any suggestions? Its really  annoying posting these questions from my phone! :(


Also, i installed gufw, but saw no option to share connections.

---

### Post by claracc on 2013-07-11
Guide to configure ufw: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by unicornswag on 2013-07-11
Okay, thanks for that link, but I dont think you realize how low my networking skills are. As much as I hate to say it i would much frefer to stay within the gui. Heres an  idea to run by you guys: what if i installed a more archaic (5.04?) Release of ubuntu from when firestarter was still supported? Assuming easytether supports  such an old release, could this possibly solve my issue? It would be fine with me since ics will be the laptops only function, I dont care if its up to date. Any opinions?

---

### Post by unicornswag on 2013-07-11
Im downloading the 5.04 iso at 5 kBps on my phone right now. Hopefully it will download in about 18 hours and be intalled by tommorow night. Hopefully this solves my problem!

---

