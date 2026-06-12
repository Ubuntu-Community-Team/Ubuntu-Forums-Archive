---
title: "The dual boot problem revisited"
date: 2020-10-06
forum: General Help
---

### Post by Panawe on 2020-10-06
Hi,

Since solving the dual boot problem I am unable to modify my second SSD, formatted NTFS for storage! I can mount it but not change it.

There must be a simple solution.

TIA

---

### Post by Panawe on 2020-10-06
Is this any help?

sda                                                                   
&#9500;&#9472;sda1
&#9474;    ext4   UbuntuStore
&#9474;                 e1be6415-e7f4-4ec9-ac6a-31577a5f164d                
&#9492;&#9472;sda2
     ntfs   StoreWin
                  BCDA2047DA20006E                                    
sdb                                                                   
&#9492;&#9472;sdb1
     vfat         7D1B-15ED                             736.1G    21% /media/phi
sr0                                                                   
nvme1n1
&#9474;                                                                     
&#9492;&#9472;nvme1n1p1
     ntfs   Godown
                  52E50B312937D2C2                      724.1G    22% /media/phi
nvme0n1
&#9474;                                                                     
&#9500;&#9472;nvme0n1p1
&#9474;    vfat         808C-0291                              60.4M    37% /boot/efi
&#9500;&#9472;nvme0n1p2
&#9474;                                                                     
&#9500;&#9472;nvme0n1p3
&#9474;    ntfs         B4908E7C908E44B8                                    
&#9500;&#9472;nvme0n1p4
&#9474;    ntfs         C4C8F400C8F3EE94                                    
&#9492;&#9472;nvme0n1p5
     ext4         558e0f13-3a5d-49a4-b124-2221b13ede94  235.5G    46% /

It's Godown that seems to be read-only!

TIA

---

### Post by oldfred on 2020-10-06
Do you have Windows fast startup on?
That sets hibernation flag and then Linux NTFS will not mount read/write. You can force read only mount. 
That is to prevent damage to hibernated system. And changes would be lost anyway when hibernation restored.
Note that Windows updates often turn hibernation back on. 

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by Panawe on 2020-10-07
Have turned Fast start Up off, reformatted drive and it's okay at the moment.

I suppose it's wait-and-see if Windows turns it back on again.

Thanks for info.

---

