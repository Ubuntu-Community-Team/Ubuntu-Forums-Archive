---
title: "Remmina RDP stopped working"
date: 2021-02-27
forum: General Help
---

### Post by transit-y on 2021-02-27
Hey everyone. I need help with the following problem.

I have two laptops with Ubuntu 20.04 and I have been using Remmina to connect to a Windows 10 PC for many months. This worked fine from both PCs, but a week ago it stopped working from the one laptop (Dell) when I changed the resolution setting from "Use client resolution" to "Use initial windows size". I changed it back but I still could not get it to work. I tried various combinations of resolutions and colour depth settings without any luck. Then I tried checking the Advanced Tab setting "Ignore certificate" and it worked the first time but the second time (and later tries) it stopped working again. Unchecking the "Ignore certificate" setting had no effect.

I tried with the second laptop (Lenovo) and everything was working fine, but when I changed the resolution setting it stopped working as well. I tried with various settings combinations but I could not get it to work again..

For a few days now, in both laptops, when I try to start the connection I get a black screen and a couple of seconds later the Reconnect message (0->1 out of 20) which repeats itself (it never goes to 2, 3 etc. out of 20). I have deleted the "known_hosts2" file in the .config/freerdp/ directory but the only effect was that I get an initial message to accept the certificate when the connection starts. I select accept and the result is the same black screen and then the Reconnect message. I have also tried with changing the "Security" setting from "Negotiate" to "TLS" but without any effect.

Another thing I tried was to remove the stored password of the Windows 10 PC from the Remmina settings. The effect was an initial challenge for the password, but when I type it, I get the black screen and Reconnect message again.

Can anyone help me with this? I can still connect to the Windows 10 PC from a Windows laptop using the Windows Remote Desktop client, but it is more convenient for me to work with Ubuntu.

---

### Post by cmcanulty on 2021-02-27
I used RDP extensively for remote work I do for a library. Since the upgrade to 20.04 it doesn't work at all. Before I could login to the user that wasn't logged in. Now it won't login at all. I have researched this a lot with no luck. I wonder if they have changed linux rdp to match windows rdp that only allows one user per computer?

---

### Post by HermanAB on 2021-02-27
AFAIK Remina is just a glorified frontend for FreeRDP - [https://www.freerdp.com/](https://www.freerdp.com/)

So you could try to upgrade FreeRDP, run it without Remina and see if it works better that way.

---

### Post by cmcanulty on 2021-02-27
Thanks I've tried freerdp, KRDC, vinagre, rmmina. All fail in 20.04 and worked fine in 18.04

---

### Post by QIII on 2021-02-27
Have you tried xfreerdp from the command line?

---

### Post by transit-y on 2021-02-28
Thanks HermanAB and QIII [**[COLOR=#990303][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=628170")for the tip of getting back to the basics, i.e. try with command-line. I ran xfreerdp with just the /v (server IP and port) /f (full screen mode) and /bpp:32 (colour depth) switches and was able to connect once. Then I disconnected and tried to switch from full screen to windowed mode (/w and /h switches) but could not connect again. Reverting to the initial command that worked the first time did not help :-(

The result is similar to what I get with Remmina: After the user/password challenge I get the black screen and a few seconds later it closes. The error message in my terminal window is
[I][11:20:49:484] [6144:6145] [ERROR][com.freerdp.core.transport] - BIO_read returned a system error 104: Connection reset by peer
[/I]
Any idea why this happens? It seems that the server is not happy with something and drops the connection, but why did it work the first time? Any suggestion on what other command-line options I could try?

---

### Post by HermanAB on 2021-02-28
Sounds like you need to upgrade Windows.

---

### Post by transit-y on 2021-02-28
Windows 10 PC (target of RDP) is at the most recent build and patch level, so there is nowhere to go at the moment. I guess I will need to work from my Windows installation (it has no problem connecting to the target PC) instead of my Ubuntu laptops.. Unless anyone else has any other suggestion I may try.

---

### Post by HermanAB on 2021-02-28
Once the Windows server dropped the connection there may still be a hanging process, preventing the Linux client from connecting again.  Try restarting Windows after a login failure.

---

