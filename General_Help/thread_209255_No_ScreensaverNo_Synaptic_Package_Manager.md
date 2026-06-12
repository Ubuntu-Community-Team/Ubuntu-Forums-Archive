---
title: "No Screensaver/No Synaptic Package Manager"
date: 2006-07-04
forum: General Help
---

### Post by Phil_McCrackin on 2006-07-04
I'm not really sure when this problem began, which makes it somewhat difficult to zero in on the source. I'm certain it was about the time of the last kernel update. I first noticed when my machine went idle, there was no screensaver, just a blank screen. going into the screensaver utility, the sample window remains blank for all of them. Then I decided to try to re-install them, as well as a few more goodies from the synaptic. The download carries out without a hitch. During installation however, on particular packages I get something like this:

```
Unpacking  replacement screensaver-gl ...
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--20:23:23-- ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
                  => `/tmp/file2ftVSk'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...failed: Connection timed out.
Retrying.
```

Finally, I just have to ctrl-c out (d will not kill the process) or I will be locked up completely.

I have tried repeatedly over the past few days thinking maybe the server was down or something, but I have pinged it and package transfer was normal. Other normal operations seem to  be going on okay, but I seem to be unable to get any more updates now (and still no screensaver).

Any ideas???

Thanks in advance
Phil_McCrackin

---

### Post by Dr. Nick on 2006-07-04
It would appear you tried to install seti at home at one time and it failed, and now stops anything else from installing. Do you want seti? May just go into synaptic and mark it for removal and see if that fixes it at all.

It looks like it is trying to install it, but the package isnt on your hard drive and the server doesnt have it anymore. 

Actually the entire alien.ssl.berkely server seems offline, so it might be adviseable to remove it from your sources.list file. and then running apt-get update

---

### Post by Phil_McCrackin on 2006-07-04
I tried to mark for removal, and run into the same issue as it tries to connect to alien.ssl.berkeley. Strangely, it is not listed in sources.list file at all.

EDIT: I actually got one of the packages (csh) I was trying to install (even though it was interrupted by the same issue). I still have no screensaver...-heh

---

