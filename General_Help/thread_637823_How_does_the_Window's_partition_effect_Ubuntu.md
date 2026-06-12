---
title: "How does the Window's partition effect Ubuntu?"
date: 2007-12-11
forum: General Help
---

### Post by Snakob808 on 2007-12-11
I am having a huge problem, and I hope someone can help me before I have to reinstall Windows and Ubuntu.

Yesterday, I created a limited user account in Windows, so I wouldn't be using the administrators account all the time.  I also changed some services to manual and disabled others.

Well, when I rebooted into Ubuntu, everything seemed fine until I tried to use Opera.  I could not get to any site.  I wouldn't get an error that the remote server could not be found.  I thought it might just be Opera, so I tried Firefox -- same thing.  I tried Evolution -- same.  I pulled up a terminal and tried to update -- same thing.  It's like Ubuntu is not using my ethernet card.

This morning, I booted Ubuntu, and the sda1 drive was gone off my desktop.  I went to /media/sda1 and the drive was listed, but when I tried to explore the contents of the drive-- it was blank-- BUT THE INTERNET WORKED!  

So, I rebooted, and sda1 (my Windows partition) came back, but my internet connection was lost.

How does Ubuntu use the Windows partition?  Do you have any ideas... maybe I disabled a Windows service or changed a security setting that caused Ubuntu not to connect?  

Any help will be greatly appreciated.

---

### Post by matthewcraig on 2007-12-11
Ubuntu does not use the Windows partition.  Sounds to me like you have a flaky connection.  Troubleshoot your network.

---

