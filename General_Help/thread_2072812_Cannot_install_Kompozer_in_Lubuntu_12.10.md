---
title: "Cannot install Kompozer in Lubuntu 12.10"
date: 2012-10-18
forum: General Help
---

### Post by thedoctor81877 on 2012-10-18
I am having great difficulty installing Kompozer in Ubuntu 12.10. So far I do not see it in Synaptic, and it does not appear available when I type

```


sudo apt-get install kompozer


```

When I attempt to use the terminal to install kompozer, I get the following:

```


E: Package 'kompozer' has no installation candidate


```

I have downloaded it from
 
[http://http://www.kompozer.net/download.php]("http://http://www.kompozer.net/download.php")

but find no install or read me file. Help please. Thanks!

---

### Post by sienile on 2012-10-18
If you had looked further down under the developmental version, you would have seen a Ubuntu repository link. A few clicks later, and here's your answer:
```
sudo add-apt-repository ppa:giuseppe-iuculano/ppa

sudo apt-get update

sudo apt-get install kompozer
```

---

### Post by thedoctor81877 on 2012-10-18
When I tried that I end up getting the following:

```


W: Failed to fetch http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found


```

???

---

### Post by alodeiro on 2012-10-18
> **thedoctor81877 said:**
> When I tried that I end up getting the following:

```


W: Failed to fetch http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found


```???



Same problem here... :(

---

### Post by alodeiro on 2012-10-18
> **alodeiro said:**
> Same problem here... :(

here is the solution:

[https://launchpad.net/ubuntu/quantal/+package/kompozer]("http://ubuntuforums.org/here is the solution:")

install [kompozer-data]("https://launchpad.net/ubuntu/precise/amd64/kompozer-data") first, all packages available .deb and sources :popcorn:


comments..



:guitar:

---

### Post by neilmanson on 2012-10-18
Kompozer appears to ahve been removed from the repositories for 12.10 :(

I have just installed BlueGriffon from getdeb.net which appears to be a reasonable alternative.

---

### Post by brashley46 on 2012-10-20
Bluegriffon works, but the repositories REALLY need to include a WYSIWYG HTML editor. which Bluefish is NOT . :(

---

### Post by vasa1 on 2012-10-20
> **thedoctor81877 said:**
> I am having great difficulty installing Kompozer in Ubuntu 12.10. ...

I have downloaded it from
 ...
but find no install or read me file. Help please. Thanks!
That site seems to have an unmaintained version?
Why don't you install Seamonkey instead? That has "Kompozer" built-in.
Seamonkey is available from [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) (but not from the repos.)

---

### Post by nestor77 on 2012-10-26
From sourceforge: [http://kompozer.sourceforge.net/](http://kompozer.sourceforge.net/)
in the right menu click en downloads
in the page [http://kompozer.net/download.php](http://kompozer.net/download.php)
download the installer for windows
install it with wine

it is explained in spanish

[http://tayrona.org/ubuntu/kompozer.html](http://tayrona.org/ubuntu/kompozer.html)

---

### Post by tomdkat on 2012-11-09
> **alodeiro said:**
> here is the solution:

[https://launchpad.net/ubuntu/quantal/+package/kompozer]("http://ubuntuforums.org/here is the solution:")

install [kompozer-data]("https://launchpad.net/ubuntu/precise/amd64/kompozer-data") first, all packages available .deb and sources :popcorn:


comments..



:guitar:
Thanks!  :guitar:

Peace...

---

### Post by tomdkat on 2012-11-09
> **vasa1 said:**
> That site seems to have an unmaintained version?
Why don't you install Seamonkey instead? That has "Kompozer" built-in.
Seamonkey is available from [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) (but not from the repos.)Unfortunately, the HTML editor in Seamonkey doesn't have a CSS editor. That's one of the reasons I use Kompozer. :)

Peace...

---

### Post by strugglingbadly on 2012-11-12
I have the same problem with 12.10. With reference to a previous reply:

[https://launchpad.net/ubuntu/quantal/+package/kompozer]("http://ubuntuforums.org/here%20is%20the%20solution:")

install [kompozer-data]("https://launchpad.net/ubuntu/precise/amd64/kompozer-data") first, all packages available .deb and sources 

Would any one like to explain what the above means? A list of the required files, where I get them from, which directory I need to put them, and a detailed sequence of commands would be appreciated. 'install........' is a bit too general and means nothing to me - I need step by step instructions.

Alternatively, how can I revert back to 12.04?

thanks

---

### Post by MrRedPants on 2012-11-17
STEP 1:

Download this:
[http://launchpadlibrarian.net/102977237/kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb](http://launchpadlibrarian.net/102977237/kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb)

Once it downloads, click on it, should open Ubuntu software center, click install.

STEP 2:

Download from here:
[https://launchpad.net/ubuntu/quantal/+package/kompozer](https://launchpad.net/ubuntu/quantal/+package/kompozer)

You'll see a list of options based on hardware. I downloaded the i386 because I have an intel processor. Which is this file:
[http://launchpadlibrarian.net/102977238/kompozer_0.8~b3.dfsg.1-0.1ubuntu2_i386.deb](http://launchpadlibrarian.net/102977238/kompozer_0.8~b3.dfsg.1-0.1ubuntu2_i386.deb)

Once that is downloaded, same thing - click it, opens in software center, then install.

It will then install as any other and you should be good to go.

---

### Post by dcstar on 2012-11-19
> **MrRedPants said:**
> 
.........
You'll see a list of options based on hardware. I downloaded the i386 because I have an intel processor.

"i386" has NOTHING to do with having an Intel processor, that is the old 32-bit architecture for the few remaining non-64 bit capable systems.

---

### Post by deadlylady on 2012-11-29
> **MrRedPants said:**
> STEP 1:

Download this:
[http://launchpadlibrarian.net/102977237/kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb](http://launchpadlibrarian.net/102977237/kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb)

Once it downloads, click on it, should open Ubuntu software center, click install.

STEP 2:

Download from here:
[https://launchpad.net/ubuntu/quantal/+package/kompozer](https://launchpad.net/ubuntu/quantal/+package/kompozer)

You'll see a list of options based on hardware. I downloaded the i386 because I have an intel processor. Which is this file:
[http://launchpadlibrarian.net/102977238/kompozer_0.8~b3.dfsg.1-0.1ubuntu2_i386.deb](http://launchpadlibrarian.net/102977238/kompozer_0.8~b3.dfsg.1-0.1ubuntu2_i386.deb)

Once that is downloaded, same thing - click it, opens in software center, then install.

It will then install as any other and you should be good to go.

> **dcstar said:**
> **"i386" has NOTHING to do with having an Intel processor, that is the old 32-bit architecture for the few remaining non-64 bit capable systems.**
Are you sure about that? I have an intel-processor and 64-bit system but the only file that wasn't labeled "wrong architecture" was the "i386". 
However I couldn't install the i386 either because:
> (Reading database ... 167122 files and directories currently installed.) 
Unpacking kompozer (from .../kompozer_0.8~b3.dfsg.1-0.1ubuntu2_i386.deb) ... 
dpkg: dependency problems prevent configuration of kompozer: 
 kompozer depends on kompozer-data. 
 
dpkg: error processing kompozer (--install): 
 dependency problems - leaving unconfigured 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for man-db ... 


??

Note that I already installed the Kompozer-data file without any problems?

---

### Post by Raybo on 2012-12-19
> **thedoctor81877 said:**
> When I tried that I end up getting the following:

```


W: Failed to fetch http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found


```

???

His ppa does not support quantal so that is why you get the error.

---

### Post by blackdalek on 2012-12-25
I read through this thread and now I am confused - Is it possible to install Kompozer on Ubuntu 12.10 or not?

---

### Post by TheGurkha on 2012-12-28
> **alodeiro said:**
> here is the solution:

[https://launchpad.net/ubuntu/quantal/+package/kompozer]("http://ubuntuforums.org/here is the solution:")

install [kompozer-data]("https://launchpad.net/ubuntu/precise/amd64/kompozer-data") first, all packages available .deb and sources :popcorn:

comments..

:guitar:


Thanks, that worked perfectly for me.

---

### Post by ciaps on 2013-02-15
> **MrRedPants said:**
> STEP 1:

Download this:
[http://launchpadlibrarian.net/102977237/kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb](http://launchpadlibrarian.net/102977237/kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb)

Once it downloads, click on it, should open Ubuntu software center, click install.

STEP 2:

Download from here:
[https://launchpad.net/ubuntu/quantal/+package/kompozer](https://launchpad.net/ubuntu/quantal/+package/kompozer)

You'll see a list of options based on hardware. I downloaded the i386 because I have an intel processor. Which is this file:
[http://launchpadlibrarian.net/102977238/kompozer_0.8~b3.dfsg.1-0.1ubuntu2_i386.deb](http://launchpadlibrarian.net/102977238/kompozer_0.8~b3.dfsg.1-0.1ubuntu2_i386.deb)

Once that is downloaded, same thing - click it, opens in software center, then install.

It will then install as any other and you should be good to go.
I run ubuntu studio 12.10 and that worked for me too. Easy, fast and smooth.
Thank you!

---

### Post by Island_Jon on 2013-06-23
I used the 2 quantal .deb packages successfully on Ubuntu 13.04 (Raring) and Linux Mint 15.
thanks loads.

running: Acer AS5742 Intel Core i3-370M

---

