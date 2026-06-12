---
title: "Make Lubuntu connect to hotspot"
date: 2024-09-17
forum: General Help
---

### Post by Donnie Love on 2024-09-17
My desktop uses Lubuntu (I don't know how to find out which version). I'm trying to connect to the hotspot on my phone (Galaxy A12), but it won't connect. It won't even try. Any idea why?

---

### Post by TheFu on 2024-09-20
Phone models change all the time.  

To get the version of almost any Linux, there is a file /etc/os-release Look at that.  Or run this command on Ubuntu:
```
lsb_release -a
```

Or you can run **inxi -bz**

If it is 18.04, like your profile says, that lost support in 2021, so you need to upgrade first.

---

### Post by Donnie Love on 2024-09-23
No, it's currently 21.10, which is also old I know but I don't have the hard drive space for yet another upgrade. I just want to be able to connect to my hotspot when the house Internet (frequently) goes down.

---

### Post by TheFu on 2024-09-23
21.10 lost support in July 2022, at the latest, probably before then.

Really need to stick with LTS releases and if you use Lubuntu, know that LTS supports ends 3 yrs after the release date, so moving to a newer release is required.  The next LTS release would be available every even year in April, so 3 yrs of support means you don't have to be in a hurry to migrate.   Around now is the time for skittish people to install 24.04.1 if they were running the prior 22.04.x release.

There's a point where a fresh install is needed.  In general, I do 1 upgrade then a fresh install for LTS-to-LTS-to-LTS movements  that's 
[LIST]
[*]fresh install (18.04)
[*]upgrade (20.04)
[*]fresh install (22.04)
[*]upgrade (24.04)
[*]fresh install (26.04)
[*]...  repeat. ....
[/LIST]
You get the idea.

I understand that this isn't what you want to hear.  Supporting unsupported releases isn't easy, especially in these forums. It is also harder to upgrade to a new release AFTER the old release has already lost support, so make certain that when it is time to upgrade, you don't wait too long.  I use that fancy calendar to schedule upgrades well in advance, since Ubuntu has made their release schedules extremely predictable.  We are smart humans. We can predict some things in the future, like when it is time to upgrade or do a fresh install of our Ubuntu systems.

---

### Post by Donnie Love on 2024-09-24
I avoid it as long as I possibly can. I hate upgrades.

---

### Post by guiverc on 2024-09-24
[Lubuntu 21.10 is END OF LIFE.]("https://lubuntu.me/lubuntu-21-10-end-of-life-and-current-support-statuses/")

---

### Post by yancek on 2024-09-24
>  I avoid it as long as I possibly can. I hate upgrades. 				

Which is a good reason to only install LTS releases not the short term 9 month support releases.

What steps have you tried to get you hotspot working.  Some details on steps you have taken and the results might help other to help you although I don't know that many members will be willing to help you to access the internet while using an unsupported, insecure system.

---

### Post by Donnie Love on 2024-09-24
I always use the LTS versions.
Beyond trying to connect, I don't know  what other steps to take. I took a look at the settings on both the  desktop and the phone, but I don't know what to do there. I could do  more damage than good tinkering around in there.

---

### Post by ajgreeny on 2024-09-24
> **Donnie Love said:**
> I always use the LTS versions.
Beyond trying to connect, I don't know  what other steps to take. I took a look at the settings on both the  desktop and the phone, but I don't know what to do there. I could do  more damage than good tinkering around in there.
If you are now using Lubuntu 21.10 you must know that is not an LTS version and as others have said, is way beyond its EOL time so obviously you don't always use LTS versions.

I recommend that you forget about upgrading and simply do a clean install of the current LTS version 24.04.1, so backup all your/home folders and files, install the new version then restore those /home contents.

To upgrade to 24.04 from 21.10 is not a sensible option though you could upgrade to 22.04 which is supported for another 7 months and then move from that previous LTS to the current one.

Personally I would just bite the bullet and clean install 24.04.01; much quicker, easier and less likely to cause major problems.

---

### Post by Donnie Love on 2024-09-24
I would rather do the clean installation. But I currently don't have the space to back up everything right now. That's why I've waited so long; I wasn't just being obstinate. 

I *usually* get the LTS versions. I don't remember why I got the one I have now. That was years ago.

---

