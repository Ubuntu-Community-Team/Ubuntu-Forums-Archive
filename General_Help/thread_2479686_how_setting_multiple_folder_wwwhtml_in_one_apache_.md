---
title: "how setting multiple folder www/html in one apache server"
date: 2022-10-03
forum: General Help
---

### Post by masuimulia on 2022-10-03
Dear,

I want to move the image file outside of www/html/mysite, and access it via an application made for uploading and downloading files

 the app stays at : /var/www/html/mysite  for image data on another partition that has been mounted, for example /mnt/media/mysite/image  

can it run with multiple virtualhosts on etc/apache2/sites-availables or do you have to install dual apache on different partitions?  

because so that it can be accessed from outside with a domain, for example: [www.mysites.com](www.mysites.com) 

so, thanks for the input.

---

### Post by TheFu on 2022-10-03
No. Only 1 web server is needed. Apache has supported "virtual hosts" since before I started using Apache in the mid-1990s.  Each virtual host is just a config file. It can point anywhere on the disk.  Of course, permissions for different areas of the webapp need to be carefully configured, since allowing uploads is a huge vector for system take-over.  It is commonly how over 1 million wordpress websites are compromised.  

Be careful out there, especially if you allow uploads.  There are some common best practices, like not allowing uploads to be accessed until they are validated or process and put somewhere else.  Uploads are 1-way.  Downloads are completely different and the two should never cross directories.  I actually mount my downloads for read-only access, so any bugs in the webapp cannot modify the areas with static content - that includes html and documents and other media. Those are all read-only.  Uploads get processed and cannot be accessed by even the uploader, then placed onto the storage that the read-only mount is using.

Security in Unix has many subtle techniques, to avoid being cracked.

---

