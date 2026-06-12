---
title: "Cannot upgrade from 11.04"
date: 2012-12-05
forum: General Help
---

### Post by camelface on 2012-12-05
I am trying to upgrade my 11.04 Ubuntu to a newer version. 11.04 has been by far the most stable and appreciable one so far for me, but I'd like to give my computer a little change. 

However, when I go to Update Manager and click upgrade, it tells me I have network connection problems... meanwhile I am here writing this post on the internet, so I don't get it. The same occurs if I check for any kind of update. Anyone knows what is happening? 

Oh and also, it says I have 11.04, but my upgrade option is to a new version of Ubuntu 11.04.... I don't get this as well. Why does it not propose 12.04 or 12.10 directly?

error details for UPDATE:
"W:GPG error: [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead."

error details for UPGRADE:
"W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by 3rdalbum on 2012-12-06
Support for 11.04 has ended, which is why you can't contact the repositories.

You can always do a semi-clean install from the Ubuntu 12.04 or 12.10 CD: boot the CD. run the installer, use the manual partitioning screen and tell it to install the / to the current / location without formatting. This will preserve your files in /home even if it is on the same partition as /

That's what I would recommend.

---

### Post by camelface on 2012-12-06
Weird... I downloaded the iso for 12.04. I burned it on CD and ran the CD. The upgrades were added to the Synaptic Package Manager.. Not knowing which one of the long list the OS upgrade was on, I upgrades all the things available. Now that this is complete, the Synaptic Package Manager is not responding while applying changes. Anyway, I guess I will close this..

edit: 

Well, I closed the thing and there were updates to my system but the OS did not seem to change. Then I restarted the computer and now it doesn't boot anymore. It goes to a screen (by the way, I have 10.10 it seems) that offers that I skip mounting "s" or manually boot or mount "M". But neither option engages after pressing the keys. 

Damn what did I do?

---

