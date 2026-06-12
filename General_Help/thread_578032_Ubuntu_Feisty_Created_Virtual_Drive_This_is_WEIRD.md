---
title: "Ubuntu Feisty Created Virtual Drive? This is WEIRD"
date: 2007-10-16
forum: General Help
---

### Post by Hopworks on 2007-10-16
I caused this weird thing, and now I'm not sure how to get out of it. A little long-winded, please bare with me.

Over the weekend, I had a PSU start to fail, and my Linux box was locking up, rebooting, and drives were disappearing. I just added a lot of apps, so I figured I hosed the install somehow. Hardware failures always seem to happen to me when I do something software related, adding to the list of things to think about through the diagnostic process.

Anyway, in the process of diagnosing the problem with my machine, I had disconnected the second drive (power and cable). When I put the new PSU in, I had forgot to reconnect the drive. This is where it gets really weird, at least for me.

I have hellanzb set to put processed archives on that second drive, and after the new PSU went in, I was doing just that. I didn't notice any problems because there was a second drive to me, and I accessed files on it. This morning when I rebooted the machine, I had noticed in the raid controller that there was just one drive, not two. I thought my problems were happening all over again! But when I looked inside, I saw the cables were not even connected. That realization drew strange looks from my son, as he looked at me and said "you look like you just seen a ghost". That's when it hit me. How can this be??? I accessed that drive just last night!!! Glitch in the matrix maybe? All sorts of ideas popped into my head.

At least I thought I accessed that drive last night, or the folder that resides on it, or was it Sunday. Now I was second guessing my memory (in my head), so I just reconnected it, and went on my way.

Now I found two drives in /media. disk and disk-1. You have got to be kidding me!!! So, now that I think about it, hellanzb created a folder that looks like that drive.

At least now I know what happened. If my head wasn't so cluttered with Windows ways of doing things, I might have known what happened. Live and learn.

SO! To make sure I get that data BACK onto the second drive where it belongs, I need to know what "disk" is really that second drive. Is there an easy way to tell what drive a folder resides on?

And then what, just rename that "disk-1" to "disk" when I clear the other out?

Thanks for your time!

Hop

---

