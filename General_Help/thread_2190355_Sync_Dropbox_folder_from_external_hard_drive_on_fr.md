---
title: "Sync Dropbox folder from external hard drive on fresh install (instead of server)?"
date: 2013-11-27
forum: General Help
---

### Post by rocky-oceans on 2013-11-27
I am going to do a fresh install of Ubuntu. I do not have my home folder on its own partition. I have a slow internet connection so it would take a couple of days to sync all of my 85 GB from Dropbox's servers. However, I can transfer my dropbox folder to my external hard drive and then transfer it back. Last time I tried this I had problems (Dropbox wouldn't sync anymore). Is there a correct way to do this?

I see that there are the file .dropbox and the folder .dropbox-cache. As long as I copy the whole dropbox folder those are copied also.

Any ideas?

---

### Post by jdeca57 on 2013-11-27
The question is why the sync wouldn't work and that is about your previous experience. I wouldn't use the old settings - don't copy .dropbox but simply install again. First make a backup with tar so that file dates remain the same. Then copy it back when dropbox is installed on the new system. There is suspicious little information about this on the Dropbox site because the point of Dropbox is that they are the backup but I found this: [http://howto.cnet.com/8301-11310_39-57419557-285/how-to-back-up-your-dropbox-account/](http://howto.cnet.com/8301-11310_39-57419557-285/how-to-back-up-your-dropbox-account/) so a local backup is certainly a possibility.

---

### Post by rocky-oceans on 2013-11-27
Thanks for the tips jdeca57. Do you have a recommended tar command to use? For 85 GB I suppose I should use multiple files? (the external hard drive has ext4)

---

