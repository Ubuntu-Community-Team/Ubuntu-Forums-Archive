---
title: "Trouble installing 12.04 LTS Server"
date: 2013-05-23
forum: General Help
---

### Post by hamzamian on 2013-05-23
Hi,

I'm having a few problems trying to install 12.04 LTS Server AMD64 onto a new build.

I initially downloaded the latest ISO (12.04.02) and used Universal USB Installer to create a bootable flash drive. However when booting off this drive, the installer starts up just fine but then fails on the first after selecting a keyboard and states that it can not load the installation components from the CD drive.

I tried recreating the bootable flash drive using a couple of different methods but each time I get the same result.

I then reverted to a 12.04.1 ISO that I had previously downloaded and this seems to get past this point (again creating a bootable USB drive with it). Unfortunately it fails a little further as it can't detect the network adapter.

The build is a Gigabyte GA-Z77-DS3H which has an atheros network adapter. Googling for problems with this and linux doesn't turn up a great deal but does throw up a few threads that recommend using a later version of Ubuntu to resolve the problem as the driver is not included in some of the older versions.

I tried also booting off a live CD for 12.04 LTS AMD 64 Desktop version however this just seemed to hang. I do need an LTS version of the server edition in any case....

Anyone have any suggestions about what to try next? I suppose it is possible there's a problem with the motherboard... though I'd like to confirm that before I attempt to RMA it if that is the case... In any case that wouldn't explain the problem with the 12.04.2 server install.

Thanks for your help all

---

### Post by 2F4U on 2013-05-24
Could these problems with 12.04.2 be due to a corrupt download? Did you verify the checksum of the downloaded iso?

---

### Post by hamzamian on 2013-05-24
Hi,

thanks for the suggestion, as it happens I had not verified the checksum... so I did it now. Unfortunatley they do match so it would appear to be a good download.

Any other ideas?

---

### Post by hamzamian on 2013-05-24
Hmm. Interestingly if I burn the same ISO (12.04.2 server) to disc instead and hook up an optical drive it will boot just fine.

Unfortunately, I then run into the same problem as with 12.04.1 : "No network interfaces detected"

Any suggestions?

---

### Post by prodigy_ on 2013-05-24
[http://demtrex.wordpress.com/2011/04/04/work-around-the-cd-rom-detection-issue-when-installing-ubuntu-server/](http://demtrex.wordpress.com/2011/04/04/work-around-the-cd-rom-detection-issue-when-installing-ubuntu-server/)

The post is about 10.04 but it works for 12.04 as well. The only command I added was ```
mount /dev/sr0 /cdrom
``` after ```
ln -sf /iso/ubuntu-10.04-server-amd64.iso /dev/sr0
``` Not sure that was even necessary but it worked anyway.

---

