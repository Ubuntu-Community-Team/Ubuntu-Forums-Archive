---
title: "&quot;Canonical Livepatch has experienced an internal error&quot;"
date: 2019-11-08
forum: General Help
---

### Post by scribner on 2019-11-08
For the past few months, in the upper-right part of my screen -- next to the icons for Wi-Fi, sound, and battery -- there's a shield icon with a circle with a red exclamation point. When I click on it, it says, "Livepatch is on. An error occurred when checking for Livepatch updates." When I click on "Livepatch Settings...," it says "Livepatch is on" and there's a message below that that reads, "Canonical Livepatch has experienced an internal error. Please refer to [https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues](https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues) for further information."

Does anyone know why I'm getting this message, and how I can fix Livepatch?

---

### Post by deadflowr on 2019-11-08
> Does anyone know why I'm getting this message, and how I can fix Livepatch?
No,
but you can post the suggested commands for reporting the issue:
```
snap info canonical-livepatch
canonical-livepatch status
lsb_release -a
uname -a
journalctl -u snap.canonical-livepatch.canonical-livepatchd | tail -100
```
Maybe something there is useful.
If not, open a bug (per suggested by the wiki page) and post that same output to it.

---

### Post by jetsam on 2019-11-08
I'm curious what counts as "internal?"  "Livepatch" is a web service that enables and provides live kernal updates to installed systems, targeted mostly at server systems, presumably live on the inter/infra network of (mostly) small-medium business users?  Or do I have this all wrong?

Anyways, which internals are experiencing an error here seems a relevant question.

---

### Post by scribner on 2019-11-09
It seems this issue corrected itself after I updated my computer yesterday and did a restart. Strange, as I believe I had done updates before that didn't correct the issue. The shield icon now shows a green circle with a check mark.

---

### Post by jetsam on 2019-11-09
Maybe the problem was on the server side...?  Don't worry over it too much, sometimes network services just fix themselves for no good reason.

---

### Post by deadflowr on 2019-11-09
> **scribner said:**
> It seems this issue corrected itself after I updated my computer yesterday and did a restart. Strange, as I believe I had done updates before that didn't correct the issue. The shield icon now shows a green circle with a check mark.

How old was the last kernel before the reboot?
There is a limited  number of kernels that can get livepatched.

See the last security notice as of Oct 22: [https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-October/005162.html]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2019-October/005162.html")
Currently anything older than 4.15.0-50-generic and 4.4.0-148-generic cannot be livepatched.

A reboot usually brings in a new kernel which has the patches already built in, so no patches should be required.
Thus the livepatch indicator should say all is good.

I'd recommend checking the 
```
journalctl -u snap.canonical-livepatch.canonical-livepatchd | tail -100
```
every once in a while to see that it's running smoothly.
(It runs hourly? or so.)

---

### Post by hfnabiel on 2020-06-03
I found another thread about this and someone had success by turning off their VPN. I am using ExpressVPN. I turned off the VPN, livepatch started working again. I don't know if you're running VPN or not. If you are, try turning it off and see what happens. If that doesn't work, I'm afraid I don't have any other suggestions. Good luck.

---

