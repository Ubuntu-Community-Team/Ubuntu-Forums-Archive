---
title: "Having trouble with CUDA installation (Ubuntu 16.04)"
date: 2018-01-24
forum: General Help
---

### Post by saya18 on 2018-01-24
I've installed CUDA (at least I feel like I did) and have a Nvidia driver installed but when I run a Python module that uses CUDA, I'm getting an 
error that  "libcuda.so.1 file" is not found. 

I'm using ubuntu 16.04 and using Python 3.6 /Python 2.7

This is the exact error:

```
ImportError: libcuda.so.1: cannot open shared object file: No such file or directory
```



From what I've been told, this file is a link and it needs to be  linked to my graphics card driver.

I wasn't sure how to check if i have this link but I ran this command and I got back this as an output (abridged):

```
find / -type f -name "libcuda.so.1
```




```
ind: ‘/etc/cups/ssl’: Permission denied
find: ‘/etc/polkit-1/localauthority’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-colord.service-QhckWW’: Permission denied
find: ‘/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-systemd-timesyncd.service-A46ooI’: Permission denied
find: ‘/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-rtkit-daemon.service-pZ6U3J’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/var/tmp/systemd-private-7216baf4e9e24f4b99aa9cd9d37e9779-rtkit-daemon.service-vEpGYO’: Permission denied
find: ‘/var/tmp/systemd-private-c9508c53c88848febd8d6b9c7758d44d-colord.service-6sVMbw’: Permission denied
find: ‘/var/tmp/systemd-private-7216baf4e9e24f4b99aa9cd9d37e9779-systemd-timesyncd.service-DifcXc’: Permission denied
find: ‘/var/tmp/systemd-private-7216baf4e9e24f4b99aa9cd9d37e9779-colord.service-j5hYyg’: Permission denied
find: ‘/var/tmp/systemd-private-81dcc732570e47799cb04c3cb0c5a2c6-systemd-timesyncd.service-dSg1Cz’: Permission denied
find: ‘/var/tmp/systemd-private-f72e80f0374645bda6c2d99c5628e374-colord.service-FbxlSK’: Permission denied
find: ‘/var/tmp/systemd-private-5065912711c44bfd880f3aca2d0008e7-colord.service-rq0MKq’: Permission denied
find: ‘/var/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-rtkit-daemon.service-W2mqTy’: Permission denied
find: ‘/var/tmp/systemd-private-5065912711c44bfd880f3aca2d0008e7-rtkit-daemon.service-Nmhoc5’: Permission denied
find: ‘/var/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-colord.service-yD6AKb’: Permission denied
find: ‘/var/tmp/systemd-private-310aa08f8dac48c087fb3d04eb13211d-rtkit-daemon.service-2aRSdk’: Permission denied
find: ‘/var/tmp/systemd-private-cc0e6bd6ee4c4e5a8e66d39c662b4262-systemd-timesyncd.service-cR7tKn’: Permission denied
find: ‘/var/tmp/systemd-private-81dcc732570e47799cb04c3cb0c5a2c6-colord.service-RpnOff’: Permission denied
find: ‘/var/tmp/systemd-private-93e35b4b8e084692829998454c625032-rtkit-daemon.service-FPP0C0’: Permission denied
find: ‘/var/tmp/systemd-private-f72e80f0374645bda6c2d99c5628e374-rtkit-daemon.service-KSb7II’: Permission denied
find: ‘/var/tmp/systemd-private-93e35b4b8e084692829998454c625032-colord.service-umcrrr’: Permission denied



```


Running this command:

```
ls /usr/local/cuda-8.0/doc/man/man7/libcuda.so.7 -la

```

Got me this output:

```
-rw-r--r-- 1 root root 26 Jan 26  2017 /usr/local/cuda-8.0/doc/man/man7/libcuda.so.7

```

But I couldn't find libcuda.so.1 within the same vicinity of folders. 

If i run:

And if I run nvidia-smi I get back this:



```

------------------------------------------------------+                       
| NVIDIA-SMI 340.104    Driver Version: 340.104        |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 260     Off  | 0000:01:00.0     N/A |                  N/A |
| 40%   46C   P12    N/A /  N/A |    226MiB /   895MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

    +-----------------------------------------------------------------------------+
    | Compute processes:                                               GPU Memory |
    |  GPU       PID  Process name                                     Usage      |
    |=============================================================================|
    |    0            Not Supported      




```



I'm stumped as to how to overcome this error.

Is libcuda.so.7 also a symlink?

How do I find where libcuda.so.1 is ?
And how do I link it with my graphic card driver (I don't know how to locate the driver as well).

I'v been at this for a few days. :confused::confused:

Thank you.

---

### Post by deadflowr on 2018-01-24
Please do not start duplicate threads:
Original thread here: [https://ubuntuforums.org/showthread.php?t=2383261]("https://ubuntuforums.org/showthread.php?t=2383261")

Thread Closed

---

