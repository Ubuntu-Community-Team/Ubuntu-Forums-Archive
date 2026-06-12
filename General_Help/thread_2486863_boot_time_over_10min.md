---
title: "boot time over 10min"
date: 2023-05-14
forum: General Help
---

### Post by utilisateurcherchepseudo on 2023-05-14
Hi

i have Ubuntu on a dual boot. BTW my windows has UEFI boot
also note that i'm a newbie, please dont assume I know...
i have reinstalled several times and boot time is still over 10min

as advised I ran systemd-analyze critical-chain
hope someone can help. 

```
graphical.target @1min 58.679s
&#9492;&#9472;multi-user.target @1min 58.679s
  &#9492;&#9472;plymouth-quit-wait.service @35.891s +1min 22.788s
    &#9492;&#9472;systemd-user-sessions.service @35.853s +34ms
      &#9492;&#9472;network.target @35.837s
        &#9492;&#9472;NetworkManager.service @29.382s +6.454s
          &#9492;&#9472;dbus.service @29.377s
            &#9492;&#9472;basic.target @29.218s
              &#9492;&#9472;sockets.target @29.218s
                &#9492;&#9472;snapd.socket @29.215s +2ms
                  &#9492;&#9472;sysinit.target @29.068s
                    &#9492;&#9472;systemd-timesyncd.service @28.796s +272ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @28.631s +154ms
                        &#9492;&#9472;systemd-journal-flush.service @5.040s +23.588s
                          &#9492;&#9472;systemd-journald.service @4.443s +595ms
                            &#9492;&#9472;systemd-journald.socket @4.419s
                              &#9492;&#9472;-.mount @4.405s
                                &#9492;&#9472;-.slice @4.405s
```

---

### Post by TheFu on 2023-05-14
Above says boot was 2 minutes.
Check the log files for bad hardware and look for reasons any network issues could be slow.

---

### Post by utilisateurcherchepseudo on 2023-05-15
Hi, thanks for your reply.
stragely enough i rebooted and checked boot time with my watch. real boot time was above 5min last tine. yet log shows less. see below:
```
graphical.target @2min 37.232s
&#9492;&#9472;multi-user.target @2min 37.232s
  &#9492;&#9472;plymouth-quit-wait.service @34.431s +2min 2.799s
    &#9492;&#9472;systemd-user-sessions.service @34.392s +35ms
      &#9492;&#9472;network.target @34.378s
        &#9492;&#9472;NetworkManager.service @29.351s +5.027s
          &#9492;&#9472;dbus.service @29.345s
            &#9492;&#9472;basic.target @29.211s
              &#9492;&#9472;sockets.target @29.211s
                &#9492;&#9472;snapd.socket @29.208s +1ms
                  &#9492;&#9472;sysinit.target @29.120s
                    &#9492;&#9472;snapd.apparmor.service @26.553s +2.566s
                      &#9492;&#9472;apparmor.service @24.906s +1.646s
                        &#9492;&#9472;local-fs.target @24.904s
                          &#9492;&#9472;run-snapd-ns-snapd\x2ddesktop\x2dintegration.mnt.mount @1min 1.069s
                            &#9492;&#9472;run-snapd-ns.mount @53.666s
                              &#9492;&#9472;local-fs-pre.target @7.637s
                                &#9492;&#9472;systemd-tmpfiles-setup-dev.service @5.900s +1.736s
                                  &#9492;&#9472;systemd-sysusers.service @4.885s +1.011s
                                    &#9492;&#9472;systemd-remount-fs.service @4.712s +153ms
                                      &#9492;&#9472;systemd-journald.socket @4.607s
                                        &#9492;&#9472;system.slice @4.594s
                                          &#9492;&#9472;-.slice @4.594s

```
please let me know how to check logs, i have NO idea

---

### Post by yancek on 2023-05-15
The log files are located in the /var/log directory which includes boot.log files.

---

### Post by oldfred on 2023-05-15
Some things to review, may have duplication but some have more info:

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

SSD drives now are a lot lower in cost and can speed up slow systems a lot.

---

### Post by MAFoElffen on 2023-05-15
So... are you time (with your wrist watch, the time up to the display of the graphical login screen? Or including from that to the display of the desktop?

---

### Post by ian-weisser on 2023-05-15
> **utilisateurcherchepseudo said:**
> plymouth-quit-wait.service @35.891s **+1min 22.788s**

That's the one to look into.

Please show the output of 
```
cat /lib/systemd/system/plymouth-quit-wait.service
cat /etc/systemd/system/plymouth-quit-wait.service
systemd-analyze blame
```

---

### Post by TheFu on 2023-05-15
> **utilisateurcherchepseudo said:**
> Hi, thanks for your reply.
stragely enough i rebooted and checked boot time with my watch. real boot time was above 5min last tine. yet log shows less. see below:
 ...
please let me know how to check logs, i have NO idea

To learn about most things, using a web search would be a good idea.  "ubuntu log files" is what I'd suggest.  There are many techniques and there might be a program to make it easier (IDK).

Also, **systemd-analyze** output doesn't always say what it appears to say.  That's where reading the documentation carefully will be helpful to understand all the caveats about the output for each option.  There's little need for people to reproduce any documentation already on your system.  Most of the options have good explanations and examples to show what can be known.  For example, "blame" sorts by the time, not in the order.
All this information is hidden in the manpage ... well, hidden to people who don't read manpages. For example, 
```
   systemd-analyze blame
       This command prints a list of all running units, ordered by the time they
       took to initialize. This information may be used to optimize boot-up times.
       Note that the **_output might be misleading_** as the initialization of one service
       might be slow simply because it waits for the initialization of another
       service to complete. **Also note:** systemd-analyze blame doesn't display results
       for services with Type=simple, because systemd considers such services to be
       started immediately, hence no measurement of the initialization delays can be
       done. **Also note** that this command only shows the time units took for starting
       up, it does not show how long unit jobs spent in the execution queue. In
       particular it shows the time units spent in "activating" state, which is not
       defined for units such as device units that transition directly from
       "inactive" to "active". This command hence **gives an impression** of the
       performance of program code, but cannot accurately
```

There are lots of "misleading" notes in the manpage.

---

### Post by utilisateurcherchepseudo on 2023-05-16
until login. after login the time is (usually, not always) very decent

---

### Post by oldfred on 2023-05-16
One setting I change is this in /etc/default/grub:

changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo.
It used to be slow enough I could track entries. They are what gets posted to log files.
But with new faster SSD, it scrolls by very fast. If errors it stops, but last entry is rarely the issue, usually several before last entry.

---

### Post by ne29914 on 2023-05-16
I had long boot times until I added this line to grub:
GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT
Don't remember what the problem was, but it works.

---

### Post by MAFoElffen on 2023-05-16
When SystemD was being integrated into Debian branch, while testing Ubuntu +1 Dev testing... That was when I started considering 'boot-chart' as a personal default installed app on all of my installs.

Easy to read. Times are there. And since it is a graphical chart, is easy to see what is taking up time, and when it was happening.

---

