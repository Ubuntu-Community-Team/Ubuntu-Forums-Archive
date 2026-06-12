---
title: "Ubuntu 12.10 very slow comparing to Ubuntu 12.04. How to dramatically speed it up?"
date: 2012-10-20
forum: General Help
---

### Post by abcuser on 2012-10-20
Hi,
I have installed Ubuntu 12.10 on my virtual machine. This comptuer is low spec PC. What I have noticed was drastically slower responses for anything in Ubuntu comparing to Ubuntu 12.04 Unity 2D. If I open terminal and type some letters, they are displayed few seconds after I type them. Also if I move my mouse to left-top corner to close-min-max buttons it takes about three seconds to this buttons to be displayed. Using Ubuntu 12.04 I had none of this performance problems and comparing to Ubuntu 12.10 it was super fast. Currently performing so dead slowly I see Ubuntu 12.10 useless.

Is there any way I can turn of some of the fancy features like fading out windows etc. I need some instruction to dramatically speed-up Ubuntu?
Thanks

---

### Post by 2F4U on 2012-10-20
Did you install the VirtualBox guest additions?

[http://www.securitronlinux.com/bejiitaswrath/how-to-setup-ubuntu-12-10-in-virtualbox-and-a-look-at-the-desktop-interface/](http://www.securitronlinux.com/bejiitaswrath/how-to-setup-ubuntu-12-10-in-virtualbox-and-a-look-at-the-desktop-interface/)

However, there is also a bug report:

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/1044746](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/1044746)

I am not sure if this applies to VirtualBox, since it has been posted on the Parallels forum:

[http://forum.parallels.com/showthread.php?t=263981](http://forum.parallels.com/showthread.php?t=263981)

---

### Post by carl4926 on 2012-10-20
There is no 2D in 12.10
Why not use xfce or lxde desktop

---

### Post by vasa1 on 2012-10-20
> **abcuser said:**
> Hi,
I have installed Ubuntu 12.10 on my virtual machine. This comptuer is **low spec PC**...
Don't mean to sound rude but Ubuntu isn't for you any longer. Try Lubuntu or Xubuntu.
(I also read somewhere that 12.**10** doesn't play well on virtual machines.)

---

### Post by abcuser on 2012-10-20
@2F4U, yes I installed VirtualBox guest additions, but this additions are not for performance reasons, but to have additional integration between host and guest like sharing files.
The bug link is not what happens in my case, in my case it is just very slow.
Parallels link is not what I have installed, I use VirtualBox - not the same product.

@carl4926, I know there is no Unity 2D in Ubuntu 12.10, but instead it is LLVMpipe system that solves should run systems on low specs.

@carl4926 and @vasa1, I don't want to use Lubuntu or Xubuntu, there are badly translated into my language and I like to use system in my native language. Ubuntu in the other hand is 100% translated. I am also little bit stuck with the system that I am recommending to my friends and they require translated system... And 2 years back I have tried Xubuntu and I got felling that it was just not faster that Ubuntu 2D and it also used a lot of software that I was not familiar with.

So I need some performance suggestions, not suggestion how to go away from Ubuntu. I would like to get Ubuntu 12.10 running in the similar way as Ubuntu 12.04.

---

### Post by vasa1 on 2012-10-20
> **abcuser said:**
> ...
@carl4926 and @vasa1, I don't want to use Lubuntu or Xubuntu, there are badly translated into my language and I like to use system in my native language. Ubuntu in the other hand is 100% translated. I am also little bit stuck with the system that I am recommending to my friends and they require translated system... And 2 years back I have tried Xubuntu and I got felling that it was just not faster that Ubuntu 2D and it also used a lot of software that I was not familiar with.

So I need some performance suggestions, not suggestion how to go away from Ubuntu. I would like to get Ubuntu 12.10 running in the similar way as Ubuntu 12.04.

You have explained your situation very well but the reality (at least as judged by reviews) is that Ubuntu 12.10 is more demanding of resources. You can check out page two of an [article here]("http://www.h-online.com/open/features/What-s-new-in-Ubuntu-Desktop-12-10-1730978.html") about the virtualization aspect.

---

### Post by mc4man on 2012-10-20
> **abcuser said:**
> 
@carl4926, I know there is no Unity 2D in Ubuntu 12.10, but instead it is LLVMpipe system that solves should run systems on low specs.


ATM LLVMpipe performance ranges from poor to totally unusable
So **if** your current experience is not suitable then there's nothing you can do to 'fix'.
You'll either need to wait for it to be improved, use something else or get better hardware.

---

### Post by abcuser on 2012-10-20
@vasa1, thanks for the link and the quote from it tells it all: "Where Ubuntu 12.10 runs into trouble, however, is when the operating system is being virtualised. Users who install the current release of Ubuntu in an application such as VirtualBox will immediately notice almost unbearable sluggishness. The desktop basically becomes unusable..."

@mc4man, yes thanks, now I see it, I can't fix it. Maybe LLVMpipe will get improved or VirtualBox will do something to improve performance in both cases I need to wait. It looks to me the only good option is to stay at Ubuntu 12.04 LTS at least for a while and then if performance does not improves then I will be forced to look for an alternative (new desktop environment, new distro or even new hardware).

Thanks a million times to all of the help in this thread and for provided fantastic answers. You rock!
Regards

---

### Post by subhadip_sky on 2012-10-20
Hi, I am not sure but can you try the solution stated [here]("http://askubuntu.com/questions/197771/how-do-i-enable-llvmpipe-rendering-in-unity")?

---

