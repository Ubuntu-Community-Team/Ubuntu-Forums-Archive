---
title: "TOR disappeared completely from system (ubutnu 16.04)"
date: 2017-02-13
forum: General Help
---

### Post by iapetus2 on 2017-02-13
Hello, I am extremely new to the entire Linux world. I installed TOR through the terminal exactly as instructed. I used it for about 5 days with no problems, I installed other programs as well and shut down my computer every night. Yesterday I restarted my computer because it froze on the log in screen. Once it restarted I noticed Tor was no longer locked to my launcher. I searched for it on the computer with no luck. I looked for it with terminal using the below codes.

ubuntu@ubuntu:~$ dpkg-query -L tor-browser
dpkg-query: package 'tor-browser' is not installed

 ubuntu @ubuntu:~$ dp kg-query -L tor | grep torrc
dpkg-query: package 'tor' is not installed

The other programs that I installed before and after TOR are still there with no problems. I didn't lose any saved files either just TOR. I will be reinstalling but I wanted to make sure it doesn't happen again and why it happened.

Thank You for your help!

---

### Post by yetimon_64 on 2017-02-13
> **iapetus2 said:**
> ... I installed TOR through the terminal exactly as instructed...If possible, could you please provide us with a link to those instructions you followed ?
Doing so will help us see exactly what is installed which may help narrow down what your problem is.
Cheers, yeti.

---

### Post by iapetus2 on 2017-02-13
[https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)

Option two: I run Ubuntu Xenial Xerus and want TOR version stable/

Thank you for the help.

---

### Post by yetimon_64 on 2017-02-14
If you have followed the installation instructions carefully the next codes will show if it is there.
```
apt-cache policy tor
```
and
```
which tor
```

Having followed the instructions here (setting the repository up for trusty, _*You will need to set up for Xenial*_) I get ...
```
yetiman:~ $ apt-cache policy tor
tor:
  Installed: 0.2.9.9-1~trusty+1
  Candidate: 0.2.9.9-1~trusty+1
  Version table:
 *** 0.2.9.9-1~trusty+1 0
        500 http://deb.torproject.org/torproject.org/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.2.4.27-1build0.14.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     0.2.4.20-1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```
and
```
yetiman:~ $ which tor
/usr/sbin/tor
```

I can fire tor up in the terminal however ...
```
yetiman:~ $ apt-cache policy tor-browser
N: Unable to locate package tor-browser
```
there is no tor-browser.

If you want the secure tor browser you don't need the full tor service installed as per your current instructions.
I have previously downloaded the tor browser bundle and have even unpacked it to a USB stick and can run it from there without installing anything to the OS itself.

[[COLOR=#0000ff]--Here--[/COLOR]]("https://www.torproject.org/projects/torbrowser.html.en") is a link for the tor browser download pack. If all you need is secure browsing this will do by itself. You only need the full tor installation if you have other applications or services to be re-directed through the tor set up, besides just the browser. It will depend on your usage needs as to which style of installation, full or standalone browser, you will want to do.

Hope this helps a bit, cheers, yeti.
[B]
Edit:[/B]If I recall correctly there may be a PPA with tor packaged up for ubuntu. You may want to look into (google) the ppa for ubuntu if you do need to have a full installation of tor.

---

### Post by igdfpm on 2017-02-14
torbrowser-launcher is in the repos...

Install that then run it in a terminal to install the latest stable version of the browser (can be a very slow download so bare with it) - tor tools (to tor-ify other apps) will be installed as dependencies ;)

Why make it more complicated?

---

### Post by iapetus2 on 2017-02-18
sorry for the late reply but THANK YOU SO MUCH!!

---

### Post by oldrocker99 on 2017-02-18
Since your problem is fixed, please mark this thread as [SOLVED].

---

