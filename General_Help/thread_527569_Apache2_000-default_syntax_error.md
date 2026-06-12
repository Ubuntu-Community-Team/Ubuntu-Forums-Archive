---
title: "Apache2 000-default syntax error"
date: 2007-08-16
forum: General Help
---

### Post by lwranger3 on 2007-08-16
I have been trying to set up name-based virtual hosts with Apache2, with the document root of each host set to the corresponding folder of a virtual user located in /home/vsftpd/... so, for example, the website for 'www.testsite.com' will be uploaded by user 'testsite' to /home/vsftpd/testsite from where apache2 will serve out 'www.testsite.com' requests that it receives from a client's browser.

I edited the 000-default file in /etc/apache2/sites-enabled/ but it didn't work. Unfortunately, as a result of the alterations, Apache2  has stopped working. This is so even after reverting to the original 000-default file and restarting Apache2. 

Currently getting syntax error warnings pointing to parts of the original 000-default file. It's looking a bit of a mess. Any ideas?

---

### Post by lwranger3 on 2007-08-26
Started again from scratch and all is working fine. 

The trick with name-based virtual hosting is to create a file for each site in /etc/apache2/sites-available using the default file in that directory as a template. After making the necessary changes to the template, save and close the file. It is best to save the file with the name of the website to be hosted, e.g. testsite.com, so that it is clear, when enabling the site, which file corresponds to which site.

Create a symbolic link to the file in /etc/apache2/sites-enabled to enable the site. A quick way to do this is "sudo a2ensite". The a2ensite command lists the filenames (websites) in /etc/apache2/sites-available and asks which one you would like to enable. Type in the site you want to enable and press enter.

Restart Apache2 for changes to take effect, "sudo /etc/init.d/apache2 restart"

It may seem obvious, but before testing the connection in a brower delete the browser history to make sure any previously unsuccessful attempts that may have been cached are deleted.

---

