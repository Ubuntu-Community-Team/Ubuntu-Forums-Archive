---
title: "Proxy problem in (K)Ubuntu"
date: 2007-02-26
forum: General Help
---

### Post by kitt on 2007-02-26
Hi all,
        I have installed KDE on ubuntu, and i access the internet through an http proxy.
       My problem is that many KDE apps are not able to connect to the internet. Example: adept, apt-get, etc. To use apt-get, i have to use gnome's root terminal. I am stuck!
          Whats the problem here? Do i need to look into my proxy settings more? (konqueror works , though).

---

### Post by r0ck80y on 2007-02-26
Does your /etc/apt/apt.conf have the proxy settings. If not then u can add the following in your apt.conf file:-
```

//Acquire::http::Proxy "false";
Acquire {
  http {
       Proxy "http://user:pass@proxyhost:port/";
    };
  ftp {
       Proxy "http://user:pass@proxyhost:port/";
//  Add the following line if ure behind a univ firewall and they keep local repos for ubuntu          
Proxy::proxyhost "DIRECT";
     };
};

```
See if it helps :)

---

### Post by kitt on 2007-02-26
It is still saying the same old thing:

Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

---

### Post by kitt on 2007-02-26
Oh, and one more thing, synaptic works in gnome, but gives the above error message in kde! :-(

---

### Post by dodoltengik on 2007-06-13
in my kubuntu I configure like this
.profile
export http_proxy="http://{your proxy ip}:8080"

/etc/apt/apt.conf
Acquire::http::proxy "http://10.0.1.5:8080";

after that restart the .profile
try with echo $http_proxy,

if you already got the right proxy ip, than try to tun

sudo aptitude update

I hope it can help

---

