---
title: "Why is it so difficult???"
date: 2007-04-28
forum: General Help
---

### Post by myjess on 2007-04-28
I installed Feisty, and then went about seeing if I could get wireless working. 
After days of compiling, troubleshooting, looking for other programs, compiling them, finding out that I get compile errors and have to fix them. Then install more software to compile them, it looks as if I cannot get wireless working, and from the posts here and serialmonkey, I certainly am not the only one.

When software has to be compiled, why can't everything it needs be targetted for download in the initial configure stages, instead of leaving it for the noobs like myself to try to figure out the packages. It would be so much easier then. Don't just tell us it needs downloading, but actually go get it with apt-get or something.

7.04 is such a disappointment. Yet again, my foray into Linux is brought up hard and fast by the incompatibility's in software source builds, and of course, my inexperience at sorting them out.
I am still of the opinion that I had years ago. Linux is just not ready for mass market, or, even people like me, who have been working on computers for years.

I am going to go back to 6.06 and see if wireless works with that, and if not, it's a re-format and back to whine-dows.

---

### Post by sharke on 2007-04-28
If you give us some information we may be able to help.
Regards
Sharke

---

### Post by mskadu on 2007-04-28
Sorry to hear that. Do tell us more. Maybe we can help. Did you try using the Fiesty LiveCD? Were you able to connect with it?

---

### Post by myjess on 2007-04-28
> **mskadu said:**
> Sorry to hear that. Do tell us more. Maybe we can help. Did you try using the Fiesty LiveCD? Were you able to connect with it?

Well, I can certainly take any help you may give me, but be prepared for utter stupidity and not knowing what to do next.

I have an Averatec 3225 with a ralink 2500 PCI card. 

If you haven't immediately closed this post then I shall continue.

I downloaded the serial monkey CVS and the ralink derived source driver. I was able to build the driver (which one, I can't remember). I was able to install it and an lsmod does list it. 
Every time I tried to use it then, that wiconfig or whatever it is called says there is 0% quality or somesuch, I know I should be getting some percentage. the iwlist does list my Access point (WPA).
Because I am using WPA, I knew I needed more than the default WEP installation,  so I went about both configuring the interfaces file, with a new subsection called ra0 (it already had eth0 and wlan0), and then tried to compile the ralink source utilty without any success. I then was able to compile and use as sudo, the RutilT program and was able to put in all the details, but again, with the wired network lead pulled out, I was unable to get any ping replies to my router(access point). 
I have looked at route command. I have tried ifconfig eth0 down. I have tried both ifup/ifdown and ifconfig ra0.

So after all that, it's a bust. I am married with a kid, and just do not have the time I would like to try to fix this anymore ( and that's what I mean by mass market, if it doesn't work outta the box, no-one but linux experts can spend the time fixing it).

I would love you to be able to help, but I do not hold out much hope.

btw. I have also heard of people disabling(not the right word) or excludig the built in rt2500 driver that comes with Ubuntu but I have no idea if that would help, or how to do it.

Thanks.

---

### Post by hyperair on 2007-04-28
ndiswrapper to the rescue? Do you have your windows drivers? You could use ndiswrapper to help. I'm sure there are plenty of ndiswrapper tutorials around ubuntuforums.org, so just run a search.

As for your compiling problems, the reason why they do not apt-get it automatically is because such methods are distribution independent. apt-get is the package manager of Debian-based systems. There are others, such as Gentoo's portage and the Redhat Package Manager. Even Ubuntu systems can have RPM installed, so it's best that the installer does not assume where to download the libraries from, and notify you so that you may download them.

As for stuff not working out of the box, my Windows XP and Windows Vista installations didn't work with my wireless card out of the box, but Ubutnu did. It's just your luck.

---

### Post by curtk69 on 2007-04-28
well linux is free compared to a pricey xp or even pricier vista you should expect some work

and btw i have had alot of troubles with windows wireless setups too. sometimes its just plug it in and it works other times theres all kinds of problems, sometimes with the same hardware, just reinstalled in an older or newer install of xp.. no wireless experience with vista but i doubt its any better than xp

---

### Post by myjess on 2007-04-28
Guys, 
what is this.

People said they could help me, but the last two replys are more to do with windows bashing than helping me out. OK, ok, so people have had problems with windows, but at least they do not have to compile and fix, and then compile. The driver is an executables. It gets downloaded and works.

Please stop the windows bashing and help me out. I would not have replied to this post only people said they would try.

Thank you.

---

### Post by Tomosaur on 2007-04-28
> **myjess said:**
> Guys, 
what is this.

People said they could help me, but the last two replys are more to do with windows bashing than helping me out. OK, ok, so people have had problems with windows, but at least they do not have to compile and fix, and then compile. The driver is an executables. It gets downloaded and works.

Please stop the windows bashing and help me out. I would not have replied to this post only people said they would try.

Thank you.

Well, perhaps you could have relaxed on the 'Linux is not ready' front.

In any case - if you could post the error messages you get during the configuration / compilation stages, perhaps someone could point you to the right packages you need to download. It can be annoying when the ./configure script doesn't sort everything for you - but if you have no connection anyway, there's not much it can do. It should, however, tell you what packages you need before you are able to compile.

---

### Post by sharke on 2007-04-28
myjess
Please read threw this [https://launchpad.net/ubuntu/+source/network-manager/+bug/78037](https://launchpad.net/ubuntu/+source/network-manager/+bug/78037)
There is some fixes that have been used with this card but not having one i cant test for you. Please let us know how it goes.
Regards
Sharke

---

### Post by hyperair on 2007-04-29
Ah from what I read it's the NetworkManager that throws a fit around with your card eh? It did the same thing for mine as well, but mine was using the acx driver. From here you have two paths you can go: tell NetworkManager you want to configure manually (leftclick the icon and configure manually) and then manually configure your essid and your encryption and all.. or use ndiswrapper. In my case I used ndiswrapper just for playing around but NetworkManager definitely works with ndiswrapper drivers.

---

### Post by markmaus on 2007-05-16
Try editing your /etc/X11/xorg.conf file and change your video driver from "via" to "vesa"   You will loose 3D video support, but you won't have the shared IRQ problems that are preventing your wireless from working.  I have the Averatec 33225 and the Unichrome S3 video driver in Linux does not work very well on this motherboard.

---

