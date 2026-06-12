---
title: "Cloud Based Home Directory"
date: 2013-08-11
forum: General Help
---

### Post by hwttdz on 2013-08-11
Does anyone know if it is possible to use a cloud service (ubuntu one, google drive, dropbox..., I have no allegiance for this question) for a home directory.  I guess it would require mounting the directory at user login?  The hope is to use a reasonably small ssd drive for / and keep ~ on the cloud.

---

### Post by hwttdz on 2013-08-17
Any ideas?

---

### Post by newb85 on 2013-08-17
Question 1: Do you want the entire home directory on the cloud service, or just the major subdirectories (Documents, Downloads, etc.)?
Question 2: Do you need to mount the cloud service directory as your home folder, or is it good enough to use the service as a copy of your home directory?

I prefer to use Ubuntu One to sync all my important subdirectories of home.  That way, the files are on my local machine, but as the internet is available, everything is kept synced across my machines and backed up to the cloud.  But maybe that approach doesn't suit your needs...

---

### Post by hwttdz on 2013-08-17
Thanks.
1) I'm going to put the whole directory on the cloud.  I'll probably pull photos and put them on flickr.
2) I would like to mount it.  If I resort to rsync I can think of a number of solutions.

---

### Post by Kevin_Arnold on 2013-08-17
I can't imagine putting the entire home directly on "the cloud" would be a good idea. Applications store a lot of config/cache data in the hidden folders in your home directory, which they'd have to access via the internet every single time they wanted to run.

If you do want to do this, I'd keep the home directory local and just mount the individual folders up to the cloud. Pictures and Documents, etc.

I have no idea if there is anything for Amazon or Google but you can use "cloudfuse" to mount Rackspace Cloud Files.

---

