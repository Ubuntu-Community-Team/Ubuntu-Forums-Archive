---
title: "I can't access to my windows files via ubuntu ?"
date: 2012-10-28
forum: General Help
---

### Post by aigljd on 2012-10-28
Hi guys,

I'm not able to access my windows file via ubuntu. When I click on my HD icon in my files explorer I get this error message :

"Adding read ACL for uid 1000 to `/media/jeremy' failed: Operation not supported"

Do you know how I can solve this issue ?

Thanks a lot for your help ;)

---

### Post by Linuxisfast on 2012-10-28
> **aigljd said:**
> Hi guys,

I'm not able to access my windows file via ubuntu. When I click on my HD icon in my files explorer I get this error message :

"Adding read ACL for uid 1000 to `/media/jeremy' failed: Operation not supported"

Do you know how I can solve this issue ?

Thanks a lot for your help ;)

Disable firewall on the Windows machine.

---

### Post by aigljd on 2012-10-29
I'm on a dual boot on the same computer : win7 + ubuntu.

I tried disabling the firewall but it didn't change anything :(

Any other suggestion ? :)

---

### Post by Morbius1 on 2012-10-29
Back in the golden age of Linux all these non system partitions would mount to /media/LABEL or /media/UUID with owner = the user that mounted it.

Today ( as of 12.10 ) it's mounted to /media/username/LABEL with a somewhat different ownership / permissions methodology dependant on ACL ( access control lists ). Why was this done? Because it's more complicated to do it this way, no one was expecting it to do it this way, and as it turns out it's buggy ( [https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/1068660](https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/1068660) ) - that's why.

Check out the bug report above for a workaround.

---

### Post by aigljd on 2012-10-29
I will check this topic and give you feedback ! Thanks ;)

---

### Post by aigljd on 2012-10-30
I used this to mount the folders correctly :

sudo mkdir /media/${USER}
sudo chown ${USER}:${USER} /media/${USER}
chmod 750 /media/${USER}

And it works ! 

Thanks ;)

---

