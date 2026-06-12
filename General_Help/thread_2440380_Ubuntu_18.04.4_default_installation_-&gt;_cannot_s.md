---
title: "Ubuntu 18.04.4 default installation -&gt; cannot switch user"
date: 2020-04-09
forum: General Help
---

### Post by rory4ever on 2020-04-09
Hi,

After a default installation of Ubuntu 18.04.4. desktop (x64) I created a few additional users. 
I tend to switch a lot between those users so it's a must for me to be able to do this without any problem. 
At first it works ok but after a while Ubuntu won't let me switch users anymore. When I click on 'switch user' the screen turns black for 4-5 seconds and I get the lock screen and I need to fill in my credentials for the current user. 
I can click on "change user" in that screen but it does just the same. 
Maybe a running process blocking stuff? I just want to get the user list when I click on 'switch user" 

Any advise is much appreciated. If no solution can be found, a workaround will do.

---

### Post by DuckHook on 2020-04-09
Welcome to the forums. rory4ever,

Each user takes up a significant chunk of RAM. Depending on the number of users, what apps each user has up and running and your amount of system RAM, you could be exhausting your RAM and offloading processes to SWAP. Too much of that and you start thrashing. Even without thrashing, SWAP is hundreds of times slower than RAM.

Why do you need so many users? How many do you have running concurrently? What is your end goal? Perhaps there's another way to achieve this without spawning a whole bunch of users.

Though there's not really enough info to go on, if you must run lots of users, then it's long established knowledge that lots of system RAM is essential. The more the better.

---

### Post by rory4ever on 2020-04-09
> **DuckHook said:**
> Welcome to the forums. rory4ever,

Each user takes up a significant chunk of RAM. Depending on the number of users, what apps each user has up and running and your amount of system RAM, you could be exhausting your RAM and offloading processes to SWAP. Too much of that and you start thrashing. Even without thrashing, SWAP is hundreds of times slower than RAM.

Why do you need so many users? How many do you have running concurrently? What is your end goal? Perhaps there's another way to achieve this without spawning a whole bunch of users.

Though there's not really enough info to go on, if you must run lots of users, then it's long established knowledge that lots of system RAM is essential. The more the better.

Thanks. Yes, it makes sense that RAM can be a bottleneck. But to be honest.. I only have 3 users and sometimes only 1 of them has a browser session open and even then switching users won't work. I have 16GB of RAM so that should be quite sufficient. 
I also don't experience a "lag" or delay of some kind when switching users, all I end up with is the lock screen while I expected the user list screen...

---

### Post by DuckHook on 2020-04-09
My bad. I didn't read your initial post thoroughly. I now understand your issue.

You do indeed have sufficient RAM. This should not be the problem. I'm afraid that I'm of little help here. I have only the one user on my system and don't want to create another, so experimentation is not possible.

If I understand you properly this time, your problem is that "switch user" doesn't actually permit you to switch users. It just shoots you back to the first user's unlock screen, depriving you of the chance to choose. Never heard of this behaviour before. Hopefully, someone else with multiple users already set up will see this thread and give some guidance.

---

### Post by rory4ever on 2020-04-10
> **DuckHook said:**
> My bad. I didn't read your initial post thoroughly. I now understand your issue.

You do indeed have sufficient RAM. This should not be the problem. I'm afraid that I'm of little help here. I have only the one user on my system and don't want to create another, so experimentation is not possible.

If I understand you properly this time**, your problem is that "switch user" doesn't actually permit you to switch users. It just shoots you back to the first user's unlock screen, depriving you of the chance to choose**. Never heard of this behaviour before. Hopefully, someone else with multiple users already set up will see this thread and give some guidance.


Yes, that's the issue. The only way to switch users is by logging out the current user. I've had this issue also with my previous installation and as a workaround I used XUBUNTU (which uses XFCE if I remember correctly) and I was able to switch users without any problem, with every situation or configuration and with even 5 users. I didn't like the desktop environment though so I ditched it.

---

### Post by silentstone on 2020-04-10
Are you actually able to login to all of your users when none are currently logged in?
Can you run multiple simultaneous GUI sessions with different users logged in? you know, CTL+ALT+F6...

---

### Post by rory4ever on 2020-04-11
> **silentstone said:**
> Are you actually able to login to all of your users when none are currently logged in?
Can you run multiple simultaneous GUI sessions with different users logged in? you know, CTL+ALT+F6...

yes, and yes :) 
It's only occurring maybe 50% of the time. When I reboot I can always switch user without any issue..

---

### Post by silentstone on 2020-04-12
Ok, so users and permissions are set up correctly. Check logs, especially for xorg/xsession/wayland and display manager?

---

