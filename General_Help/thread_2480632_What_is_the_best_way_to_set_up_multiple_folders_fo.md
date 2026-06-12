---
title: "What is the best way to set up multiple folders for www and html on an apache server?"
date: 2022-11-04
forum: General Help
---

### Post by olivertwist04 on 2022-11-04
Dear,


The image file should be moved outside of www/html/mysite and accessed via an application made for uploading and downloading files


In the case of image data on another partition that has been mounted, such as /mnt/media/mysite/image, the app remains at /var/www/html/mysite


Do you have to install dual Apache on different partitions in order to run multiple virtualhosts on etc/apache2/sites-availables?


In order to make it accessible from outside with a domain, for example:[https://cartbrostraders.com/](https://cartbrostraders.com/)


Thank you for your input.

---

### Post by TheFu on 2022-11-04
> **olivertwist04 said:**
>  
Do you have to install dual Apache on different partitions in order to run multiple virtualhosts on etc/apache2/sites-availables?


No.  Use 1 install of the web server you choose. Nearly all of them support virtual hosts.

Be very careful allowing uploads.  This is a very common way to have the system cracked, taken over, and used by nefarious people for bad things.

---

