---
title: "How to recover a clobbered Kubuntu/Ubuntu (Solved)"
date: 2015-12-11
forum: General Help
---

### Post by pwabrahams on 2015-12-11
I was running Kubuntu 14.10 when my system got clobbered as a result of a misconfigured update.  All of my applications were lost as well as KDE -- startkde wouldn't run.  Fortunately, though, my home directory was intact.  Here's how I got my system back to life (description modified to omit false starts).

My attempts to work with what was left of Kubuntu got nowhere, so I reinstalled it (more precisely, I installed Kubuntu 14.04 so that I could update it for several years).  During the installation, I reused the same system partition (the one containing my home directory) but did *not* reformat it.  Having done that, I had a running basic Kubuntu with a single user.  I gave this user a *different* user name: **imposter**.  My old username was **paul**, so **/home** now contained two directories: **imposter** and **paul**.  Unfortunately they both had numeric ID 1000.

So here's what I did (all as root, of course):

1. I logged in as **imposter** (my only choice) and created another user **deity** with administrative privileges and (default) numeric ID 1001.

2. I logged out of **imposter**.

3. I logged in as **deity**.

4. I deleted **imposter** using **deluser**.

At this point, there was just one user (**deity**) and two directories in **/home**: **paul** (#1000) and **deity** (#1001).

5. I created a new user **paul** with automatic login.

6. I issued the command **usermod paul -d /home/paul -u 1000 -g 1000**.

7. I logged out of **deity** and logged in as **paul**.

At this point I had my system back, though it was missing many packages.  I reinstalled the missing packages and was up and running again.

I constructed this description from my memory of what I did, so it might not be entirely accurate.  Comments and corrections are most welcome.

In case you're wondering, I did not install 15.10 (or 15.04) because it does not allow different wallpaper on different desktops, which I see as an very unfortunate regression.

I  hope this will be useful to the community.

---

### Post by sammiev on 2015-12-11
I see you posted that you were using 14.10 which has reached (EOL) in July 2015.

Likely was why your system got clobbered as a result of a mis-configured updates.

---

### Post by pwabrahams on 2015-12-11
Yes, I suspected 14.10 might be at fault, which is why I reloaded 14.04 rather that 14.10.  I originally used 14.10 because I didn't expect version 15 to be such a disaster for me so I figured I would update to it when it came out.  But the lack of different wallpapers on different desktops was a disaster for me.

---

### Post by Bucky Ball on 2015-12-11
Thanks for letting us know. :)

LTS releases can net-upgrade directly to the next LTS, skipping the interim releases in between. Consequently, 14.04 LTS can be upgraded via the net to the next LTS, 16.04 LTS, in the latter part of next year. This means you don't need to leave the LTS path if you don't want to (LTS has five years support now). :)

Good luck.

---

### Post by yoshii on 2015-12-12
> **pwabrahams said:**
> I was running Kubuntu 14.10 when my system got clobbered as a result of a misconfigured update.  All of my applications were lost as well as KDE -- startkde wouldn't run.  Fortunately, though, my home directory was intact.  Here's how I got my system back to life (description modified to omit false starts).

My attempts to work with what was left of Kubuntu got nowhere, so I reinstalled it (more precisely, I installed Kubuntu 14.04 so that I could update it for several years).  During the installation, I reused the same system partition (the one containing my home directory) but did *not* reformat it.  Having done that, I had a running basic Kubuntu with a single user.  I gave this user a *different* user name: **imposter**.  My old username was **paul**, so **/home** now contained two directories: **imposter** and **paul**.  Unfortunately they both had numeric ID 1000.

So here's what I did (all as root, of course):

1. I logged in as **imposter** (my only choice) and created another user **deity** with administrative privileges and (default) numeric ID 1001.

2. I logged out of **imposter**.

3. I logged in as **deity**.

4. I deleted **imposter** using ***deluser***.

At this point, there was just one user (**deity**) and two directories in **/home**: **paul** (#1000) and **deity** (#1001).

5. I created a new user **paul** with automatic login.

6. I issued the command **usermod paul -d /home/paul -u 1000 -g 1000**.

7. I logged out of **deity** and logged in as **paul**.

At this point I had my system back, though it was missing many packages.  I reinstalled the missing packages and was up and running again.

I constructed this description from my memory of what I did, so it might not be entirely accurate.  Comments and corrections are most welcome.

In case you're wondering, I did not install 15.10 (or 15.04) because it does not allow different wallpaper on different desktops, which I see as an very unfortunate regression.

I  hope this will be useful to the community.



Pretty clever except I think you made an error in your text:  you said you deleted users using "deluser"; i think you meant "deity", since that was the admin.  Right?

---

