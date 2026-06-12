---
title: "Failed to claim resource error"
date: 2017-10-06
forum: General Help
---

### Post by ayi36421 on 2017-10-06
I booted up my Linux Ubuntu. It popped first two messages, then kubuntu booting screen, then goes back to some "Boxy" program. The error messages above are:


```
    Platform MSFT0101:00 Failed to claim resource 1
    ACPI MSFT0101:00 Platform device creation failed: -16
    USB 1-5: Device Descriptor Read/64, Error -71
    USB 1-5: Device Descriptor Read/64, Error -71
    USB 1-5: Device Descriptor Read/64, Error -71

```

There is lots of people with the same first error message but the second message varies in each post I visit.


Most of them suggest disabling something called "TPM" they link image to motherboard, no settings, no commands, no BIOS, straight up tampering with steel which I really don't want to do.
  
Other people cannot boot into computer at all (it happens before they can interact with dual boot). And they get no answer.


There's also this post, which has instructions but for something called "watchdog" not "MSFT0101" and before I waste 3 hours going back and forth just to find out the commands don't work on my MSFT thing.
[https://askubuntu.com/questions/926738/cant-load-failed-to-claim-resource-1](https://askubuntu.com/questions/926738/cant-load-failed-to-claim-resource-1)


I'd rather create an entire post and know for certain, than execute commands and find out I formatted entire drive.


I am programmer, but I have little to no experience with Linux. Keep that in mind.


-- Greetings, J. Doe.


PS: Ask me any information you need.
PS 2: I already asked this on Stack Overflow, but forgot how useless they can get.


It may have been corrupted file system.


In recovery version of kernel. System told me that partition may require manualy `fsck`. So I did. I went to normal version of kernel. Typed in **fsck /dev/sda1**, sda1 being Linux partition, I just kept pressing "y" when it asked "fix?" and now I get to my computer. It still spouts the same errors before image of kubuntu can load, but at least now I can access my computer and account.

---

