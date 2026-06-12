---
title: "Way to check that install is OK?"
date: 2017-04-02
forum: General Help
---

### Post by lysander6662 on 2017-04-02
Today I reinstalled 16.04, I will go into why elsewhere. Anyway, I tried to install the restricted extras and didn't realise that I had to hit tab in order to get the OK button highlighted! I couldn't work out how to highlight it so I killed the process. Therefollows a tale of n00bness that seemed to eventually work, but which could have gone very wrong.

I ended up with the red no entry icon in the panel and the error "broken count > 0".

When trying to fix this I ran

```
sudo apt-get remove ubuntu-restricted-extras

```

And got a notification that 


**Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)**


I tried to get round this by using the command 


```
sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock   

```

Now this is where things get interesting. The screen went black for about ten seconds before Ubuntu managed to get to the login screen. After logging in it would then go back to the login screen, and black, a couple more times. Restarting the computer through the panel was hopeless, but REISUB eventually had to be used and one or two more restarts.

After this I was able to enter the following 

```
sudo apt-get clean
sudo apt-get update

```
Then I was prompted to enter the following 

```
sudo dpkg --configure -a

```

Which I did, followed by
```

sudo apt-get install -f
```

I ended up back in the licence agreement for the restricted extras. I then realised I had to hit tab, OK'd the agreement and it installed, apparently "with no errors".

Everything seems to be working absolutely fine now, and everything has been stable for a few hours. But is there any way I can check that everything is OK and nothing broken, so to speak? That'll teach me to be hasty in the future.

---

### Post by Bucky Ball on 2017-04-02
Open a terminal.

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
``` 

Run those three and if there's no errors, there's no issues (probably). ;)

You probably went off on a wild goose chase here:

```
Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
```

That means you have two package managers open at the same time. You probably had the Software or Synaptics open while you were trying to run 'apt' commands in a terminal. That won't work. 

They all use apt but not at the same time. You can only have one open if you intend to use apt.

The more specific you are the better we can help. You're talking about hitting an okay button but give no indication of the app you're using. You can't assume we know (I don't; Synaptic? In which case 'broken=0' is a good thing.). :)

---

### Post by lysander6662 on 2017-04-02
Thanks for that, Bucky, here's the output of your suggestion:

```
lysander@psychopig-xxvii:~$ sudo apt autoremove
[sudo] password for lysander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


lysander@psychopig-xxvii:~$ sudo apt update
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:3 http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu xenial InRelease
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:5 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu xenial InRelease
Hit:6 http://repository.spotify.com stable InRelease                           
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:8 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:9 https://deb.opera.com/opera-stable stable InRelease                      
Fetched 306 kB in 0s (327 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.


lysander@psychopig-xxvii:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
lysander@psychopig-xxvii:~$ 
```

So it seems ok. The "ok" button was in the terminal, which is where the ubuntu-restricted-extras was entered. Should have been more clear on that.

---

### Post by Bucky Ball on 2017-04-02
All looks fine to me. Unless the machine starts throwing some other unexplained errors, I'd say mark as 'solved' and carry on. ;)

---

### Post by howefield on 2017-04-03
> **lysander6662 said:**
> So it seems ok. The "ok" button was in the terminal, which is where the ubuntu-restricted-extras was entered. Should have been more clear on that.

The "ok" button is part of the ttf-mscorefonts-installer package. Might be useful to know what is installed with the meta package that is ubuntu-restricted-extras.

[http://packages.ubuntu.com/xenial/ubuntu-restricted-extras](http://packages.ubuntu.com/xenial/ubuntu-restricted-extras)
[http://packages.ubuntu.com/xenial/ubuntu-restricted-addons](http://packages.ubuntu.com/xenial/ubuntu-restricted-addons)

The second link (-addons package) refers to the packages that are installed when you elect to install the codecs, ect, during the Ubuntu installations option but are also a dependency for the -restricted-extras package.

---

### Post by lysander6662 on 2017-04-03
Yes, I decided to install the codec packages during installation, installing VLC seemed to solve one other problem I was having with loading videos. Thank you to you both.

---

