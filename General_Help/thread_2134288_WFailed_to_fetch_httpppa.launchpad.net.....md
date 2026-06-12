---
title: "W:Failed to fetch http://ppa.launchpad.net/...."
date: 2013-04-10
forum: General Help
---

### Post by Odee on 2013-04-10
Hi, i have an problem.
When i click to system settings and install upgrades i got an following error:
W:Failed to fetch [http://ppa.launchpad.net/intuitivenipple/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/intuitivenipple/ubuntu/dists/quantal/main/binary-i386/Packages)  403  Forbidden
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I tried already find a solution on other forums but nothing about intuitivenipple quantal dists.

Can you help me please?

---

### Post by ibjsb4 on 2013-04-10
> I tried already find a solution on other forums but nothing about intuitivenipple quantal dists.

I am not finding anything either.  You can uncheck it for now in software sources.  That will allow to you to update your system.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by Jason Kuzhively on 2013-04-17
Okay, I solved this problem. I knew this was a problem with the repositories as soon as I read the title. The thing your system failed to fetch seems to be something called intuitivenipple. You can fix this problem by going to the Software Sources and opening the Other Software tab in which will be listed your repositories. Disable the one that your system failed to fetch...

If the above method didn't work somehow then there is another way you can do this:

First, Open Terminal and type this command in
```
cd /etc/apt
```

Second, type in this command which will open a text file called sources.list
```
sudo gedit sources.list
```

Third, try to find the line that your system says it failed to fetch. It must be there. After you find it, *delete only that line... Nothing else*. Then simply save and close it.

After, you completed the above steps try running software updates or opening terminal and typing *sudo apt-get update. *&#8203;If everything goes fine, it should work.

---

### Post by Odee on 2013-04-24
It works, thank you two. I dont know what is intuitivenipple :)

---

### Post by Jason Kuzhively on 2013-04-27
Wait a second, Intuitive-Nipple?????? LOL!!! Damn, that is really funny!!! :D

---

