---
title: "mdadm DEVICES"
date: 2015-02-01
forum: General Help
---

### Post by Rick P. on 2015-02-01
I currently have two Raid 5 arrays in my server using 10 drives and use the following in my mdadm.conf file:
DEVICE /dev/sd[c-m]1

Every now and again my wife restarts the server for whatever reason when it has been running long enough (weeks to months) that removable drives have been plugged into it for whatever reason. Upon restart those drives end up becoming /dev/sdg, /dev/sdh, etc ... with the drives connected to my SAS adapter going to /dev/sdn, /dev/sdo, etc ...  This gives an error at boot which causes her consternation. 

Assuming that I don't plug a raid member drive into a USB port is there a problem revising the DEVICE line to DEVICE /dev/sd[c-q]1 or something to ensure all the RAID drives are included in the DEVICES line at boot? 

Thanks
Rick

---

