---
title: "Very Slow Boot"
date: 2021-08-17
forum: General Help
---

### Post by jgw on 2021-08-17
I have a machine and it takes it a very long time to boot up.  The last time I started pushing buttons and, finally, got to see what was going on.  It paused, for a very long time, on something like; "no keyboard found".  This system plays back videos.  For the display and the sound it goes through a denon receiver.  I have never had a problem like this before but I suspect the denon.  My keyboard is wireless and works fine and is there all the time though and that should be enough.  This has been working for a very long time so I can't figure out why its behaving poorly now.  This started after I updated to 21.04

Thoughts?

---

### Post by Timothy Taylor on 2021-08-17
Your system is very similar to mine.
Maybe this something has something to do with the recent update and issues re NVIDIA graphics?

Try
> systemd-analyze blame

to see what's holding things up.

---

### Post by jgw on 2021-08-17
thanks for the reply.  Here it is:
```
greg@movies:~$  systemd-analyze blame 
3min 11.915s apt-daily-upgrade.service
     30.489s plymouth-quit-wait.service
     18.634s man-db.service
     16.783s snapd.service
     10.000s NetworkManager-wait-online.service
      9.482s networkd-dispatcher.service
      9.268s dev-sdb3.device
      7.375s udisks2.service
      5.227s logrotate.service
      4.677s dev-loop2.device
      4.668s dev-loop0.device
      4.660s dev-loop4.device
      4.628s dev-loop1.device
      4.597s dev-loop3.device
      4.585s dev-loop6.device
      4.509s dev-loop5.device
      4.480s dev-loop8.device
      4.469s dev-loop9.device
      4.425s dev-loop10.device
      4.360s dev-loop11.device
      4.336s dev-loop12.device
      4.232s dev-loop15.device
      4.158s dev-loop13.device
lines 1-23

```

---

### Post by oldfred on 2021-08-18
It looks like it is trying to do an update as part of boot. 
That should not be the default, but many have that issue.

And are you using snaps?
I uninstall all snaps & only use .deb versions.

Some settings to review & fixes:
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by mIk3_08 on 2021-08-18
> **oldfred said:**
> 
And are you using snaps?
I uninstall all snaps & only use .deb versions.


Thanks for this advise oldfred. I also use this trick long time ago and it helps my system to boot faster.
It was amazing. It works for my system very well. I suggest that you follow this advise 
and explore all the links that is oldfred is given you. It will help you a lot jgw. I assure you
you won't regret it. Good Luck and Enjoy.[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=382468")

---

### Post by jgw on 2021-08-18
Oldfred,

Thanks for the reply.

I think I found the problem.  That system is used to play movies and tv with Kodi.  I have an hdmi connection from the machine to a Denon Receiver which handles my video and audio.  The video part is gotten pretty strange (have a request to denon for that).  Anyway, I hooked the machine all up and then removed the connection to the denon and it took about 2/3 minutes to boot up.  After it was up I plugged in the denon.  I am starting to think I might be better off to hook it up directly along with the audio which I haven't trued yet but will today.

---

### Post by TheFu on 2021-08-18
Do not to use non-LTS releases unless absolutely mandatory. Using non-LTS releases is asking for problems. 

I usually wait a few months after the LTS before I start playing with it and wait a year before installing it into production.  For a media center, if I don't want to sleep on the couch, I'll make 100% certain it runs perfect, always, for years. My better half will put up with a few days  over 2-4 yrs with issues, but that's about it.  Happy wife. Happy life.

Avoiding issues is my first goal. Sometimes we can't avoid them. ;(

As for troubleshooting. If you think it is the keyboard, swap in a different keyboard. Use a wired one.  That solve it? If so, then you have the answer. If not, you can move on to other stuff.

---

### Post by mIk3_08 on 2021-08-19
> **TheFu said:**
> Do not to use non-LTS releases unless absolutely mandatory. Using non-LTS releases is asking for problems.

I absolutely agree with TheFu. non-LTS release (non-Long Term Support) will only make you trouble specially when you are a first timer user of Ubuntu Linux
Operating System. Definitely you will encounter more difficulty when using this non-LTS (non-Long Term Support) release in the long run.
So, That is why the Ubuntu community forum will only advise the LTS (Long Term Support) release Ubuntu Operating System for very Safe use for a new-user.
I think non-LTS release (non-Long Term Support) are for Quality Testing purposes only for the Ubuntu Linux expert users only.

---

### Post by jgw on 2021-08-22
Thank you for the replies!

Everything is now working and the boot is a lot faster.  I just started going down the suggestions, one after another and that seemed to do the job.  Oh, I didn't upgrade with a non-LTS, I waited.

---

### Post by ajgreeny on 2021-08-22
> **jgw said:**
> Thank you for the replies!

Everything is now working and the boot is a lot faster.  I just started going down the suggestions, one after another and that seemed to do the job.  Oh, I didn't upgrade with a non-LTS, I waited.
So did you reinstall 20.04, or what do you mean by the comment that you waited; waited for what?

If you are still using 21.04 you will have to upgrade to 21.10 eventually prior to the release of 22.04 next April or you will have an unsupported version running; very insecure and risky!
This is precisely why most users stick with the LTS versions as our daily system; these have support for either 5 or 3 years depending on which of the Buntu family OSs you use. If you do choose to use the intermediate versions, the non-LTS ones, you have to keep upgrading  every 6 months, more or less, to keep using a supported version.

---

### Post by jgw on 2021-08-23
I waited for 21.  I got 21.04 and have assumed that it was a long time support version.  I guess I was wrong so I will wait again.  Oh well...............

---

### Post by ajgreeny on 2021-08-25
Yes, the even year's versions released in April, ie 20.04, 22.04, etc etc, are the LTS ones, all others, including 21.04, have only 9 months support.

---

### Post by jgw on 2021-08-25
Thanks for reply and info!

I had no idea (obviously) and will probably forget.  Does this mean if one is released in 2022 (even) it will be or will they notify as LTS the one that is LTS?  If I remember correctly I was using 20.04 and I believed that 21.04 was replacing that and 20.04 would no longer be supported which is why I went to 21.04  I must have been wrong.

---

### Post by ajgreeny on 2021-08-25
Look at this page at the Get Ubuntu site, [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) and you will see there are two versions available, 20.04 LTS and the more recent 21.04, not shown as LTS.
As I said, 22.04 will be the next LTS version and following that will be 24.04, 26.04 etc, etc, where the first part of the number is the year, and the second half of the number is the month, ie, April.

---

### Post by jgw on 2021-08-25
Yep, I screwed up!  Comes under the heading of "getting schooled".  As before, I will wait.  The difference is that, this time, I will pay attention!  Thank you (really)!

---

### Post by jgw on 2021-08-26
I understand that.  Just have to live with it.  Don't want to go back to 20.04 so will move on to 21.10 when it comes along.  I have, however, been educated about this so I will pay attention.

---

