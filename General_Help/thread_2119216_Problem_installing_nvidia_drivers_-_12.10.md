---
title: "Problem installing nvidia drivers - 12.10"
date: 2013-02-23
forum: General Help
---

### Post by Juniorr on 2013-02-23
Sorry for the title but somehow everything got screwed after driver installation on 12.10.

---

### Post by MG&amp;TL on 2013-02-23
Something broke the window manager.

I see you've got some terminals open. What happens if you run 

```
compiz --replace
```

and 

```
/usr/lib/nux/unity_support_test -p
```

?

---

### Post by howefield on 2013-02-23
Do you have the kernel headers to match your kernel version installed ?

If I recall, they may not be installed by default in 12.10.

PS. Thread title changed to reflect subject.

---

### Post by Juniorr on 2013-02-23
I did ```
sudo apt-get remove --purge nvidia*
``` and it got back to normal, with nouveau drivers. Then I tried once more installing the 310 experimental driver and got a resolution of 640x480. Once again tried to purge nvidia and now I can't change my monitor resolution hehehe

@MG&TL: Output said "OK" in green to everything.

@howefield: I have no idea what you're talking about ):P

I will do a fresh install, can you give me tips so this situation doesn't happen again?

---

### Post by howefield on 2013-02-23
> **Juniorr said:**
> @howefield: I have no idea what you're talking about ):P

I just booted into 12.10 to get the same issue ;-)

Having updated to a newer kernel, without the appropriate headers but a simple matter of installing them sorted it.

Don't know if I have caught you before you reinstall or not,..

Once installed and fully updated open a terminal and type

```
uname -a
```

to get the kernel version that you are using. In the attached screenshot you can see that I have

```
3.5.0-24-generic
``` 

I use synaptic package manager so after loading it I'll search for 3.5.0-24 and install linux-headers-3.5.0-24-generic, then install the nvidia drivers and you should be good.

This may well be the case every time you update the kernel, you'll need to update the appropriate headers.

---

### Post by mc4man on 2013-02-23
I guess this is the current bug on, possibly 12.10 will EOL before anything resolved
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

Noted near top of quantal issues sticky
[http://ubuntuforums.org/showpost.php?p=12304169&postcount=3](http://ubuntuforums.org/showpost.php?p=12304169&postcount=3)

---

### Post by Yellow Pasque on 2013-02-23
Incorrect resolution and glx errors... this also happens when a user tries to install the nvidia driver on an Optimus laptop.

@OP: give output of:
```
lspci | grep -i VGA
```

---

### Post by Juniorr on 2013-02-23
@howefield: Mine's 3.5.0-25, so can I just install the headers on Software Center?

@mac4man: Would that command install the appropriate headers for my current kernel?

@temujin: I have a fresh install of 12.10, what does that command do and how does it affect on a install with no proprietary drivers?

---

### Post by howefield on 2013-02-23
> **Juniorr said:**
> @howefield: Mine's 3.5.0-25, so can I just install the headers on Software Center?

I don't use the Software Centre, so not sure on that, but you can open a terminal and type

```
sudo apt-get install linux-headers-3.5.0-25-generic
```

If they are already installed it will tell you, if not it will install them plus any dependencies.

---

### Post by Juniorr on 2013-02-23
Yes, it said 13.1MB needed to be downloaded. I'll do it, and then install the driver. Do I need to reboot after these headers install?

---

### Post by howefield on 2013-02-23
You've prompted me to update my 12.10, from the screenshot you can see that I have an updated kernel waiting, but the headers aren't marked for updating.

I'll need to install them manually or I'll have an issue with nvidia drivers also.

---

### Post by howefield on 2013-02-23
> **Juniorr said:**
> Yes, it said 13.1MB needed to be downloaded. I'll do it, and then install the driver. Do I need to reboot after these headers install?

Yes, you'll need to reboot.

---

### Post by Juniorr on 2013-02-23
Well now everything seems to be fixed :D

On last question:

Am I going to have to do these same steps every time my kernel gets updated? Is there a way to make Ubuntu automatically install the headers too?

---

### Post by howefield on 2013-02-23
> **Juniorr said:**
> Well now everything seems to be fixed :D

Excellent, well done. :)

> Am I going to have to do these same steps every time my kernel gets updated? Is there a way to make Ubuntu automatically install the headers too?

Most likely for the time you run 12.10 you will likely need to remember to manually update your kernel headers when a kernel upgrade is done. 

13.04 seems fine, so if you ever upgrade to that, the issue will likely be a distant memory.

---

### Post by Juniorr on 2013-02-23
As a matter of fact I just came from 13.04. I was having lots of problems with drivers there too, some crashes, games freezing etc so I'll wait until April =)

Anyway, thanks a lot for your help! ):P

---

### Post by mc4man on 2013-02-23
> **Juniorr said:**
> 
@mac4man: Would that command install the appropriate headers for my current kernel?

I would try (no guarantees) installing linux-headers-generic which is a meta package ("This package will always depend on the latest generic kernel headers available."
Then see..

(at least here in 13.04 where that meta package is installed, -  every time the kernel upgrades so does that kernels specific linux-headers-X.X.X-X-generic package

---

### Post by mc4man on 2013-02-23
Just to follow up on - 
Have a 12.10 install I put in several weeks ago, never really updated

Did install linux-headers-generic meta package & nvidia back then.

So there was a kernel update available & it updated linux-headers-generic meta & installed the approipiate linux-headers-generic package - see screens.

In this case which there was no need for a new kernel nvidia module to be built so all is well on reboot. 
Whether it would have built a new module if needed no idea, that's not all that common after release.

The orig. bug I had on this got duped to the one linked but was more specific to the issue on fresh 12.10 installs of i386 or amd64.
That issue is the linux-headers-generic meta package is not default installed so no specific linux-headers-generic package is installed & installing nvidia or ati, ect. will not do so.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1068456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1068456)

So yes -install the meta package

---

