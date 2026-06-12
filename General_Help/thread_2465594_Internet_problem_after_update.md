---
title: "Internet problem after update"
date: 2021-08-06
forum: General Help
---

### Post by rancid-raptor3 on 2021-08-06
hello sir,

newbie ubuntu here.

I have the following problem: my ubuntu updated itself, after that, I had to restart the notebook. so I restarted the laptop but after that, I have this problem: no internet. 
until that point the internet worked great, I was connected to wi-fi no problem.
but after it updated itself internet stop worked. no wi-fi found.

I searched the internet for hours and I tried various things... after a while, I found a solution on this tutorial: [https://www.youtube.com/watch?v=Sn2-D46J968](https://www.youtube.com/watch?v=Sn2-D46J968)

so basically the solution was:   open terminal, write this: "sudo systemctl start NetworkManager.service"  then I enter my password and after that my internet starts working


but now I have this problem: if I restart the laptop, the internet stop working again, so I'm forced to write again "sudo systemctl start NetworkManager.service".

what can I do to fix this thing? I want when I open the laptop the internet to work by itself like it used to be. 

thank you

---

### Post by ActionParsnip on 2021-08-06
You could use /etc/rc.local as a fix. It'll run the command at boot and as root. It's not graceful but it'll work

---

### Post by TheFu on 2021-08-06
Probably a startup dependency problem in systemd. The wifi networking startup is happening before some other dependency hasn't been met.

There are lots and lots of places to put a script to be started or you could trace through systemd documentation to determine why the dependency issue is happening.  Some links for research:
[https://askubuntu.com/questions/1256233/problems-with-network-online-target-dependency-in-systemd](https://askubuntu.com/questions/1256233/problems-with-network-online-target-dependency-in-systemd)
[https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/](https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/)

rc.local hasn't worked for me without creating another Unit file first. In theory, unit files for systemd are more user-friendly than the old-school bash scripts we'd create.  I find it just the opposite. Write one of the old school start/stop/restart/status scripts this morning. Took 5 minutes.  

Just to understand which dependencies I need before and after that same script in systemd would take me 30 minutes to figure out, then I have to decide which of 5,000 possible options in a Unit file to use. Pain.

---

### Post by tea for one on 2021-08-06
> **rancid-raptor3 said:**
> my ubuntu updated itself, after that, I had to restart the notebook. so I restarted the laptop but after that, I have this problem: no internet. 
until that point the internet worked great, I was connected to wi-fi no problem.
but after it updated itself internet stop worked. no wi-fi found.

Did the update provide a newer kernel?

If so, perhaps you could try and boot into an earlier kernel?

---

### Post by TheFu on 2021-08-06
> **tea for one said:**
> Did the update provide a newer kernel?

If so, perhaps you could try and boot into an earlier kernel?

Someone else claimed that wifi stopped working when a new kernel 5.11 was installed automatically earlier this week.  They were on 5.8 previously and didn't remember specifically asking for 5.11.  [https://www.omgubuntu.co.uk/2021/02/new-linux-5-11-kernel-features](https://www.omgubuntu.co.uk/2021/02/new-linux-5-11-kernel-features) could be helpful to read for the major things in the 5.11 release.  That article is pretty clear that 5.11 isn't for end users. It is for devs, but then it says this:
> The Linux 5.11 kernel (or later) will feature in Ubuntu 21.04 in April, and will be backported to Ubuntu 20.04 LTS in the summer.
I guess this is "summer?"

a) this sort of stuff if why I don't allow automatic updates
b) Canonical could be pushing the newer kernel for some serious kernel security issue in the 5.8 series.

I patch on Saturdays, so I'll see if I get the 5.11 kernel without asking in the morning. My 20.04 install is on 5.4 series, however.  So are all my 18.04 systems.

New kernels can be bad for old drivers until the driver devs all catch up. In theory, they've had since Feb to get everything ready.

---

