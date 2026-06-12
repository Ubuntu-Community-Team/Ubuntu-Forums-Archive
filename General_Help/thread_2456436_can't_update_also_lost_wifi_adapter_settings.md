---
title: "can't update also lost wifi adapter settings"
date: 2021-01-11
forum: General Help
---

### Post by john_ellis2 on 2021-01-11
Hi Everyone,

Hope everyone is staying safe.

I have a couple of issues, wonder if anyone else is having the same problems.

I am using Ubuntu 20.04

First issue is, I can't update my system, either by using apt-get or the software centre, when I look at the software centre I get the following message
"unable to download updates: E: The repository 'http://ppa.launchpad.net/speed-dreams/ppa/-ubuntu focal release' does not have a release file"

When I try and run apt-get update I get the same out put.

Has anyone else had this, not sure what the repository speed reams is to be fair, not one I have added to the list.

Second issue is, my wifi adaptor was working fine, never had a problem with it, on Saturday I wanted to do a zoom call so I plugged in the Ethernet cable so I got full speed internet, I come to use my laptop today and wifi has completely disappeared.

The wifi issue, I will do some research, I managed to fix one of my other systems after doing a clean install I had no wifi, managed to plug in the Ethernet cable and follow a video on you tube which sorted the problem, I just think it's strange.

Any help with the updates problem would be much appreciated.

Cheers

John

---

### Post by howefield on 2021-01-11
The first issue is down to that particular "speed reams"PPA not having a focal release. It doesn't exist for  hence the error.

Best to remove it from your sources.list, it is probably in your /ect/apt/sources.list.d/ folder.

The wifi issue is best to be posted to the [Networking & Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") forum.

---

### Post by john_ellis2 on 2021-01-11
Hi howefield,

We are on the same page, just gone to the sources file and removed that repo, thankfully my system is now up to date.

I will take a look at the wifi issue tomorrow, im knackered :)

Thanks again

John

---

### Post by howefield on 2021-01-11
Cool, thanks for the update.

Good luck with the wireless issue, there are some very knowledgeable people who frequent the Networking & Wireless forum. :)

---

### Post by john_ellis2 on 2021-01-11
Hi howefield,

Thank fully I wrote down the commands from the last time I had a wifi problem lol, for now at least the problem is solved.

Thanks again for the advise on the repo

John

---

