---
title: "how to create asound config to save Alsa mixer settings?"
date: 2013-07-18
forum: General Help
---

### Post by eival on 2013-07-18
trying to get the gnome alsa mixer to save my settings when i close it but its not, ive found some old terminal codes but its not working, atleast for Ubuntu 12.04 LTS any thoughts?


```
sudo alsactl store 0
```
```
sudo cp -p /etc/asound.state
```
this is the problem
```
cp: missing destination file operand after `/etc/asound.state'
```

---

### Post by steeldriver on 2013-07-18
Well you need to give it the name of a file to copy *to*

However iirc 'alsactl store' creates its file at /var/lib/alsa/asound.state rather than at /etc/asound.state, also unless you want to save different states per user you don't need to copy that file, you can leave it where it is and just do 'alsactl restore' on reboot from your /etc/rc.local file - see here --> [http://ubuntuforums.org/showthread.php?t=1983423&p=11982132#post11982132](http://ubuntuforums.org/showthread.php?t=1983423&p=11982132#post11982132)

---

### Post by eival on 2013-07-18
> **steeldriver said:**
> Well you need to give it the name of a file to copy *to*

However iirc 'alsactl store' creates its file at /var/lib/alsa/asound.state rather than at /etc/asound.state, also unless you want to save different states per user you don't need to copy that file, you can leave it where it is and just do 'alsactl restore' on reboot from your /etc/rc.local file - see here --> [http://ubuntuforums.org/showthread.php?t=1983423&p=11982132#post11982132](http://ubuntuforums.org/showthread.php?t=1983423&p=11982132#post11982132)


isnt there another terminal code to have it apply the settings automatically when you reboot as well?

never mind, it appears to of saved and stay applied when i rebooted

---

