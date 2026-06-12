---
title: "Application to watch a directory and upload"
date: 2008-01-12
forum: General Help
---

### Post by krendar on 2008-01-12
Sorry for the bad subject title, didn't know what to write.

I need an application that can constantly watch a directory for changes and upload to a server when changes happen. I found and tried curlftpfs and it sorta works but if several files are changed it seems to completely kill the connection.

I wonder if you have any suggestion to other applications I could try?

Note:

1. Must watch CONSTANTLY. I need to upload files immediately a cron job that does every few minutes is too slow!

2. Server got an FTP Server running which I could upload via. Server runs Debian and I got root access so I can install server apps if necessary.

---

### Post by ghostdog74 on 2008-01-12
> **krendar said:**
> I need an application that can constantly watch a directory for changes 

1) create a dummy file in that directory.. Call that .dummy
2) use find command with the -newer option to find files that are newer that .dummy
   eg ```
 find /fullpath -newer ".dummy" -type f 
```
3) to constantly watch the directory you can use loop.eg

```

 while true
 do
      find files newer than dummy using the find command with [-newer option
      for each file found 
     do
         ftp file to destination
     done
      touch the dummy file with touch command to reflect new date and time
      sleep 2 seconds since you don't want minutes.
  done

```

---

### Post by erpo on 2008-01-12
You could also try rsync instead of FTP. Some advantages of rsync are:
1. rsync over ssh (the easiest way to run rsync) encrypts everything, including your username and password. With FTP, the data and your username and password are transmitted over the Internet in the clear.
2. rsync knows to only transmit the changes. When it's done running, the directory on the server will be an exact copy of the directory on the client with a minimum of delay due to connection trhoughput. If you like, you can configure rsync not to delete files in the server's directory that are not present on the client.

rsync and ftp are dumb solutions, not in the sense that they're not often good solutions, but in the sense that they don't need to know very much about the problem you're trying to solve. If you give more information about why you're trying to sync one directory with another, we may be able to suggest better/easier/safer tools for the job.

---

