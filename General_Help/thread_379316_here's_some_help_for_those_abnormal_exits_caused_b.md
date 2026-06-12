---
title: "here's some help for those abnormal exits caused by updating ALSA."
date: 2007-03-08
forum: General Help
---

### Post by pixeldotz on 2007-03-08
i tried compiling the snapshot of 3/7 alsa hg. this caused my ubuntu installation to become unbootable. after some searching i was able to fix the problem (about 10 minutes) so i thought i'd put together a quick guide.

you will need-

-ubuntu/xubuntu/kbuntu 6.10 LIVECD since this is what i had.

i have ubuntu 6.10 installed but used my xbuntu livecd to fix it.

now boot up your livecd and mount your hard drive. my harddrive was partitioned as /dev/sda1 and /dev/sda2 i mounted sda2 simply because that was where my entire distro was installed too.

open a terminal and type

```
sudo mount /dev/sda2 /mnt
```

now in the same terminal type

```
sudo mousepad /mnt/etc/modules
```

now comment out everyline that loads a module. put a # in front of each one. save and exit.
shut down your pc and reboot into your regular install, do not use the livecd this time.

once there, go ahead and compile alsa to whatever previous version worked for you. in my case it was 1.0.14.rc3.

once all that is done go ahead and edit /etc/modules again. since you are now back in your regular install of ubuntu, it would be this line

```
sudo gedit /etc/modules
```

*the difference in editors is because ubuntu has gedit and xubuntu has mousepad, i don't know what kubuntu has.*

UNcomment all those lines you commented before and save and exit. close everything out and reboot. now everything should start up as normal with no problems.

in my case it turned out that snd-hda-intel in etc/modules was causing me problems with the snapshot of alsa hg. once i put 1.0.14.rc3 back on my system booted fine. i even purposely broke it again with the snapshot hg version to make thats what it was. however i did have to comment all those modules to get back in there and put rc3 back on. i don't know what this was but that's what worked for me.

---

