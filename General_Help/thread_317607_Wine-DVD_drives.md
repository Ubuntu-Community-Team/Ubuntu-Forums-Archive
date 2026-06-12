---
title: "Wine-DVD drives??"
date: 2006-12-12
forum: General Help
---

### Post by eriefisher on 2006-12-12
Just installed wine and dvd decrypter/dvdshrink. How do I get these programs to see my dvd drives. Is there someway to create this path.

---

### Post by yabbadabbadont on 2006-12-12
Try following the instructions in the wine appdb for these applications.

DVD Decrypter
[http://appdb.winehq.org/appview.php?iAppId=1558](http://appdb.winehq.org/appview.php?iAppId=1558)

DVD Shrink
[http://appdb.winehq.org/appview.php?iAppId=1533](http://appdb.winehq.org/appview.php?iAppId=1533)

Hopefully that will help.  I've used those directions in the past to get both of those programs working with wine, although they ran rather slowly.  Now I just use them in win2k running under vmware.

---

### Post by eriefisher on 2006-12-12
Thanks for the links.

Is the speed that much better under vmware.

---

### Post by yabbadabbadont on 2006-12-12
I never really sat down and timed the two.  It was just my impression that it was faster.  I know it was faster running natively in win2k when I was still dual-booting, but that is to be expected.  Still, it is the kind of operation that you just kick off and then go do something else for a while anyway...  so I guess it doesn't really matter, as long as the end product works.

---

### Post by eriefisher on 2006-12-12
Yeah your right there. Are there any tricks I should know about if I try vmware?

---

### Post by yabbadabbadont on 2006-12-12
Have your Windows installed in a VM and working, and don't worry about making the VM disk huge.  Just make it big enough so that you can install all the apps you want to run under windows plus a bit more for safety.  Then you can add virtual drives to your VM so that you have the necessary space for ripping, re-encoding, and burning your backups.  You may even want to create a new virtual drive and then move your page file to it so that your main disk image won't get fragmented quite so much.

---

### Post by eriefisher on 2006-12-12
Thanks for the tip. I'm looking at the vmware site now and unsure what I'm looking at. I'll figure out.

---

### Post by yabbadabbadont on 2006-12-12
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server)

That is how I got vmware server running in Dapper.

---

### Post by eriefisher on 2006-12-12
Thanks again, I'm going to give it a try when I have more time.

---

