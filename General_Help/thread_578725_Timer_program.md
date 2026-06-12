---
title: "Timer program?"
date: 2007-10-17
forum: General Help
---

### Post by gukarma on 2007-10-17
Hello,

I am a first timer with 7.10 and I am enjoying it very much! Very intuitive and easy so far.

I do need one functionality, though: a shutdown timer. I had one in jetaudio for windows and jetaudio isn't compatible with ubuntu. 

I am also confused about how to install programs. The system add menu works well, but I need programs outside of that list. I want to install, for instance, zsnes. There is no ".exe." or ".bin" file in the zip I got. I know this is a basic question. I will read whatever you tell me to that teaches me how to do that.

Thanks.

---

### Post by raja on 2007-10-17
The equivalent for an 'exe' file that you will get for a debian based distro (which Ubuntu is) will be a '.deb' file. So, if the application you want is not in the official repositories (search in the package manager), you can see if someone else has packaged it as a 'deb' file. [Getdeb]("http://www.getdeb.net/") is a popular place to get such unsupported packages.
If this is not available, the source code may be available and you may be able to compile it yourself, but it is not definitely recommended in the early stages. So the bottomline is that if the application is not available in the repository or in the unofficial debian package providers, you may not be able to use it.

---

### Post by gukarma on 2007-10-17
The getdeb site worked great - thanks!

Still waiting on a timer, however.

---

### Post by callan79 on 2007-10-18
> **gukarma said:**
> The getdeb site worked great - thanks!
Still waiting on a timer, however.

Easy solution for you, at terminal :

```

sudo shutdown -h 20
sudo shutdown -h 14:00
sudo shutdown -h now

```

These items perform the following :

 - shutdown in 20 minutes
 - shutdown at 2pm
 - shutdown now

If you want to reboot instead, use -r instead of -h

Cheers :)
Callan

---

