---
title: "My start up time increased and doesnt match that given by systemd-analyze"
date: 2020-04-24
forum: General Help
---

### Post by stuseem on 2020-04-24
Hi all,

Ive tried to search for an answer to this but I can find. So would appreciate help.

Ubuntu is installed on the my SSD and have a separate HDD in the computer. The HHD is just for data, but it used to have a ~500MB boot partition that was left over from way back when i had Win7 installed on that HDD. I recently deleted that partition to stop the grub screen firing on boot. 
[B]
Since I did this the grub menu doesnt show anymore but the total boot and start time increased from 13 to 23 seconds. [/B]

Now, during start up the splash screen (which shows the Ubuntu logo) no longer shows. Previously it did. Instead, the screen goes off at this point and the system seems to stall, then after a while it goes straight to the log in screen. 

As i said, it takes ~23secs to start up but when I run **systemd-analyze** in the terminal these are my results:

```
Startup finished in 1.499s (kernel) + 6.460s (userspace) = 7.959s 
graphical.target reached after 6.449s in userspace

```

When I run **systemd-analyze** critical-chain these are my results:

```
graphical.target @6.449s
&#9492;&#9472;multi-user.target @6.449s
  &#9492;&#9472;unattended-upgrades.service @3.006s
    &#9492;&#9472;systemd-logind.service @2.120s +884ms
      &#9492;&#9472;basic.target @2.068s
        &#9492;&#9472;sockets.target @2.068s
          &#9492;&#9472;snapd.socket @2.067s +772us
            &#9492;&#9472;sysinit.target @2.062s
              &#9492;&#9472;snapd.apparmor.service @1.970s +91ms
                &#9492;&#9472;apparmor.service @1.051s +915ms
                  &#9492;&#9472;local-fs.target @1.050s
                    &#9492;&#9472;run-snapd-ns-canonical\x2dlivepatch.mnt.mount @2.569s
                      &#9492;&#9472;run-snapd-ns.mount @2.496s
                        &#9492;&#9472;swap.target @467ms
                          &#9492;&#9472;swapfile.swap @321ms +145ms
                            &#9492;&#9472;systemd-remount-fs.service @296ms +23ms
                              &#9492;&#9472;systemd-journald.socket @286ms
                                &#9492;&#9472;-.mount @283ms
                                  &#9492;&#9472;system.slice @283ms
                                    &#9492;&#9472;-.slice @283ms

```

Ive timed my start up 5 times and its always ~23seconds, definitely not ~8 seconds that these results claim. 

I'm assuming when the screen goes blank the OS 'disconnects' or something, hence it not registering the whole time??

Any ideas? Might this be to do with my deleteing of the partition on my HDD?

Thanks for any help!

PS - just updated to 20.04 and its the same.

---

### Post by mastablasta on 2020-04-24
snap could increase it i believe. is it default now?

BTW mine is 45 sec. i am not complaining. same PC with winXP takes 10 mins.
small laptop (netbook?!) takes 15 mins to boot into win 7 and about 45 secs to Kubuntu.
windows 10 work laptop i3-6100U takes about 8-10 minutes (5400rpm HDD) especially now that MSteam get loaded on start. takes me another 10 minutes to load all work related apps.

---

### Post by stuseem on 2020-04-24
I'm new to Ubuntu so pretty sure Ive  had snap from when I got Ubuntu. And originally, before I deleted that partition on the HDD, it was loading in 13 seconds. I'm assuming it had snap then.

Yeah I'm not complaining, I know 23 seconds aint no chore! Its just I know something is wrong as a month ago when I had Win10 on this PC it was starting in 18seconds so i know something is wrong.

Its also that the **systemd-analyze** seems to think its starting in 8 seconds. Which just isnt the case. haha.

---

