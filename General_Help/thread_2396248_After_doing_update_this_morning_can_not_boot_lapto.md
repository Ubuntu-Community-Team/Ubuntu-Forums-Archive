---
title: "After doing update this morning can not boot laptop."
date: 2018-07-12
forum: General Help
---

### Post by irv on 2018-07-12
I was asked if I wanted to do an update this morning and I said yes. It updated in the background and everything seem to go well. Did not get any error messages and it did not ask me to reboot. I was going to be gone all day, so when I finished uing it, I shut it off the normal way from the menu.
Now it will not boot up I keep getting this screen
[ATTACH=CONFIG]280378[/ATTACH]

I tried booting into repair mode and tried most of the options 
I can boot a USB live OS but I hate to have to do a complete new install because I have everything just the way I want it.
Any suggesting would be helpful.

By the way, it will not go into safe mode either.

---

### Post by irv on 2018-07-12
Once in a while, it will hang on this Line.
```
started Login Service Service.manger.dispatcher Service.....tem changes.pp link was shut down.....
```

---

### Post by #&amp;thj^% on 2018-07-12
Have you tried an older kernel?
And it has been said moving the mouse or spamming the shift key will get to a DE but not everyone had that luck but worth a shot.

---

### Post by irv on 2018-07-12
I have been pounding my head trying to come up with something that works, then we had a storm move into our area. I had to run outside and put the umbrella down on the patio-table so it wouldn't blow away. When I got back in the house the Internet went out. I was sitting at a Root prompt, and tried a few things like startx, logging in as myself and even did an update, upgrade but without the Internet, I didn't think that would work. I then exited out of the prompt back to the council 
I again tried the normal boot, and it went to the login and then the desktop.
I got the Internet back and I am afraid to try and shut the laptop off.
I am going to leave it run tonight and maybe I will get brave tomorrow and try a reboot.

---

### Post by irv on 2018-07-12
Okay, I got brave and tried a reboot. it was taking a long time to boot so I tried hitting the shift key and space bar and the enter key and then it came to the login screen. After getting back to the desktop, I tried powering it off and again it was taking forever to boot. I did the same thing hitting all the keys. it finaly came up again.
By the way, I did try an older kernel. 
I will play around more tomorrow.
Thanks for the help.

---

### Post by apeitheo2 on 2018-07-12
If pushing keys seems to bring up the login prompt faster, then you might have hit the bug that's going around right now.
```
sudo apt install haveged
sudo systemctl enable haveged
```
More information here: [https://ubuntuforums.org/showthread.php?t=2395459&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&p=13781140#post13781140)

Hope that helps. Good luck!

---

### Post by irv on 2018-07-13
Thanks for all the info, I am going to mark this thread solved for now. Yes, it seems to be the same issue as the one posted above.

---

