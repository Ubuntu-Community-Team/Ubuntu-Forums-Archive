---
title: "Cannot burn dvd"
date: 2008-03-02
forum: General Help
---

### Post by stepheny on 2008-03-02
I have been using Ubuntu for a few years now and have not had this problem before. Suddenly I cannot burn DVD's. When I insert a dvd and click on "make data dvd"  the Nautilus window with the location burn:/// opens and I paste the files I want to burn there and then click "burn dvd". A message window then opens but everything is grayed out and I cannot close the window. I have to kill the process to stop it.

Since starting to write this post the situation has got even worse, now when I insert a dvd the message "Nautilus cannot display burn:///" appears. 

I was trying to burn a copy of my home directory that I have made using Rsync, it is 1.11GB. I have removed all files from  /media/dvd including hidden ones.

Any help would be appreciated.

---

### Post by fedex1993 on 2008-03-02
um i would recommend install k3b and burning a dvd that way it works way better also the dvd may not be the right format is another thing

---

### Post by stepheny on 2008-03-04
The problem was that I was trying to burn a directory which had more than 6 levels. I was not aware of the iso six levels limit.
I read that I could avoid this limitation by using -D in with mkisofs but first I tried using Gnomebaker to write an ISO which worked fine. I then burned the ISO onto a DVD and that worked, all levels seem to be present on the DVD.

---

