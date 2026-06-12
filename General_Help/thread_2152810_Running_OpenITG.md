---
title: "Running OpenITG?"
date: 2013-06-09
forum: General Help
---

### Post by PloXyZeRO on 2013-06-09
Sorry if this is not the place to ask this, I'm not sure
But I've recently installed Ubuntu and I'm still figuring out my way around the OS. I've been able to get most things working (except my Nvidia card but bumblebee helped with that)

But one thing I can NOT get working at all is OpenITG. I downloaded [FONT=arial][OpenITG beta 2 linux.zip]("http://openitg.gr-p.com/full-linux/OpenITG%20beta%202%20linux.zip")[/FONT] from [http://openitg.gr-p.com/](http://openitg.gr-p.com/) and I tried running openitg-beta-2 but nothing happens at all. No window shows up or anything. Can anyone help me out with this? The project is also on githib: [https://github.com/openitg/openitg](https://github.com/openitg/openitg)

Thanks!

Edit: Forgot to include details about my system
Using Ubuntu 13.04 64-bit
Alienware M11x R2
Integrated graphics: Intel HD Graphics (Intel Ironlake Mobile according to Ubuntu)
Descrete graphics: Nvidia GeForce 335M (Not in use unless I use the optirun command in terminal w/bumblebee installed which is a bit annoying)
Processor: Intel i5 U 520 @ 1.07GHz x4
RAM: 4 GB (Ubuntu says 3.7 GiB)

---

### Post by Alex_James on 2013-10-07
You have to run it via terminal. First, go into the OpenITG beta 2 folder, and into data folder. Open static.ini and add line "ShowLoadingWindow=0"
Next, open the terminal by pressing ctrl + alt + t. use command cd "destination folder" (cd ~/Desktop/Openitg beta 2 for desktop)
then use ./openitg-beta-2 to run. You may encounter errors when you launch if you use 64 bit ubuntu, as openitg requires you to have 32 bit binaries.

---

### Post by Alex_James on 2013-10-07
oh, and you can find the 32 bit libraries* to make it work. that post I meant libraries, not binaries

---

### Post by bentennison16 on 2014-01-15
> **Alex_James said:**
> oh, and you can find the 32 bit libraries* to make it work. that post I meant libraries, not binaries

Hey man,

it's sad ITG seems to be dying (since it's not talked about much on here or anywhere else for that matter...)

Anyways, I'm also trying to install the openitg on my linux mint (and I'll just assume it wont matter whether its ubuntu or mint). In which case where do I get the LIBRARIES you mentioned above?

Please anyhelp would be appreciated.

oh btw. this is the msg i get from the terminal when trying to launch the program

igor@igor-Studio-1745:~/Downloads/OpenITGbeta2$ ./openitg-beta-2
./openitg-beta-2: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory
igor@igor-Studio-1745:~/Downloads/OpenITGbeta2$ 

libjpeg.so.62  BLA BLA BLA.... any ideas? if its to do with the libraries, where do I get them ? 

Many thanks

Cheers,

---

### Post by daitenshi on 2014-03-21
It's unfortunate I noticed this so late, but I've been through the same thing and am now successfully running OpenITG on Ubuntu running in an old DDR Extreme cabinet.

I messed around with Ubuntu 64bit and got the libraries where needed until I ran up to a certain point where I needed an older version of the X libraries which my video card driver was dependent on and it ended up being a huge, frustrating waste of time. I believe parts of OITG's source even have to be modified to work if you get all of the libraries.. It simply wasn't built for 64bit and I highly doubt there will be a release in the near future.

I suggest for anybody attempting to run OpenITG on Linux, install a 32bit variant.

If you're worried about limiting your RAM, you can select a PAE kernel on boot, but even 2GB should be overkill, and OP's setup only has 4GB anyway.

---

### Post by Duriano on 2014-06-07
This didn't work for me. what am i doing wrong?

---

