---
title: "ideas on vpn performance"
date: 2020-04-03
forum: General Help
---

### Post by edstevens on 2020-04-03
Running ubuntu 16.04 LTS.
Have Aruba VPN 3.0.0.82618 and Reminna 1.1.2.  Have been using this successfully to connect to my office and work from home as needed.  The connection at the office takes me directly to my workstation (Windows 10 Pro), so my ubuntu laptop is just the remote desktop.

This has worked fine for quite some time, with an occasional slow down or drop-off.  But now we are all working full time from home.  And performance is painfully slow.  I often feel that I'm on a 2400-baud (or slower!) modem.  

Now, the "obvious" answer is that with all the increased work-from-home vpn activity, I'm looking at a simple bandwidth issue.  But here's the twist.  None of my colleagues (all running Windows on there personal computers, making the same type of vpn connection) are reporting any issues.  And to put the icing on the cake, I also have a Win 10 Pro personal laptop and when I connect with it, there are no performance issues.  

So, two different machines.  Accessing the same wireless router/home network as their first network link.  The Windows 10 machine gives good performance, while the Ubuntu machine has very very slow performance.  The Ubuntu machine exhibits no performance issues outside of this vpn link to the office.

Obviously, as a practical matter I can work with the Win 10 machine, but I'd like to get an understanding of what I'm observing, and correct it if possible.

---

### Post by TheFu on 2020-04-03
Standard troubleshooting.
* simplify
* test
* check all log files
* Repeat

Do that until the cause has been determined.
* Is networking fast between the systems on the LAN?
* Is networking fast to internet servers?
* Is networking fast without any remote desktop?
* Is networking fast without Reminna? Use a different client.

Take careful measurements.
Be consistent between MBps and Mbps.
Run each test at least 5 times. 10 would be better.

---

### Post by edstevens on 2020-04-04
standard troubleshooting.
* simplify
** How to simplify further?  I'm already running two machines side by side, one with good performance and one with poor. We know the 'boundaries' of the problem.  A windows 10 machine running Windows remote desktop across a VIA vpn, traveling across common carriers to my company's network has good performance.  An Ubuntu machine sitting right next to it, running Reminna as its counterpart to Windows Remote Desktop, running through  a VIA vpn, traveling across the same home network, the same common carriers, to the same corporate network, has performance reminiscent of an old slow dial-up modem.


* test
** I've already described the testing I've done.  I'd be open to suggestions for other tests.

* check all log files
** and which log files should I be checking, for this particular issue?

* Repeat
** I can repeat the above ad infinitum, ad nauseum.  Until I have something that reveals a previously unknown controllable variable, more testing is pointless.

Do that until the cause has been determined.
* Is networking fast between the systems on the LAN?
** I have already stated that networking is fast between everything except the Ubuntu machine and some point on the vpn.  

* Is networking fast to internet servers?
** I have already stated that networking is fast between the problem ubuntu and the internet.

* Is networking fast without any remote desktop?
** That implies is it fast for any connection that doesn' require a remote desktop.  Already stated that , yes it is.

* Is networking fast without Reminna? Use a different client.
** Lacking any other insights, I'll have to try that. I did upgrade Reminna to the latest version, but performance is no better.

---

### Post by edstevens on 2020-04-12
I switched to a different remote desktop (krdc) and that is performing much better.  Still doesn't explain *why* reminna suddenly started performing so poorly, but  I guess that will have to be a mystery to remain unsolved.

---

