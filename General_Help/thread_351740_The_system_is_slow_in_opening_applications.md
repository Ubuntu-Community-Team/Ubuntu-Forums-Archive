---
title: "The system is slow in opening applications"
date: 2007-02-02
forum: General Help
---

### Post by ghepardo on 2007-02-02
Hi,
I have a p4 3200mhz ,1gb ram and a geforce 4mx 64mb, and all 7200rpm hd's. 

I am quite satisfied from my Kubuntu, but the main problem is that is really slow opening new applications.
FIrefox takes a life to start the first time, and the same is for all other apps. Also the kmenu is slow in opening sub-menus.

Someone knows some trick to fix this out?

Thanks in advance.

---

### Post by x64Jimbo on 2007-02-02
Can you get some kind of system monitor tool to see if your CPU is spiking while this is happening? Do your HDD lights go crazy while it's loading?

---

### Post by ghepardo on 2007-02-03
no, the hdd light does not goescrazy,nor the cpu is at 100%,the system seems just like stalled.

---

### Post by l.liam on 2007-02-03
Hello

I have a also just installed Ubuntu for the first time, practically my first try of Linux -)

after a few log-ins, the system started to respond very slowly, as ghepardo described - all applications start very slowly which was not so during the first log-ins (after the installation)

im running a P4 3000Mhz Dual Core, 1gb ram, both cpu's dont go above 20% (the system monitor usually makes the bar's reach 20%)

I was playing with different BIOS settings recently, can it be related? and it what fashion?
I really dont want to give up on Linux as soon as i just started (*,)  and its not the only critical problem im experiencing with Ubuntu :confused: 

Appreciate any help

---

### Post by ferd on 2007-02-03
> **l.liam said:**
> Hello

I have a also just installed Ubuntu for the first time, practically my first try of Linux -)

after a few log-ins, the system started to respond very slowly, as ghepardo described - all applications start very slowly which was not so during the first log-ins (after the installation)

im running a P4 3000Mhz Dual Core, 1gb ram, both cpu's dont go above 20% (the system monitor usually makes the bar's reach 20%)

I was playing with different BIOS settings recently, can it be related? and it what fashion?
I really dont want to give up on Linux as soon as i just started (*,)  and its not the only critical problem im experiencing with Ubuntu :confused: 

Appreciate any help
You might try FSLint. It cleaned up my system and made it more responsive.

---

### Post by ghepardo on 2007-02-05
THe problem for me is that the RAM becomes fastly aall used by the system. Why?

---

### Post by Oki on 2007-02-05
As I understand it Linux are using the RAM diffrently then Windows; Linux use all the RAM. This is not bad since it can free it for new applications, and makes it easyer for the CPU. Correct me if I am wrong, I am new to Linux.

---

### Post by kerry_s on 2007-02-05
Actually that's normal for KDE, sometimes it's fast, but over time it slows to a crawl. It just has to many connected parts, just to launch 1 simple app, it has to launch 2 or 3 others first then the app you wanted. If you really want a fast system that doesn't slow down over time, then try Xubuntu(xfce4). There are things you can do to try to speed things up, but there just temporary, it's just something about kde that makes it slow down. :confused:

---

### Post by x64Jimbo on 2007-02-05
> **kerry_s said:**
> Actually that's normal for KDE, sometimes it's fast, but over time it slows to a crawl. It just has to many connected parts, just to launch 1 simple app, it has to launch 2 or 3 others first then the app you wanted. If you really want a fast system that doesn't slow down over time, then try Xubuntu(xfce4). There are things you can do to try to speed things up, but there just temporary, it's just something about kde that makes it slow down. :confused:
Hmmmm... Speak for yourself. I leave my KDE session open for very long periods of time without any slowdowns.

---

### Post by kerry_s on 2007-02-05
> **x64Jimbo said:**
> Hmmmm... Speak for yourself. I leave my KDE session open for very long periods of time without any slowdowns.

How olds your install? How often do you use it? Do you stick with just kde apps? Tweaks? Do you maintain it constantly?

