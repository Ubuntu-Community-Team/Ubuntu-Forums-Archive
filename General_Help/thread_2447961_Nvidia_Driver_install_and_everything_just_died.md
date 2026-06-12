---
title: "Nvidia Driver install and everything just died"
date: 2020-07-29
forum: General Help
---

### Post by shammakh2 on 2020-07-29
So I was programming .. Oh and I am very new to linux ...
Anyways
I wanted to start using my GPU Nvidia GeForce GT 540M
So I installed the latest nvidia driver which was a bad idea and I restarted 
And everything died

This is what happened
I broke my system 
[https://imgur.com/a/q0W2iEu](https://imgur.com/a/q0W2iEu)

As you can see in the video, when I switch to tty2
The tty1 screen keeps flickering, its crazy.... cant even type

Anyways
After that I tried to purge all nvidia related stuff off my system and restart
I also blacklisted nouveau after doing `ubuntu-drivers devices` and `ubuntu-drivers autoinstall`

But at this point I have no idea what I am doing
And I need help

Oh btw
`sudo systemctl start gdm` 
But it doesn't work so yeh

Help pls

---

### Post by NM5TF on 2020-07-29
> **shammakh2 said:**
> So I was programming .. Oh and I am very new to linux ...
Anyways
I wanted to start using my GPU Nvidia GeForce GT 540M
So I installed the latest nvidia driver which was a bad idea and I restarted 
And everything died

This is what happened
I broke my system 
[https://imgur.com/a/q0W2iEu](https://imgur.com/a/q0W2iEu)

As you can see in the video, when I switch to tty2
The tty1 screen keeps flickering, its crazy.... cant even type

Anyways
After that I tried to purge all nvidia related stuff off my system and restart
I also blacklisted nouveau after doing `ubuntu-drivers devices` and `ubuntu-drivers autoinstall`

But at this point I have no idea what I am doing
And I need help

Oh btw
`sudo systemctl start gdm` 
But it doesn't work so yeh

Help pls

"so I was programming"

were you...doing what exactly ???

"I wanted to start using my GPU Nvidia GeForce GT 540M"

was it not working before ??? was your system working before you installed nvidia drivers ???

did not see the video you uploaded to imgur, just a blank screen...

"After that I tried to purge all nvidia related stuff off my system and restart"

how did you attempt this.....what procedure did you follow ???

"I also blacklisted nouveau after doing `ubuntu-drivers devices` and `ubuntu-drivers autoinstall`"

why did you blacklist nouveau ???  if your system was working before the nvidia install, it was most likely using noveau....

"But at this point I have no idea what I am doing
And I need help"

I believe it.....

since you provide no system information, how can you expect to get help ???

rather than trying to fix your mess, wouldn't it be easier to just re-install Ubuntu.....

tommy

---

