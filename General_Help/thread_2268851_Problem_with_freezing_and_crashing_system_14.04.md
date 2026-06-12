---
title: "Problem with freezing and crashing system 14.04"
date: 2015-03-12
forum: General Help
---

### Post by jesus-freak on 2015-03-12
I've been using Ubuntu since 12.10. I've used every release since that one and never had any issues at all. But when 14.04 came out I decided to make a change and I installed Deepin2014 (based on ubuntu 14.04). I really loved it and found it a very unique and fresh OS. However, it had a problem where it would start freezing up after being used for a few hours. Since it is a Chinese OS< I couldn't really get any help for it so I gave up and decided to try Ubuntu 14.04. At first it seemed fine but then it started doing the same thing as deepin. So when it happened in Ubuntu, I opened system monitor and I noticed that it was using quite a lot of Swap. I have 4GB of ram and while I was only using about 1.2GB at the time, the Swap was at 30% which I thought was a little odd. I tried changing the swappiness, I even turned off the swap to see if that changed anything but nothing seemed to work. I thought that it might be my memory going bad so I ran a memtest in the grub start up and let it run for 5 passes and it didn't find anything. Now, last night while I was working it was the worst ever. I was using 1.2GB I think and had Skype and a browser open and the swap went up to 100% (3GB) and one of the four processors was just nailed at 100%, even after I shut down skype and the browser it was just solid at 100%. SO I quickly checked the running processes to see which one was using all of the CPU. I selected "Show all" and looked carefully down the list. At that point there were only three things using the CPU - Compiz 3% Gnome system monitor 5% kswapd0 25% maxthon 5% Xorg 2%. Everything else was at zero. I have no idea what is going on here. Here is my computer [http://www.cnet.com/products/toshiba-satellite-a665-s6086-16-core-i3-370m-windows-7-home-premium-64-bit-4-gb-ram-500-gb-hdd/specs/]("http://www.cnet.com/products/toshiba-satellite-a665-s6086-16-core-i3-370m-windows-7-home-premium-64-bit-4-gb-ram-500-gb-hdd/specs/")

---

### Post by jesus-freak on 2015-03-12
Anyone have any ideas on this? I really need some help here!!

---

### Post by spier on 2015-03-12
Just a thougth, but I 'd try boot into an older kernel.

14.04.2 started freezes after a kernel upgrade, to 3.13.45. Booting  into 3.13.44 solves if for now.

---

### Post by jesus-freak on 2015-03-12
Thanks for the tip. I had not thought of that. I will try that and see if my work this evening goes any smoother. I will post later and report if that helped or not. Thanks again

---

### Post by jesus-freak on 2015-03-13
It doesn't look like it's a kernel as I downgraded and still had the same issue. Any other ideas?

---

### Post by spier on 2015-03-13
Hmm, I would investigate the hardware... Is it running too hot? 

Maybe booting  a liveCD to see what happens.

---

### Post by jesus-freak on 2015-03-20
Hey, sorry to take so long in replying but a lot happened since last time. First, I installed Xubuntu thinking that since it was a lighter OS that it might run better on my system. But it crashed shortly after install. I then re installed it and installed the programs that I need for work and once again it started acting up. One of the CPUs was always at 100% and it was using WAY to much ram. The only things I installed for my work were Skype, Skype call recorder, dropbox and Kingsoft Offcie. So I started digging around in the system monitor and found this process from Kingsoft Office that was running and using too much ram and CPU. I ended the process and the CPU dropped and the ram went down. So I un-installed Kingsoft office and installed Libre Office and I haven't had any issues since!! I'm still using Xubuntu and loving it! I'm not 100% sure that the problem is completely resulved so I will keep this thread open for a few more days and if everything behaves, then I will close it. Thanks for the help and be careful with Kingsoft Office. It looks really nice and has some cool features but wow, it has caused me nightmares.

---

