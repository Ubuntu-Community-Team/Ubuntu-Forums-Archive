---
title: "virtual camera stop working in OBS after upgrading to Ubuntu 21.04"
date: 2021-07-11
forum: General Help
---

### Post by irv on 2021-07-11
Not sure if the install of Ubuntu 21.04 removed something needed to run the virtual camera in OBS. After upgrade it installed OBS 26.1.2 so I did
```
sudo rm /etc/apt/sources.list.d/btbn*
```
But it could not find it to remove it. Then I did a
```
sudo add-apt-repository ppa:obsproject/obs-studio
```
```
sudo apt-get update
```
```
sudo apt-get purge obs-*
```
```
sudo apt-get install obs-studio
```
I am now at OBS Studio 27.0.1 I still have the button for 
> Start Virtual Camera
But it will not work. My question is: Is there something I am still missing? The way I ran the purge it should have removed obs-plugins and then reinstall them
Just for the record, I am not using "Wayland" but "xorg."

---

### Post by irv on 2021-07-11
I found this:
> Bad News, Everyone!
As of 2021-07-02, upgrading to Ubuntu (or Pop!_OS) 21.04 creates a problem with the Virtual Camera feature of OBS Studio. Fortunately, there is a workaround that&#8217;s only very mildly annoying.

I&#8217;m experiencing the problem in this issue: [https://github.com/obsproject/obs-studio/issues/4808](https://github.com/obsproject/obs-studio/issues/4808).

I work around the problem by doing the following:

Exit OBS Studio.
$ sudo modprobe -r v4l2loopback
Launch OBS Studio.
Press Start Virtual Camera.
If I stop the Virtual Camera, then I need to repeat these steps in order to restart it. Not so bad. I wish the OBS Studio team well in fixing the problem; I wish I knew enough to be able to help.
and it works, but not a good way to do this.

---

