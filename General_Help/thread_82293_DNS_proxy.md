---
title: "DNS proxy"
date: 2005-10-26
forum: General Help
---

### Post by MrMinute on 2005-10-26
Hello!
I would like to use a DNS proxy because I have to deal with slow nameservers. I installed pdnsd but I did not managed to run it properly. The configuration of pdnsd seems fine for me. The file /var/cache/pdnsd/pdnsd.cache does not grow in size thus I think my system does not use pdnsd.

How could I configure pdnsd correctly or do you recommend me another DNS proxy?

---

### Post by MrMinute on 2005-10-30
I found the solution because of this german wiki entry [http://www.ubuntuusers.de/wiki/netzwerk:dns_router](http://www.ubuntuusers.de/wiki/netzwerk:dns_router) . To setup your own local DNS cache you  have to define your computer as the first DNS. This I can do by editing the file

```
sudo editor /etc/dhcp3/dhclient.conf
```

and remove the comment from the line

```
# prepend domain-name-servers 127.0.0.1
```

to

```
prepend domain-name-servers 127.0.0.1
```

That's it. Now you have to restart the network with

```
sudo /etc/init.d/networking restart
```

and if not already you have to start pdnsd manually

```
sudo /etc/init.d/pdnsd start
```

Now verify if everything is working properly.

```
grep nameserver /etc/resolv.conf
```

should return at least two lines. The first line should be

```
nameserver 127.0.0.1
```

which can be followed by one or more different entries. You can test pdnsd with

```
dig @127.0.0.1 www.ubuntu.com a
```

which should return no errors. To verify that pdnsd is storing it's cache permanently to the harddisk, you can look if the size of the cache storage file is more than 8 Byte.

```
ls -l /var/cache/pdnsd/pdnsd.cache
```

Remember that you are now using a permanent DNS cache. Thus, you will not recognize an update of a DNS entry if it is already cached. Therefore it could be a good idea to remove single entries if you recognize problems with them. 
Use the following command for this but substitute <domainname> with the particular domainname, e.g ubuntu.com

```
sudo pdnsd-ctl record <domainname> delete
```

Next time you access this domainnamr, pdnsd will retrieve the actual DNS entry and caches it again.

From time to time e.g. after vacations it could be usefull to clean the whole cache. It can be done by executing

```
sudo pdnsd-ctl empty-cache
```

---

### Post by almostlinux on 2005-10-30
thanks a lot ...  i was just thinking of setting up loca dns cache

---

### Post by tassoman on 2006-01-05
My cachefile is written only if i restart pdnsd service.
Moreover how can i set cache expire after N days?

---

### Post by MrMinute on 2006-01-09
From "man pdnsd.conf":

ttl=number;
              Specifies  the  ttl  (time  to live) for all resource records in
              this section after  this  entry.  This  may  be  redefined.  The
              default is 86400 seconds (=1 day).

---

