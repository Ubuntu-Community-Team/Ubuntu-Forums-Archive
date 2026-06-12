---
title: "Amazon instant video stopped working after updates."
date: 2013-04-11
forum: General Help
---

### Post by ERRRIMMAD on 2013-04-11
A heads up to some about a potential problem, (maybe) and hoping to figure this out for 100%.

 I have been installing a new hard drive to my computer, a crucial m4 SSD as my ubuntu os drive.

 during the install I had amazon instant video working using flash and hal, then I updated and it stopped.

 I wondered if amazon changed their feed, I checked my old drive and it worked fine, (keep in mind I did not update my old drive).

 I went back to my SSD and undid the edits I made to fstab and rc.local regarding the optimizing of my SSD.

No good, still had problems.

I checked the plugins for my web browsers, I seem to have the same web browser plugins installed, IE IcedTea, VLC, etcetera, still no amazon instant video.

 So finally I went and looked at the recent updates that might have broke the player, I noticed Macromedia Flash had a 8kb update recently, although I'm not sure this is the culprit.

Anyways, anyone have any ideas?

---

### Post by snowguy on 2013-04-12
I'm having the same issue. I believe the recent update to flash is the culprit. I haven't found a work around.

---

### Post by mlhudson on 2013-04-12
Same boat here! Hoping that there's a fix soon. I'm watching this thread, so if anyone hears the answer, please be kind and share! :)

---

### Post by ERRRIMMAD on 2013-04-12
I don't know exactly whats going on yet, I can tell you I have tried the following so far.

I reinstalled Ubuntu multiple times, I have not been able to get Amazon instant video to work so far, I have tried to repeat all the steps I took when I did get it working on my new SSD drive, no good so far, I can't seem to figure out what happened, I know for a fact amazon instant video was working on the new SSD drive, now I can't repeat the procedure successfully, what happened that made it different?

Anyways, I will try another install later, this time I will allow swap on the install because I messed up the first time and did not disable swap, I'm not 100% sure if amazon instant video worked the first time or second time I installed, meaning with or without the swap, if I need swap I'm thinking I can add a second rotational drive for that.

Anyways, I'll keep going until I get to the bottom of this, until then I will not upgrade my old rotational drive or I will lose amazon instant video.

---

### Post by snowguy on 2013-04-12
Here's my guess as to what is happening and why a reinstall isn't much help. The package is just a plugin installer, not the actual plugin. So even if you install the old version of the plugin installer, I wonder if it may be going and getting the new version of the plugin.  

I'm just guessing here and would love other people's comments.

Also, if any one else is a member of askubunt, you may want to follow my question there. 
[http://askubuntu.com/questions/280721/how-can-i-revert-to-previous-version-of-flash](http://askubuntu.com/questions/280721/how-can-i-revert-to-previous-version-of-flash)

So far no responses to the question. If  you think it is a good question please upvote it to get it more attention.

If I'm not able to resolve otherwise I may offer a bounty there. 

One thing I haven't had time to try is using the package adobe-flashplugin. I got the idea from looking at this old question: [http://askubuntu.com/questions/49298/whats-the-difference-between-flashplugin-installer-and-adobe-flashplugin](http://askubuntu.com/questions/49298/whats-the-difference-between-flashplugin-installer-and-adobe-flashplugin)

I haven't had a chance yet to see if the adobe plugin is still available in the partner repositories.

---

### Post by snowguy on 2013-04-12
Rob S posted the solution on the Amazon customer forum: [http://www.amazon.com/forum/amazon%20video%20on%20demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdMSG=addedToThread&cdPage=1&cdThread=Tx167YET6CH0PQI&newContentID=Mx3J1ILN68W9ZF7&newContentNum=15#CustomerDiscussionsNRPB](http://www.amazon.com/forum/amazon%20video%20on%20demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdMSG=addedToThread&cdPage=1&cdThread=Tx167YET6CH0PQI&newContentID=Mx3J1ILN68W9ZF7&newContentNum=15#CustomerDiscussionsNRPB)

and I reposted on the askubuntu question:
[http://askubuntu.com/questions/280721/how-can-i-revert-to-previous-version-of-flash](http://askubuntu.com/questions/280721/how-can-i-revert-to-previous-version-of-flash)

Given the solution, Errimand, it may be that when you are reinstalling ubuntu you are also updating to the latest version of all packages and this is why, even after reinstalling, your system is broken. In any case, let me know if the fix doesn't work for you. It did for me. Good luck.

---

### Post by ERRRIMMAD on 2013-04-13
Thanks, I'll give it a shot tomorrow, installing a swap did not change anything, I also installed offline and no change. 

I hope the solution you got works, thanks again. XD

---

### Post by NotteScura on 2013-04-13
My solution to this problem, revert back to the older version of Flash plugin (11.2.202.275)....

32-bit Download: [https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.i386.tar.gz](https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.i386.tar.gz)

```

tar -xzf install_flash_player_11_linux.i386.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins

```

64-bit Download: [https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.x86_64.tar.gz](https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.x86_64.tar.gz)

```

tar -xzf install_flash_player_11_linux.x86_64.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins

```

Credit for the links goes to SlackBuilds.org and Robby Workman (found here: [http://slackbuilds.org/repository/14.0/multimedia/flash-player-plugin/](http://slackbuilds.org/repository/14.0/multimedia/flash-player-plugin/) ).

Note: I have the 64-bit version installed, so I can't be positive that the instructions for 32-bit actually work.

---

### Post by ERRRIMMAD on 2013-04-13
Thanks Snowguy and Nottescura for your help.

It was flash, it's working now, Nottescura's solution worked best for me.

It might be of interest to others with my particular problem, my build was Ubuntu Studio 12.04, however I almost never worry about that because 99.9% of the time what works on Ubuntu also works on Ubuntu Studio for obvious reasons.

Strange, my first install I must have just downloaded the old version of flash right before they switched the repositories to the new version, then after amazon instant video was working I updated and that updated to the new flash, which broke everything.

Just a random coincidence.

Why the hell can't Ubuntu repositories just leave the old versions of flash and make it easy to revert back if they want, I mean what is the point keeping a version of flash in the repositories just because it's the latest, even when all it will do is break everything.

---

### Post by mlhudson on 2013-04-13
> **NotteScura said:**
> My solution to this problem, revert back to the older version of Flash plugin (11.2.202.275)....

32-bit Download: [https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.i386.tar.gz](https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.i386.tar.gz)

```

tar -xzf install_flash_player_11_linux.i386.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins

```

64-bit Download: [https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.x86_64.tar.gz](https://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.275/install_flash_player_11_linux.x86_64.tar.gz)

```

tar -xzf install_flash_player_11_linux.x86_64.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins

```

Credit for the links goes to SlackBuilds.org and Robby Workman (found here: [http://slackbuilds.org/repository/14.0/multimedia/flash-player-plugin/](http://slackbuilds.org/repository/14.0/multimedia/flash-player-plugin/) ).

Note: I have the 64-bit version installed, so I can't be positive that the instructions for 32-bit actually work.


Works for me on 64-bit also. Straight away. Heroic. Thank you!!

---

### Post by gmarcus2 on 2013-05-07
I have been having this same problem, and I'm really glad to see a solution here. I am not very technical, and I don't understand how to proceed. I have uninstalled flash from Safari, and I know that I am on a 32 bit Mac OS 10.6.8. I click the link, something downloads, but when I go back to the flash page, it still shows nothing is installed. Any help/suggestions would be greatly appreciated.

---

