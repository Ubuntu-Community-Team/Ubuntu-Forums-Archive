---
title: "Ubuntu freezes"
date: 2007-01-12
forum: General Help
---

### Post by sheine on 2007-01-12
Recently Ubuntu has started to freeze. The pattern is that after being turned on, whether used  or not, things slow down, the cursor motion becomes jerky, and then the whole system freezes. If I shut off the power and restart, I get another hour of good service until the same thing happens.

At first I thought that it was an overloading of the memory by the caches in the browsers. But, even with lots of memory this still happens.

As a check on my hardware, I loaded another Debian based system, Simply Mepis. It operates well all day leading to the conclusion that my Ubuntu problem is not a hardware problem.

Any ideas? I do not want to reinstall Ubuntu as it is a nuisance.

---

### Post by awells527 on 2007-01-12
What's your memory and page file usage when your computer is slowing down?

---

### Post by mvaniersel on 2007-01-12
Have you checked how high the CPU usage is when the system gets slow? (See System->Administration->System monitor)

---

### Post by Iowan on 2007-01-12
Something getting hot??

---

### Post by sheine on 2007-01-12
The problem is that when it starts to freeze I cannot use my mouse to access anything including system information.

Right now my memory usage is 81% and CPU 8%.

---

### Post by sheine on 2007-01-12
If something is getting hot, I would have had trouble in Mepis.

---

### Post by sheine on 2007-01-15
Why would /usr/lib/opera use 35% of my memory even after I cleaned out the private data?

---

### Post by sheine on 2007-01-22
Since I could get no solution for my problem here, I tried it in linux forums. So far I have had no solution there either but two responses both of which say that they have switched to Mepis. Since Mepis is based on Ubuntu why should it work better?

---

### Post by Kuoi on 2007-03-03
I think I have the same problem like you are.

Is it like 'something' is scanning your hdd , and the hdd  is very busy ?

I can't get in to system info , or services to see what is 'scanning' , but will look for something.

I tried to full uninstall ClamAV (anti-virus) , but that didn't help.
Will look further.

Kuoi

---

### Post by Kuoi on 2007-03-03
BTW : I was  using Firefox and Songbird at the same time , last time I had the problem .

Maybe this helps ?
I've just uninstalled Beagle  ,see if this was the problem.

Kuoi

---

### Post by Kuoi on 2007-03-03
I've used Synaptic to uninstall "Beagle".
Then I've opened "System->Administration->System monitor" ( hope it's this , i have a Dutch Ubuntu ) , to see the running processes.
I've stopped ( right click the processes , and click "stop" ) the Beagle and Beagle-helper services, because they we're still running hard after the Synaptic uninstall.

I've restarted the computer , and the services are away it seems.
Let's see if it helps, but my guess is that this was the problem.

It's an indexing service , and it can take some memory when it starts indexing.
After a time it should be working much quicker , but it did the opposite on my computer.

It's still a guess, but I'm pretty sure.

Kuoi
.

---

### Post by Kuoi on 2007-03-05
I must say , I didn't had the problem anymore after uninstalling Beagle.

I bet you've Beagle on your Ubuntu.
If so , uninstall it.

Kuoi

---

