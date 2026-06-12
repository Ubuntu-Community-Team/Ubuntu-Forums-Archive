---
title: "Python, Proftpd and file locking?"
date: 2014-03-23
forum: General Help
---

### Post by RavenB72 on 2014-03-23
I have Proftpd installed and have several ftp accounts created.  JPG images are being uploaded at random intervals. I wrote a Python script that runs in a 1 minute crontab. It searches for the latest image file uploaded by each user. It then copies the file to a new file file with a specific name. After creating the file it then deletes all the other files in the folder. I think this is where I am having a problem. Everything runs fine for several days. Eventually though Proftpd shuts down. I can restart it and it will run for a few more days.

I am thinking that this a file access/ locking issue. I was thinking that if Proftpd has a file open and is writing to it, the Python script would simply fail to access with no real harm done. What happens when the script is trying to delete a file that Proftopd is currently writing and is there a way I can handle this situation? I have seen a few instances where the final image is truncated, which indicates that it was being copied while the user was still uploading it. 

Thanks

---

