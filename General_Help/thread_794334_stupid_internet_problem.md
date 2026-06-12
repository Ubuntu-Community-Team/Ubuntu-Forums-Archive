---
title: "stupid internet problem"
date: 2008-05-14
forum: General Help
---

### Post by mihailojocic on 2008-05-14
My internet connection was good about 10 days. After that something strange happens. I can open google, gmail and few other sites, everything else is unavailable (waiting [www..](www..).) . Skype and other chat programs also work fine. Can somebody help me to resolve this problem?

I use Ubuntu 8.04 and I try to connect with firefox and opera

Thanks

---

### Post by pytheas22 on 2008-05-14
Pick a site that you can't open in your web browser, and please do these things to help narrow the problem down to it sources.  I'll use ubuntu.com as an example of a site that you can't access:

1. In a terminal, type:

```
ping ubuntu.com
```

and post the output here.

2. In a terminal, type:

```
host ubuntu.com
```

You should get output telling you which IP address corresponds to the site (for ubuntu.com, it's 91.189.94.158).  Type this number into the address bar of your web browser.  Does the page load?

3. Create a new user account and log in using it.  Are you able to access the pages there?

4. Install firestarter, a GUI for configuring your firewall:

```
sudo apt-get install firestarter
```

Run the application by typing "sudo firestarter" in a terminal.  After configuring it, click the button to turn the firewall off.  Does this make a difference in the pages you can access?

These things will help determine whether the problem is related to a firewall, DNS resolution, your web browser or some user configuration setting.

---

### Post by mihailojocic on 2008-05-14
first thanks for help

1. In a terminal, type:

```
ping ubuntu.com
```

and post the output here.

PING ubuntu.com (91.189.94.158) 56(84) bytes of data.
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=1 ttl=43 time=62.6 ms
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=2 ttl=43 time=61.7 ms
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=3 ttl=43 time=56.8 ms
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=4 ttl=43 time=55.8 ms
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=5 ttl=43 time=60.4 ms
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=6 ttl=43 time=64.4 ms
...
...
...

2. I can't load the page when type IP address

3. I was create new user account and I'm no able to open any page

4. I can't install firestarter. APT can't access to internet (waiting for headers)

I was try to install it manually but many files are missing when i type ./configure

what now?

---

### Post by pytheas22 on 2008-05-14
Alright, a little strange...you can ping the sites but you can't access them over http or through whatever port apt uses.  This could be a firewall issue, although it's weird that you can access a few sites.

First, try downloading the firestarter Debian package from [http://packages.ubuntu.com/hardy/firestarter](http://packages.ubuntu.com/hardy/firestarter), and try to use it to turn the firewall off.

Also, can you boot to a live CD and try to load web sites there?

---

### Post by badfish591 on 2008-05-14
it sounds to me like your having DNS problems, maybe one of your ISPs DNS servers is down?
maybe try pinging your DNS servers like you tried doing to the website.
and maybe flushing your DNS cache with ```
sudo /etc/init.d/nscd restart
```

---

### Post by mihailojocic on 2008-05-15
> **pytheas22 said:**
> Alright, a little strange...you can ping the sites but you can't access them over http or through whatever port apt uses.  This could be a firewall issue, although it's weird that you can access a few sites.

First, try downloading the firestarter Debian package from [http://packages.ubuntu.com/hardy/firestarter](http://packages.ubuntu.com/hardy/firestarter), and try to use it to turn the firewall off.

Also, can you boot to a live CD and try to load web sites there?


When I boot from CD i have internet. 

Les night I didn't have any connections but this morning I was start my laptop and internet works just fine. I was install firestarter immediately and now i just can wait. This is not first time for me to have this problem. Before I was thinking that I kill Ubuntu. Stupid me! :-)

---

### Post by pytheas22 on 2008-05-15
Glad to hear it's working now.  Sounds like perhaps it was a problem with ISP, if the Internet suddenly is fixed again and Ubuntu wasn't changed.  But at least you have Firestarter now so you can watch the connection if there's a problem again.

---

