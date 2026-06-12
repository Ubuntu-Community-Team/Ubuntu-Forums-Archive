---
title: "How to share a folder outside home directory? [Ubuntu 16.04.1]"
date: 2016-09-28
forum: General Help
---

### Post by JJamesR on 2016-09-28
Hi guys,
 
I'm tinkering with Ubuntu 16.04.1 and I'm struggling to share a folder outside of my home directory. 

I have two additional 1TB hard drives on the system which I would like to access from the network i.e. Windows clients, Kodi, etc, etc. 
I can share a folder inside my home directory easily but I can't seem to do so if I follow the same steps on a folder on either of the 1TB drives. I know it's got something to do with permissions but I'm not sure how to resolve it.  

Any assistance would be greatly appreciated!

---

### Post by cariboo on 2016-09-29
What file system do you additional drives use? What have you tried so far?

---

### Post by JJamesR on 2016-09-29
I've attached screenshots here.
The drives are formatted as Ext4.
These are the steps I've followed to share a folder on any of these drives. 
1. Create the folder eg. "business"
2. Right click on folder > "Local Network Share"
3. Enable all three options: Share this folder; Allow others to create and .....; Guest access....
4. I get the pop up message stating that Nautilus needs to add some additional permissions after which I allow that. 
5. I then attempt to connect to it from my Windows 10 machine with no success. [Both are set to WORKGROUP]

---

### Post by bab1 on 2016-09-30
> **JJamesR said:**
> Hi guys,
 
I'm tinkering with Ubuntu 16.04.1 and I'm struggling to share a folder outside of my home directory. 

I have two additional 1TB hard drives on the system which I would like to access from the network i.e. Windows clients, Kodi, etc, etc. 

I can share a folder inside my home directory easily but I can't seem to do so if I follow the same steps on a folder on either of the 1TB drives. I know it's got something to do with permissions but I'm not sure how to resolve it.  

Any assistance would be greatly appreciated!

Only the root user (uid=0) can create shares outside of your home directory.  It is fairly simple to setup a Samba share using the terminal command line (the bash shell).  As the root user, you will need to create a data directory and edit the /etc/samba/smb.conf file to create the share.  Are you a member of the sudo group?

By what means (and where) are the external 1TB hard drives mounted to the internal Linux file system?

How many users need access to this root created share; or do you just want to allow everyone access?  Do you understand the Linux user permissions scheme?

Are you willing to use the terminal command line to set this share up?

---

