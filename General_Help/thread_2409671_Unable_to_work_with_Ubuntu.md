---
title: "Unable to work with Ubuntu"
date: 2019-01-05
forum: General Help
---

### Post by takeawaydave on 2019-01-05
Shame to say that trying out Ubuntu 18.04 has turned out to be a bit of a waste of time. 

I have a fairly new laptop (well 3 years old Dell Precision 7510) and with Window 10 1809 turning out to be a bit of a disaster plus the fact that every thing now seems to be sent to OneDrive I thought wy not regain some privacy and move to this LTS release.

Pretty gutted this with the time spent and late nights spent here but probably have to switch back. 

The list of things is:

Slow Ethernet adapter ([https://ubuntuforums.org/showthread.php?t=2409623](https://ubuntuforums.org/showthread.php?t=2409623)) - only get 10 Mb/s
No SD Card Reader
No smart card reader (I need this since I log in to several sites using smart card authentication
External display connected via USB-C to DP cable keeps crashing if I try to arrange the displays

Getting fairly good battery life however the laptop seems so hobbled with these problems that it hardly seems worth to keep running Ubuntu.

Is there something I can try and do here ? No idea where to start... just frustrated after a late night of getting nowhere.

---

### Post by kc1di on 2019-01-05
Since this is a Dell you might want to ask them for a copy of their version of Ubuntu as it may have the drivers you need to get the Sd Card working. Worth a try any way. 
I have several Dell Laptops they all work quite well with Ubuntu and other distros also.  Don't give up too quick.

---

### Post by cmcanulty on 2019-01-05
Yes Dell is the most supportive of Ubuntu of the major manufacturers. I also run several Dells with no issues on smart cards or SDs

---

### Post by takeawaydave on 2019-01-05
As far as I read there is no longer any special Dell Ubuntu iso build. 

[https://www.reddit.com/r/Dell/comments/719dij/service_tag_latitude_7480_with_ubuntu_preinstalled/](https://www.reddit.com/r/Dell/comments/719dij/service_tag_latitude_7480_with_ubuntu_preinstalled/)

Anything worthwile from Project Sputnik was merged in to the main Ubuntu branch.

---

### Post by takeawaydave on 2019-01-05
> **cmcanulty said:**
> Yes Dell is the most supportive of Ubuntu pf the major manufacturers. I also run several Dells with no issues on smart cards or SDs

I would be interested if its not too much trouble to understand a little more the smart card and SD Card Reader you have running. Any chance you could post details please?

---

### Post by cmcanulty on 2019-01-06
Dell search today

[https://www.dell.com/learn/us/en/555/campaigns/xps-linux-laptop_us]("https://www.dell.com/learn/us/en/555/campaigns/xps-linux-laptop_us")

---

### Post by Kris_M on 2019-01-06
I tend to use a separate USB card reader for reading cards. They're cheap.

I can't recall installing much if anythiing from Lenovo to make this work on Ubuntu.

Check for latest BIOS.

---

### Post by takeawaydave on 2019-01-07
Got the fingerprint scanner working last night:
```
sudo apt install cardpeek pcscd libpcsclite1 libccid pcsc-tools
```
My smart card provider SuisseID provided the rest on there website (i'll include here for reference):
[https://update.swisssign.com/repo/manual.html](https://update.swisssign.com/repo/manual.html)

---

### Post by takeawaydave on 2019-01-07
> **cmcanulty said:**
> Dell search today

[https://www.dell.com/learn/us/en/555/campaigns/xps-linux-laptop_us]("https://www.dell.com/learn/us/en/555/campaigns/xps-linux-laptop_us")

OK - toys are back in the pram.. things are looking much better today (despite being a Monday morning.

As of now:

Ethernet is working at 1 Gb/s - still need to understand why autonegotiate needs to be disabled on the port (either client or switch side)
SD Card Reader is working
SC Reader is working

Not holding out much for the Finger print reader and not looking forward to understanding why graphics crash when rearranging monitors.

---

### Post by cmcanulty on 2019-01-07
Something to think about. I have in the past used windows and had problems. To posts for help I waited weeks and then got generic useless info. See how helpful the ubuntu forums are with good replies.

---

### Post by Kris_M on 2019-01-07
don't trust your fingerprint recognition software.

I also find, it now being winter here in the colonies and dry skin and all, that my finger doesn't stay the same. 

Just my 2 cents.

---

### Post by him610 on 2019-01-07
@Kris_M
++> don't trust your fingerprint recognition software

Several years ago, a commercial fingerprint reader took about _ten_ tries to read my fingerprints. The fingerprints were needed for a security clearance. So yeah, fingerprint recognition software is probably not as certain, nor consistent, as a password.

---

