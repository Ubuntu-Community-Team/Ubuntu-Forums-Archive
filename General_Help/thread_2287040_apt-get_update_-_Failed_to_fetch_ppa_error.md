---
title: "apt-get update - Failed to fetch ppa error"
date: 2015-07-16
forum: General Help
---

### Post by MickSulley on 2015-07-16
Running trusty server 3.13.0-57-generic

When I run apt-get update it terminates with ```
W: Failed to fetch http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have checked in the source list and there are no PPA's at all, so what causes this?

Cheers
Mick

---

### Post by v3.xx on 2015-07-16
That ppa is not supported in trusty.

[https://launchpad.net/~stedy6/+archive/ubuntu/stedy-minidna](https://launchpad.net/~stedy6/+archive/ubuntu/stedy-minidna)

---

### Post by steeldriver on 2015-07-16
Did you check for the PPA in the /etc/apt/sources.list.d/ directory as well as the /etc/apt/sources.list file?

---

### Post by MickSulley on 2015-07-16
That's it!  /etc/apt/sources.list.d/stedy6-stedy-minidna-trusty.list

commented that out and it is fine.

Just need to figure out how to stream media now :-)

Thanks

---

### Post by deadflowr on 2015-07-16
Minidlna is available in the normal repositories.

---

### Post by QDR06VV9 on 2015-07-16
Some are having problems 'Unable to locate package minidlna error'
About 4 months ago a friend had this error, and I had found a solution at least for him.
Here is the fix that worked.
 
This short yet detailed tutorial guide covers how to install MiniDLNA on Ubuntu 14.04 LTS server and desktop editions, this is for people who are experiencing E: Unable to locate package minidlna error with a sudo add-repository fix. 

This will install the latest version of MiniDLNA as well as the essential library's, tutorial also covers setting up the minidlna.conf file for linking to media files (Video, Audio and Pictures).

Commands used during Video:
```
lsb_release --a
clear
sudo apt-get install software-properties-common python-software-properties
sudo add-apt-repository ppa:djart/minidlna
sudo apt-get update
sudo apt-get install minidlna
sudo pico /etc/minidlna.conf
sudo service minidlna restart 
```
The Video is here [https://www.youtube.com/watch?v=qBhIiT85DNk](https://www.youtube.com/watch?v=qBhIiT85DNk)
Hope this helps 
Regards

---

### Post by deadflowr on 2015-07-16
> [COLOR=#000000]Some are having problems 'Unable to locate package minidlna error'[/COLOR]

In trusty you need to enable t*rusty-backports* in the Software and Updates update tab, if it has not been enabled yet.
(This applies only for trusty; precise utopic vivid and wily are in the normal repos -no need to enable backportsfor any of those releases.)

---

### Post by MickSulley on 2015-07-16
Just to complete the story - I had installed minidla a while back when I bought a smart TV so that I could stream video from my server.  I removed the minidla ppa to fix the problem listed above and following the fix I was about to try to find a way to install minidla again, but first I tried streaming video from the server and it works.  I don't know if the latest server release has some additional stuff to make it work, but it seems to work fine without minidla.

Thanks
Mick

---

