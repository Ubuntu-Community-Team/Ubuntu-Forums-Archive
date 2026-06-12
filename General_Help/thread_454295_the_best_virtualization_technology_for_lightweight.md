---
title: "the best virtualization technology for lightweight hardware"
date: 2007-05-25
forum: General Help
---

### Post by teh_chris on 2007-05-25
i have an older box (1ghz athlon, 512 mb RAM) that i want to park at a friend's house and run a couple of servers on.  i have used vmware server in the past on more powerful machines but with such a low powered box i am concerned with system overhead.

my friend has a better uplink speed than i do (my cable company gives us 10mbit down but only 100k up) and his place isn't nearly as busy as mine is from a network traffic standpoint:  my place has 3 MMO players, a voip phone,  bittorrent, xbox live, the works.  i have to use QOS to keep everyone happy.  my friend's place is just him and a dog and neither of them are online as much as my family is.

the services i want to run are probably not going to see much use except one, which will be either teamspeak or ventrillo (for all the MMOs :)). voice is clearly impacted by system performance, hence my concern over efficiency.  i am not interested in running windows in any fashion, just linux servers, probably all of them ubuntu.

since the other servers will be mail and web in some fashion, i think it's a good idea to run reach service isolated from the other, so in case the mail server tanks, or the message board gets hacked, the other services will run just fine and the host is in no danger.  i doubt more than 6 people will be talking, browsing, and mailing on the machine at once, but you never know.

my first thought was to use openVZ since it's supposed to be uber-efficient, but the install documentation for it is lacking for anything but RPM based distros.  i thought about using centOS, but they don't have a single CD server version for centOS 5 (unlike ubuntu), and i have not been able to locate a single CD version for 4.   i am not keen on downloading and burning 6 CD's and then spending forever removing stuff i don't need.

there are other technologies as well which i am not familiar with, but i am still interested in hearing about.

so my questions are: 
1) in your experience, how efficient is VMWare when using essentially identical OSes?
2) if VMWare is not a good choice, is there any documentation for openVZ working on 6.06 or 7.4?
3) if i am out of luck with openVZ on a stock install of ubuntu, is there a way to add RPM support to ubuntu or does anyone know of a server oriented linux distro with RPM support?
4) if neither VMWare or openVZ is the right tool for ubuntu in this scenario, what other technologies might be better suited?

i don't really care what distro i end up using, or what virtualization technology i end up with, as long as it's the right tool for the job and for the hardware that i have.

---

### Post by ezrollers on 2007-05-25
I can't say that I'm too happy with vmware, but it might be cuz i'm running it on a sluggish hdd on my laptop, then again your hdd on that server my be slow too, and memory could be an issue, espcially if you plan to run several virtual machines.

I've heard of Xen, but have never tried it myself, it's supposed to be a better virtualisation technology than vmware and the like.

I imagine that the pc does not have a dvd drive. I'd put a dvd drive from my main pc on it and install centos from dvd.

---

### Post by teh_chris on 2007-05-25
> **ezrollers said:**
> 
I've heard of Xen, but have never tried it myself, it's supposed to be a better virtualisation technology than vmware and the like.

I imagine that the pc does not have a dvd drive. I'd put a dvd drive from my main pc on it and install centos from dvd.

if xen has decent install docs for ubuntu, and is more efficient than vmware, then i am interested in it as well.

i had considered the DVD install, or even an FTP based install (used to install redhat that way all the time back in the 5.0-7.3 days don't know if that is possible anymore) only i don't know how bloated and GUI centric centOS is.  i stopped using redhat at version 8 because of it's bloat and GUI dependence and converted to slack/*BSD.  ironically, it was VMWare that induced me to try ubuntu since that is the only "non-redhat" distro that they support.  there was a lean security focused distro based on redhat called trustix, but i am not sure it is an active project anymore.

does anyone have some experience with centOS?  how does it measure up to ubuntu from a server standpoint?  how about xen?  maybe virtualbox?

---

