---
title: "From China, how to install Tor Browser on Ubuntu18?"
date: 2018-08-05
forum: General Help
---

### Post by yys2 on 2018-08-05
Hi all,
I have installed and used Tor Browser on my unbuntu16 with the following commands
```

sudo [COLOR=#0000FF]add-apt-repository pp[COLOR=green]a:webupd8team/tor-browser
sudo apt-[COLOR=#0000FF]get update
sudo apt-get install tor-browser[/COLOR][/COLOR][/COLOR]
```
It works well.

Now, I try to switch to Ubuntu 18, and find that I can&#8217;t install Tor Browser with the above commands.
Here is the log message:
```

sudo add-apt-repository ppa:webupd8team/tor-browser
Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]                                
Hit:2 http://cn.archive.ubuntu.com/ubuntu bionic InRelease                                                 
Get:3 http://cn.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                          
Ign:4 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu bionic InRelease                                         
Get:5 http://cn.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                                              
Err:6 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu bionic Release                                          
  404  Not Found [IP: (omitted )]
Reading package lists... Done                                                                                               
E: The repository 'http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


$ sudo apt-get update
Hit:1 http://cn.archive.ubuntu.com/ubuntu bionic InRelease                               
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]                                                 
Ign:3 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu bionic InRelease 
Err:4 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu bionic Release    
  404  Not Found [IP: 91.189.95.83 80]
Get:5 http://cn.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]    
Get:6 http://cn.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                                              
Reading package lists... Done                                                                                               
E: The repository 'http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


$ sudo apt-get install tor-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tor-browser

```

I also find that I can install "Tor Browser", "Tor Browser Launcher Settings" from "Ubuntu Software". But, after launching them, they can't download Tor Browser at all, because the networks are blocked from China.


My questions are:
1. Is the following method for installing Tor Browser on Ubuntu 18 available ?
```

sudo [COLOR=#0000FF]add-apt-repository pp[COLOR=green]a:webupd8team/tor-browser
sudo apt-[COLOR=#0000FF]get update
sudo apt-get install tor-browser[/COLOR][/COLOR][/COLOR]
```

2. If it is not available on Ubuntu 18, how can I install and use Tor Browser on Ubuntu 18 from China?

Cheers
Yao

---

### Post by Frogs Hair on 2018-08-05
There have been no updates for that PPA in 74 weeks, so not likely updated for 18.04.Tor is in the Ubuntu repository You can also  download and extract  the preferred  tor package and run it using launcher in the folder though how secure the method I can't answer. 


[https://linuxconfig.org/how-to-install-tor-browser-in-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-tor-browser-in-ubuntu-18-04-bionic-beaver-linux)


[https://launchpad.net/~webupd8team/+archive/ubuntu/tor-browser](https://launchpad.net/~webupd8team/+archive/ubuntu/tor-browser)

---

### Post by coffeefiend on 2018-08-05
> **yys2 said:**
> 
I also find that I can install "Tor Browser", "Tor Browser Launcher Settings" from "Ubuntu Software". But, after launching them, they can't download Tor Browser at all, **because the networks are blocked from China**.

Do you have access to any secure VPNs?

---

