---
title: "Need help with ftp upload speeds.."
date: 2016-01-14
forum: General Help
---

### Post by mohaafan on 2016-01-14
Hi,

I have a VPS from ramnode.com [I'm sorry if I'm not allowed mention hosting company names here].  I also have a VPS from nfoservers.com.  The both have the same VPS specs.  The ftp download speeds for both are good and they are at a about 8MB/s each.  However, the ftp upload speed for the VPS from ramnode.com is only 1.2MB/s while it is 9MB/s for the VPS from nfoserver.com.  I am using the SFTP protocol in the fillezilla settings as all the other options don't work. I have optimized the settings in filezilla to try to max out the upload speed for the VPS from ramnode.com without any success.  I have also used WinSCP and tried transfering with the SCP protocol and still it is about 1.2MB/s upload.  Apparently the VPS from ramnode.com is using sftp.  I did not install any ftp server on the VPS.  I think it was installed by default when I installed their Ubuntu 14.04 distribution on the VPS.  Do I have to modify the conf file for sftp on the VPS to make it upload faster to the max speed or is this the the only max upload speed I can get? I can't find the conf file for sftp on the VPS.  When I signed up to the VPS today, it said they have a 1GBps network. I am not sure what that means exactly.  So, how can I configure sftp on the VPS to increase the upload speed?

Thank you for your help in advance.

---

### Post by sgage on 2016-01-15
> **mohaafan said:**
> Hi,

I have a VPS from ramnode.com [I'm sorry if I'm not allowed mention hosting company names here].  I also have a VPS from nfoservers.com.  The both have the same VPS specs.  The ftp download speeds for both are good and they are at a about 8MB/s each.  However, the ftp upload speed for the VPS from ramnode.com is only 1.2MB/s while it is 9MB/s for the VPS from nfoserver.com.  I am using the SFTP protocol in the fillezilla settings as all the other options don't work. I have optimized the settings in filezilla to try to max out the upload speed for the VPS from ramnode.com without any success.  I have also used WinSCP and tried transfering with the SCP protocol and still it is about 1.2MB/s upload.  Apparently the VPS from ramnode.com is using sftp.  I did not install any ftp server on the VPS.  I think it was installed by default when I installed their Ubuntu 14.04 distribution on the VPS.  Do I have to modify the conf file for sftp on the VPS to make it upload faster to the max speed or is this the the only max upload speed I can get? I can't find the conf file for sftp on the VPS.  When I signed up to the VPS today, it said they have a 1GBps network. I am not sure what that means exactly.  So, how can I configure sftp on the VPS to increase the upload speed?

Thank you for your help in advance.

Very often (usually?) Internet speeds from an ISP are asymmetrical, with download being much faster than upload. You will see in your contract with the ISP what the promised up/down speeds are. If you're getting 8 down, 1.2 up really isn't that bad, in my experience.

---

