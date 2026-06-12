---
title: "added ftp user with home inside of /var/www/html - permission help"
date: 2023-03-23
forum: General Help
---

### Post by scoob8000 on 2023-03-23
I have an existing server running a simple webpage.

I'm trying to add a user that can log in with vsftpd and have their home folder inside of /var/www/html

I've done that and added that user to the www-data group.   

The user can log in and upload, but apache doesn't have permission to access anything the user uploads and displays a 403 forbidden error.

I'm sure this is simple as changing ownership of the directory or something but I'm stumpped.

---

### Post by TheFu on 2023-03-23
a) plain FTP should have died out.  Use sftp instead.  **sudo apt install ssh fail2ban** sets that up.  Any Linux file manager can use sftp:// URLs to access it (or ssh://)
b) When seeking help about permissions, showing the directory and permissions is required to prevent misunderstandings.  Need to see the parent directory permissions too.  So, please post **ls -al /var/www/html **, wrapped in forum code tags so it looks the same here as it does in a terminal. Without the code tags, it will be too hard to read. Please make it easy to help you.
c) Manually putting files directly in an active website isn't a best practice.  Best practice says to create a script to push the files in a 100% consistent way, optimize any images for web viewing, etc.  The script should deploy for you.  The script can be as simple as 1 rsync command or it could pull the files from a version control system repo ... like git.

---

### Post by scoob8000 on 2023-03-23
This is for a legacy application on a local only network.

I found my problem, was in vsftpd.conf.    The default umask doesn't set uploaded files with the correct permissions.

---

### Post by TheFu on 2023-03-23
> **scoob8000 said:**
> This is for a legacy application on a local only network.

I found my problem, was in vsftpd.conf.    The default umask doesn't set uploaded files with the correct permissions.

Would be helpful to others if you posted the exact solution. Please help the community.
Regardless, plain FTP should have died in 2002.

---

