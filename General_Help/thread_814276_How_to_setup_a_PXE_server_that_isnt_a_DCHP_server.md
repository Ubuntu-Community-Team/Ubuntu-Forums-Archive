---
title: "How to setup a PXE server that isnt a DCHP server"
date: 2008-05-31
forum: General Help
---

### Post by markp1989 on 2008-05-31
Im looking to setup a PXE server to boot GEEXBOX , using the torrent slave as the host , torrent slave is already using NFS for geexbox to access the media on it. 

Almost every PXE how to i have seen goes through setting it up as a DCHP server, I already have my router doing DCHP which i cannot change. 

The torrent slave is running ubuntu 7.10 server 32bit

Will any one be willing to walk me through setting up a pxe sever? 

Thanks, Mark

---

### Post by quelx on 2008-05-31
Does your router allow you to set a PXE/bootp host under it's dhcp settings?  if so then put the tftp server address there.  The clients have to get that information from the DHCP server, though it doesn't have to be on the same box.

---

### Post by markp1989 on 2008-05-31
Here is a screen shot of the DCHP page for my router configuration 

router is speed touch 510

---

### Post by quelx on 2008-05-31
Why not choose **No DHCP** and set up your own using **dnsmasq**?

There is no option for a bootp/PXE server so network booting will not work with your router handling dhcp.  **dnsmasq** is relatively easy to setup:

[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

---

### Post by markp1989 on 2008-06-06
I just decided to leave the networking as it is, because its the family network i dont want to change it.

I decided it would be easier to leave things as they are for now .

Thanks for the information and the link you gave me

---

