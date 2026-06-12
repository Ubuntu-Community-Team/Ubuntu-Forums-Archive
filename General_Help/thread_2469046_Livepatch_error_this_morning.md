---
title: "Livepatch error this morning"
date: 2021-11-18
forum: General Help
---

### Post by sussexlad on 2021-11-18
Livepatch is reporting "An error occurred when checking for Livepatch updates" this morning.

What to do please ?

---

### Post by sussexlad on 2021-11-18
To answer my own question, I followed the instructions here and updated my subscription.   [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

Well, I thought it had cured it by enabling Livepatch - icon turned green - but on reboot, it's again gone red, so not the answer.

Any advice appreciated.

---

### Post by thanantonop on 2021-11-18
Hi, 
I am facing the same from last night. I have also opened a new post for that. Maybe it's something general to many users.

---

### Post by sussexlad on 2021-11-18
If I run 'sudo ua detach' followed by 'sudo ua attach (XXXXpasscodeXXXXXX) it then works and the icon turns green, until next restart.   :-(

---

### Post by mIk3_08 on 2021-11-18
> **sussexlad said:**
> If I run 'sudo ua detach' followed by 'sudo ua attach (XXXXpasscodeXXXXXX) it then works and the icon turns green, until next restart.   :-(
First thing disable the livepatch by using the command below.
```
sudo snap run canonical-livepatch disable
```
Then second remove Livepatch
```
sudo snap remove canonical-livepatch
```
Remove the machine ID
```
sudo rm /etc/machine-id
```
setup new machine id
```
sudo systemd-machine-id-setup
```
Then do a clean Install with new Livepatch then restart
```
sudo snap install canonical-livepatch 
```

---

### Post by thanantonop on 2021-11-18
The same also for me. It seems that it's something as general issue and not to only you

---

### Post by sussexlad on 2021-11-18
Have tried that but still had to detach and reattach to get the green icon. As others have suggested, it look like a more general issue. Thanks.

---

### Post by thanantonop on 2021-11-18
I did the same, i detach and then I rettach and i had green status but on the next reboot i had the same issue again. In the logs i see this error on my side:
Failed to refresh patch information: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/ad3220e57a634fb3a1ff5032ed270%3E

---

### Post by sussexlad on 2021-11-19
Well, interestingly, this morning, Livepatch has reported an available update and applied it as usual, despite the icon still being red, so it appears to be  a rather trivial defect.
Be good to get it right though.

---

### Post by mIk3_08 on 2021-11-19
> **sussexlad said:**
> Have tried that but still had to detach and reattach to get the green icon. As others have suggested, it look like a more general issue. Thanks. Do a ua detachment. Be sure you have secured your Ubuntu advantage account so that you can run your subscription token. 
```
sudo ua detach
```
attach with your new token.
```
sudo ua attach
```

---

### Post by sussexlad on 2021-11-19
Thanks for the suggestion but the icon still returns to red following the next restart/reboot. Your procedure then turns it green, until the next time !
As Livepatch still appears to be working, I'm inclined to ignore it.

---

### Post by mIk3_08 on 2021-11-20
> **sussexlad said:**
> Thanks for the suggestion but the icon still returns to red following the next restart/reboot. Your procedure then turns it green, until the next time !
As Livepatch still appears to be working, I'm inclined to ignore it.
I think you should wait for the updates. the Livepatch is already on but the icon turns red. you can manually turn it to disable and turn it back on vice versa for the meantime every time you turn your computer on while waiting for the update of your Livepatch. No worries this will be okay eventually. 
So Good Luck and cheers.

---

### Post by pantazi on 2021-11-20
Unsure whether the Livepatch error is significant, but since the red icon appeared, I've been unable to access two bank accounts, the login page hangs on both.
I use  Brave browser but have access to the accounts via Firefox with no problem.

As above, I think it will resolve itself and hope that is my problem solved.

---

### Post by rocco.martinello on 2021-11-20
Hi to all,


here in Italy (Boves, not very far from Turin) the same problem (It started yesterday).
Probably it is a global problem and I hope that it will be fixed as soon as possible.

---

### Post by deadflowr on 2021-11-20
I never have this error, but then again I run it on a server, which is always on, so I never run into reboot issues with it.
The issue is probably more of a desktop-centric notification issue than a live patch issue.

Best to run the commands listed in the FAQ page: [https://ubuntu.com/security/livepatch/docs/faq]("https://ubuntu.com/security/livepatch/docs/faq")
```
snap info canonical-livepatch
canonical-livepatch status
lsb_release -a
uname -a
journalctl -u snap.canonical-livepatch.canonical-livepatchd | tail -100
```
that should give some useful info about what's happening.

How many users who run livepatch on the desktop version still reboot the system with regularity?
Seems moot.

It should also be of note if you run normal updates, those will install newer kernels, which will also notify you of any required reboots.
These updated kernels are always fully patched, and in some cases patched earlier than the patches for the livepatched would be.

That said, I would recommend users who are somewhat security-minded to sign up for security notices here:
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce")
Livepatch notices are included.

---

### Post by rocco.martinello on 2021-11-20
Hello deadflowr and thank you very much for your answer!!!
I did what you told me and the results are the following:

```
rocco@rocco-desktop:~$ snap info canonical-livepatch
name:      canonical-livepatch
summary:   Canonical Livepatch Client
publisher: Canonical&#10003;
store-url: https://snapcraft.io/canonical-livepatch
contact:   snaps@canonical.com
license:   unset
description: |
  Canonical Livepatch Client
commands:
  - canonical-livepatch
services:
  canonical-livepatch.canonical-livepatchd: simple, enabled, active
snap-id:      ******************************** [I replaced the id with asterisks.]
tracking:     latest/stable
refresh-date: yesterday at 13:41 CET
channels:
  latest/stable:    10.0.1 2021-11-17 (119) 9MB -
  latest/candidate: 10.1.0 2021-11-18 (123) 9MB -
  latest/beta:      10.1.0 2021-11-18 (123) 9MB -
  latest/edge:      10.1.0 2021-11-18 (123) 9MB -
  core20/stable:    10.0.1 2021-11-17 (121) 9MB -
  core20/candidate: 10.1.0 2021-11-19 (125) 9MB -
  core20/beta:      10.1.0 2021-11-19 (125) 9MB -
  core20/edge:      10.1.0 2021-11-18 (125) 9MB -
  core18/stable:    10.0.1 2021-11-17 (122) 9MB -
  core18/candidate: 10.1.0 2021-11-18 (124) 9MB -
  core18/beta:      10.1.0 2021-11-18 (124) 9MB -
  core18/edge:      10.1.0 2021-11-18 (124) 9MB -
  core/stable:      10.0.1 2021-11-17 (119) 9MB -
  core/candidate:   10.1.0 2021-11-18 (123) 9MB -
  core/beta:        10.1.0 2021-11-18 (123) 9MB -
  core/edge:        10.1.0 2021-11-18 (123) 9MB -
installed:          10.0.1            (119) 9MB -
********************************************************************************
rocco@rocco-desktop:~$ canonical-livepatch status
ERROR: ld.so: object 'libesets_pac.so' from /etc/ld.so.preload cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object 'libesets_pac.so' from /etc/ld.so.preload cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object 'libesets_pac.so' from /etc/ld.so.preload cannot be preloaded (cannot open shared object file): ignored.
last check: 45 minutes ago
kernel: 5.11.0-40.44~20.04.2-generic
server check-in: succeeded
patch state: &#10003; no livepatches needed for this kernel yet
tier: updates (Free usage; This machine beta tests new patches.)
machine id: ******************************** [I replaced the id with asterisks.]
********************************************************************************
rocco@rocco-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal
********************************************************************************
rocco@rocco-desktop:~$ uname -a
Linux rocco-desktop 5.11.0-40-generic #44~20.04.2-Ubuntu SMP Tue Oct 26 18:07:44 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
********************************************************************************
rocco@rocco-desktop:~$ journalctl -u snap.canonical-livepatch.canonical-livepatchd | tail -100
nov 20 15:30:10 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 15:30:10 rocco-desktop canonical-livepatch[947]: Failed to refresh patch information: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/********************************/updates" failed. [I replaced the code with asterisks.]
nov 20 15:30:10 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 15:30:10 rocco-desktop canonical-livepatch[947]: Task "refresh" returned an error: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/********************************/updates" failed, retrying in 30s. [I replaced the code with asterisks.]
nov 20 15:30:37 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 15:30:37 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 15:30:37 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:30:37 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 15:30:37 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 15:30:37 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 15:30:37 rocco-desktop canonical-livepatch[947]: Task "refresh" completed succesfully after 1 retries.
nov 20 15:32:09 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:09 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:09 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:27 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:37 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:37 rocco-desktop canonical-livepatch[947]: Disabling client using resource token.
nov 20 15:32:39 rocco-desktop canonical-livepatch[947]: Registering client with authorization token.
nov 20 15:32:40 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 15:32:40 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 15:32:40 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:40 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 15:32:40 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 15:32:40 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 15:32:40 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:41 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:42 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:32:42 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:34:54 rocco-desktop canonical-livepatch[947]: Error in livepatch check state: check-failed.
nov 20 15:34:54 rocco-desktop canonical-livepatch[947]: Sending client deregistration request to server.
nov 20 15:34:54 rocco-desktop canonical-livepatch[947]: Cannot disable machine: no content.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Updating config.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Config change detected, signaling restarting.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Server received context done, stopping.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Server received context done, stopping.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Socket server shutting down.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Periodic worker "refresh" received context Done, stopping.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Received context done signal (context canceled), stopping kernel event listener.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Socket server shutting down.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Detected config change, reloading.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Starting client daemon version 10.0.1.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Client daemon started.
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Starting periodic worker "refresh".
nov 20 15:36:02 rocco-desktop canonical-livepatch[947]: Livepatch client not enabled, skipping refresh.
nov 20 15:36:04 rocco-desktop canonical-livepatch[947]: Validating client resource token.
nov 20 15:36:04 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 15:36:04 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 15:36:04 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 15:36:04 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 15:36:04 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 16:43:32 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 16:43:32 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 16:43:32 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 16:43:32 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 16:43:32 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 17:32:49 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 17:32:49 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 17:32:49 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 17:32:49 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 17:32:49 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 18:18:34 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 18:18:34 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 18:18:34 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 18:18:34 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 18:18:34 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 19:19:56 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 19:19:56 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 19:19:56 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 19:19:56 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 19:19:56 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 20:16:40 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 20:16:40 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 20:16:40 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 20:16:41 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 20:16:41 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 21:30:48 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 21:30:48 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 21:30:48 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 21:30:48 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 21:30:48 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 22:24:56 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 22:24:56 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 22:24:56 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 22:24:56 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 22:24:56 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 20 23:27:37 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 20 23:27:37 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 20 23:27:37 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 20 23:27:38 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 20 23:27:38 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 21 00:37:56 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 21 00:37:56 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 21 00:37:56 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 21 00:37:56 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 21 00:37:56 rocco-desktop canonical-livepatch[947]: No patch payload available.
nov 21 01:44:41 rocco-desktop canonical-livepatch[947]: Client information is recent, not refreshing.
nov 21 01:44:41 rocco-desktop canonical-livepatch[947]: Processing machine status.
nov 21 01:44:41 rocco-desktop canonical-livepatch[947]: Sending status update the livepatch server.
nov 21 01:44:41 rocco-desktop canonical-livepatch[947]: No updates available at this time.
nov 21 01:44:41 rocco-desktop canonical-livepatch[947]: No patch payload available.
```
What do you think about it?
I tried to change the ID provided by Canonical on their website, but no luck.
I tried to uninstall and install again LivePatch, but no luck.
I tried the command ```
sudo canonical-livepatch refresh
```, but no luck.
I tried to reinstall the update ```
ubuntu-advantage-tools 27.4.1~20.04.1
```, but no luck. (I don't know if this update can be related to the problem.)
I gave the commands above while the "LivePatch shield" has the "Green mark". Rebooting the shield acquires the red mark.
How can I solve this problem?

---

### Post by nickt2 on 2021-11-21
It appears that my error has vanished now (0921 GMT, November 21st), without intervention from me.

---

### Post by pantazi on 2021-11-21
Mine still there (1000 GMT)

---

### Post by nickt2 on 2021-11-21
> **pantazi said:**
> Mine still there (1000 GMT)

And now it has come back again on my machine. I don't think I'll post anything else on this forum or on Ask Ubuntu, for fear of writing misleading information. I think I'll leave it up to Canonical to fix this properly

---

### Post by sussexlad on 2021-11-21
> **deadflowr said:**
> I never have this error, but then again I run it on a server, which is always on, so I never run into reboot issues with it.
The issue is probably more of a desktop-centric notification issue than a live patch issue.

I suspect you are correct. I run both a DT and a LT and there is no issue with the LT.
Even the DT comes up green, around 1 in 10 boots so it might even be a timing issue of some kind ??
Still as I said, the updates still appear, so not too serious - just good to have things right.

---

### Post by rocco.martinello on 2021-11-22
Hi to all,

I submitted a bug on Launchpad to the following URL:
[https://bugs.launchpad.net/ubuntu/+bug/1951817](https://bugs.launchpad.net/ubuntu/+bug/1951817)

Best,

Rocco

---

### Post by mIk3_08 on 2021-11-22
I just booted my Linux Ubuntu machine right now and my Livepatch turns to be okay now. I don't know what happen but its alright now. I haven't received any updates but My Livepatch Icon is working okay now. Back to the full operation now with no errors. Cheers.

---

### Post by pantazi on 2021-11-23
Mine ok as well. Still have problem logging into banking, but that appears to be a Brave browser script issue.

---

### Post by sussexlad on 2021-11-23
+1. Been OK for several starts now.

---

### Post by mIk3_08 on 2021-11-24
> **pantazi said:**
> Mine ok as well. Still have problem logging into banking, but that appears to be a Brave browser script issue.
Have you tried other web browser like Firefox or any other?  Maybe other web browser will work. Firefox web browser for me works smoothly and I haven't encounter any errors on it since I used it. It only crashes sometimes but it will be okay then when it restarts.

---

### Post by pantazi on 2021-11-25
Firefox works ok, thanks, I had already tried it. See#13.  After a bit of research I enabled scripts for the two sites and now all ok.   Don't know why it happened as no settings had been altered, maybe an update caused it. Anyhow thanks for taking the time to help.

---

### Post by slaytanicprion on 2022-01-12
I'm having (maybe?) a similar issue. Today there was a lot of updates, including kernel update and CVE's being corrected. Livepatch hasn't installed them in advance, unlike the last time such a thing happened (2 weeks ago maybe, after I got Livepatch working on Ubuntu Mate, which isn't that obvious and demands a lot of research and even then modifying what you find to make it work. Isn't it supposed to catch all the kernel and CVE correcting updates in advance without needing to reboot? I didn't reboot and there's nothing new according to Livepatch. I'm starting to think those who say it is not a very useful feature are right. But maybe I'm not understanding things correctly. There was a lot of updates to very old kernels 4.x.x in the updates today, I wonder why that is and why I had to install them, but I did, it went on fine, because they were all interlinked with relevant updates.

---

### Post by slaytanicprion on 2022-01-12
> **mIk3_08 said:**
> Have you tried other web browser like Firefox or any other?  Maybe other web browser will work. Firefox web browser for me works smoothly and I haven't encounter any errors on it since I used it. It only crashes sometimes but it will be okay then when it restarts.  I agree, the old sly Fox is the best, those complaining about memory usage were right around the time Quantum came out (v.60 I think?), my complaint was a lot of important add-ons were not working anymore, but I got an AMD with 8 cores and 32gb of Corsair Vengeance Pro RAM, same setup since years in fact, not about to change motherboard to have DDR4 or is it DDR5 already now?   Anyways, Brave looked very promising when it first came out, but it was even more of a memory hog than FF and then I learned some rather unsettling things about it....that I can't recall now, the users are all pointing at the intro page that shows how many trackers its blocking and it is making crypto with participating websites (when almost no websites participate in their BAT crypto, I don't see the point of that), but with the correct add-ons on FF, you can make as private as possible...less so than before version 85 when ESNI was there and cloudflare worked with it, ESNI was hated at government spy agency levels, so I kept Firefox 79 that came with Ubuntu Mate 20.04 when you installed it until Cloudflare themselves stopped supporting it, it's impossible to pass their test now, they say that ECH is coming, yet it's not, haven't seen a sign it is being implemented anywhere yet.

---

### Post by TheFu on 2022-01-12
Perhaps I'm just stupid, but doesn't rebooting defeat the entire purpose of live-patching?

---

### Post by slaytanicprion on 2022-01-12
Well, yes, but you gotta reboot sometime or another. I didn't say I rebooted. I said that a lot of updates (kernels, CVE's), unlike 2 weeks ago, were not preemptively patched with Livepatch this time when I had updates to make with the ones from today. Livepatch saw nothing, despite seemingly very important updates that fall into its territory. So after the updates were installed, software updater asked me if I wanted to reboot, when it wouldn't if Livepatch had done what it did last time, catch them as they came in and give me a log about it when I clicked the shield icon and clicked on Livepatch Settings.

---

