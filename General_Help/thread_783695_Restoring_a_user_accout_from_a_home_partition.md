---
title: "Restoring a user accout from a home partition"
date: 2008-05-05
forum: General Help
---

### Post by Athanasius on 2008-05-05
I am using Hardy (i686) and I reformatted my root partition.  I am able to use the account that I made while installing, using same account info on my home partition.  The problem is that I want to restore another account but when I enter the name (dan, in this case) to restore the "dan" account it tells me :Home directory already exists, please enter a different home directory path.  I don't want to change the name of the directory, I want to keep everything the same so that "dan" can access his account.  How can this be done?

---

### Post by amohanty on 2008-05-06
When you get the user manager from 
System->Administration->Users and Groups->Add User

Go to the advanced tab and type in the path to the existing home dir. If that does not work in a terminal type:

sudo useradd dan

This will not create the folder /home/dan if it already exists. 

Then use the graphical user manager to setup other stuff for dan.

hth
AM

---

### Post by Athanasius on 2008-05-06
Thank you, you are a life-saver!

---

### Post by Uncle Mort on 2008-05-16
I also found this a lifesaver, so many thanks amohanty.

An extra wrinkle: I found that the User Ids of your recreated accounts have to match those allocated to the relevant folder.  I also managed to lose my family's accounts and had difficulty re-attaching to their folders.

Before using useradd, go to 'home' in Nautilus and look at the 'Properties' for each of the lost users.  In Permissions it will have an ID number for the Owner instead of the name. These, I think, will need to match up with your recreated user accounts.  Thus, for example:

/home/arthur  has ID 1001
/home/bert        ID 1002
/home/cathie      ID 1003

Probably in the order you originally created them.

I found that the filestore re-linked with the intended owner by doing:

sudo useradd -u 1001 -c Arthur arthur
sudo useradd -u 1002 -c Albert bert
sudo useradd -u 1003 -c Catherine cathie


-u is for ID (obviously!) and -c is for comments, commonly used for the Description.  More detail by entering man useradd in terminal.

You can go back in to System > Administration > Users and Groups to edit in the finer points by UI afterwards.

No doubt there is a more elegant way of doing this, but it worked for my stumbling beginnings!

---

