---
title: "can't start X; how to enable nvidia-glx-new via commandline?"
date: 2008-05-28
forum: General Help
---

### Post by lewis1711 on 2008-05-28
X won't start because 

"Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but this X module has the version 1.09631.

So I downloaded nvidia-glx-new, and tried to enable it via restricted-manager (feisty), but it just uninstalls nvidia-glx-new and installs nvidia-glx (a documented error), and so I get the API mismatch error again.

Also for some reason even when I copy and paste the xorg.conf info from my live cd into the box in question, x still won't start and still says I have an API mismatch. must have something to do with me extracting the kernel source...I tried to get the nvidia.run driver file thing I had working, and I think I just made the problem worse.

The REALLY confusing thing is it was working fine until I restarted one day. I had nvidia-glx enabled and all was rosey.

Any ideas?

---

### Post by PmDematagoda on 2008-05-28
Just start from scratch again, do:-
```
sudo apt-get remove --purge nvidia-glx nvidia-glx-new
```

Then reinstall the driver with:-
```
sudo apt-get install nvidia-glx-new
```
and run nvidia-xconfig with:-
```
sudo nvidia-xconfig
```

See if that solves your problem.

---

### Post by Guinness70 on 2008-05-28
thanks PmDematagoda

after yesterday's update of Gutsy puter wouldnt recognize my graphics card
and put my 19" TFt on 800x600

i followed your instructions and looks like its all fixed.

---

### Post by lewis1711 on 2008-05-29
> **PmDematagoda said:**
> Just start from scratch again, do:-
```
sudo apt-get remove --purge nvidia-glx nvidia-glx-new
```

Then reinstall the driver with:-
```
sudo apt-get install nvidia-glx-new
```
and run nvidia-xconfig with:-
```
sudo nvidia-xconfig
```

See if that solves your problem.

Thanks Pm

No luck, I did all the above, but the same thing. Further more, upon typing

```
dpkg-query -l | grep nvidia
```

I get told both nvidia-glx-new and nvidia-glx are still there. 

I don't understand why apt-get remove --purge hasn't removed nvidia-glx.

Any anymore ideas?

---

### Post by PmDematagoda on 2008-05-29
Just do the apt-get removal command for nvidia-glx-new and nvidia-glx and see if nvidia-glx still remains.

---

