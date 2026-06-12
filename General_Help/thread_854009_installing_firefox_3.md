---
title: "installing firefox 3"
date: 2008-07-09
forum: General Help
---

### Post by revenge2 on 2008-07-09
Hey guys i downloaded Firefox 3 from the Mozilla site. But i dont know how to install it. How do i install Firefox from the Firefox-3.0.tar.bz2 file?

-Thanks

---

### Post by iaculallad on 2008-07-09
> **revenge2 said:**
> Hey guys i downloaded Firefox 3 from the Mozilla site. But i dont know how to install it. How do i install Firefox from the Firefox-3.0.tar.bz2 file?

-Thanks

It's available in the repo: Try to install using the terminal:

```
sudo apt-get install firefox-3.0
```

---

### Post by Bubba64 on 2008-07-09
You can extract into the home file and launch it from a folder in the file then build a launcher in the edit menus, and just right click on the other FF in the menu to see what the launcher looks like. Did you look to see if FF3 was in synaptic, before you downloaded this one from Mozilla it is a hassle to get the plugins to work with the download, good luck if you want more help post what distro your running.

---

### Post by balaknair on 2008-07-09
If you're running Hardy Heron, just use Synaptic to install FF3 from the Ubuntu repositories. It's simpler to get plug ins working and won't mess up your Firefox profiles.

For earlier versions of Ubuntu, check this page-
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Have fun

---

### Post by revenge2 on 2008-07-09
> **Bubba64 said:**
> You can extract into the home file and launch it from a folder in the file then build a launcher in the edit menus, and just right click on the other FF in the menu to see what the launcher looks like. Did you look to see if FF3 was in synaptic, before you downloaded this one from Mozilla it is a hassle to get the plugins to work with the download, good luck if you want more help post what distro your running.

uhh question. what is the difference of using the terminal?. When you type in sudo apt-get install firefox 3.0 where does it come from? is it downloaded from somewhere? and do you not need to specify the directory if it was on the pc?.

Could someone please tell me the difference between using the terminal and using synaptic package manager?.

How do you use the synaptic packager manager?.

And what would you do when you have downloaded .tar.bz2 files? how would you install or run them?.

-Thanks

---

### Post by zvacet on 2008-07-09
> Could someone please tell me the difference between using the terminal and using synaptic package manager?.

Synaptic is front end for apt,so you will get same result if you use terminal or synaptic.To use synaptic go to the system<admin>synaptic package manager and click on it.In search box type nwme of the package you want to install and swynaptic will find it.On the left of package you will see white box.Click on it if you want to install.When package is installed that box will become green.

[Here]("http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux#Ubuntu_7_10_and_8_04")

---

### Post by stchman on 2008-07-09
> **revenge2 said:**
> Hey guys i downloaded Firefox 3 from the Mozilla site. But i dont know how to install it. How do i install Firefox from the Firefox-3.0.tar.bz2 file?

-Thanks

What Ubuntu are you running?  In Ubuntu Hardy it is the default.  In Kubuntu it is in the repos.

---

### Post by Chappy7777 on 2008-07-10
> **revenge2 said:**
> Hey guys i downloaded Firefox 3 from the Mozilla site. But i dont know how to install it. How do i install Firefox from the Firefox-3.0.tar.bz2 file?

-Thanks

I was reading the FFox forums and it seems that many, or most of those who installed FFox 3 have a problem w/cookies. As in, FFox 3 is not retaining them from login to login (to FFox 3). IOW, every time you use it, you need to
enter any info that the cookies usually hold. To some this may sound like security heaven, but Mozilla isn't happy about it. 

I didn't notice if this was just a MS bug, or if it happens in Linux as well. I assume the latter.

---

