---
title: "ABSOLUTE Beginner - I'm trying to embrace the light but my Dark Master ruined me"
date: 2012-11-03
forum: General Help
---

### Post by alaphonse on 2012-11-03
*heavy sigh* I'm missing something here. 

I've Installed Ubuntu 10.04 Lucid Lynx and I've managed a wired connection to the net. I'm having some very BASIC problems.

1. Can't manange wireless connection . I know the network is live, I have 3 other PC's on it. I type in the correct keys/phrase - nothing. Any idea?

2. I'd like to play my games. They need Java and Flash to work. I downloaded the correct Java for Ubuntu 10.04 Lucid Lynx but for the life of me I can't figure out how to install. I've extracted the files, looked at all the files, read the Read Me [worthless, referred me to License URL] Search produces all kinds of codeish geeky goobley gook. I want to click Install and not mess with command line blah blah blah. Do I need a different version of Linux that has these already built in or ????.

---

### Post by Skifu on 2012-11-03
If I understood correctly, you can access the internet with wired, but not wireless connection?
If this is the case, then:

To install Java without command lines, open up Ubuntu Software Center, search for "java" and install "OpenJDK 7"


As for the wifi issue, i think the drivers need to be changed, and that might be kinda codeish geeky goobley gook

[http://ubuntuforums.org/showthread.php?t=1953710](http://ubuntuforums.org/showthread.php?t=1953710)


Have you checked if you could enable some drivers from system System>Administration>*Additional Drivers*?
Is your system up to date?

---

### Post by sammiev on 2012-11-03
You may need a new version of Ubuntu with more up to date drivers.

---

### Post by blackbird34 on 2012-11-03
Yes. I'd suggest Ubuntu 12.04, it picks up a lot of the more recnt hardware out of the box, especially for wifi.

---

### Post by Old_Grey_Wolf on 2012-11-03
I would also suggest installing or upgrading to 12.04. 10.04 will not be supported anymore in about 6 months. 12.04 will be supported until April 2017.

If you want to continue using 10.04, going to System > Administration > Additional Drivers and enabling the wireless drivers may be all you need to do. 

If it doesn't, we will need to determine the wireless card you are using. Enter these commands in a terminal and copy/paste the output in a post here to this thread.

```
lsusb
```

```
lspci -v
```

---

### Post by Old_Grey_Wolf on 2012-11-03
I would also suggest installing or upgrading to 12.04. 10.04 will not be supported anymore in about 6 months. 12.04 will be supported until April 2017.

If you want to continue using 10.04, going to System > Administration > Additional Drivers and enabling the wireless drivers may be all you need to do. 

If it doesn't, we will need to determine the wireless card you are using. Enter these commands in a terminal (press the key combination Ctrl+Alt+t to get to a terminal) and copy/paste the output of the commands in a post to this thread.

```
lsusb
```

```
lspci -v
```

---

