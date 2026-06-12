---
title: "rsync with password"
date: 2014-12-08
forum: General Help
---

### Post by patdundee on 2014-12-08
Hi Guys

I need the correct command to sync a remote server with a local server so i can run it as a cron job I need it to check for and copy all updated files including subfolders and files whilst keeping all file and folder attributes

Currently i do it manually and entering the password when requested using the following 
rsync -a user@IPADDRESS:/Source folder/ DESTINATION

I need to add this as a cron job where I can also send the password without being asked for it.

Any help would be greatly appreciated 

P

---

### Post by nerdtron on 2014-12-08
You can try importing you local keys to the remote computer so that you can run ssh/rsync with password. This is the recommended way in scripts and cron jobs.

You just have to do this the first time only.
First create your keys:
```
 ssh-keygen
``` 
Just keep pressing enter to accept defaults.

Then copy your ID to the remote machine.
```
 ssh-copy-id user@IPaddress
```
Input the password.

Now try your rsync command or try to ssh again on the server and you should login automatically.

---

### Post by patdundee on 2014-12-08
Hi nerdtron
That seems to have worked great thanks
Do you happen to know the correct flags to sync only the files or folders that have been added or updated since the last sync whilst keeping all attributes?

P

---

### Post by patdundee on 2014-12-08
would i be right in thinking -a -**&#8211;update would do this ?**

---

### Post by patdundee on 2014-12-08
found it :) rsync -a -u

---

