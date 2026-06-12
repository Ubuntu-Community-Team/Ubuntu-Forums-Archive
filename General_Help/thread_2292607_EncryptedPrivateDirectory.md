---
title: "EncryptedPrivateDirectory"
date: 2015-08-29
forum: General Help
---

### Post by stephenroblin on 2015-08-29
Hello,

I just installed ecryptfs using the instructions from this page: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory).  I have three questions:

1. How do I know that I successfully encrypted my home folder? 

2. I see that there is now a "Private" folder in the "Home" folder. To encrypt documents, like my main "Documents" folder, should I copy and paste the folder in the "Private" folder? 

3. I ran the commands under the "Storing Your Keys, Email and Other Data in ~/Private" in the above link. However, it will not allow me to move .evolution/ to "Private." What should I do to resolve this issue? 

I look forward to receiving guidance.

All the best,

Stephen

---

### Post by TheFu on 2015-08-30
Login with a different userid and try to view the encrypted directory of another userid.

Encrypted HOME directories use a slow encryption method. Better on a personal workstation to use whole drive encryption, IMHO. Regardless, please have excellent backups.  If you are going to the effort to do this, you might be interested in following Linux Foundation's Workstation Security Guide: 
[https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

---

### Post by stephenroblin on 2015-08-30
Thanks for your feedback. I didn't encrypt it successfully. I logged in with a different user and could access the documents in the "Private" folder. 

Do you think I should uninstall ecryptfs? And then encrypt the home directory?

---

### Post by TheFu on 2015-08-30
No. I think you should start over with **whole-disk encryption** based on dmluks.  There is a checkbox in the installers that I've used.  The performance of user-home-directory encryption is terrible, painful, and breaks all sorts of things like system backups.  THAT is completely unacceptable to me.

---

### Post by stephenroblin on 2015-08-30
THanks. I"ll look into that.

---

