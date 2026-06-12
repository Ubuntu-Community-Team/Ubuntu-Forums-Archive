---
title: "Permissions"
date: 2006-11-06
forum: General Help
---

### Post by mollmann on 2006-11-06
I'm currently using Ubuntu 6.0 and I can't cd to /var/log/squid/

When I use the command "ls -l /var/log/squid/" I get this response. Also when I try using "chown proxy /var/log/squid/*" nothing happens. 

I'm totaly stumped...

total 0
?--------- ? ? ? ?                ? /var/log/squid/access.log
?--------- ? ? ? ?                ? /var/log/squid/access.log.1
?--------- ? ? ? ?                ? /var/log/squid/access.log.2.gz
?--------- ? ? ? ?                ? /var/log/squid/cache.log
?--------- ? ? ? ?                ? /var/log/squid/cache.log.1
?--------- ? ? ? ?                ? /var/log/squid/cache.log.2.gz
?--------- ? ? ? ?                ? /var/log/squid/store.log
?--------- ? ? ? ?                ? /var/log/squid/store.log.1
?--------- ? ? ? ?                ? /var/log/squid/store.log.2.gz

---

### Post by boban on 2006-11-06
Try :
```

sudo su

```

Then you'll be acting as root - you'll can cd to whatever you want :)

---

### Post by boban on 2006-11-06
And one more advice - don't change permissions of files if you don't know for sure that it won't hurt anything (with logs it SHOULD be ok, but I've never tried)... 

But - you can do chown with root permissions:
```

# normal way
sudo chown sombody some_file_or_dir 
# recursive (will change permissions for anything in folder some_dir)
sudo chown sombody some_dir -R

```

---

### Post by mollmann on 2006-11-06
Problem solved,

The directory had these permissions
drwxr--r-- 2 proxy        proxy

So I just used the command "sudo chmod 755 /var/log/squid/"

and now all the files in the directory look like this

total 260
-rw-r----- 1 proxy proxy   3481 2006-11-06 08:15 access.log
-rw-r----- 1 proxy proxy  93840 2006-11-05 19:14 access.log.1
-rw-r----- 1 proxy proxy   3943 2006-11-04 13:30 access.log.2.gz
-rw-r----- 1 proxy proxy    453 2006-11-06 07:35 cache.log
-rw-r----- 1 proxy proxy    454 2006-11-05 07:35 cache.log.1
-rw-r----- 1 proxy proxy    229 2006-11-04 07:35 cache.log.2.gz
-rw-r----- 1 proxy proxy   4876 2006-11-06 09:21 store.log
-rw-r----- 1 proxy proxy 120502 2006-11-06 07:21 store.log.1
-rw-r----- 1 proxy proxy   8736 2006-11-05 07:21 store.log.2.gz


Thanks for the quick response guys...
: )

---

