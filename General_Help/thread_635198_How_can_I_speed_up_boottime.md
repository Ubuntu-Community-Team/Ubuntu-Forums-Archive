---
title: "How can I speed up boottime"
date: 2007-12-08
forum: General Help
---

### Post by Kobin on 2007-12-08
I'm wondering if anyone knows how to improve the time it takes to boot Ubuntu?

The reason is that I would like to use Ubuntu on an old laptop, Pentium III 700 Mhz, 128 Mb ram, just installing the commandline system and then using flux- or openbox. And I am also considering to use GeUbuntu.
I have TinyMe installed right now, which boots into openbox in 1 minute. It works fine but I would rather  use Ubuntu or GeUbuntu.
I tried to install Ubuntu commandline system. It took 1 and a half hour to install in comparison with 30 minutes for tiny me. Well thats not so important since its not something I would have do so often.
But the big problem for me was that it took 3 minutes just to boot to commandline, and ofcourse extra after I added X and openbox. Not nice on a laptop.
But I am thinking that if it is possible for TinyMe, shouldn't it then somehow also be possible to configure Ubuntu to have similar performance?

Hope someone has some ideas that go beyond saving 5 or 6 seconds..

---

### Post by staticvoid on 2007-12-08
sudo apt-get install bootchart bootcharter
(not sure which one it is)

it will generate a log of what takes how much time to boot, then, somehow, you'll be able to fix it to go faster :) I wish I could help you more.. : /

for me, Debain linux has booted the quickest. but I have 1 ghz cpu so booting my kubuntu system really does not take much time... lol  :D


sv

---

### Post by oldos2er on 2007-12-08
The minimum spec for RAM in Ubuntu is 256MB; if I were you I'd bump up the RAM in your machine to as much as it can handle.

---

### Post by roachk71 on 2007-12-08
I'm not too sure whether this approach would work or not, with only 128MB of RAM, but you could use:
```
sudo apt-get install prelink
```and issue this command:
```
sudo prelink -amvfR
```This command will prelink your ELF binaries with their shared libraries, decreasing load time.

Another way to speed load times would be installing Preload, but I don't recommend this with such limited memory (192 or 256MB would be a conservative minimum.)

Another approach would be installing sysv-rc-conf and disabling any services you don't need at boot time, but be careful.

I used to own an old (1997) Compaq laptop with only 72MB RAM. Somehow, I was able to get Mandrake 7.1 installed and running with very few problems, but with KDE it was agonizingly slow. Then I switched it to Damn Small Linux, which was much faster (though it still took no less than 50 seconds to boot.) And that machine couldn't be expanded further.

---

