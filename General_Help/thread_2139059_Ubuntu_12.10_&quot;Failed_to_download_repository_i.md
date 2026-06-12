---
title: "Ubuntu 12.10 &quot;Failed to download repository information&quot;"
date: 2013-04-25
forum: General Help
---

### Post by domdit on 2013-04-25
Wondering if anyone can help me out with this, whenever I try to use update-manager I get this error. I was able to update the other day but now I seem to be getting this problem :

[HTML]Failed to download repository information

Check your Internet connection.

W:Failed to fetch http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/quantal/main/source/Sources  404  Not Found

, W:Failed to fetch http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

, W:Failed to fetch http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

, E:Some index files failed to download. They have been ignored, or old ones used instead.[/HTML]

I am not sure how to go about fixing this as I never had this problem before. was hoping to update to 13.04 today:cry:

Thank you

---

### Post by ppjdee on 2013-04-25
Maybe this will help [http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-using-a-ppa](http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-using-a-ppa)
I would DL the iso from [http://www.ubuntu.com](http://www.ubuntu.com) or [http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/) and burn it to a disk or make a bootable usb drive.

---

### Post by ibjsb4 on 2013-04-25
This PPA has no 12.10 listing and needs to be removed in your software sources list.

[http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/](http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by domdit on 2013-04-25
Thank you!! the banish404 script worked perfectly! if theres a way to give u "beans" or something (first time needing to use forum) just reply and ill do it :)

---

### Post by mörgæs on 2013-04-26
No, we don't have that functionality. 
You have written a 'thank you' and the thread is marked 'solved' using the drop-down box, not the title (I removed that) so everything is fine. Welcome.

---

