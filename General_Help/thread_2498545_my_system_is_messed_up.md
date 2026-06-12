---
title: "my system is messed up"
date: 2024-06-18
forum: General Help
---

### Post by jgw on 2024-06-18
This morning, when I turned on my computer it was no longer hooked to the internet.  I tested the line and it was fine (using another machine right now).  So, something is wrong and I have no idea what it might be.  I normally have both network and network.  Now both are gone.  I figured i would use system-info to find out what is going on.  My problem there is that its been over a year since I have done that and want to make sure of stuff.  I have a system-info file which has been fixed to run.  It was made in 2021.  

I can use that file or should I download a new "system-info" file, then:
sudo chmod +x ./system-info
./system-info
which will get me the report and reason why my machine is screwed up (hopefully)

Thoughts?

---

### Post by deadflowr on 2024-06-18
I think running the older system-info should do, for now.
It should at least output the basics.
Newer versions have fixes and some added enhancements.
But I'm not sure if they'd output anything better.

If it doesn't output quality info, then you might try to grab a newer version.

---

### Post by yancek on 2024-06-18
What 'line' are you referring to that you checked?  Are you using an ethernet cable and you checked both ends?  Were you doing anything or making any changes yesterday that might have had an effect on your connection?      

>   I normally have both network and network. 

What exactly does 'network and network' mean?

Posting the output of system-info would be a good start.

---

### Post by jgw on 2024-06-19
Thank you for the reply!

I just saw the message come in as my mail is now working as is everything else.  I have no idea why.  It may have something to do with thunderbird, I just do not know.  I have read that, sometimes, ubuntu will get slow.  This has never happened to me so, again, I do not know.  I suspect I will just have to see what happens if I reset but I will defer to the next time I start this machine.  I also have another machine and that one started right off the bat when it came up so its my regular one that's a little snarkey.

Thanks again!

---

### Post by TheFu on 2024-06-20
Issues like this often are caused by a DNS hiccup.  Could be local or the remote DNS servers. Impossible to know now.  Network problems that are really DNS problems appear the same to most people.

---

