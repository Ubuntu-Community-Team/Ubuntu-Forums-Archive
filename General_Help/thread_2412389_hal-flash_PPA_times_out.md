---
title: "hal-flash PPA times out"
date: 2019-02-12
forum: General Help
---

### Post by questerlej on 2019-02-12
Hello,

Long-time dabbler in Ubuntu here, finally giving it a concerted try as an eventual daily driver.

I am a Hulu subscriber, so I naturally want to be able to watch Hullu shows and TV channels. In the past, I've been able to do so by installing the hal-flash PPA: flexiondotorg/hal-flash.

However, the PPA currently appears to time out for some reason. Can other users confirm? If it is down, are there any alternate dowload locations? I've reached out to Martin Wimpress for assistance but in the interim I thought I'd ask here as well.

Thanks,
Luke

---

### Post by again? on 2019-02-12
The ppa appears to have libhal1-flash packages up to bionic.
[https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash](https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash)

What release are you using?
libhal1-flash seems to be available in Ubuntu universe repo Bionic up.
[https://packages.ubuntu.com/search?keywords=libhal1-flash&searchon=names&exact=1&suite=all&section=all](https://packages.ubuntu.com/search?keywords=libhal1-flash&searchon=names&exact=1&suite=all&section=all)

---

### Post by questerlej on 2019-02-12
> **guber2 said:**
> The ppa appears to have libhal1-flash packages up to bionic.
[https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash](https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash)

What release are you using?
libhal1-flash seems to be available in Ubuntu universe repo Bionic up.
[https://packages.ubuntu.com/search?keywords=libhal1-flash&searchon=names&exact=1&suite=all&section=all](https://packages.ubuntu.com/search?keywords=libhal1-flash&searchon=names&exact=1&suite=all&section=all)
Thanks for your help! That certainly did the trick! I'm running Cosmic and all seems to be working fine now. I'm a cord cutter so keeping access to Hulu is very important.

---

### Post by deadflowr on 2019-02-12
hulu doesn't require hal-flash as it now uses html5.
What you do need is to enable Protected Content in Firefox.
Google Chrome has this feature enabled by default.
You should only need regular flash (non-hal) for ads.

---

### Post by monkeybrain20122 on 2019-02-12
In addition to  what deadflower said above. hal-flash has not been working for ages, not sure who put it in universe. [https://github.com/cshorler/hal-flash/issues/26](https://github.com/cshorler/hal-flash/issues/26)

---

