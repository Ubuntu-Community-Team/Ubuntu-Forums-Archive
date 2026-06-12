---
title: "problem starting partimage..."
date: 2008-02-06
forum: General Help
---

### Post by Mia_tech on 2008-02-06
after installing partimage with:

#apt-get install partimage & apt-get install partimage-server

I can open partimage the client but I'm unable to open the server with sudo partimaged

any help appreciated

---

### Post by bodhi.zazen on 2008-02-06
Can you describe the problem ? Are you getting an error message ?

See if this link hleps :

[http://www.digitalissues.co.uk/html/os/misc/partimage.html#11](http://www.digitalissues.co.uk/html/os/misc/partimage.html#11)

---

### Post by Mia_tech on 2008-02-06
no no error message or anything....I typed:

#sudo partimaged

and I get back my shell

#

and nothing happens

---

### Post by bodhi.zazen on 2008-02-06
Is it running ? Can you connect ?

You can list your running processes with :

```
ps aux | grep part
```

If not, try :

```
sudo partimaged -D
```

---

### Post by Mia_tech on 2008-02-06
this is what I got:

jorge@ubuntu-box:~$ ps aux | grep part
partimag  7013  0.0  0.1   5972  1680 ?        Ss   07:10   0:00 /usr/sbin/partimaged -D -d /var/lib/partimaged/
root      9098  0.0  1.1  18132 14576 pts/2    T    16:55   0:01 apt-get install partimage
root      9104  0.0  0.2  18132  2928 pts/2    T    16:55   0:00 apt-get install partimage
jorge    10258  0.0  0.0   2880   752 pts/2    R+   19:12   0:00 grep part

and the port is not open on the server, I just ran nmap localhost, and the default port 4025 is not open so I didn't bother to try to make a connection...

---

### Post by bodhi.zazen on 2008-02-06
Well, I am not an expert on partimage, but I looks like it is running.

> partimag 7013 0.0 0.1 5972 1680 ? Ss 07:10 0:00 /usr/sbin/partimaged -D -d /var/lib/partimaged/

I would try connecting , and if you have a problem would assume it is a network / firewall issue ?

---

