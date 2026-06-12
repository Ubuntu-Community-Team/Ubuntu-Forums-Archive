---
title: "Bash Script for backing up to Amazon Glacier"
date: 2015-02-10
forum: General Help
---

### Post by webmanoffesto on 2015-02-10
I want to backup my data to Amazon Glacier (because it's very cheap). I found a BASH script that may gather all the files which need to be backed up and encrypt them before sending them to Glacier. But as a non-programmer it's hard for me to evaluate the script.
Please look at the script below and tell me if it seems good, or if you can recommend something better.
From [http://www.triatechnology.com/encrypted-incremental-backups-to-amazon-glacier-in-linux/](http://www.triatechnology.com/encrypted-incremental-backups-to-amazon-glacier-in-linux/)  
```

[COLOR=#666666]*#!/bin/bash*[/COLOR]
[COLOR=#666666]*#*[/COLOR]
 
[COLOR=#666666]*# Note, to pull a file from s3 use "s3cmd get s://bucket/file destinationfile"*[/COLOR]
[COLOR=#666666]*# You must have the proper .s3cfg file in place to decrypt the file.*[/COLOR]
 
[COLOR=#666666]*# You may also use "gpg encryptedfile" and supply the encryption code if you download*[/COLOR]
[COLOR=#666666]*# from the web interface. Good luck.*[/COLOR]
 
[COLOR=#666666]*# The bucket should be set to transfer to Glacier. To retreive, you need to initiate a*[/COLOR]
[COLOR=#666666]*# retrieval request from the s3 web interface. To retreieve and entire folder, there is a*[/COLOR]
[COLOR=#666666]*# windows program called S3 Browser that can transfer entire folders out of Glacier.*[/COLOR]
 
[COLOR=#666666]*# Define the folders of files to be backed up in SOURCE*[/COLOR]
[COLOR=#007800]SOURCE[/COLOR]=[COLOR=#7a0874]**(**[/COLOR]
[COLOR=#ff0000]"/home/owner/Documents"[/COLOR]
[COLOR=#ff0000]"/home/owner/Pictures"[/COLOR]
[COLOR=#ff0000]"/mnt/files/Photographs"[/COLOR]
[COLOR=#ff0000]"/mnt/files/Documents"[/COLOR]
[COLOR=#ff0000]"/mnt/files/Home Movies"[/COLOR]
[COLOR=#7a0874]**)**[/COLOR]
 
[COLOR=#007800]IFS[/COLOR]=$[COLOR=#7a0874]**(**[/COLOR][COLOR=#7a0874]**echo**[/COLOR] [COLOR=#660033]-en[/COLOR] [COLOR=#ff0000]"[COLOR=#000099]**\n**[/COLOR]\b"[/COLOR][COLOR=#7a0874]**)**[/COLOR]
[COLOR=#007800]logFile[/COLOR]=[COLOR=#000000]**/**[/COLOR]mnt[COLOR=#000000]**/**[/COLOR]files[COLOR=#000000]**/**[/COLOR]scripts[COLOR=#000000]**/**[/COLOR]backupmanifest.log
[COLOR=#007800]bucket[/COLOR]=MyBucket
[COLOR=#007800]s3cfg[/COLOR]=[COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR]owner[COLOR=#000000]**/**[/COLOR].s3cfg
[COLOR=#c20cb9]**touch**[/COLOR] [COLOR=#007800]$logFile[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] Finding files and performing backup: Please wait...
 
[COLOR=#666666]*# for loop to go through each item of array SOURCE which should contain the*[/COLOR]
[COLOR=#666666]*# directories to be backed up*[/COLOR]
 
[COLOR=#000000]**for**[/COLOR] i [COLOR=#000000]**in**[/COLOR] [COLOR=#ff0000]"[COLOR=#007800]${SOURCE[@]}[/COLOR]"[/COLOR]
[COLOR=#000000]**do**[/COLOR]
 
[COLOR=#666666]*# nested for loop to run find command on each directory in SOURCE*[/COLOR]
 
[COLOR=#000000]**for**[/COLOR] x [COLOR=#000000]**in**[/COLOR] [COLOR=#000000]**`**[/COLOR][COLOR=#c20cb9]**find**[/COLOR] [COLOR=#007800]$i[/COLOR][COLOR=#000000]**`**[/COLOR]
[COLOR=#000000]**do**[/COLOR]
[COLOR=#666666]*# x is each file or dir found by 'find'. if statement determines if it is a regular file*[/COLOR]
 
[COLOR=#000000]**if**[/COLOR] [COLOR=#7a0874]**[**[/COLOR] [COLOR=#660033]-f[/COLOR] [COLOR=#ff0000]"[COLOR=#007800]$x[/COLOR]"[/COLOR] [COLOR=#7a0874]**]**[/COLOR]
[COLOR=#000000]**then**[/COLOR]
[COLOR=#666666]*# create a hash to mark the time and date of the file being backed up to compare later for*[/COLOR]
[COLOR=#666666]*# incremental backups*[/COLOR]
 
[COLOR=#007800]fileSize[/COLOR]=[COLOR=#000000]**`**[/COLOR][COLOR=#c20cb9]**stat**[/COLOR] [COLOR=#660033]-c[/COLOR] [COLOR=#000000]**%**[/COLOR]s [COLOR=#007800]$x[/COLOR][COLOR=#000000]**`**[/COLOR]
[COLOR=#007800]modTime[/COLOR]=[COLOR=#000000]**`**[/COLOR][COLOR=#c20cb9]**stat**[/COLOR] [COLOR=#660033]-c[/COLOR] [COLOR=#000000]**%**[/COLOR]Y [COLOR=#007800]$x[/COLOR][COLOR=#000000]**`**[/COLOR]
[COLOR=#007800]myHash[/COLOR]=[COLOR=#000000]**`**[/COLOR][COLOR=#7a0874]**echo**[/COLOR] [COLOR=#007800]$x[/COLOR] [COLOR=#007800]$fileSize[/COLOR] [COLOR=#007800]$modTime[/COLOR] [COLOR=#000000]**|**[/COLOR] sha1sum[COLOR=#000000]**`**[/COLOR]
 
[COLOR=#666666]*# If statement to see if the hash is found in log, meaning it is already backed up.*[/COLOR]
[COLOR=#666666]*# If not found proceed to backup*[/COLOR]
 
[COLOR=#000000]**if**[/COLOR] [COLOR=#000000]**!**[/COLOR] [COLOR=#c20cb9]**grep**[/COLOR] [COLOR=#660033]-q[/COLOR] [COLOR=#007800]$myHash[/COLOR] [COLOR=#007800]$logFile[/COLOR]
[COLOR=#000000]**then**[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] Currently uploading [COLOR=#007800]$x[/COLOR]
 
[COLOR=#666666]*# s3cmd command to put an encrypted file in the s3 bucket*[/COLOR]
[COLOR=#666666]*# s3out var should capture anything in stderr in case of file transfer error or some other*[/COLOR]
[COLOR=#666666]*# problem. If s3out is blank, the transfer occurred without incident. if an error occurs*[/COLOR]
[COLOR=#666666]*# no output is written to the log file but output is written to an error log and s3out is*[/COLOR]
[COLOR=#666666]*# written to the screen.*[/COLOR]
 
[COLOR=#007800]s3out[/COLOR]=$[COLOR=#7a0874]**(**[/COLOR]s3cmd [COLOR=#660033]-c[/COLOR] [COLOR=#007800]$s3cfg[/COLOR] [COLOR=#660033]-e[/COLOR] put [COLOR=#007800]$x[/COLOR] s3:[COLOR=#000000]**//**[/COLOR][COLOR=#007800]$bucket[/COLOR][COLOR=#000000]**/**[/COLOR][COLOR=#007800]$HOSTNAME[/COLOR][COLOR=#007800]$x[/COLOR] [COLOR=#000000]2[/COLOR][COLOR=#000000]**&**[/COLOR]gt;[COLOR=#000000]**&**[/COLOR]amp;[COLOR=#000000]1[/COLOR] [COLOR=#000000]**&**[/COLOR]gt; [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]null[COLOR=#7a0874]**)**[/COLOR]
[COLOR=#000000]**if**[/COLOR] [COLOR=#7a0874]**[**[/COLOR] [COLOR=#ff0000]"[COLOR=#007800]$s3out[/COLOR]"[/COLOR] = [COLOR=#ff0000]""[/COLOR] [COLOR=#7a0874]**]**[/COLOR]
[COLOR=#000000]**then**[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] [COLOR=#007800]$x[/COLOR] :[COLOR=#000000]**///**[/COLOR]: [COLOR=#007800]$fileSize[/COLOR] :[COLOR=#000000]**///**[/COLOR]: [COLOR=#007800]$modTime[/COLOR] :[COLOR=#000000]**///**[/COLOR]: [COLOR=#007800]$myHash[/COLOR] [COLOR=#000000]**&**[/COLOR]gt;[COLOR=#000000]**&**[/COLOR]gt; [COLOR=#007800]$logFile[/COLOR]
[COLOR=#000000]**else**[/COLOR]
[COLOR=#666666]*# s3out had content, but was possibly a warning and not an error.. Checking to see if*[/COLOR]
[COLOR=#666666]*# there exist an upload file within the last 2 minutes. If so, the file will be considered*[/COLOR]
[COLOR=#666666]*# uploaded. Two minutes is to account for variance between local and remote time signatures.*[/COLOR]
 
[COLOR=#007800]date1[/COLOR]=$[COLOR=#7a0874]**(**[/COLOR][COLOR=#c20cb9]**date**[/COLOR] [COLOR=#660033]--date[/COLOR]=[COLOR=#ff0000]"[COLOR=#007800]$(s3cmd ls s3://$bucket/$HOSTNAME$x | awk '{print $1 " " $2 " +0000"}')[/COLOR]"[/COLOR] +[COLOR=#000000]**%**[/COLOR]s[COLOR=#7a0874]**)**[/COLOR]
[COLOR=#007800]date2[/COLOR]=$[COLOR=#7a0874]**(**[/COLOR][COLOR=#c20cb9]**date**[/COLOR] +[COLOR=#000000]**%**[/COLOR]s[COLOR=#7a0874]**)**[/COLOR]
 
[COLOR=#007800]datediff[/COLOR]=$[COLOR=#7a0874]**(**[/COLOR][COLOR=#7a0874]**(**[/COLOR][COLOR=#007800]$date2[/COLOR]-[COLOR=#007800]$date1[/COLOR][COLOR=#7a0874]**)**[/COLOR][COLOR=#7a0874]**)**[/COLOR]
 
[COLOR=#000000]**if**[/COLOR] [COLOR=#7a0874]**[**[/COLOR][COLOR=#7a0874]**[**[/COLOR] [COLOR=#007800]$datediff[/COLOR] [COLOR=#660033]-ge[/COLOR] [COLOR=#660033]-120[/COLOR] [COLOR=#7a0874]**]**[/COLOR][COLOR=#7a0874]**]**[/COLOR] [COLOR=#000000]**&**[/COLOR]amp;[COLOR=#000000]**&**[/COLOR]amp; [COLOR=#7a0874]**[**[/COLOR][COLOR=#7a0874]**[**[/COLOR] [COLOR=#007800]$datediff[/COLOR] [COLOR=#660033]-le[/COLOR] [COLOR=#000000]120[/COLOR] [COLOR=#7a0874]**]**[/COLOR][COLOR=#7a0874]**]**[/COLOR]
[COLOR=#000000]**then**[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] There was a possible error but the [COLOR=#000000]**time**[/COLOR] of the uploaded [COLOR=#c20cb9]**file**[/COLOR] was written within
[COLOR=#7a0874]**echo**[/COLOR] the [COLOR=#c20cb9]**last**[/COLOR] [COLOR=#000000]2[/COLOR] minutes. File will be considered uploaded and recorded [COLOR=#c20cb9]**as**[/COLOR] such.
[COLOR=#7a0874]**echo**[/COLOR] [COLOR=#007800]$x[/COLOR] :[COLOR=#000000]**///**[/COLOR]: [COLOR=#007800]$fileSize[/COLOR] :[COLOR=#000000]**///**[/COLOR]: [COLOR=#007800]$modTime[/COLOR] :[COLOR=#000000]**///**[/COLOR]: [COLOR=#007800]$myHash[/COLOR] [COLOR=#000000]**&**[/COLOR]gt;[COLOR=#000000]**&**[/COLOR]gt; [COLOR=#007800]$logFile[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] [COLOR=#000000]**`**[/COLOR][COLOR=#c20cb9]**date**[/COLOR][COLOR=#000000]**`**[/COLOR]: [COLOR=#007800]$x[/COLOR] had warnings but seemed to be successfully uploaded and was logged to main log [COLOR=#c20cb9]**file**[/COLOR] [COLOR=#000000]**&**[/COLOR]gt;[COLOR=#000000]**&**[/COLOR]gt; [COLOR=#007800]$logFile[/COLOR].err
[COLOR=#000000]**else**[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] [COLOR=#007800]$s3out[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] [COLOR=#000000]**`**[/COLOR][COLOR=#c20cb9]**date**[/COLOR][COLOR=#000000]**`**[/COLOR]: [COLOR=#007800]$s3out[/COLOR] [COLOR=#000000]**&**[/COLOR]gt;[COLOR=#000000]**&**[/COLOR]gt; [COLOR=#007800]$logFile[/COLOR].err
[COLOR=#000000]**fi**[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] [COLOR=#660033]------------------------------------------------------------------------------------[/COLOR]
[COLOR=#000000]**fi**[/COLOR]
[COLOR=#000000]**fi**[/COLOR]
[COLOR=#000000]**fi**[/COLOR]
 
[COLOR=#000000]**done**[/COLOR]
[COLOR=#000000]**done**[/COLOR]
 
[COLOR=#666666]*# processed all files in SOURCE. Now upload actual script and file list. They are not encrypted.*[/COLOR]
 
[COLOR=#7a0874]**echo**[/COLOR] Uploading [COLOR=#007800]$logFile[/COLOR]
s3cmd put [COLOR=#007800]$logFile[/COLOR] s3:[COLOR=#000000]**//**[/COLOR]Linux-Backup [COLOR=#000000]**&**[/COLOR]gt; [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]null
[COLOR=#7a0874]**echo**[/COLOR] Uploading [COLOR=#007800]$0[/COLOR]
s3cmd put [COLOR=#007800]$0[/COLOR] s3:[COLOR=#000000]**//**[/COLOR]Linux-Backup [COLOR=#000000]**&**[/COLOR]gt; [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]null
 
[COLOR=#7a0874]**echo**[/COLOR]
[COLOR=#7a0874]**echo**[/COLOR] Backup to S3 has been completed. You may proceed with life.

```

---

