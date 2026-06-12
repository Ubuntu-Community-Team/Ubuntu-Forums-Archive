---
title: "Package dependency issues transmission"
date: 2013-09-05
forum: General Help
---

### Post by prem1er on 2013-09-05
I'm running 12.04 and had updated my repos to pull a newer version of transmission. After a couple months during a system update I had an error telling me that transmission-common was the incorrect version. So, now I can't run apt-get install/update without errors. Here is the versions I currently have installed


```
prem1er@bubbles:~/download$ transmission-daemon -V
transmission-daemon 2.82 (14160)
prem1er@bubbles:~/download$ transmission-gtk -v
transmission-gtk 2.82 (14160)

transmission-common - 2.82-0ubuntu0.12.04.2 is installed

```

The problem is that both of these packages have a dependency on a different version of transmission-common and I can't meet both (as in >=). What do I need to do here to fix this? TIA

---

### Post by varunendra on 2013-09-06
Have you already tried a purge --> reinstall of the packages? That is -
```
sudo apt-get purge transmission transmission-daemon transmission-gtk transmission-common
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install transmission
```

If they don't help, please post the error messages when doing "apt-get update", plus outputs of -
```
dpkg -l | grep transmission
apt-cache show transmission-common | grep Version
apt-cache show transmission-gtk | grep Version
```

---

### Post by prem1er on 2013-09-06
Thanks for the reply. No, I wanted to try and avoid doing a reinstall, because I have some configurations that I wanted to keep. Basically I'm running 2 instances of transmission at the same time to segregate certain files. I can always save my configurations, but will a purge remove the following directories?

/var/lib/transmission and /etc/transmission

---

### Post by varunendra on 2013-09-06
> **prem1er said:**
> I can always save my configurations, but will a purge remove the following directories?

/var/lib/transmission and /etc/transmission

I'm not sure. Best to back them up as well if they contain something you consider important.

---

### Post by prem1er on 2013-09-06
Ok, I'll give it a shot and report back.

---

### Post by prem1er on 2013-09-06
> **varunendra said:**
> Have you already tried a purge --> reinstall of the packages? That is -
```
sudo apt-get purge transmission transmission-daemon transmission-gtk transmission-common
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install transmission
```

This worked for me. I did need to backup my configuration as the purge parameter removed the files. All seems to be good now. Thanks.

---

### Post by varunendra on 2013-09-06
Great !! Was experimental for me too. :D

Thanks for the feedback !

---

