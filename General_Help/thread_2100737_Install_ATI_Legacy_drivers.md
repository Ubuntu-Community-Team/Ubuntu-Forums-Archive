---
title: "Install ATI Legacy drivers"
date: 2013-01-02
forum: General Help
---

### Post by dave_t on 2013-01-02
Hi, I need some help installing the fglrx legacy drivers in 12.04. I have a ATI 4350 HD card.  I am following the steps outlined here

 [http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html]("http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html")

but when I get to the "sudo apt-get install fglrx-legacy" command I get an error, "E: Unable to locate package fglrx-legacy".

Any idea why this would be? Thanks

---

### Post by Calinou on 2013-01-02
Did you run these commands?

```
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy
```

---

### Post by QIII on 2013-01-02
There is absolutely no reason to add any PPA or follow any complex and inscrutable instructions found on the web if you are using Precise.

The repository for Precise contains the 12.4 fglrx driver and you need do nothing more than install it from there.  Just don't install the "updates" version, as it rarely works properly.

That driver will happily support both your card and X Server 1.12, which is used by Precise.

The instructions in the cited URL are for installing the legacy drivers on 12.10.*  I HIGHLY RECOMMEND AGAINST FOLLOWING THOSE INSTRUCTIONS, EVEN IN QUANTAL*.  Downgrading to X Server 1.12 effectively breaks Quantal and there is no way of telling what consequences will arise in the future.

Better to stick with a whole Precise as an LTS supported for 5 years than to move forward with a broken Quantal.

---

### Post by dave_t on 2013-01-03
> **Calinou said:**
> Did you run these commands?

```
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy
```

Yes, I did. It was on the last line that I was running into the issue mentioned.

> **QIII said:**
> There is absolutely no reason to add any PPA or follow any complex and inscrutable instructions found on the web if you are using Precise.

The repository for Precise contains the 12.4 fglrx driver and you need do nothing more than install it from there.  Just don't install the "updates" version, as it rarely works properly.

That driver will happily support both your card and X Server 1.12, which is used by Precise.

The instructions in the cited URL are for installing the legacy drivers on 12.10.*  I HIGHLY RECOMMEND AGAINST FOLLOWING THOSE INSTRUCTIONS, EVEN IN QUANTAL*.  Downgrading to X Server 1.12 effectively breaks Quantal and there is no way of telling what consequences will arise in the future.

Better to stick with a whole Precise as an LTS supported for 5 years than to move forward with a broken Quantal.

OK, thanks for clearing that up. I was under the impression that the legacy drivers were required for older ATI cards. I'll install the fglrx drivers under restricted drivers later.

---

### Post by QIII on 2013-01-03
> **dave_t said:**
> I was under the impression that the legacy drivers were required for older ATI cards. I'll install the fglrx drivers under restricted drivers later.

Catalyst 12.4 *is* a legacy driver now.  However, it was not when Precise was released and it is still in the Precise repo.  It works fine with Precise.

The problem comes when you use any distro that uses X Server 1.13 or later, because driver development has stopped for cards prior to the HD 5000 series, and the older driver will not work with X Server 1.13.

---

### Post by dave_t on 2013-01-03
> **QIII said:**
> Catalyst 12.4 *is* a legacy driver now.  However, it was not when Precise was released and it is still in the Precise repo.  It works fine with Precise.

The problem comes when you use any distro that uses X Server 1.13 or later, because driver development has stopped for cards prior to the HD 5000 series, and the older driver will not work with X Server 1.13.

I think I took it for granted that the 12.04 would have the same issue. Lesson learned. Thanks again.

---

