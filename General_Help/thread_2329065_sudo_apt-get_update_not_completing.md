---
title: "sudo apt-get update not completing"
date: 2016-06-27
forum: General Help
---

### Post by Robbyx on 2016-06-27
14.04 64 bit:

This is from the end of update  showing the error messages. How do  I repair things so there are on faults on 
sudo apt-get update (NB vivaldi is not installed and not showing in synaptic, VLC is installed and being used) 

W: GPG error: [http://download.videolan.org](http://download.videolan.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
W: GPG error: [http://repo.vivaldi.com](http://repo.vivaldi.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC26F777B8B44A1
W: Failed to fetch [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

---

### Post by QDR06VV9 on 2016-06-27
Try this... and update again

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY_ID 6BCA5E4DB84288D9

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY_ID 2CC26F777B8B44A1

```
The two gstreamer with 404 error's Do not know what is up with that.
I think that PPA was for backporting gstreamer from 12.04...And you should be able to remove it now or Comment it out in your source list.

---

### Post by Robbyx on 2016-06-28
Thank you for your comment, which I followed.
An update still gets the following result. 
How do I comment the gstreamer out? I assume it should be in one of the files in etc/apt but which one, if at all?




```
W: GPG error: [http://repo.vivaldi.com](http://repo.vivaldi.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC26F777B8B44A1
W: Failed to fetch [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by QDR06VV9 on 2016-06-28
Humm? that is the key it is asking for....but anyway to comment out the Gstreamer PPA
```
gksudo gedit /etc/apt/sources.list 
``` 
And Put this "#"in front of the PPA
ppa:gstreamer-developers/ppa
Or you could just un-tick it in synaptic.
But if you are unsure just post back the contents of the <gedit /etc/apt/sources.list.

---

### Post by Robbyx on 2016-06-28
Thank you. I have removed gstreamer. 

Vivaldi is not in the sources.list (I searched on vivaldi).   Where else should I look? I did find it in synaptic and removed  it but the error message has not gone away.

---

### Post by QDR06VV9 on 2016-06-28
Ah Ha! Yes I see where vivaldi has no Key.
But it should show in Synaptic> Settings> Repositories> Other Software.
And just Un-tick it or Remove it your choice.
**And just saw you already removed it.**
Try Logging out and back in again and Update once more.
Fingers Crossed.

---

### Post by Robbyx on 2016-06-28
The vivaldi entries were in other files in the etc/apt directory  such as list. d.  I have now removed all traces of it in the other files and  the problem has gone away. Thank you for your help.

---

