---
title: "Ubuntu bitlocker encryption with TPM equivalent"
date: 2018-11-02
forum: General Help
---

### Post by pebbledash2 on 2018-11-02
Hello

I am currently a Windows 10 user and before I make the switch is there a similar offering on Ubuntu? I understand that full disk encryption can be selected when installing from a Live USB but with bitlocker I was easily able to pair full encryption with the TPM (Trusted platform module) and a password. Without both the system would not boot up.

Is this available out of the box with ubuntu or would I have to install third party software? How easy is this to achieve? Also what kind of encryption would I be looking at - would it be as secure as bitlocker?

Thanks!

---

### Post by TheFu on 2018-11-03
Almost everything in any Linux distro is "3rd party software."  That's the nature of the Linux ecosystem for all distributions. For someone coming from a single-source, proprietary, background, this is something new.  Learn more here: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[https://tomkowapp.com/2016/04/09/Ubuntu-TPM-encryption/](https://tomkowapp.com/2016/04/09/Ubuntu-TPM-encryption/) I've never used the TPM paired with Ubuntu.
There are instructions there for Ubuntu 16.04.

---

### Post by TheFu on 2018-11-05
Just saw this today concerning select models of SSD with onboard encryption:

> Cryptography guru Matt Green pulled no punches today...

    Being earnest now: Microsoft trusting these devices to implement Bitlocker has to be the single dumbest thing that company has ever done. It&#8217;s like jumping out of a plane with an umbrella instead of a parachute.
ref: [https://www.theregister.co.uk/2018/11/05/busted_ssd_encryption/](https://www.theregister.co.uk/2018/11/05/busted_ssd_encryption/)

---

### Post by C.S.Cameron on 2018-11-06
Use VeraCrypt with Windows/Linux partitions. 
Got it.

---

### Post by TheFu on 2018-11-06
> **C.S.Cameron said:**
> Use VeraCrypt with Windows/Linux partitions. 
Got it.

Huh?

---

