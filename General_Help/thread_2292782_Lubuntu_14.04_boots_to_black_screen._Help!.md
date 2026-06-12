---
title: "Lubuntu 14.04 boots to black screen. Help?!"
date: 2015-08-31
forum: General Help
---

### Post by cordy2 on 2015-08-31
I installed Lubuntu on my old laptop about four months ago and it's been working great. Until yesterday, that is. I booted up as usual, the Lubuntu loading screen appeared, and when the login screen should have popped up, it just stayed eternally dark. 

I pressed esc during the loading screen to get the command line screen where it asks you your login and password. I've tried sudo apt-get update among some other things. I booted up in recover mode and it says: 'Starting LightDM Display Manager [fail]', and below that it says 'initctl: Event Failed'. 

Does anyone know how to fix this? 

(I'm still a noob regarding Linux, so an easy explanation would be most appreciated!)

---

### Post by mörgæs on 2015-09-01
Hi, welcome to the fora.
Have you tried booting into an older kernel?

---

### Post by timotheus3 on 2016-01-14
im no expert, but you could try reinstalling lubuntu-desktop by using, it may get it working again or it may not, i would review the logs first though to see if you can pin down the problem

```
sudo apt-get install --reinstall lubuntu-desktop
```
or 
```
sudo aptitude reinstall lubuntu-desktop
```

---

### Post by greengeek2 on 2016-02-10
Hello, I'm having same issue. I have a Dell Inspiron 1501 (AMD64 AthlonX2) with Lubuntu 14. I've read several threads and researched for last 2 days with no luck.

When I start, the monitor/screen flashes a few times then goes black. 

I've tried  a cd boot repair and a live cd. I also tried connecting laptop to another monitor with no luck. Can't acccess grub/terminal either. 

Any ideas? Thanks for any input.

Apologies if on wrong thread. Let me know if I should start a new one. Again, thanks in advance.

---

### Post by mörgæs on 2016-02-11
Are you able to get any kind of system running, live boot or installed, perhaps with something like Bodhi Linux or Puppy?

---

### Post by greengeek2 on 2016-02-11
Hi! As I mentioned in my first post, I've tried a boot repair CD and a Lubuntu CD. The screen flashes a few times. However, when I do both, I can VERY faintly see the screen i.e. for the Lubuntu cd, I see the languages (english is highlighted). 

And I've read so many try this/try thats....I've pressed enter, esc, ctrl alt, etc...
don't know the exact steps to do, like should I press the keys first then power on or power on then tap key(s)? Not sure. 

And everything I've read, people can get into grub which I can't.

Any help is appreciated.

PS: Logging out, will check back in abt 7-8 hrs. Sleep happens. ;) Thanks again.

---

### Post by mörgæs on 2016-02-11
When you attach an external monitor which keys did you press in order to send the picture to the monitor?

> **greengeek2 said:**
> The screen flashes a few times. However, when I do both, I can VERY faintly see the screen i.e. for the Lubuntu cd, I see the languages (english is highlighted). 


That sounds like a broken inverter. If you google the symptoms for that or watch it in Youtube, does it match what you see?

---

### Post by greengeek2 on 2016-02-11
When I attach an external monitor, it stays black no matter what key I press. It worked the first time I connected. Then I did the apt-get update/apt-get upgrade and that's when external monitor quit working with laptop.

Would like to know how to remotely remove drivers from the laptop (if possible from my Lubuntu desktop) to see if that can be a problem as well. Or can I re-install Lubuntu with out wiping the drive and starting over. Am looking at broken inverters to see if that may be the problem. 

Thanks for all of your help!

---

### Post by mörgæs on 2016-02-13
> **greengeek2 said:**
> When I attach an external monitor, it stays black no matter what key I press. It worked the first time I connected.

Yes, but I asked which keys you pressed in order to redirect the video signal.

Removing drivers is normally not necessary (and often not possible) in Buntu. In stead of wrangling 14.04 I suggest that you try Lubuntu 15.10 in a live boot.

---

