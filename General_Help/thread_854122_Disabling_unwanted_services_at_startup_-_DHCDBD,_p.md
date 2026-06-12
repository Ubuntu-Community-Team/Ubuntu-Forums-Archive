---
title: "Disabling unwanted services at startup - DHCDBD, pulseaudio etc"
date: 2008-07-09
forum: General Help
---

### Post by Avinash.Rao on 2008-07-09
Hi guys,

I am in the process of speeding up my Ubuntu boot. I have done a clean install and i have installed all the required OS updates. The only application i have installed is Thunderbird.

I checked the RC directories and i found the following.

S24dhcdbd, S25bluetooth, S25pulseaudio etc. 
The man pages for dhcdbd says it initiates a SBUS and connects to a DHCP Server. Could anyone explain what this actually means? Do i really need this service for my setup as i don't connect to any DHCP server, my laptop connects to a broadband modem directly.
Also, bluetooth and pulseaudio services? I am assuming thats the Pulseaudio service is the audio service for the OS. Can i disable bluetooth.

In the Services Gui tool, i noticed 
1) Action Scheduler (Anacron)
2) Action Scheduler (atd)
Do i need both, i don't have anything scheduled that needs to be executed at startup.

3) Audio settings management (alsa-utils)
I have disabled this.
4)Automated crash reports (apport) ? 

5) There are 2 computer activity logger klogd, sysklogd, do i require both? Which one does the actual log to /var/log/syslog

Any help is appreciated
Avinash

---

### Post by AlanInVancouverBC on 2008-09-02
I just deleted the two schedulers and now I can't boot!

---

### Post by Frogbarf on 2008-09-02
> **Avinash.Rao said:**
> The man pages for dhcdbd says it initiates a SBUS and **_connects to a DHCP Server_**. Could anyone explain what this actually means? Do i really need this service for my setup as i don't connect to any DHCP server, my laptop connects to a broadband modem directly.

DHCP is the process whereby your ISP dynamically assigns you an IP address and sets up various network parameters dynamically. In the good old days of dialup connections and Trumpet Winsock, while the IP address was assigned dynamically on connection, the other network parameters had to be manually set. These included iirc things like DNS addresses, time server addresses, etc. Now all that stuff is set automagically and invisibly via DHCP.

Your laptop talks to the ISP's DHCP server _through_ your broadband modem. The modem alone only converts the squeaks and squeals to a digital signal your ethernet card can handle.

I can't guarantee it's entirely jargon-free, but the Wikipedia has an article on DHCP at [http://en.wikipedia.org/wiki/Dhcp](http://en.wikipedia.org/wiki/Dhcp)

I don't know what "initiates a SBUS" means.:lolflag:

---

### Post by dhansel on 2009-11-10
This high CPU Idle usage is quite a delima. I am new to the Ubuntu world, starting out with 9.04 and have 9.10 on one of my hard drives.
It seemed that 9.10 was pretty fast, but now as many have said the speed is at a crawl and without anything going on the CPU usage is at 80-100%.

I was watching the system monitor CPU graph tonight and noticed it drop to Zero when I would click on the System tab. That tab gave the release and personal things about the computer, so by clicking on the System tab the CPU went down to 5% or lower.

When I went back to the usage graph the CPU speed went right back to to 85%.

I know it will be fixed at some point. I, as an end user tester learning it I like it better than Windows 7.
I just got a new MSI A6000 dual core 2.3gig notebook computer with 4 gigs ram, 340gig HD, HDMI and 3 years warranty and a 16" screen for a $ 450.00. It's pretty fast. I am looking for notebook computers to come down even further as Christmas approaches.


Well, that's my .02 worth, now it is sit back, read the blogs and wait for the patches to come in.

Thanks.... [email]dhansel@juno.com[/email]

---

