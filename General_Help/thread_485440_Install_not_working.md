---
title: "Install not working"
date: 2007-06-26
forum: General Help
---

### Post by UK-Wobbie on 2007-06-26
Hey all i was installing secondlife and the download box pop up on the screen and then it crashed :(
I reboot my pc and when i have a go installing a game or anything it says!

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. 

Thats from Synaptic Package Manage



The package might be corrupted or you are not allowed to open the file: please check the permissions of the file.

Thats from the install windows of deb. :(


When i have a go installing anything i get that! And i can not do my updats to!
I get the same message.

Can any one help me? I do not wanna restall my computer or anything! 
Thanks

---

### Post by Qu4k3R on 2007-06-28
You might need to chmod the *.deb file

Open the terminal, go to the path where is the package to install;
Then do this:

> 
sudo chmod 777 <file_name_.deb>
sudo chown <your_username> <file_name_.deb>


Then you could do:
> 
sudo dpkg -i <file_name_.deb>

To install the package.

PS: Are you installing secondlife from where?
I will try to install it.

---

