---
title: "Copy File from Windows 7 w/Bad Sectors"
date: 2013-05-06
forum: General Help
---

### Post by partloer on 2013-05-06
So after I connected my Dad's old hard drive that has bad sectors I am having problems copying one file.  I removed the hard drive from his Windows 7 desktop and connected it to my Ubuntu desktop.  I then mounted the hard drive with disk utility.  I can access and copy other file except this one file.  

When I drop and drag the file to my desktop the following error occurs "Error while copying "filename.xls" There was an error copying the file into /home/username/Desktop Error opening file '/home/username/Desktop/filename.xls': Permission denied"  

I also have tried sudo cp in the terminal and receive the following errors: cp: reading 'filename': Permission denied cp: failed to extend '/home/username/Desktop/filename.xls': Permission denied

I also cannot just open the spreadsheet directly then save as to my desktop.

My thoughts are that this file is part of the bad sector(s) however is there any other way to confirm this or method to recover this file.  Thanks in advance

---

