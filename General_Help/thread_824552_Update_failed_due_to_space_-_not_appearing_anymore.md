---
title: "Update failed due to space - not appearing anymore"
date: 2008-06-10
forum: General Help
---

### Post by tom-ubuntu on 2008-06-10
Hi all

I tried to update my system this morning. 32 packages I think. After downloading it failed immediately because my /boot was filled. After deleting old kernels, I had to run

dpkg --configure -a

which solved something (initramfs) shortly. 

I started again the Updatemanager. But there was no package to be updated anymore.... Tried also with aptitude and apt-get, but nothing to update.

What do I need to do get the latest updates?

Thanks for any help!

Cheers
Tom

---

### Post by plucky on 2008-06-10
> What do I need to do get the latest updates?


Check the history in Synaptic package manager to see if the updates were installed.

If not then ```
sudo apt-get update
sudo apt-get upgrade
``` should get the updates and install them,assuming your sources.list has the repositories selected.


Good Luck

---

### Post by tom-ubuntu on 2008-06-10
> **plucky said:**
> Check the history in Synaptic package manager to see if the updates were installed.

If not then ```
sudo apt-get update
sudo apt-get upgrade
``` should get the updates and install them,assuming your sources.list has the repositories selected.


Good Luck

Will check Synaptic. Thanks. Did not know that there is a history. 

Will try again if I get back home.  It is exactly what I did with apt-get; also tried to update with aptitude and the update-manager. But it goes to the same DB/Sources so should not make any difference.

And yes, the sources.list is up to date, as I saw the updates before the error occurred.

Thanks for your reply!

---

### Post by tom-ubuntu on 2008-06-10
Checked the history in Synaptic; all the updates are marked with committed. But it is not possible, that they have been processed in a second.

Reinstalled everything with Synaptic manually. Machine is now up to date again.

Thanks for any help and tips supplied.

---

