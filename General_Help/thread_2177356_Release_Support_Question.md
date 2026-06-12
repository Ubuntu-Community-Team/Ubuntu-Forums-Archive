---
title: "Release Support Question"
date: 2013-09-28
forum: General Help
---

### Post by cessanfrancisco on 2013-09-28
I understand that Ubuntu 12.04 LTS is the "long-term support" version and will have support until April 2017.  While 12.10 will have support until April 2014, and fianlly 13.04 will only be supported until January 2014.

I'm just curious, how do the developers arrive at these dates, and at what point does 12.10 and, eventually 13.04, become LTS?

Thanks for your clarification.

---

### Post by howefield on 2013-09-28
Have a browse here..

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by sudodus on 2013-09-28
There is a two year cycle for LTS releases (April even years, 8.04, 10.04, 12.04, 14.04 ...). It is possible to upgrade from one LTS version to the next one. There are also point releases. The current one is 12.04.3 LTS.

The other versions (released in October and April between the LTS releases used to get 18 months support, but it was decreased to 9 months from 13.04. The idea is to use the LTS releases for production and the other releases for development, testing, and in cases new hardware is not supported in the LTS version. So you are supposed to upgrade from 13.04 to 13.10 between October and January.

---

### Post by cessanfrancisco on 2013-09-28
Thanks.

I sort of get it now.  So if I am understanding it correctly, 13.04 is next in line to become LTS, in April of 2017.  Is this assumption this correct?  If not, which version will bcome the new LTS in 2017?

---

### Post by grahammechanical on 2013-09-28
To add a little more. Someone very important in Canonical, the company that supports Ubuntu, wanted to do away with the Interim releases altogether and just have 2 yearly releases with Long Term Support of 5 years for those users who want stability and a rolling development branch for those who wanted to run Ubuntu at the edge of its development. But the decision was not his alone and a compromise was reached to reduce the support of Interim releases from 18 months to nine months.

It is expensive in time and money (if the developer is a paid employee) to maintain all the different Ubuntu versions. Support has only just ended for Ubuntu 8.04 server edition because each server edition is supported for 5 years. Desktop editions were supported for 3 years. But now the LTS desktop edition has the same length of support as the server edition. But whether you see costs as being money or time they have to be reduced somewhere. 

To answer your last question, the next LTS version will be Ubuntu 14.04 and then after that it will be Ubuntu 16.04. So, users have these options:

1) Install an LTS version and use it for 5 years and then upgrade to the LTS version that was released a year earlier.
2) Install an LTS version and upgrade to the next LTS version in 2 years time.
3) Install an LTS version and upgrade to the newest LTS version if not after 2 years then after 4 years.
4) Install Ubuntu and go from version to version upgrading between 6 and 9 months each time.
5) Install the development branch of the next Ubuntu release under development and keep doing that for as long as the novelty exists.
6) Mix and Match as they want.

Regards.



Regards

---

### Post by Iowan on 2013-09-28
> **cessanfrancisco said:**
> Thanks.

I sort of get it now.  So if I am understanding it correctly, 13.04 is next in line to become LTS, in April of 2017.  Is this assumption this correct?  If not, which version will bcome the new LTS in 2017?


LTS releases are predefined, releases do not "become" LTS. 
Next LTS release will be 14.04.
If the pattern holds, expect LTS versions 16.04 and 18.04.

---

### Post by cessanfrancisco on 2013-09-28
Ok.  This is all very interesting.  So if LTS are predefined, which one is scheduled to be the next one after 12.04, in 2017?

---

### Post by cessanfrancisco on 2013-09-28
Just for clarity, I am assuming that other Ubuntu-based distros, i.e. Mint, Kubuntu, etc, must obviously adhere to this schedule as well?

---