---

### Post by x64Jimbo on 2007-02-06
The install is probably 3 months old, I use it every day, I use whichever apps I feel like, I'm running latest Beryl, Automatix2, and other tweaks, and I do update the packages whenever the icon appears. Nothing really out of the ordinary for keeping it running all the time. Man, it's on all the time. I never turn it off.

---

### Post by kerry_s on 2007-02-06
Hmm, That's interesting i run my systems pretty much like that to. I run kde on my laptop(acer aspire 3500, 1.4mhz,512ram,10gig hd) it's always on never turned off. But i find after about 6 months things start to get very laggy, even if i reboot the system. So i usually just do a clean install when it starts to get laggy. I run mine with all the common tweaks, it's very fast when tweaked, but like i said it eventually decreases in performance. I find that with linux it always seems to act differently on each computers hardware. The laptop is for grandma and the kids, so i don't really worry about it till they start to complain. I use a desktop system with Xubuntu cutdown, all crap i don't use removed, others replaced with faster apps.

The kde tweaks: (i'll try & remember :) )
Remove all unneeded apps
Replace the ones not used with ones used
Use the konqueror preload
Preload firefox using /etc/rc.local ("user" is the account name)->
> sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
> sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
hdparm -W1 -c3 -m16  /dev/hda &
turn off ipv6 with bad_list in /etc/modprobe.d (alias net-pf-10 off)
I use a hosts block list<-attached

To be continued....

---

### Post by x64Jimbo on 2007-02-07
Hmmm. I think this might be the difference:
My machine is an AMD Athlon 64 3700+, has 1MB L2 cache, 2GB RAM, and 2X300GB Hard disks. A faster machine is harder to bog down.

---

### Post by kerry_s on 2007-02-07
> **x64Jimbo said:**
> Hmmm. I think this might be the difference:
My machine is an AMD Athlon 64 3700+, has 1MB L2 cache, 2GB RAM, and 2X300GB Hard disks. A faster machine is harder to bog down.

Yeah, i dought any distro can bog down a machine with killer specs like that. :)  I picked up that laptop used on craigslist $300 so i just got to make due. Later when i can afford it, i will upgrade the ram to a gig.

But still i find it weird that it even starts to get laggy around 6 months. It's the only system i run with kde, my other systems are either running Xubuntu or a custom server-fluxbox install and they run about the same amount of time. I usually update all my systems to the new release all at once.

Just have to chalk it up to 1 of the great tech mysteries. :)

---

### Post by x64Jimbo on 2007-02-07
Is it by chance the machine that you use on the most frequent basis? KDE is a much bigger window manager than the others, and may be just using more memory to start with, so as you add programs and functions to your machine, it starts running out. I bet as soon as you upgrade that RAM, you'll stop seeing those lags.

---

### Post by typhoongs on 2007-02-07
Having onboard display card may slow down the system, like my system. Relatively my system is good cos i have minimal running processes and 512Mb RAM , AMD2600+ but if i open firefox and another RAM killer program, my system goes crazy if i switch from one program to other, the program which i switched does not come up quickly, and when that is occurs i can see tha my HDD is very busy. I think this is because of my graphics card.

---

### Post by ringmaster on 2007-04-08
> **kerry_s said:**
> 
The kde tweaks: (i'll try & remember :) )
Remove all unneeded apps
Replace the ones not used with ones used
Use the konqueror preload
Preload firefox using /etc/rc.local ("user" is the account name)->
> sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
> sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
hdparm -W1 -c3 -m16  /dev/hda &
turn off ipv6 with bad_list in /etc/modprobe.d (alias net-pf-10 off)
I use a hosts block list<-attached

To be continued....

Thank you, Kerry; the hdparm line speed up my system!!
But the W1 option is a bit risky when the power cuts off...
I would recomend this:

hdparm -q -A1 -q -d1 -q -c3 -q m16 /dev/hda

at the end of the /etc/hdparm.conf file. The -q option is to silence the output.

---

