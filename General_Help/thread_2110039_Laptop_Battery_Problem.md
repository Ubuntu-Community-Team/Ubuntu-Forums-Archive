---
title: "Laptop Battery Problem"
date: 2013-01-29
forum: General Help
---

### Post by mattyasaurus on 2013-01-29
Hi guys!

I have a Dell Inspiron N5050 laptop which was purchased early December 2012. When I purchased it came with Windows 7 and I made the complete switch to Ubuntu 12.04.01 LTS earlier this month.

Since the complete switch I have noticed that my battery life has decreased quite drastically.  I would say since running Ubuntu I get around an hours usage and when I had windows 7 installed it lasted around 2 to 2.5 hours (approximately).

I was just wondering if there was anything specific that could be causing this??

Thanks in advance for any help that can be provided!

---

### Post by hawthornso23 on 2013-01-29
Video drivers are a likely suspect. Have you got the proprietary drivers installed?

---

### Post by omeomi on 2013-01-29
Does the laptop have a dedicated videocard aside from the Intel HD graphics chip? If so, you will need to look into [Bumblebee]("http://bumblebee-project.org/") or similar to shut down the dedicated videocard when not in use. This caused the battery of my Dell to run out very fast initially as well.

---

### Post by BlinkinCat on 2013-01-29
Hi,

At some stage you may be interested in this -

[http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)

Others recommend it - :P

---

### Post by offgridguy on 2013-01-29
I haven't tried this myself, but it looks interesting.

[http://ubuntuforums.org/showthread.php?t=1607911](http://ubuntuforums.org/showthread.php?t=1607911)
[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

edit; afterthought,i do get better battery life with lubuntu than with ubuntu 12.04.

---

### Post by mattyasaurus on 2013-01-29
The only video card in use is the Intel HD so i wouldn't think I should need to install Bumblebee??
I installed the proprietary drivers after finding some information doing a google search but it has made no difference. After installing the drivers using Terminal I also found  when I open 'Additional Drivers' It states that 'No proprietary drivers are in use on this system.' So they are either not actually installed or at a guess I'm thinking there just not needed on my system?? Don't know if this could affect battery life?

I could try the TLP - Linus advanced power management that BlinkinCat has posted a link to - [http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)
Would anyone else recommend this process?

Thanks again!
[]("http://linrunner.de/en/tlp/tlp.html")

---

### Post by BlinkinCat on 2013-01-29
> **mattyasaurus said:**
> 
I could try the TLP - Linus advanced power management that BlinkinCat has posted a link to - [http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)
Would anyone else recommend this process?

Thanks again!


I know nothing about it as I don't need it. I simply read somewhere on the forums that people gained from it. If it does work for you I would appreciate if you would let me know so that I could pass the information on to others having similar problems.

Cheers and good luck - :P

---

### Post by mattyasaurus on 2013-01-29
> **BlinkinCat said:**
> I know nothing about it as I don't need it. I simply read somewhere on the forums that people gained from it. If it does work for you I would appreciate if you would let me know so that I could pass the information on to others having similar problems.

Cheers and good luck - :P

OK no problem I will try it out.. Anything is worth a go at the minute as I use my laptop for work related things whilst on the move and currently I haven't really been able to do this. I will keep you updated! Thanks again :)

---

### Post by mattyasaurus on 2013-01-29
After installation of TLP it seems like the battery life may have increased slightly, I am going to have a play around with the configuration and see how that works out, Hopefully though the problem will not be a problem for much longer so I am going to mark this thread as solved. Thanks again guys. :P

---

### Post by SafeBatteries on 2013-01-29
The Dell software for windows comes installed with a number of software related "Power Plans" that kick into effect when running on battery power. 

Some of the features that come to mind quickly are....
-Lowering the brightness based on a light sensor. This can be done manually, but its a pain.
-slowing down WiFi so it consumes less power.
-Slowing CPU 
-Slowing graphics card

Perhaps reloading Windows and then installing an VM with Ubuntu may be your best option for preserving the power management software.

I also have some software that I have used to profile laptop power consumption. Could be helpful if you stick with Ubuntu and want to profile the changes you make.

When I find I will post a link to it.

---

### Post by xianbei on 2013-01-29
Jupiter is a program that does a good job incorporating power plans into Ubuntu:

```
sudo apt-get install jupiter
```

There is a service that adds a few minutes too:

```
sudo apt-get install laptop-mode-tools
```

Bonne chance.

---

### Post by hawthornso23 on 2013-02-08
Be careful with laptop-mode-tools. My experience has been that some of its settings are dangerously aggressive. 

The first problem I had with it was turning off my USB mouse after less than 5 seconds of inactivity and then not turning it back on again. That can be fixed by editing the appropriate config file. 

Next however I discovered it was spinning down my harddisk almost immediately it became inactive. That meant I was seeing  spin-cycle behavior when running programs like gvim which backup to disk regularly. Having the disk spin up and down every ten seconds is not only noisy and very annoying - it is also very bad for the life of the disk.

I might have been able to fix that too, but instead I decided to  uninstall laptop-mode-tools because I have lost trust in it. It is just a bit too aggressive in its efforts to save power.  I do like to save power, but I am also interested in other goals like having a laptop with hardware that works and a disk that isn't going to die early through being constantly abused.

---

