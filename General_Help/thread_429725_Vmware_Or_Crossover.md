---
title: "Vmware Or Crossover"
date: 2007-05-01
forum: General Help
---

### Post by ade234uk on 2007-05-01
I would like to run WIndows inside Ubuntu.
From your experience which is faster

VMWare running WIndows XP

OR

Crossover Office

I just tried Win4Lin and the performance was shocking.

---

### Post by fAlCoNNiAn on 2007-05-01
> **ade234uk said:**
> I would like to run WIndows inside Ubuntu.
From your experience which is faster

VMWare running WIndows XP

OR

Crossover Office

I just tried Win4Lin and the performance was shocking.

when you say performance was shocking, do you mean slow or fast?

---

### Post by ade234uk on 2007-05-01
Performance was slow.

What is the performance of XP like in Ubuntu using VMWARE?

I want to use Ubuntu as my main desktop, but work forces me to use XP so why not have both. Then in Beryl and I can just shift the cube, job done.

---

### Post by water on 2007-05-01
I'm also considering the options here, but my consideration is "vmware vs. virtualbox vs. whatever"

What I need is : [LIST]
[*]to use dual screens under Windows
[*]use a Windows vpn client over both wired & wireless (hopefully without limiting Ubuntu's networking...)
[*]copy paste between Windows & Ubuntu
[*]access files between Windows & Ubuntu
[*]use bluetooth to connect to my cellphone under Windows
[*]to access the usb ports under Windows[/LIST]It would also be nice to have the Windows applications running in some kind of standalone mode so I only see the applications and not Windows...

Any recommendations?

:water

---

### Post by ade234uk on 2007-05-01
Crossover Office will do the job, but it depends what you want to run.

---

### Post by brharri1 on 2007-05-01
Crossover office will allow you to run windows apps from within linux, since it is based on WINE. I use it for microsoft office and it works well. VMware allows you to "boot windows from within linux," that is, you will have the entire windows environment in a window in linux, within which you can run any windows app. Wine/crossover is faster. I only use VMWare as a last resort if crossover cannot properly run an app. One caveat; VWware doesn't allow you to use your hardware accelerated graphics, and beyond that it only uses hardware that is recognized by your linux. 

Hope this helps.

---

### Post by rev_b on 2007-05-01
Well, I use both with excellent results. I have Crossover with Office 2003 (word, excel and powerpoint), and it integrates very well and works 100%, even with CUPS.

I also have a virtual machine with XP installed that I use to run native windows programs, but certainly don't need to . Performance is very acceptable, but of course it's not the same as a real machine. I also have the virtual machine file in a usb 2.0 HDD, and that doesn't help either. VMWare really put's dual core CPU's into use, as I noticed a huge boost in multitasking within the virtual machine when upgraded to a dual opteron.

So if it's only M$ office you need, crossover will serve you well.

---

### Post by ali4949 on 2007-05-01
Hello
I just finished installing vmware server on my feisty installation. I did win2k install on the virtual machine to run some windows native applications, and the performance is excellent ( almost as fast as a native install of win). I am going to do a remastered installed of win2k by using nlite and removing the components of win2k that I dont need. Right now the memory consumption for the guest host is around 70 MB, but I think I can bring it down to 40 MB. Keep in mind that my system is a T30 laptop with a pentium 4-M, 768 MB Ram. I had allocated 192 MB of ram for the guest OS while setting up the VM. The only problem I have encountered so far is USB disk support, but that seems to be a bug with feisty and Thinkpads. After experiencing the virtual machine performance I dont think I ll have to worry about leaving applications behind. VMware server is definitely worth a try for any one wanting to run windows apps. Plus its free and gives you the chance to install future versions of not only unbuntu but other distros as well before upgrading or just for testing purposes.

---

### Post by jrusso2 on 2007-05-01
Crossover office is a version of wine developed to run a specific group of Windows applications such as microsoft office.  You do not need a copy of windows to run crossover office

Vmware and Virtual box are virtual machines which run Windows in a virtual machine.  You need a copy of windows to run them.  Plus the application you plan to run.

Virtual machines will run any windows application except some games.
Cross over will only run a specific group of windows applications.

---

### Post by water on 2007-05-02
thanks, has anyone got any vmware vs. virtualbox experience?

:water

---

### Post by kenmiles on 2007-05-02
I use VMware player to run my existing windows partition.
[http://www.ubuntuforums.org/showthread.php?t=361528](http://www.ubuntuforums.org/showthread.php?t=361528)

Regards, Kenneth.

---

### Post by kenmiles on 2007-05-02
orry, wrong link. Here is the correct one
[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

Regards, Kenneth

---

### Post by ade234uk on 2007-05-02
> **kenmiles said:**
> orry, wrong link. Here is the correct one
[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

Regards, Kenneth

Im interested in the speed. Is it as good as running Windows Natively?

---

### Post by kenmiles on 2007-05-05
It will never be as good as a native installation but it is not far off on my machine and it beats duel booting.
sorry for the delay but I have just had to replace my motherboard!
Regards, Kenneth.

---

