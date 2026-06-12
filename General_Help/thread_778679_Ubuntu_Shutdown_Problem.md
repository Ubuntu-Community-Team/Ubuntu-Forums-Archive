---
title: "Ubuntu Shutdown Problem"
date: 2008-05-02
forum: General Help
---

### Post by williamm on 2008-05-02
Hi All,
I started using ubuntu 8.04 about a week ago. I am very pleased with almost everything, but the shutdown process seems to have suffered WRT previous versions.

On selecting shutdown, I first get five lines of text thus:
Starting anac(h)ronistic cron anacron [ok]
Starting deferred execution scheduler adt [ok]
Starting periodic command scheduler crond [ok]
Checking battery state [ok]
Running local boot scripts (etc/rc.local) [ok]

There is then about a minute's delay, before a lot of text runs past much to quickly to be read.
The last line reads:

Network Manager mn_dbus_signal_device_status_change: assertion 'cb_data> data-> dbus_connection failed.

After all this, the Ubuntu goes through its normal shut down and turns the computer off.
I should also mention that this happens on both desktop and laptop computers, and also my friend Charlie has the same problem on his two computers.

Three questions:
Is there something that needs to be corrected?
If so What? and
If nothing is wrong how can I stop this annoying behaviour?

---

### Post by kpkeerthi on 2008-05-02
Strangely I received the same network manager message when I was using it in Archlinux (I switched to a much better tool called netcfg lately). I think its an upstream issue in network-manager0.6.6 and not really ubuntu's.

---

### Post by mridkash on 2008-05-02
When you see that screen, press ctrl-alt-f7 it'll say, 'Shutting Down Gdm' that is what takes about 2 minutes on my laptop.

---

### Post by noynac on 2008-05-02
This issue is discussed in the following thread:

[http://ubuntuforums.org/showthread.php?t=772733&highlight=window+login+shutdown](http://ubuntuforums.org/showthread.php?t=772733&highlight=window+login+shutdown)

See posting 13 for a possible fix.

---

### Post by mridkash on 2008-05-04
I tried that method but it works only once. It is quite strange.

---

