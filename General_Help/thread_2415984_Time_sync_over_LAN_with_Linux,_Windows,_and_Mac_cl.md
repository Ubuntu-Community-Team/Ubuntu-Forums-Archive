---
title: "Time sync over LAN with Linux, Windows, and Mac clients"
date: 2019-04-03
forum: General Help
---

### Post by KneadToKnow on 2019-04-03
I've tried so many different things to resolve this issue that I'm pretty sure I've tied my brain in a knot, so I'd like to start out with basics and get help from there.

My environment is as follows: one Ubuntu 18.04.1 LTS which syncs its clock with nist.gov; to minimize hits to that site, I then want my other PCs (1 Linux Mint 18.2 Sonya, 2 WindowsXP SP3, and 1 Macbook OS X 10.11.6 El Capitan) to sync their clocks against the Ubuntu machine (which I will call the server even though it's just another desktop). All devices are on the same Windows workgroup using Samba/SMB and on the same subnet on my LAN.

I would like help with steps to verify what is going on with the Ubuntu server that might be causing it to reject calls from the clients to sync time. My goal would be for each client to be polling the server once a day to sync time. Each client is set up currently to the limits of my ability to do that, but I know at least one of them is not correctly syncing because its clock is drifting.

Thanks in advance for any help.

---

### Post by SeijiSensei on 2019-04-03
Are you running ntpd on the "server?"

[https://help.ubuntu.com/lts/serverguide/NTP.html.en](https://help.ubuntu.com/lts/serverguide/NTP.html.en)

---

### Post by KneadToKnow on 2019-04-03
I don't think so. I followed the link you gave and I do not appear to be running chrony, which is the only thing I see any details about under "Serve the Network Time Protocol." I also followed the "Ubuntu Time" link, and I do not have the file /etc/ntp.conf on the "server" PC, which is mentioned in the ntpd section.

Tomorrow, I'll install chrony and report back.

---

### Post by KneadToKnow on 2019-04-04
I have now installed chrony on the server. Per the chrony documentation at [https://blog.ubuntu.com/2018/04/09/ubuntu-bionic-using-chrony-to-configure-ntp](https://blog.ubuntu.com/2018/04/09/ubuntu-bionic-using-chrony-to-configure-ntp) I added "allow" to enable it to answer requests. That's all I can do this morning, so I'll do some testing tonight or tomorrow and get back. Thanks for pointing me at that!

---

### Post by SeijiSensei on 2019-04-04
I don't know from "chrony." I just install ntpd and let it rip.

```
sudo apt-get install ntpd
```

is pretty much all it takes.

---

### Post by KneadToKnow on 2019-04-04
From the link you posted:

> If in addition to synchronizing your system you also want to serve NTP information you need an NTP server. There are several options with chrony, ntpd and open-ntp. The recommended solution is chrony.

Since that page provided no information on installing ntpd, I went with the "recommended solution." :)

---

### Post by SeijiSensei on 2019-04-05
I see. Maybe they think ntpd is overkill. It does have provisions for servers to use things like atomic clocks for scientists and others who need precise time-keeping.

If chrony is working for you, great.

---

### Post by KneadToKnow on 2019-04-05
Things seem to be working with the addition of chrony! Thanks so much for your help in getting me back on track!

---

