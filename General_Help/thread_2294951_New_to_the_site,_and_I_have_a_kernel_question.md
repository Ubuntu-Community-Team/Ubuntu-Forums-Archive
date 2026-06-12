---
title: "New to the site, and I have a kernel question"
date: 2015-09-14
forum: General Help
---

### Post by jackieching on 2015-09-14
Hello, I am relatively new to the site. I have two computers. One runs Zorin OS9 and another runs 14.04. I am using my 14.04 computer as the guinea pig in the house. Trying out new things on it to make sure that I know what I am doing before doing them to the main family computer. Well anyway, I just updated the kernel on this computer to 4.02. Was this a mistake? I've been searching the forums and I can't find anyone suggesting that anyone do so. I just figured that the newest stable version would be best to have. Thanks in advance to any replies that I get to this.

---

### Post by QIII on 2015-09-14
*Moved to **General Help***

Ubuntu, Linux & OS Chat is a chat area, not a support area.

---

### Post by Bashing-om on 2015-09-14
jackieching; Hello; My Welcome to the form.

If it works, no mistake, but you are experimenting. Let us know what breaks.

[INDENT][INDENT]nothing ventured
[INDENT][INDENT][INDENT]nothing gained
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-09-14
> **jackieching said:**
>  I just updated the kernel on **this** computer to 4.02. 
Which computer are you referring to?
How, exactly, did you upgrade the kernel? Did you follow some instructions?
Does your upgraded system work?

Generally, best practice is to use the kernel provided by the Ubuntu repositories for your release.
Wandering off the beaten path to install a kernel from some other source is not recommended...unless you want to be a tester and revel in the joy of looking for breakage and filing bug reports.

---

### Post by jackieching on 2015-09-14
This is where I got the instructions. [http://ubuntuhandbook.org/index.php/2015/08/upgrade-kernel-4-2-ubuntu/](http://ubuntuhandbook.org/index.php/2015/08/upgrade-kernel-4-2-ubuntu/) The one that I changed to 4.2 is my 14.04 computer. It seems to be working fine. I was under the impression that getting the latest kernel is an important part of making sure that your system has the latest updates, but the more I look into it and read forums I figured out that that is not the case.

---

### Post by coldraven on 2015-09-14
If you run "Software & Updates" you can choose in the settings how often it will check for updates etc. New kernels regularly get automatically installed.

---

### Post by jackieching on 2015-09-15
So should I switch it back, or should I do like Bashing-om said and use it as is unless something breaks? It is working fine right now, and like I said this computer is going to definitely be the guinea pig of the house so that I can try new things with it.

---

### Post by grahammechanical on 2015-09-15
This is the way things work in Ubuntu. We get a new release every six  months. And with each new release we get an updated version of what is  called a hardware enablement stack. That means an updated Linux kernel  and hardware driver modules.

Every Ubuntu release has a 26 week  development period during which during which updated kernels and  libraries are introduced for testing before release day. Anyone one can  install a development release. I am running the development version of  15.10 right now and it has only recently got the Linux 4.2 kernel.

Most  Ubuntu releases are only supported for 9 months. But every 2 years the  April release is given 5 years support. These versions are called Long  Term Support (LTS). Ubuntu 14.04 is LTS. To keep LTS releases up to date  with the latest hardware the LTS receives an updated hardware  enablement stack every six months or so.

Since 14.04 was released  it has received 3 of these updated hardware enablement stacks which are  called point releases. The last one was in August. So, 14.04 is now  14.04.3. And it has the kernel that was in Ubuntu 15.04. But 14.04 will  not receive the kernel that will come in 15.10 until about 6 months  after 15.10 has been released.

This is why you are being told  that by installing kernel 4.2 in Ubuntu 14.04 you have effectively  become a tester. Welcome and keep with it.

You might like to follow discussions in the Ubuntu Development section of this forum. Some examples relating to kernel 4.2 

[http://ubuntuforums.org/showthread.php?t=2294860](http://ubuntuforums.org/showthread.php?t=2294860)

[http://ubuntuforums.org/showthread.php?t=2291971](http://ubuntuforums.org/showthread.php?t=2291971)

And kernel 4.3

[http://ubuntuforums.org/showthread.php?t=2294800](http://ubuntuforums.org/showthread.php?t=2294800)

Regards.

---

### Post by efflandt on 2015-09-15
For a mainstream system you would usually just do whatever the Software Updater automatically recommends. That is usually safe at tested, although, some of use did have some issues with a recent kernel update that interfered with Steam (and I hear wine), but the solution was simply to boot a previous kernel until a newer kernel fixed what broke.

If you have cutting edge hardware you may need versions of the kernel or drivers (modules) that are newer than mainstream. In some cases that might be installing a newer version of a kernel or something from the normal repositories, or in some cases it might involve adding a ppa to get some packages from another source. Or you may want to experiment with the latest system under development or beta testing. But it helps to have a functioning system to fall back on.

For example I have my main system on my hard drive. For a while I was testing development versions on an SSD. Although, currently my SSD still has a 12.04 version (updated from 11.10) and my hard drive has fresh 14.04 (last January). I did have some initial teething problems on 14.04 because the default nouveau and nvidia-current drivers did not work for my GTX 750 Ti with the new Maxwell chip, but since I now know which nvidia drivers work and how to install them even on a new system, that is no longer an issue. But since I am sure that everything is sorted out and working fine on 14.04, I may try something newer on my SSD.

---

### Post by jackieching on 2015-09-15
Okay, thanks for all of the input. This makes things a lot clearer to me than reading old forum posts did. I will keep it as is for now and let anyone know if I have any problems with it.

---

