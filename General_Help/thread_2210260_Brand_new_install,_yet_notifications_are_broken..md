---
title: "Brand new install, yet notifications are broken."
date: 2014-03-09
forum: General Help
---

### Post by Roasted on 2014-03-09
Hello friends. In the name of storage capacity for my work laptop, I just removed my SSD and put in a larger 2.5" HDD to house my VMs. I did a fresh install of Ubuntu 13.10 64 bit less than a day ago. So far all I've done is installed all of the necessary applications I need. Nothing crazy. No major tweaks. Only thing I did tweak wise was install the Unity Tweak Tool.

I found an article online that shows how you can reset Unity back to default, so I did that. After doing that and rebooting, notifications worked, so I suspected Unity Tweak Tool was to blame. Then ten seconds later my notifications stopped working when I noticed my Empathy icon was wiggling while I was not getting a chat notification in the upper right corner. Rhythmbox does the same thing when I have it minimized and I am hitting my media keys to play the next/previous song.

I didn't bring any hidden files or folders over from my old install on the SSD. I simply did a fresh install and rebuilt everything on my own. The only data I copied was raw data... documents, pictures, music, virtual machines, etc. That was it.

Is anybody else seeing this? With all of the 13.10 64 bit machines I have, I have never seen this once. Yet here on this laptop, I'm seeing it continuously. FYI - I was using this very laptop on the SSD with no issues, but since the fresh install with the new drive it's been a different story. The hard drive has been scanned and there are no errors on it.

EDIT - Reinstalled notify-osd, no change. Created another user, logged in, notifications work. I went back to my main user thinking for sure notifications would be broken, and therefore suggest that something hidden in my home directory was messed up... but nope... notifications now work (temporarily, I'm betting) on my main user just fine. It's almost frustrating that they work because the only thing that changed since they last didn't work was created a new user, which should have had zero impact on the issue.

---

### Post by Roasted on 2014-03-10
Notifications broke randomly again. I was in a conversation using Empathy with a buddy of mine and they were working fine. Out of no where while on Firefox I heard the beep for a new message, but saw no notification.

Come on... Anybody have any idea? Is anybody seeing anything like this?

EDIT - They fixed and broke themselves again all in the span of 5 minutes. Rebooted, notifications worked one time, next time, no dice.

EDIT II - While I was not having any other issues with this install so far, I did some checking. MD5's of the ISO matched fine, but I am unable to check the integrity of the DD on my flash drive. Reason being I run a 16 GB flash drive with multisystem on it, so it chainloads a bunch of different ISOs. Thing is, it just goes straight to the ISO, bypassing typical menu options (such as check disk for errors, etc), which left me unable to verify that the DD of Ubuntu was fine. I just redid that flash drive too, so perhaps it's worth considering that maybe there's an issue with it. Likewise, I have DD'd this particular flash drive a *lot* over the two years I've had it. It's the only flash drive I use for installing ISOs... so maybe it's beginning to get worn down. Who knows.

I opened up a brand new 4GB flash drive I had in my bag and DD'd Ubuntu 13.10 to it. Checked the disk, one error. Eh? I DD'd it again and checked the disk for errors TWICE. No issues on the 2nd DD. I did a full reinstall and so far I'm not having any issues. That said, it's early yet, so we'll see how this pans out... but if nothing else I just wanted to update this thread with some misc thoughts/trials.

---

