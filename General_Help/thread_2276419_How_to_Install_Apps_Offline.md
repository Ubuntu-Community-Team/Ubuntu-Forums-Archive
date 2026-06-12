---
title: "How to Install Apps Offline?"
date: 2015-05-02
forum: General Help
---

### Post by gr8 on 2015-05-02
How do I install apps offline? I downloaded HPLIP printing from HPs website. When I tried to install it through terminal it told me there were missing dependencies and it wouldn't install. Do I have to download the list of fourteen dependencies as well to install offline?

---

### Post by CantankRus on 2015-05-02
Yes, as with installing most software you will need to install dependencies as well.

---

### Post by Bucky Ball on 2015-05-02
For a start, you should install it from the repositories, not the HP website. That way the dependencies will be dragged in with it.

You are wanting to install this on an offline machine I take it? Easy way: install Synpatic Package Manager from the repos (Software Centre)> Launch it> search and select HPLip to install BUT don't click apply. Instead, go to 'File> Generate Package Download Script'. Make sure you have a USB plugged in with enough freespace to store the app and dependencies. Away you go. When done, remove the USB, stick it into the offline machine and install.

For more detail see [here]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript").

Just a note: ALWAYS check in the repositories before installing stuff from third-party PPAs and websites. ;)

---

### Post by gr8 on 2015-05-02
Solved, thank you.

I usually download from the official website because it's, well, official. Who knows what I'm getting in the repositories? Can't anybody throw any old modified code in there?

---

### Post by deadflowr on 2015-05-02
> **gr8 said:**
> 
Can't anybody throw any old modified code in there?
No, they cannot.
Only those who have been given upload rights can do so. 
More here on that:
[https://wiki.ubuntu.com/ContributeToUbuntu#Maintaining_Ubuntu](https://wiki.ubuntu.com/ContributeToUbuntu#Maintaining_Ubuntu)
Ubuntu also contains the source code for that particular package that you can also download, which the installation file that it has in the repository is directly built off of.

---

