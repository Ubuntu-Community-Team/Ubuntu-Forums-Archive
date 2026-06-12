---
title: "Problem Installing Java as Root"
date: 2008-06-05
forum: General Help
---

### Post by kramer2718 on 2008-06-05
I'm trying to install java ee with Sun's binary installer.  It seems to run okay if I just do:

$ ./java_ee_sdk-5_05-linux.bin

but I want to install it in a system directory, so I'm trying:

$ sudo ./java_ee_sdk-5_05-linux.bin

If I open up a root prompt, it still doesn't work.  I tried logging in to kde as root, but ubuntu forbids it.

Any help would be appreciated.

---

### Post by Xiong Chiamiov on 2008-06-05
Install java through the repos instead.  Do a search for "java" in Synaptic (adept for Kubuntu) and pick the one you want (probably a package starting with sun-java).

See [how to install things in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by kramer2718 on 2008-06-06
Which java package has EE suport?  The descriptions just don't say.

---

### Post by tomcheng76 on 2008-06-06
i think the repository just have J2SE JRE/SDK.
did u change the permission of the file?
try
> 
chmod 755 ./java_ee_sdk-5_05-linux.bin


---

