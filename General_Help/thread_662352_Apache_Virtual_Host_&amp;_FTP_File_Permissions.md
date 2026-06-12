---
title: "Apache Virtual Host &amp; FTP File Permissions"
date: 2008-01-08
forum: General Help
---

### Post by atjensen11 on 2008-01-08
Hello,

I have several virtual hosts set up under Apache which are working just fine.  I want to begin to allow users to FTP to these directories as well.  FTP is setup and users can connect, but cannot modify any files.

Assuming it was a permissions issue, I looked at the permissions of all the folders that contain the virtual hosts.  Their current owner:group is root:root so I am sure this is the problem.

What is the favored or standard approach?  Do I make a new system user and/or group?  Or do I set the ownership to a user that already exists like the user for the FTP server or WWW server?

I guess I am looking for feedback on others accomplish this.

Thanks.

---

### Post by Poleh on 2008-03-20
I too am interested in hearing suggestions on this. I currently host vhosts under the user folders (/public_html) which makes the FTP'ing easier, but makes getting apache to see the files quite difficult.

I had thought of hosting the vhosts under /var/www where the default is, and then symlinking those back to the home folders for user ftp, but hit the user permissions problems as well...

---

