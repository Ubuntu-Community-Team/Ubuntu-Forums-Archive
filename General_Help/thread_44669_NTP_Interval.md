---
title: "NTP Interval"
date: 2005-06-27
forum: General Help
---

### Post by twistymcgee on 2005-06-27
I have NTP enabled on my machine and the time is still getting ahead.  This happened when I was running windows as well and I had to drop the time sync interval down to 5 hours.  I'm wondering how I change the interval in Ubuntu.  Anyone know?

Thanks

---

### Post by tomchuk on 2005-06-27
You can put a ntpdate script in /etc/cron.hourly, but this is frowned upon. NTP server admins get hammered every hour on the hour from people running ntpdate via a cron job, it makes much more sense to spread out the load.

The real solution is to install ntpd (the NTP daemon) and let it keep your clock updated. It will sync at random intervals and uses previous knowledge about the way your clock drifts to keep you updated even without hitting an NTP server.

Also make sure to use pool.ntp.org for your server as it uses DNS round robin to spread the load to many different NTP servers.

Just install ntp-simple and you should be good to go.

---

### Post by twistymcgee on 2005-06-27
I have ntp-simple installed.  When I set it up I right clicked on the date time in the top right corner of the screen then selected "Adjust Date & Time".  In the popup window I checked "Periodically synchronize clock with internet servers".  Then chose some servers.  Currently my clock is about 6 minutes fast when compared with my cell phone.  So should I assume this gap should get shorter as time goes by and ntp does it's thing?  In windows I had to drop the interval because it kept sneaking ahead too fast.

---

### Post by tomchuk on 2005-06-27
I have no idea what that little clock applet does - for all I know it just runs ntpdate periodically. As long as ntpd is running everything should be working fine.

---

### Post by twistymcgee on 2005-06-27
I think it must just be a way to manipulate ntp.conf.  The hosts I selected in it actually appear at the bottom of ntp.conf.  I'm still puzzled as to why i am now 7 minutes ahead.

---

