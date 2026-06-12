---
title: "No apache MPM package installed error"
date: 2013-02-10
forum: General Help
---

### Post by yeikel on 2013-02-10
Hi guys ):P

I am running Ubuntu 11.10 and I am  trying to install apache2 but I had not luck .

What I did :

```
sudo apt-get install apache2

```

After that , the next should be "start the service" , with a simple 

```
sudo /etc/init.d/apache2 start

```

BUT , I get this >> "No apache MPM package installed"

```
root@local:/# sudo /etc/init.d/apache2 start
No apache MPM package installed
root@local:/#

```


I tried to figure out what is the problem finding in google but all I did was to waste my time, I tried to re-install everything a couple of times and same result , Now I am out of ideas so that is why I am asking here. I hope that someone could be able to help me .


Thanks you so much.

---

### Post by sandyd on 2013-02-10
try
```

sudo apt-get update
sudo apt-get install apache2-mpm-prefork
```

Also - fyi - support for Ubuntu 11.10 ends this April 2013 - I advise you upgrade to receive the latest packages (you can still use 11.10, but it will no longer be supported, and you will have to switch to the old-releases.ubuntu.com repo)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by yeikel on 2013-02-10
> **sandyd said:**
> try
```

sudo apt-get update
sudo apt-get install apache2-mpm-prefork
```Also - fyi - support for Ubuntu 11.10 ends this April 2013 - I advise you upgrade to receive the latest packages (you can still use 11.10, but it will no longer be supported, and you will have to switch to the old-releases.ubuntu.com repo)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Thanks for your reply , but it gives me that  apache2-mpm-prefork is already installed

I tried re-installing it and the end of the install process the error appears again 


```
apache2-mpm-prefork (2.2.20-1ubuntu1.3) ...
No apache MPM package installed
```


edit : Finally fixed , thanks! (now I have others problems haha)

---

### Post by nsquared on 2013-03-12
> **yeikel said:**
> Thanks for your reply , but it gives me that  apache2-mpm-prefork is already installed

I tried re-installing it and the end of the install process the error appears again 


```
apache2-mpm-prefork (2.2.20-1ubuntu1.3) ...
No apache MPM package installed
```


edit : Finally fixed , thanks! (now I have others problems haha)


I have the same problem. How did you solve it?

---

### Post by afaquejam on 2014-01-19
1. Stop the apache server if it is running.
    ```
sudo service apache2 stop
```

2. ```
 sudo apt-get purge apache2 apache2-utils apache2.2-bin apache2-common
```

3. ```
apt-get autoremove
``` 
    After this, I rebooted my machine. But I think it should work without rebooting.

4. ```
sudo apt-get install apache2
```

5. Enjoy. Lash out on me by replying to this comment, if it doesn't work.

---

