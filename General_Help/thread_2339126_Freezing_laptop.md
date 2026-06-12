---
title: "Freezing laptop"
date: 2016-10-05
forum: General Help
---

### Post by serbp on 2016-10-05
Hey!
I istalled Ubuntu 16.04 LTS. The instaling process was OK no error message but when I want to Shut Down/Suspend/Restart my laptop freeze.

Thanks

---

### Post by QIII on 2016-10-05
Hello!

Could you give us a better description of the behavior?

---

### Post by serbp on 2016-10-06
Hey!!!
when I want to shut down the laptop it is freezing on the shut down screen and nothing happens. I wait for more then 10 min and nothing happen. I could shut down the laptop only if I press the power button for 5 sec. The same thing happen for suspend and restart. If I choose suspend or restart the laptop freeze and nothing happen. The only thing I can do is to shut down from power button. I'll appreciate if you could give me the solution to my problem.
Thanks

---

### Post by QIII on 2016-10-06
Please use the default font when you post.

What are the specifications of the laptop?

---

### Post by mörgæs on 2016-10-06
Does this help? 
[https://lists.ubuntu.com/archives/xubuntu-users/2016-September/009622.html](https://lists.ubuntu.com/archives/xubuntu-users/2016-September/009622.html)

I am aware that the link is about a delay and not a complete freeze, but if you don't print from the computer it's still worth trying.

---

### Post by serbp on 2016-10-06
The laptop is Dell Inspiron 15, Intel® Celeron(R) CPU N2840 @ 2.16GHz × 2 ,RAM 4 GiB, HDD 500GB.

---

### Post by RobGoss on 2016-10-06
What version of Ubuntu are running on that machine it may not be the best choice for that machine. Give Lubuntu a try and see how that works

---

### Post by mörgæs on 2016-10-07
> **RobGoss said:**
> What version of Ubuntu are running on that machine it may not be the best choice for that machine. Give Lubuntu a try and see how that works

Why is that? Which part of the hardware do you deem too weak for Ubuntu?

---

### Post by RobGoss on 2016-10-07
> **mörgæs said:**
> Why is that? Which part of the hardware do you deem too weak for Ubuntu?

As to your question I think if your processor is not capable of handling the work load that Ubuntu has it's better to choose another distro that will work more efficiently, and that goes for not having enough Ram as well. 

**Example**: Some light versions of Ubuntu require only **512** of Ram, if you only have lets say **786** or even **512 , **you are right on the border line and may encounter running in to issues with speed because we all know as Ubuntu is developing it is **consuming** more and more resources      

I think it's safe to say Ubuntu runs better on machines with more **Ram **& faster **processors** and updated **drivers**. In most cases I see a lot of Ubuntu users for the first time trying to install a distribution that just won't  on the machine they have for what ever reason. Ubuntu gives it's user's the option to choose other distributions if one does not work try another one

Being able to distro hopp is a great thing and should always be something a new Ubuntu user should try in most cases it works out well when you find the right OS that runs like a champ on your machine. 

I have a Toshiba laptop which is about** 15 years** old, it has been running great until about **3 weeks **ago I was trying different distro's on this machine as I always do and for some reason it would not let me install any distribution I threw at it light or heavy

But being the stubbron mule I am, I did not give up and keep trying to install an OS that worked. I was getting all kind of disk errors and messages telling me it might be something wrong with the **disk drive** or the **DVD** drive. With the errors I was getting I never for a second felt it was Ubuntu that was the problem I knew it was my machine that was at fault and proceeded with a successful installation 

After about two weeks of trying to install an OS on it I was able to install **Linux lite**. Know mind you this I tried a number of times to install Lite on it and all the time I was getting theses errors messages but I did not give up

My point is this, If you're trying to install any distribution of Ubuntu on a machine and having no luck move on to one that works for the machine you have if all else fails

---

### Post by mörgæs on 2016-10-07
I think it's safe to say that a Bay Trail processor with 4 GB of memory should be more than enough to run Ubuntu. How 15 years old gear behaves is hardly relevant.

---

### Post by QLee on 2016-10-07
> **mörgæs said:**
> I think it's safe to say that a Bay Trail processor with 4 GB of memory should be more than enough to run Ubuntu. How 15 years old gear behaves is hardly relevant.

+1

Something relevant might be found here:

Kernel Bugs
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)

Launchpad Bugs
[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1531865](https://bugs.launchpad.net/ubuntu/+s...x/+bug/1531865)

Ubuntu Thread (or any of the numerous other threads)
[https://ubuntuforums.org/showthread.php?t=2314964](https://ubuntuforums.org/showthread.php?t=2314964)

I hope that can help you.

---

### Post by cariboo on 2016-10-07
I've had lockup problems with my laptop all through the Yakkety development cycle:

```
inxi -G
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Bay Trail GLX Version: 3.0 Mesa 12.0.3
```

Since the 4.8,x kernels have come about, the lockup problems have gone away. you can try the 4.8.x kernels here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/)

---

### Post by serbp on 2016-10-10
[IMG]http://imgur.com/a/SBfuY[/IMG]This is the last screen [http://imgur.com/a/SBfuY](http://imgur.com/a/SBfuY)

---

### Post by mörgæs on 2016-10-11
You don't seem to respond to the ideas posted.
Have you tried what Cariboo and I suggested? If so please post the results.

---

