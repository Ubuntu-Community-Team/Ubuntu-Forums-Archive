---
title: "Unable to empty trash. [Resolved]"
date: 2007-02-26
forum: General Help
---

### Post by AceRimmer on 2007-02-26
Hello, I'm using Gnome on Edgy and when I hit 'empty trash' nothing happens.  If I open the trash and chose 'empty trash' from the menu I get this message. 
> "/home/aaro...devices/c:" cannot be deleted because you do not have permissions to modify its parent folder.

I'm not sure what I must have done but can anyone give me a tip on what I need to fix?  The permission for my user name shows create and delete permissions. 

Thanks.

---

### Post by aysiu on 2007-02-26
Is that a Windows partition you have mounted inside your home folder?

---

### Post by almalaci on 2007-02-26
I have the exact same problem, I'm not using windows partitions together with ubuntu so that's not the case. In my case it's a simple permission problem and from your error message AceRimmer I guess yours is too.
It would be much better though if emptying the trash would empty the files that have the permission and only leave the ones that don't.

---

### Post by SishGupta on 2007-02-26
open your trashbin however you do

go to view>show hidden files

try do delete things one by one until you get to the one that wont delete

report back

if you KNOW that everything in the trash is actually trash and theres been some permish problem try

sudo rm -rf ~/.Trash



a similar problem happened to me back in dapper. hasn't happened since.

---

### Post by aysiu on 2007-02-26
I'd strongly advise against **ever** typing the phrase ```
sudo rm -rf
``` into the terminal. That can be *very* dangerous.

Deleting through the graphical user interface is the safest way to go.

Alt-F2 ```
gksudo nautilus
``` Then go to /home/almalaci/.Trash and delete everything in that folder.

---

### Post by m.musashi on 2007-02-26
I had this problem before. I was installing something from source and when I deleted the stuff I didn't need anymore it put the files in my trash but they were owned by root. Since I can delete them it wouldn't let me empty the trash. I suspect you might have files in your trash that you don't own. Open the trash and see if any have a red X. Check the permissions. If that is the case then you can remove them as aysiu suggests.

---

### Post by aysiu on 2007-02-26
Alternatively, you can just make sure you own everything in your trash: ```
sudo chown -R almalaci:almalaci /home/almalaci
``` and then empty the trash.

---

### Post by m.musashi on 2007-02-26
> **aysiu said:**
> Alternatively, you can just make sure you own everything in your trash: ```
sudo chown -R almalaci:almalaci /home/almalaci
``` and then empty the trash.

I tried that in my case but it didn't work. Although I tried to change permission only in /home/jim/.trash. Maybe that had something to do with it. Root nautilus worked fine though.

---

### Post by AceRimmer on 2007-02-27
There was a hidden ./wine directory from an old install of wine that I didn't have permission for since I did use sudo or anything to delete the trash I guess.  I fixed it.  Thanks for the replies.

---

### Post by almalaci on 2007-02-27
Thanks for all the many different ways of helping me emptying the trash but actually I don't have a problem doing it, I just do sudo nautilus with revealing the hidden files. As to how the undeletable files get there I don't question since I do things as root sometimes.

My point in the end was that ubuntu could do better at dealing with the files that have the permissions to be deleted and only leave the ones that are problematic by the simple right click on the trash can and not have to open it.
Although the >sudo chown -R almalaci:almalaci /home/almalaci< sounds like a good solution, will try it.
Thanks again!

---

### Post by aysiu on 2007-02-27
> **almalaci said:**
> Thanks for all the many different ways of helping me emptying the trash but actually I don't have a problem doing it, I just do sudo nautilus with revealing the hidden files. I would advise using *gksudo nautilus*, actually, instead of *sudo nautilus*. It's just a good habit to get into. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> My point in the end was that ubuntu could do better at dealing with the files that have the permissions to be deleted and only leave the ones that are problematic by the simple right click on the trash can and not have to open it. Maybe you should file a bug report on this (if one doesn't already exist):
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by almalaci on 2007-03-01
OK, Thanks!

---

