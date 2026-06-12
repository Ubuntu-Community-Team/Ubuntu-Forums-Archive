---
title: "Sporadic freeze problem"
date: 2007-08-23
forum: General Help
---

### Post by cygnus81 on 2007-08-23
Hey there,

My Ubuntu mysteriously freezes from time to time.
At first I thought it happens when my memory (512MB) gets full (I watched the memory gauge in the Xfce panel). But it happened a couple of times when the memory wasn't full (and besides, I believe swapping occurs every now and then, regardless if the RAM is full, so whats the difference I thought). 
Then I though it might be the Xfce desktop, so I switched back to GNOME. But it continued.

The weired thing is the music (Amarok) continues playing in the background (until the song ends), but the screen (including the clock) and the input devices (mouse&keyboard) freeze. Furthermore, when I press (shortly) the power button, I can hear (not see) that X Server is shutting down and then see that the system is going down.

It seems to me that my X Server freezes.

Here is a relevant portion of my syslog (there are no entries that repeat every time it freezes):
```

...
(many more entries like this)
Aug 23 12:55:31 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1088999 (expecting 1088998, lost or reordered)
Aug 23 12:55:31 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089003 (expecting 1089002, lost or reordered)
Aug 23 12:55:31 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089030 (expecting 1089029, lost or reordered)
Aug 23 12:55:32 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089068 (expecting 1089067, lost or reordered)
Aug 23 12:55:35 [dhclient] DHCPREQUEST on eth1 to 213.57.35.2 port 67
                - Last output repeated twice -
Aug 23 12:55:37 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089118 (expecting 1089117, lost or reordered)
Aug 23 12:55:47 [dhclient] DHCPREQUEST on eth1 to 213.57.35.2 port 67
                - Last output repeated 3 times -
Aug 23 12:56:03 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089159 (expecting 1089158, lost or reordered)
Aug 23 12:56:11 [dhclient] DHCPREQUEST on eth1 to 213.57.35.2 port 67
Aug 23 12:56:14 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089173 (expecting 1089172, lost or reordered)
Aug 23 12:56:24 [dhclient] DHCPREQUEST on eth1 to 213.57.35.2 port 67
                - Last output repeated 2 times -
Aug 23 12:56:46 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089201 (expecting 1089200, lost or reordered)
Aug 23 12:56:51 [dhclient] DHCPREQUEST on eth1 to 213.57.35.2 port 67
                - Last output repeated twice -
Aug 23 12:57:03 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089251 (expecting 1089249, lost or reordered)
Aug 23 12:57:03 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089254 (expecting 1089252, lost or reordered)
Aug 23 12:57:03 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089263 (expecting 1089262, lost or reordered)
Aug 23 12:57:03 [pptp] anon log[decaps_gre:pptp_gre.c:407]: buffering packet 1089269 (expecting 1089268, lost or reordered)
Aug 23 12:57:09 [dhclient] DHCPREQUEST on eth1 to 213.57.35.2 port 67
                - Last output repeated 35 times -

**(This is when i pressed the power button (long press). The time on the (frozen) clock was 12:57)**

Aug 23 13:01:07 [init] tty4 main process (6630) killed by TERM signal
Aug 23 13:01:07 [init] tty5 main process (6631) killed by TERM signal
Aug 23 13:01:07 [init] tty2 main process (6634) killed by TERM signal
Aug 23 13:01:07 [init] tty3 main process (6635) killed by TERM signal
Aug 23 13:01:07 [init] tty1 main process (6636) killed by TERM signal
Aug 23 13:01:07 [init] tty6 main process (6637) killed by TERM signal

(and thats later that day..)

Aug 23 18:51:09 [kernel] [    0.000000] Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Thu Jun 7 20:16:13 UTC 2007 (Ubuntu 2.6.20-16.29-386)

....

```

Any ideas ?

---

### Post by raijinsetsu on 2007-08-23
What are you using for a video driver and video card? Also, what release of *buntu are you using?

---

### Post by cygnus81 on 2007-08-23
> **raijinsetsu said:**
> What are you using for a video driver and video card? Also, what release of *buntu are you using?

My video card is "VIA P4M800 S3 UniChrome Pro VGA Adapter".
My video driver is "vesa" (I tried to use "via" once but it did not work).
And my Ubuntu release is 7.04 fiesty, with GNOME.

Thanks for any idea :D

---

