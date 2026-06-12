---
title: "apt-get kills system"
date: 2007-09-03
forum: General Help
---

### Post by Drok on 2007-09-03
I am new to Ubuntu, and attempting to update on Ubuntu server 7.04 (LAMP). I ran the commands
```

sudo apt-get update

sudo apt-get upgrade

```
both start downloading something (still new not sure what =/ ) and shortly after (within seconds,  well before anything is finished) the system shuts down completely. I don't think this is a hardware problem as from my windows box i was able to ftp half of the hard drives capacity worth of data to it without any problems. The server is an old sony vaio p2 400 it was able to run win98 fairly well ( as well as win98 ran at least) with 384? megs of ram.

If anybody has any possible solutions (or other methods of testing) to my problem i would be greatly appreciative of any feedback. 

My current thought is that for some reason data transfer from the internet is not functional. ( or apt-get is funky) I do have internet access through the server, ( i can ping google at least) so I know that the router is set up properly. quite frankly i am just confused!

---

### Post by southernman on 2007-09-03
How can you compare what is most likely a much newer box (regardless of OS), to a box that a typical Windows end user would consider a boat anchor? You can't!

It's almost assuredly a hardware problem! 1000's of people run apt-get or aptiutude commands all day without fail.

I suggest plopping in a CD and run a memtest on the box... just let it run overnight to get a good ideal if it's memory related at least. It could be a power supply going bad/overheating, flaking motherboard, flaky connections and so on.

---

### Post by PmDematagoda on 2007-09-03
Like what southernman said it must either be something with your hardware or you tinkered and damaged your Ubuntu OS, I've done apt-get many times and haven't got a problem upto now. 

And just because Windows 98 works doesn't mean XP will work or Ubuntu 7.04 will work because Windows 98 has lesser requirements than newer systems. 

I've had Windows 98 work in a PII 198MB RAM computer but if I've tried Ubuntu 7.04 it would work with extreme difficulty just the way XP did when I ran it on my computer. 

Why don't you try something lighter like Xubuntu? You might have more success.

All this said, getting back to topic:). Why don't you do the memory test as suggested by southernman?

---

### Post by Drok on 2007-09-03
Is there a way to do a mem test without the cd? the box currently does not have a cd-rom installed. If it were a memory issue, why would the system only shut down during an apt-get operation? I had a copy of phpbb3 installed on it, and I was accessing it through the network, and I can also transfer large files over the network without any issues. What is different about apt-get that would shed light on a memory issue?

would installing Xubuntu really provide any difference in performance, considering as I am currently running the server edition without any gui?

> **southernman said:**
> How can you compare what is most likely a much newer box (regardless of OS), to a box that a typical Windows end user would consider a boat anchor? You can't!

Im sorry for the bad sentence structure, I was able to upload through ftp from my windows box to my LAMP server over 3 gigs of data, with a sustained rate of about 2.2 MB/s. For this reason alone I don't think it would be a hardware issue. What would be so different between the two transfers? Why would one work and the other not?

---

