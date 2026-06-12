---
title: "Gnucash 2.0.1 install on Edgy"
date: 2007-01-04
forum: General Help
---

### Post by Benchrest on 2007-01-04
If someone could make a howto of installing Gnucash 2.0.1 on Edgy I would appreciate it. I have determined that unlike Breezy, with Edgy Gnucash is only installable from source. I will give my installation procedure that is unproven. But it seems little is available.

Uncommended the four optional repositories in the /etc/apt/sources.list

run sudo aptitude update

run sudo apt-get build-dep gnucash

The above prehaps would be best to run as aptitude. I got a download of 116 routines! And if failed at the end because of timeout that left 3 missing. I then download them. Took over and hour.

Ran sudo apt-get source -b gnucash

It ran for a short time and gave error message that dpkg-dev may not be installed. I installed it and called it a night.

This morning attempted to pick up with sudo apt-get source -b gnucash and got message 29 dependancies missing.

I decided to try from the beginning. 

sudo aptitude update
sudo apt-get build-dep gnucash

went quickly this time as I guess it recognized most had been downloaded last night.

Then ran sudo apt-get source - b gnucash

This has now been running near 3 hours! I would say over 10,000 lines of messages conservatively. I am concerned it might be in a loop. About every 500 lines I think it is repeating, but the messages are going so fast it's hard to tell.

I been torn between posting this in the installation forum vs tips etc. but rather than fix my problem I would hope someone could post an installation procedure known to work.

Thanks

---

### Post by PriceChild on 2007-01-04
*moved approved and bumped*

---

### Post by druhboruch on 2007-01-04
It worked for me:

[http://www.geole.info/Deb-Packages-for-Ubuntu-Edgy.73.0.html?&l=1](http://www.geole.info/Deb-Packages-for-Ubuntu-Edgy.73.0.html?&l=1)

---

### Post by Benchrest on 2007-01-04
I will give it a looksee. Thanks.

My source assembly did finish after 3 hours and 20 minutes. I then was able to install the package. Was able to start the program but no further testing.

---

### Post by Benchrest on 2007-01-04
the geol web site is not what I am looking for. It seems to only be a download site but no instructions. Gives a little on new features but not how to install. I want something for the novice who has never installed source before. Perhaps I will give it a try after I find my install really works. 

However, being a novice I'm not sure what commands are best and still have no idea if installing 119 dependencies sounds right. Even if mine works, I might have installed many more dependency packages than I need.

There maybe a basic process documented that would be used to install any source program. I will do some searching in that direction.

---

### Post by druhboruch on 2007-01-04
I think that the instructions are very clear:
[http://www.geole.info/Repository-for-deb-packages-deb.9.0.html?&l=1](http://www.geole.info/Repository-for-deb-packages-deb.9.0.html?&l=1)

:confused:

---

### Post by stebrepar on 2007-01-05
I installed the 2.0.1 package just fine the other day from Automatix on my Edgy/6.10 system.
-- 
Stephen

---

### Post by nix4me on 2007-01-05
I used synaptic to install it just now and it installed just fine on my Edgy machine.

nix4me

---

### Post by rbmorse on 2007-01-05
> **Benchrest said:**
> I will give it a looksee. Thanks.

My source assembly did finish after 3 hours and 20 minutes. I then was able to install the package. Was able to start the program but no further testing.

I just installed 2.0.4 on Feisty from source, the whole process took less than 30 minutes AFTER I spent an hour sorting dependencies. Linux documentation/error messaging still sucks.

---

