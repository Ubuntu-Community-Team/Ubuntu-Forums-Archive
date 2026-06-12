---
title: "Permissions best practice"
date: 2014-12-10
forum: General Help
---

### Post by nathanb2 on 2014-12-10
I'm not very familiar with Ubuntu permissions.

Background:
We place form builder files on a hospital intranet via ftp. The forms create their own csv files in a subfolder of the form. The intranet user is www-data, which becomes the owner of the csv file. The default permission on the csv folder is 775. 

We have various users that upload forms. I would like to be able to ensure that the form can create its own csv file via www-data user when a particular user uploads the form files. I tried adding www-data to the uploader name's group, but still get permission denied errors when submitting the form. I do not want to give the user the rights that www-data user has-- I want to restrict their write permissions to certain folders.

What is the best way to enable the form to be submitted such that the uploader does not have to manually change the csv folder to 777?

Thank you!

---

### Post by nathanb2 on 2014-12-10
Wait... I believe it's working now... just took some time or something.

---

