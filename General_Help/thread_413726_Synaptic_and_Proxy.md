---
title: "Synaptic and Proxy"
date: 2007-04-19
forum: General Help
---

### Post by chakkaradeep on 2007-04-19
Hi All,

I dont know why, but many have ignored this !

I connect to internet through Proxy Authentication. I made apt-get to work with this by having the apt.conf at /etc/apt

> 
chaks@chaks-laptop:~$ cat /etc/apt/apt.conf
Acquire::http::Proxy "http://uname:pwd@proxy.student.otago.ac.nz";
Acquire::ftp::Proxy "ftp://uname:pwd@proxy.student.otago.ac.nz";


And my http_proxy and ftp_proxy variables to set too,

> 
http_proxy=http://uname:pwd@proxy.student.otago.ac.nz
ftp_proxy=ftp://uname:pwd@proxy.student.otago.ac.nz


To even be more safe, I have set the system wide proxy settings in *System->Preferences->Network Proxy*

Now, In Synaptic, I have set the Proxy again in the *Preferences->Network*

After all these settings change, Synaptic does not work . It fails to download packages or perform Reload and throws error that *Proxy Authentication is needed*

apt-get works fine.

One weird thing what I found is, If you open synaptic as *sudo synaptic* it works but not as *gksu or gksudo synaptic* ! Why is *gksu or gksudo* does not recognize proxy settings ???

Is there any solution for this ? I know there is thread associated with this, but there is no solution and thats the reason I have started it again.

---

### Post by chakkaradeep on 2007-04-20
Anybody there ? :)

---

### Post by SiCk949 on 2007-04-23
the same problem for me... :(

---

### Post by lennie2 on 2007-04-24
Did you resolve this I have the same problem and is new to Linux :-(

---

### Post by chakkaradeep on 2007-04-24
> **lennie2 said:**
> Did you resolve this I have the same problem and is new to Linux :-(

I am sorry lennie. I have searched the whole internet and many forums, and even filed under Ubuntu's bug section,but no response :(

---

### Post by strabes on 2007-04-24
Put proxy settings at the end of ~/.bashrc:

```
gksudo gedit ~/.bashrc
```

> export http_proxy "http://username:yourpassword@proxyurl:yourport"

Then run ```
source ~/.bashrc
```

---

### Post by chakkaradeep on 2007-04-24
> **strabes said:**
> Put proxy settings at the end of ~/.bashrc:

```
gksudo gedit ~/.bashrc
```



Then run ```
source ~/.bashrc
```

All the options are done strabes, it just doesnt work :(

---

