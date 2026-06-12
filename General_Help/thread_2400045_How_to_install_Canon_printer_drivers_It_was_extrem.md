---
title: "How to install Canon printer drivers? It was extremely user unfriendly task!"
date: 2018-09-01
forum: General Help
---

### Post by postcd on 2018-09-01
Hello,

i have Ubuntu 16.04.5 LTS
LightDM

i see it not automatically recognized the printer Canon MG2150

i found various commands on the internet and did:

 ```
2039  wget -v http://gdlp01.c-wss.com/gds/6/0100003926/01/cnijfilter-mg2100series-3.60-1-deb.tar.gz
 2041  tar -xzf cnijfilter-mg2100series-3.60-1-deb.tar.gz
 2043  cd cn*
 2045  sh install.sh
```

It told me that the nijfilter-mg2100series depends on libtiff4, but this package is not installed. So i found a command that i executed:

```
wget http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_**i386**.deb
```

(alternative for 64bit OS is: ```
wget http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_**amd64**.deb
```)

```
sudo dpkg -i libtiff4_3.9.7-2ubuntu1_i386.deb
```

Then run again: ```
sudo bash nijfilter-mg2100series-3.60-1-deb/**install.sh**
```

The result:

```
The printer registration has not been completed.
Register the printer manually by using the lpadmin command.
```

```
$ lpadmin
Usage:

    lpadmin [-h server] -d destination
    lpadmin [-h server] -x destination
    lpadmin [-h server] -p printer [-c add-class] [-i interface] [-m model]
                       [-r remove-class] [-v device] [-D description]
                       [-P ppd-file] [-o name=value]
                       [-u allow:user,user] [-u deny:user,user]


```

When googling that messages, i seen commands: 
```
cd /etc; sudo ./cupsys restart
service cups restart
```
But cups do not exist. "Failed to restart cups.service: Unit cups.service not found."

So i did: ```
sudo apt-get install cups
```
I proceed even it installed alot of packages, 28MB (quite big, do not know if i could anyhow minimized it more?)

After that i see cups (printing service) is running and on System tools / Printers i can see i can add new printer (i though before i was unable to add the printer, i may be wrong), and on next page i saw Canon MG2100. So i added it and tried to test. The printing finished OK.

I am wondering if this is normal process every newbie Linux user had to go thru. This is unbelievable and a joke - user unfriendly. Is there any easier process i should have been going thru to install the printing software?

---

### Post by Impavidus on 2018-09-02
No, not every newbie has to go through that process. Those who have an HP printer just plug it in and it works, but not all hardware manufacturers are equally willing to help Linux users with good and easily installable drivers. It's a bit of hit-and-miss with hardware support on Linux. With some luck or careful planning everything works out of the box, but sometimes printers, scanners, graphics and wifi drivers give difficulties.

However, I thought cups was supposed to be installed by default. It was on every (Xu/U)buntu install I ever did. Libtiff should also be there, but that's libtiff5, not libtiff4, which is outdated. It seems that that driver is rather old.

Also note that instructions you find on the web are often outdated.

---

### Post by kurt18947 on 2018-09-02
Impavidus is right, it depends on the manufacturer. In my experience HP & Brother are fairly simple, Canon and Epson require some knowledge. Since moving to Ubuntu, I always do a bit of research on prospective hardware before purchasing. If a manufacturer can't be bothered to make an effort to support Linux, I can't be bothered to buy their product.

---

### Post by QIII on 2018-09-02
@postcd:

Had you included your text in code tags instead of quote tags (as with many of the other items in the post), the formatting would have been preserved for a long URL.

For example:

```
https://www.amazon.com/Ubuntu-Unleashed-2019-Covering-18-04/dp/013498546X/ref=sr_1_fkmr1_1?ie=UTF8&qid=1535907756&sr=8-1-fkmr1&keywords=ubuntu+18.04+handbook
```

versus

[https://www.amazon.com/Ubuntu-Unleashed-2019-Covering-18-04/dp/013498546X/ref=sr_1_fkmr1_1?ie=UTF8&qid=1535907756&sr=8-1-fkmr1&keywords=ubuntu+18.04+handbook](https://www.amazon.com/Ubuntu-Unleashed-2019-Covering-18-04/dp/013498546X/ref=sr_1_fkmr1_1?ie=UTF8&qid=1535907756&sr=8-1-fkmr1&keywords=ubuntu+18.04+handbook)

The Forum software intelligently shortens URLs to avoid excessive text.  The shortened links are still clickable.

If you had intended for others to be able to see the commands and results as you saw them in a terminal, placing the text in code tags would have preserved them.

---

