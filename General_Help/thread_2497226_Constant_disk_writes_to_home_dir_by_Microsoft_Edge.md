---
title: "Constant disk writes to home dir by Microsoft Edge &amp; Google Chrome"
date: 2024-04-27
forum: General Help
---

### Post by russnash37 on 2024-04-27
I just installed Ubuntu 24.04 LTS after using Linux Mint for some time, but am having issues with Microsoft Edge constantly writing to disk (home partition). I have also noticed that Google Chrome has the same problem, so perhaps this is a Chromium issue? In each case, the browser is sitting on a new tab page with no other tabs open.

Here is the accumulative output of iotop over a period of about 2 minutes:

```
   TID  PRIO  USER     DISK READ DISK WRITE>    COMMAND                                                                   
 193517 be/4 russ         52.00 K     51.53 M msedge --enable-features=WebRTCPipeWir~ktopPWAsRunOnOsLogin [ThreadPoolForeg]
    868 be/3 root          0.00 B     47.30 M [jbd2/dm-0-8]
 193518 be/4 russ          0.00 B     41.64 M msedge --enable-features=WebRTCPipeWir~ktopPWAsRunOnOsLogin [ThreadPoolForeg]
 193549 be/4 russ          0.00 B     15.98 M msedge --type=utility --utility-sub-ty~iations-seed-version [ThreadPoolForeg]
 193468 be/4 russ          0.00 B      7.98 M msedge --enable-features=WebRTCPipeWir~blyTrapHandler,DesktopPWAsRunOnOsLogin
 193532 be/4 russ          0.00 B      3.17 M msedge --enable-features=WebRTCPipeWir~ktopPWAsRunOnOsLogin [ThreadPoolForeg]
```

After some googling, I have tried several fixes from similar issues:

1. Clearing browser data.
2. Disabling extensions.
3. Resetting settings.

Unfortunately, none of the above has helped.  
Has anyone else had this issue and can offer any advice?

---

### Post by hong-xu on 2024-04-29
Isn't the browser just read and write cache files constantly? What's negatively impacting you?

If your home partition is slow, you can symlink the cache directory to a faster partition.

---

### Post by Tommy_CZ on 2024-05-06
I have the same problem on new installation. ext4 filesystem, edge is unusable because of milions of 3secs stutters/freezes on all pages. The SSD is m2. On btrfs it worked flawlessly.

---

### Post by gezzer2 on 2024-05-06
there seems to be a problem with any and all deb files installing. it was on one off the Ubuntu sites but i cant find now.
as a work around if you want a chrome type browser chromium snap is available from the app store and is very good.
i am using it as i cant get Vivaldi to run from a deb install ..

found the article in question.
 [https://www.omgubuntu.co.uk/2024/04/ubuntu-24-04-released](https://www.omgubuntu.co.uk/2024/04/ubuntu-24-04-released)

---

