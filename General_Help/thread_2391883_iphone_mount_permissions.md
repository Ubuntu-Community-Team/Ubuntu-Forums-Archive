---
title: "iphone mount permissions"
date: 2018-05-14
forum: General Help
---

### Post by fattyz on 2018-05-14
Hi this is a generic Linux question I hope and the distro in particular would not change how this works?  I've been a member a long time, I hope you can exercize a little patience.

Mounting iphone.  I got my iphone mounted (mint 18.3) but to repeat the process I am getting permission denied errors.

I log in and enter in terminal

Idevicepair pair

This brings up the "trust this computer" on the iPhone. Then I hit trust and do it again all good.

Next the mount commands (I created the directories in the first step, /media/iPhone.

"sudo chown <your user>:<your group> /media/iPhone
ifuse /media/iPhone/"

IDK if I don't type it in right or I'm not logged in right but I'm getting permission denied, even if I "sudo -i" or "sudo su" which makes me root.

I had to try mint because I just couldn't get Ubuntu working correctly on this Dell Laptop.

Thanks so much, altough I've been using this a long time I'm still a noob.

---

### Post by fattyz on 2018-05-14
I guess this has to do with if or not I used the caps correctly IDK anyway I'll keep on messing around with it.

Thanks

---

### Post by yancek on 2018-05-14
Pretty detailed instructions at the link below.  Have you tried:  sudo chmod 777 /media/iPhone

[https://askubuntu.com/questions/812006/how-can-i-mount-my-iphone-6s-on-ubuntu-16-04/817481](https://askubuntu.com/questions/812006/how-can-i-mount-my-iphone-6s-on-ubuntu-16-04/817481)

> Mounting iphone.  I got my iphone mounted (mint 18.3) but to repeat the process I am getting permission denied errors

Not sure what you mean by that.  Do you umount before trying to mount again?   Have you edited the /etc/fuse.conf file as discussed at the link?

---

