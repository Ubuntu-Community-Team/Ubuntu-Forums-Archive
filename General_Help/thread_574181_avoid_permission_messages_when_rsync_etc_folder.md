---
title: "avoid permission messages when rsync /etc folder"
date: 2007-10-12
forum: General Help
---

### Post by jmvidalvia on 2007-10-12
I hired a remote rsync host, where I upload my files with rsync cron.
I also would like to rsync /etc folder, but get a lot of errors because some files are not readable for ordinary users.
I wouldnt like to use root to rsync that folder.
Is there any way to avoid error messages.
I checked man rsync, and neither -q (quiet) mode nor --ignore-errors (this is when deleting) really avoid messages.
Any great idea?
Thanks a lot!

---

### Post by reckless2k2 on 2007-10-12
if you rsync using the root crontab in a job then you'll be fine with the errors. why do you want to do it as a regular user? you will have problems no matter what because some files are not world readable. 

did you do rsync -avz as well?

---

### Post by jmvidalvia on 2007-10-12
> **reckless2k2 said:**
> if you rsync using the root crontab in a job then you'll be fine with the errors. why do you want to do it as a regular user? you will have problems no matter what because some files are not world readable. 

did you do rsync -avz as well?

Yes I did, well just -az to avoid verbose mode.
I will have to use root account then...
thank you very much

---

