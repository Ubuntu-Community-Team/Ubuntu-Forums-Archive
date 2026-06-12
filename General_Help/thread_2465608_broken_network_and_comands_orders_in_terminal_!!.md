---
title: "broken network and comands orders in terminal ?!!"
date: 2021-08-06
forum: General Help
---

### Post by fairbird on 2021-08-06
Today after run my ubuntu 20.04 I have got as screenshot shown, there is no network connection appear ...
And also the command in terminal does not work with sudo ... for example if I want to try and test update package list with (sudo apt update )It was take long time and nothing happens ..

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288935&stc=1[/IMG]

I using live lcd right now !!
any idea how to solve it ?!!
Thank you

---

### Post by tea for one on 2021-08-06
Can you boot into an earlier kernel - may be lucky?

---

### Post by fairbird on 2021-08-06
The ubuntu booting normally with currently kernel. 
The problem not with bottling, with broken sudo (x) command in terminal such as (sudo apt update) nothing happens and no error message also shown to me.
so I can not fix network from terminal.

Also if i do restart or shutdown. Take long time.

---

### Post by TheFu on 2021-08-06
> **fairbird said:**
> The ubuntu booting normally with currently kernel. 
The problem not with bottling, with broken sudo (x) command in terminal such as (sudo apt update) nothing happens and no error message also shown to me.
so I can not fix network from terminal.

Also if i do restart or shutdown. Take long time.

That wasn't the question.

At boot, there are options to choose which kernel is used.  There should be 2 or 3 kernels in the list. By default, the latest gets used.  Try an older kernel.  This is called "troubleshooting."

Please report back on how that goes and whether networking works with the older kernel or not.

sudo is tied to networking, so attempting to use sudo requires multiple timeouts before stuff can happen, if the settings allow it.  It is looking to match the hostname and DNS records to ensure sudo isn't being attacked.  It is possible to configure sudo so that it doesn't work when networking isn't up. This is not the default. It should work, eventually, when networking is down.

Also, when testing keep track of which kernel works and which kernel doesn't work.

---

### Post by TheFu on 2021-08-06
As for other troubleshooting steps - we need for you to tell us some information about the network, system, network devices involved.  "It doesn't work" is pretty limited.  
What card? 
Which drivers? 
Which kernel?  
Did the prior kernel, drivers work with the card?  
wifi or wired?  
Did anything change with the switches, routers, or wifi?  
Are you doing something crazy like using a cellular modem?

We need some information?
Have you looked at the system log files? 

You say you are posting here using a Live CD.  Do you mean a "Try Ubuntu" setup?  Is everything else the same?  If it works on the same computer with the same hardware under a Try Ubuntu environment, that's good news. It is very unlikely the problem is hardware.  It could be configuration, kernel, or driver, however.

---

### Post by fairbird on 2021-08-06
Ok... Now I have boot from other kernel (5.8.0-63-generic) and every things work just fine.
So the issue from latest version of kernel maybe (5.11.0-25-generic)

Thank you

---

### Post by TheFu on 2021-08-06
Whoa.  You aren't running the latest LTS release?  That would be a 5.4.x kernel and if you use the HWE, I think that's a 5.8 kernel.
How can you have 5.11?

---

### Post by fairbird on 2021-08-06
I don't know really ... Coming after latest update yesterday I think ..

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal



```

```
~$ dpkg --list | grep -i -E --color 'linux-image|linux-kernel' | grep '^ii'
ii  linux-image-5.11.0-25-generic          5.11.0-25.27~20.04.1                       amd64        Signed kernel image generic
ii  linux-image-5.4.0-80-generic           5.4.0-80.90                                amd64        Signed kernel image generic
ii  linux-image-5.8.0-63-generic           5.8.0-63.71~20.04.1                        amd64        Signed kernel image generic
ii  linux-image-generic                    5.4.0.80.84                                amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-20.04          5.11.0.25.27~20.04.10                      amd64        Generic Linux kernel image

```

```
~$ v="$(uname -r | awk -F '-virtual' '{ print $1}')"~$ echo "$v"
5.8.0-63-generic

```

---

### Post by TheFu on 2021-08-06
Why solved?  Did you do something for the wifi driver to work in the newer kernel?  Others would like to know.

I'm still confused by 3 different kernel line versions on the box. I've just never seen that before, unless someone went out of their way, specifically, to install a specific kernel.

*New* isn't always better.  I always say, "new" is the enemy of "stable".  As long as the kernel you have is working and it is a supported Ubuntu release, Canonical will patch any major issues and all security problems.  There are people on 4.15 kernels still.

I forced all my 18.04 systems to the 5.4.x kernel because the plan is to move to a 20.04 release and already being on the correct kernel reduces the unknown risks (in my mind, if not reality).  To do that, I specifically installed the HWE packages.

---

### Post by fairbird on 2021-08-06
I have removed all kernel and just keep the version of ([COLOR=#000000]5.8.0-63-generic[/COLOR]) ...
I will wait for new kernel when release it then I will test it again ..

Thank you for your answers and interest ...

---

### Post by tea for one on 2021-08-06
> **TheFu said:**
> Whoa.  You aren't running the latest LTS release?  That would be a 5.4.x kernel and if you use the HWE, I think that's a 5.8 kernel.
How can you have 5.11?


Just a bit of info, there was a very recent kernel upgrade within the last 48 hours.
I use 20.04 LTS and the 5.11 kernel appeared as a regular update on 04 or 05 August.

```
edited@edited:~$ ls /boot | grep vmlinuz-
vmlinuz-5.11.0-25-generic
vmlinuz-5.8.0-63-generic
edited@edited:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal
edited@edited:~$
```

Anyway, the OP is now up and running albeit with an earlier kernel.

---

### Post by TheFu on 2021-08-07
Ok, just patched my 20.04 box.
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal

$ dpkg -l |grep linux-image
ii  linux-image-5.4.0-77-generic          5.4.0-77.86                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-80-generic          5.4.0-80.90                           amd64        Signed kernel image generic
ii  linux-image-generic                   5.4.0.80.84                           amd64        Generic Linux kernel image
```

So people on the 5.4 kernel don't get pushed to 5.11.

---

### Post by tea for one on 2021-08-07
> **TheFu said:**
> Ok, just patched my 20.04 box.
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal

$ dpkg -l |grep linux-image
ii  linux-image-5.4.0-77-generic          5.4.0-77.86                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-80-generic          5.4.0-80.90                           amd64        Signed kernel image generic
ii  linux-image-generic                   5.4.0.80.84                           amd64        Generic Linux kernel image
```

So people on the 5.4 kernel don't get pushed to 5.11.

5.8 kernels were pushed to 5.11 because of HWE (I think, although I'm not 100% sure)

I've never really studied all the kernel upgrade variations but it looks like there are two kernel paths for LTS releases:-

[LIST]
[*]GA (General Availability) Kernel
[*]HWE (Hardware Enablement) Kernel
[/LIST]
Info gleaned here:- [https://www.thomas-krenn.com/en/wiki/Ubuntu_LTS_Hardware_Enablement_Stack_information](https://www.thomas-krenn.com/en/wiki/Ubuntu_LTS_Hardware_Enablement_Stack_information)

The Kernel upgrade seems to depend on the user's original installation and whether HWE was added (as a user choice) later.

Anyway, @TheFu, I bet you knew this all along ;)

---

### Post by him610 on 2021-08-08
Looks like 5.11 has been released...
```

Linux b450m 5.11.0-25-generic #27~20.04.1-Ubuntu SMP Tue Jul 13 17:41:23 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal
XFCE

```
Mine was updated within the last few days.

---

