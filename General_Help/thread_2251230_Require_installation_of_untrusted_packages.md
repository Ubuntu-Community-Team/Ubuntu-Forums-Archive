---
title: "Require installation of untrusted packages?"
date: 2014-11-02
forum: General Help
---

### Post by tashfeen_ekram on 2014-11-02
I am currently running 11.10 and trying to updrage and install the patches before upgrading the OS. I am unable to install any updates as it gives me the "Requires installation of untrusted packages" message. 

There are of course many posts on this but aftery trying all of them, I am still unabel to sovle the issue.

I have tried what is here:

[http://askubuntu.com/questions/184117/requires-installation-of-untrusted-packages](http://askubuntu.com/questions/184117/requires-installation-of-untrusted-packages)

and 

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

and

[https://askubuntu.com/questions/117015/update-error-require-installation-of-untrusted-packages/347857#347857?newreg=f1fa30dd3e3c493f86c3c479d7cce087](https://askubuntu.com/questions/117015/update-error-require-installation-of-untrusted-packages/347857#347857?newreg=f1fa30dd3e3c493f86c3c479d7cce087)

When I run sudo apt-get update I get the below:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by sammiev on 2014-11-02
11.10 is dead. You will need to move to 12.04 or 14.04

---

### Post by tashfeen_ekram on 2014-11-02
ALso, when I treid to clear the cahce by creating a new with below commandds

 	 		 			 			 				cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update 			 		

Then when I use the GUI to try to run the patches it says "Failed to download repository information"

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by tashfeen_ekram on 2014-11-02
Ah.... How do I do that? Do i not need to do the patches before upgrading to 12 or 14?

---

### Post by Bucky Ball on 2014-11-02
You need to do a clean install. 11.10 is not supported here or by Canonical. Please read this and post a new thread if you need any further help installing 12.04 or 14.04 LTS as this thread title will be unrelated. I recommend 14.04 which is supported until 2019. Good luck.

Please read [THIS]("http://ubuntuforums.org/showthread.php?t=2229730") and please use code tags when posting code (see the last link in my signature). Thanks. 

*Thread closed.*

---

