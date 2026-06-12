---
title: "Another way to install"
date: 2006-07-27
forum: General Help
---

### Post by .::welemski::. on 2006-07-27
Hi, I just wondered everytime you need to install an application or a functionality you will  need to use an apget or doing a deb-src etc. All uses and internet connection on a machine where you would want to install the app.

Is there a way that to download these applications on a different machine with a faster internet connection and install the downloaded source/application/bins to the other machine.

I know we can download all thi bins and src on the net but my question is using the repositories in ubuntu. It is very hard to destinquish which one on the lists is needed. since aptget and synaptec automatically detect application dependencies.

Because it would take me 5 10 hours just for installation on a dial up modem.
How would you do this if you're on an internet cafe'?

---

### Post by gingermark on 2006-07-27
In the future, [APTonCD](http://www.cypherbios.org/aptoncd/) will probably be what you want.

In the meantime you could download the [UbuntuPlus](http://ubuntuforums.org/showthread.php?t=183933) CD - although browsing the [UbuntuPlus Repository](http://www.tikal26.net/ubuntu/apt/dists/dapper/main/binary-i386/Packages) there doesn't seem to be a lot for Dapper at the moment.

If you have access to a computer with a fast connection and a decent amount of freespace, and you can use it for a considerable amount of time, you could attempt to backup the repositories onto DVD. That guide is [here](http://ubuntuforums.org/showthread.php?t=205569).

Hope that helps.

---

### Post by aysiu on 2006-07-27
I think the best thing to do is get this:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

Or... use a Ubuntu live CD on your computer with a faster connection. Let's say you wanted to install *alien*, *kword*, and *epiphany*.

Boot up the live CD on the faster connection computer. Then go to the terminal and type in ```
sudo apt-get clean
sudo aptitude update
sudo aptitude install kword epiphany-browser alien
``` Then go to /var/cache/apt/archives and copy all the .deb files to a USB key or iPod or some external drive.

Then copy those .deb files to the other computer's desktop and then ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by .::welemski::. on 2006-07-28
Im using a mac with a fast internet connection. How would I do this?
Is there any program that I should install? It would be great if it will support pause and resume....

---

### Post by aysiu on 2006-07-28
> **.::welemski::. said:**
> Im using a mac with a fast internet connection. How would I do this?
Is there any program that I should install? It would be great if it will support pause and resume....
So you have a Ubuntu box with a slow or no internet connection, and you have a Mac with a fast connection?

Same deal. Boot the Ubuntu live CD on your Mac.

---