### Post by Iowan on 2013-09-28
Sorry - I was editing ahead...
> Next LTS release will be 14.04.
If the pattern holds, expect LTS versions 16.04 and 18.04. 
Not all  "other Ubuntu-based distros, i.e. Mint, Kubuntu, etc, ... adhere to this schedule".
[Unlike Ubuntu, Lubuntu 12.04 is not a LTS]("http://www.lubuntu.net/blog/lubuntu-1204-now-available")
[Mint]("http://forums.linuxmint.com/viewtopic.php?f=6&t=132095") seems to have their own release schedule.

---

### Post by grahammechanical on 2013-09-28
> **cessanfrancisco said:**
> Just for clarity, I am assuming that other Ubuntu-based distros, i.e. Mint, Kubuntu, etc, must obviously adhere to this schedule as well?

No, not at all. The flavours, as they are called, are independently developed. The developers may or may not have the resources to support a version for 5 years or not. For example, Lubuntu 12.04 is not given 5 year (LTS) support status. 

By the way, Linux Mint is not a Ubuntu flavour. Do not include it. Those developers may say that it is built upon Ubuntu but they have moved away from Ubuntu so far that they are not allowed to use any form of the name "ubuntu" in their name. What support they give I do not know.

Ubuntu is open source software so people can take the source code and "fork" it and that is allowed but possible misrepresentation of the code being Ubuntu is not allowed. I answered some of your recent questions in my earlier post. You may need to re-read it.

Regards.

---

### Post by cessanfrancisco on 2013-09-28
Thanks.  I get it.

But what about Kubuntu, for example?  Let's suppose I'm using the Kubuntu LTS release which is 12.04.  Then KDE releases Plasma 4.10.  Does that conflict with the older version of Ubuntu (since it's not 13.04) if the user updates Plasma?  I guess my over all question, now, is with the LTS releases occuring every 8 years where does that leave the end user if the desktop, i.e. Plasma, updates more frequently?

Thanks again.

---

### Post by cessanfrancisco on 2013-09-28
Finally, I have one more question related to this topic...

When the new version (13.10) is released, what does that mean for those of us using 13.04?

From what I gather our options are the following:
1.  Upgrade to 13.10 
2.  Stay with 13.04

If I decide to stay with 13.04, what happens?  Do I no loger receive updates until I switch to the latest version or the LTS version?

Thanks for clarifying.  I really appreciate it.

---

### Post by oldos2er on 2013-09-28
Check the link Howefield posted, 13.04 is supported until Jan. 2014.

---

### Post by cessanfrancisco on 2013-09-28
Thanks for your reply, oldo2ser.

Yes, I did read that reply.  But I what happens after January '14, if I am using 13.04?  Will I no longer receive updates (unless I upgrade to the latest version as of Jan. '14, or the LTS version)?  

Thanks!

---

### Post by craig10x on 2013-09-28
Right...you no longer will receive updates so best to upgrade to 13.10 which will get you 9 months more...Once 14.04 comes out, upgrade to that and then you can decide if you want to stay with that one (which will be an LTS with 5 yrs support...the LTS version comes out every 2 years)...

One can upgrade from 6 month version to the next (including the LTS ones)...Once you are in an LTS, you have several options...continue upgrading on a 6 month basis or stay with the LTS for as long as 5 years if you choose to or you can do like many do and just upgrade LTS to LTS every 2 years....those options can be set in your software sources in the section regarding upgrades...

When doing an upgrade (as opposed to clean installs) i think the best way to do it is from a live iso session installer which offers the option on the list...

---

### Post by cessanfrancisco on 2013-09-28
Perfect!  Thanks for your help everyone!  Have a great weekend!

---

### Post by Iowan on 2013-09-28
> **cessanfrancisco said:**
>   Will I no longer receive updates (unless I upgrade to the latest version as of Jan. '14, or the LTS version)?  

Correct!  I've had a few machines that I used past EOL. They still work, you just can't add packages from repos... and you don't get security updates.

<I must have taken a nap... :( >

---

