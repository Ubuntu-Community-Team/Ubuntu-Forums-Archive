---
title: "Unbuntu is laggy, choppy and general preformance is terrible"
date: 2020-05-06
forum: General Help
---

### Post by inquadrat on 2020-05-06
I made a full unbuntu installation, on my SSD, as i changed from using windows to unbuntu 20.
However since i first installed unbuntu its preformance is nothing less of terrible and im starting to regret doing this in the first place.
Generally everything is kind of choppy, its still usable, but like its bad, its pretty bad, everything is much slower and laggier.

I searched on internet for a solution but couldnt really find one, and terminal doesnt tell me much.

I dont know what to do really, this is first time i truly tried to use linux and im very unpleasantly surprised. I hoped that like preformance is supposed to be way better than on windows...

[https://imgur.com/a/6JDLQBk](https://imgur.com/a/6JDLQBk) (image of my cpu and ram usage, im running moizila firefox with couple tabs, discord, pdf viewer, command prompt and terminal and rhytmbox)

---

### Post by rbmorse on 2020-05-06
It would be helpful to know more about your hardware.  

I'm assuming a laptop of some ilk, likely one with dual Intel/Nvidia display adapters, but it would be nice to know for sure.

---

### Post by Autodave on 2020-05-06
Linux will blow away any version of Windows that you may be running.  Please give us the specs on your equipment.

---

### Post by HermanAB on 2020-05-06
Don't guess about what the problem is.  Run 'top' and see what it is, then fix it.

Anyhoo, if you want raw speed, install Xubuntu, OpenBSD or Slackware.  Those will blow your socks off.

---

### Post by sgage on 2020-05-06
OP has a specific issue - Ubuntu 20.04 is not laggy, choppy, etc. If he really wants help, he'll post details and engage in some troubleshooting, and we'll get to the bottom of it.

---

### Post by oldfred on 2020-05-06
It looks like it is using a lot of swap.
And a system with 8GB of RAM should never use swap.
You must have something else major running.

What does top or Htop show. You probably have to install htop.
sudo apt install htop

---

### Post by kurt18947 on 2020-05-06
> **oldfred said:**
> It looks like it is using a lot of swap.
And a system with 8GB of RAM should never use swap.
You must have something else major running.

What does top or Htop show. You probably have to install htop.
sudo apt install htop

+1 for HTOP. I find it easier to make sense of HTOP than TOP but maybe that's just me. I also find System Monitor useful although that adds another load. Isn't there a systemd utility that helps point to what's using the most resources? Analyze something or other?

---

