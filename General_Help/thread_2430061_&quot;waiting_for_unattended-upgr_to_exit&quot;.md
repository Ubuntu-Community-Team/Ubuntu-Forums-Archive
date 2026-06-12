---
title: "&quot;waiting for unattended-upgr to exit&quot;"
date: 2019-10-27
forum: General Help
---

### Post by djroff on 2019-10-27
Hey, this is probably a simple thing to fix, if you know Linux Terminal, but I don't yet.  There has to be a way to find and shut down a running application that isn't supposed to be running.  In this case, it's interfering with a software update.  I logged into Ubuntu (19.04) to make some changes today, and it asked me if I wanted to upgrade to 19.10.  I told it "Ask me later", because I didn't want to get into it at the time.  (Truth be known, I had already tried a few hours earlier, and the upgrade broke about 2/3 of the way through -- just went to a black screen with a blinking cursor, and sat there.  I wound up restoring from a backup, and shelving the upgrade for later, when the bugs are worked out.  But that's another story.)  I did, however, want to install the regular patch, so I opened Software Updater and started.  But when the progress bar opened, it froze at "waiting for unattended-upgr to exit".  It's been that way for a half-hour now, and nothing has gotten installed.  I didn't tell it to go ahead with the distro upgrade, as I said.  So why is it acting like there's an "unattended upgrade" in progress?  And how can I kill it, so life can go on?

---

### Post by kurt18947 on 2019-10-27
You're not the only one with "unattended upgrade" issues. I'm usually able to get past my problem one of two ways. First is to simply wait a few minutes, second is to open System Monitor and kill any processes that mention upgrade. I do think this is a bug.

---

### Post by Mark Phelps on 2019-10-27
I ran into a similar situation with 19.04.  It prompted to Upgrade, I said later.  I then did some other updates that were waiting and rebooted.

After I rebooted, it asked again -- so I accepted -- but like you, it hung on "waiting".  I waited 10 minutes and killed it.

A couple of hours later, I started the PC again, it asked again, I said OK -- and this time it worked -- and seemed to go OK.

I rebooted afterward and everything appeared to work OK in 19.10.

Then, the next day, when I started the PC (I shut it down overnight), it would not boot.  I tried typical repairs and none of them worked.  So, I used the USB stick I made of 19.10 and installed afresh. It's been a couple of days, and the fresh install worked.

I was surprised the update worked, because I usually don't do that -- but in actuality, it appears that it did not.

---

