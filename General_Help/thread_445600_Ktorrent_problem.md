---
title: "Ktorrent problem"
date: 2007-05-16
forum: General Help
---

### Post by Angelbeast on 2007-05-16
I've been haing all kinds of trouble with torrent clients. I'm running Ubuntu 64 bit. I seem to get the best speeds from ktorrent but it seems to choke my bandwidth and i can't browse web pages. Is there any way that i can fix this?

---

### Post by Angelbeast on 2007-05-19
*bump*

---

### Post by toasterofirony on 2007-05-19
Try scaling back the no. of connections/ upload speed.

---

### Post by Angelbeast on 2007-05-19
> **toasterofirony said:**
> Try scaling back the no. of connections/ upload speed.

thanks i'll try that...i had uninstalled it though  and i'm trying to reinstall it by compiling it from the source code because i want to learn how to do it. Some other things i want to install are only available that way. Well it looked like i was having some success but then it just topped with this error:

> checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
ron@ron-laptop:~/Desktop/ktorrent-2.1.4$ make
make: *** No targets specified and no makefile found.  Stop.
ron@ron-laptop:~/Desktop/ktorrent-2.1.4$ make install 

this is what i put in the terminal:

> tar -xvzf ktorrent-2.1.4.tar.gz
cd /home/ron/Desktop/ktorrent-2.1.4
./configure
make
make install 

You wouldn't happen to know what i did wrong would you?

---

### Post by toasterofirony on 2007-05-19
Ummm, not compiled anything for a while, but I'm guessing you're lacking libcpp.

Also, when compiling you might want to think about including checkinstall to make it into a .deb, thus making it easier to remove it as and when you feel like it.

Check out [this forum]("http://ubuntuforums.org/forumdisplay.php?f=44") for more advice on compiling etc.

---

### Post by Angelbeast on 2007-05-19
> **toasterofirony said:**
> Ummm, not compiled anything for a while, but I'm guessing you're lacking libcpp.

Also, when compiling you might want to think about including checkinstall to make it into a .deb, thus making it easier to remove it as and when you feel like it.

Check out [this forum]("http://ubuntuforums.org/forumdisplay.php?f=44") for more advice on compiling etc.

Thanks :-)

I'll check it out in the morning...Well it's morning now...but sleep is calling...*LOL*...thanks again...

---

