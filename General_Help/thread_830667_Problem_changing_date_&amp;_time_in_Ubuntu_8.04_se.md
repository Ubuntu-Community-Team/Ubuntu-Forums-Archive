---
title: "Problem changing date &amp; time in Ubuntu 8.04 server"
date: 2008-06-16
forum: General Help
---

### Post by spice_prash on 2008-06-16
Hi,

I am using Ubuntu 8.04 as a mrtg server in our network. Now by timezone mistake in installation it shows me previous days date and time.

Now I want to change the date and time of the server permanently.

I used the command date .. but again after 1 minute it comes to the previous settings.
I also used ntpdate and configure /etc/default/ntpdate file and put 3.asia.pool.ntp.org as a NTPSERVER.

Still didn't work,.

I've also checked the ntpdate-debian command. but I am getting the same result.

I can change the time temperory for 1 minute only.

Please help me on this ......

---

### Post by tomcheng76 on 2008-06-16
may be you can try this
> 
$ sudo ntpdate stdtime.gov.hk
$ sudo hwclock -w


---

### Post by spice_prash on 2008-06-16
I've changed the timezone by below command, and it works like a charm 

root@mrtg:~# dpkg-reconfigure tzdata
Current default timezone: 'Asia/Kolkata'
Local time is now:      Mon Jun 16 12:33:00 IST 2008.
Universal Time is now:  Mon Jun 16 07:03:00 UTC 2008.

---

