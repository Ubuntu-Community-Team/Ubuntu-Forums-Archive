---
title: "Continue upload to ftp when closing putty"
date: 2014-12-01
forum: General Help
---

### Post by chuckie86 on 2014-12-01
I want to upload to ftp using ftp. Now i enter ftp ftp.host.com, than enter username and then enter password. Than i enter prompt, switch to local dir and then upload using the mput command.
Mostly i use the mput * command to upload all the files in the dir. 

How can i do this, that when i close putty, it will be still uploading the files?

---

### Post by nerdtron on 2014-12-01
Two options here:
1. Use screen to make a virtual terminal and then detach to it. (this way you can go back to it later and see if uploads are successful)
2. Use a script and make it run on the background. (you can really go back to it, you need check the files manually if they are uploaded.

Using the screen method is simple, If you want this method, we ca provide a simple tutorial on it.

Using the script method:

```
#!/bin/bash
##  These are the credentials for the ftp upload
HOST='ftp.host.com'
USER='user_name'
PASSWD='pass_123'

## We can go the directory first for easy access
cd /path/to/dir
echo 'Starting upload'

## These are commands inside FTP which will redirect to the original ftp command
ftp -v -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
prompt
binary

mput *
quit
END_SCRIPT
```

Now save the file as upload.sh. To run the upload on the background:
```
bash upload.sh &
```


3. Another option is to use the ncftpput command. Here's a very good tutorial [http://www.cyberciti.biz/tips/linux-upload-the-files-and-directory-tree-to-remote-ftp-server.html](http://www.cyberciti.biz/tips/linux-upload-the-files-and-directory-tree-to-remote-ftp-server.html)

---

