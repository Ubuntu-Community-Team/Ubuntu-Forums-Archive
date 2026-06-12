---
title: "x11vnc crashing after 1 minute"
date: 2018-12-28
forum: General Help
---

### Post by pssturges on 2018-12-28
Hi,

I have a very long standing Mythbuntu system that I upgraded to 18.04 a few months ago. Since then, the vnc server crashes after approx one minute of a client being connected. After the apparent crash, the connection is lost and can't be re-established. The only way to re-establish a connection is to reboot the server machine.

Now, this being a long standing system, I'm pretty certain that at some time in the distant past, I have messed around with the vnc server on this machine. But I really have no idea what I may have done. I'm not even certain that the standard default server is installed. What I can say is that x11vnc server is currently installed and starts on boot.

One of the issues I have found in trying to get to the bottom of this is that I don't seem to be able to find any x11vnc logs nor any of the config files that are applied when it is launched. I've found several guides around the web for setting up x11vnc and none of the usual logs and configs exist on my system. What I have been able to find is that webmin tells me that the instance of x11vnc was launched as follows:

```
x11vnc -rfbauth /home/phil/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb
```

I would like to modify how that command is run to at least specify a log file, but I have no idea where/how it is run.

I know there are several other vnc servers, perhaps I'd be better off with a different one?

Anyhow, any help appreciated.

Thanks

---

### Post by munelear on 2019-01-19
I had the same issue and same story of upgrade path.  I think I was able to resolve this by adding -noxrecord to the options for x11vnc. I did this based on these posts:
[https://ubuntuforums.org/showthread.php?t=1612704&page=2&p=10082455#post10082455](https://ubuntuforums.org/showthread.php?t=1612704&page=2&p=10082455#post10082455)
[https://bugs.freedesktop.org/show_bug.cgi?id=30032#c1](https://bugs.freedesktop.org/show_bug.cgi?id=30032#c1)


additional details:
$ x11vnc --version
x11vnc: 0.9.13 lastmod: 2011-08-10

vnc logs here:
~/.xsession-errors

vnc session password here:
~/.vnc/passwd

vnc is launched here, you can modify the parameters in this file:
/usr/share/mythbuntu/session.sh

Good luck.

---

### Post by pssturges on 2019-01-19
Yes! That's exactly the info I needed. All working again.
Thanks munelear!

---

