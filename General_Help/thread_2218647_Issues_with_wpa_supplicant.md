---
title: "Issues with wpa_supplicant"
date: 2014-04-21
forum: General Help
---

### Post by shadytv on 2014-04-21
Hi, I'm having several issues related to wpa_supplicant, on the last few releases of ubuntu it would randomly crash and i couldn't connect to to or see any wireless networks, so i could only have a wired network until the program was updated now when i try to resume from suspend apportcheckresume crashes and when I look at the bug report it says that wpa_supplicant is failing to come back up. This program is literally going to chase me back to Windows if i can't get any help. I need a reliable OS for school.

As for troubleshooting i have completely removed it from /sbin and copied a new one from a live CD, and formated/reinstalled ubuntu I'm on my last straw with this garbage program. Are there alternatives for this?

ANY replies would be helpful...

---

### Post by wieman01 on 2014-04-21
Hello, 

Don't give up just yet, I think your problems can be resolved. I know this is a cheap shot, but I created a HOWTO many years ago which should still work for you. Do you want to give it a try?

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Of course I cannot be sure if this will help resolved your problems altogether, but it's worth a shot.

---

### Post by shadytv on 2014-04-21
> **wieman01 said:**
> Hello, 

Don't give up just yet, I think your problems can be resolved. I know this is a cheap shot, but I created a HOWTO many years ago which should still work for you. Do you want to give it a try?

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Of course I cannot be sure if this will help resolved your problems altogether, but it's worth a shot.

Hi, Thank you for the reply! I reread what I wrote and feel i did a bad job explaining the problem. Back when I was on 13.04 and the beginning of 13.10. I had serious issues with wpa_supplicant crashing. This was fixed with an update to the software, but just last week I started noticing a problem with putting Ubuntu into suspend.The system would go into suspend fine but when I try to resume it, the system kills. I then looked at the crash reports in /var/log and found the error:

```
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
```

So this make me wonder why the particular software is giving me so many problems. I'm quite frustrated and I'm wondering if there are alternatives i could try.

PS. The laptop is a Toshiba Satellite A665-S6065 if that helps any....

---

### Post by wieman01 on 2014-04-22
I vaguely remember that I had issues with "suspend" as well before I decided to approach the matter in a different way. Hence I suggest that you give this tutorial a try. Like I said, it's no guarantee, however, there is a chance it does away with your wake-up problem. Want to try?

---

### Post by shadytv on 2014-04-23
I followed it step by step and I didn't seem to work :(. the only thing i really ran into was finding out that for whatever reason my "/etc/network/interfaces" file doesn't like when i add the line:

```

[COLOR=#000000]*auto wlan0*[/COLOR]
[COLOR=#000000][I]iface wlan0 inet dhcp
[/I][/COLOR]
``` 

I get the whole "waiting for network configuration" on startup (which of course it doesn't bring anything up). It still pulls down addresses through DHCP just fine without it though. 


I found a bug report that was similar to mine (different laptop)
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1301627"]
 https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1301627[/URL]

Except he gets it on boot up I ONLY get it when i resume from the crash. He also said that the fix was in an upstream kernel so I installed 3.15rc2 and it looks like part of the problem has been solved. By which, I mean I get to a log in screen and then the computer crashes. I have no problems like this in windows 7 or 8* so that rules out hardware issues. So lastly, I realized I upgraded my RAM recently so I up'd my swap size in hopes that this would do something and It didn't do a damn thing. I've been on nothing but Ubuntu for 5 years solid and this is the first problem that actually makes me want to abandon the OS altogether.

---

