---
title: "GUFW blocks Transmission"
date: 2019-01-30
forum: General Help
---

### Post by yys2 on 2019-01-30
Hi all,
 I use GUFW and Transmission in Ubuntu 18.04.1LTS x64. My Transmission has the default settings. I followed this guide([https://ubuntuforums.org/showthread.php?t=1876124](https://ubuntuforums.org/showthread.php?t=1876124))  to set GUFW. But it's unclear for me how to set GUFW for Transmission.  

Here is my configuration in GUFW: 
[https://ubuntuforums.org/attachment.php?attachmentid=282361&d=1548846196](https://ubuntuforums.org/attachment.php?attachmentid=282361&d=1548846196)

And, here is my test: 
- Turn off GUFW, then launch Transmission. Wait 2min, then the download speed is good. Then exit Transmission. 
- Turn on GUFW, then launch Transmission. Wait 30min, the download speed  is always 0, and there is no peers at all. Then turn off GUFW. Wait 2  min, the download speed is good again. 

So, it seems that GUFW blocks Transmission.


  But how to set GUFW for Transmission?  


P.S. 
On that post, @CoyoteMX gave another answer([https://ubuntuforums.org/showthread....post12248929):]("https://ubuntuforums.org/showthread.php?t=1876124&p=12248929#post12248929):")  @Azrael84; Hey, I had the same problem with Transmisson, you just have  to add a rule for 80,6969/udp, wich are the ports used by trackers,  cheers.  

But, what does "80,6969/udp" mean?  1) 80(tcp and udp),and 6969(udp) , or 2) 80(udp), and 6969(udp) 
And, what are the directions for ports 80 and 6969? (In or Out? or, In and Out?  )


Cheers

---

