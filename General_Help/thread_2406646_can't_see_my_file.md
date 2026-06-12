---
title: "can't see my file"
date: 2018-11-23
forum: General Help
---

### Post by richb201 on 2018-11-23
I am a newby and I am trying to have my daemon upload a .gz file to aws s3. My source is at $source = '/opt/bitnami/mysql/tmp/mybackup.gz'. When I try to upload I get an error message "file not found: /opt/bitnami/mysql/tmp/mybackup.gz". With Filezilla I can see that the file exists. I was thinking that maybe it is a permissions "thing". The owner of the file is "daemon daemon". I guess that is because the daemon just created that file. The permissions on it are -rw-rw----. I have tried changing that with chmod but it changes back every time I test. 

I am creating the file with

[PHP]$backup = $this->dbutil->backup($prefs);
 if ( ! write_file('/opt/bitnami/mysql/tmp/mybackup.gz', $backup))
[/PHP] 
This write succeeds in creating the file, but I just can't copy the file up to S3. Any ideas how to fix this?

---

### Post by TheFu on 2018-11-23
I don't know anything about php, but mentioning that in the title and putting it into the Programming subforum might get better responses.

But I do know file permissions.  
The userid running the php program needs to have read permissions  for the file you want to get and it needs to have directory write permissions for the place you want to put the file.  If those are on two different systems, then there are 2 userids - the local one and the remote one.

Also, whenever discussing permissions, we prefer to see it in the text output from **ls -l**.  So 
```
$ ll index.html .
drwxr-xr-x 42 thefu       www-data      4096 Apr  7  2016 ./
drwxr-xr-x 18 thefu       www-data      4096 Aug  8  2016 ../
-rw-r--r-- 1 thefu thefu 1052 Oct 10  2010 index.html
```
tells me everything we need to know about the file and directory.

index.html cannot be modified by www-data, which is usually the userid running apache.  That means www-data has read-only permissions to the file AND to the directory.  Only my userid can write to the file or the directory.  These are standard Unix permissions.  If you spend 45 minutes working through a Unix file permissions tutorial, you'll know 85% of what you need to know about permissions.  Just remember to think multi-user all the time. The userid running the process accessing or writing any file(s) matters.

---

