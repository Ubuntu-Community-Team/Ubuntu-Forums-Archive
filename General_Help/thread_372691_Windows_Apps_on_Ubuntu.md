---
title: "Windows Apps on Ubuntu"
date: 2007-02-28
forum: General Help
---

### Post by Voltaic Shock on 2007-02-28
I was wondering if I can install VS 2003/2005 on Ubuntu under Wine or use VMWare to install XP and then install them that way.

I have to have VS 2003/2005 for work purposes along with SQL Server (it pays my bills - :P)

I am trying to swich over to Ubuntu but still rely on Windows for some apps.

Voltaic Shock

---

### Post by etank on 2007-02-28
I don't know about running it in wine but loading it on a XP VM will do the trick. You could also look at virtualbox for running the VM. It seems to be a little lighter weight than VMware.

---

### Post by Voltaic Shock on 2007-02-28
> **etank said:**
> I don't know about running it in wine but loading it on a XP VM will do the trick. You could also look at virtualbox for running the VM. It seems to be a little lighter weight than VMware.

Thanks!

I figure if I can't get everything running in Linux then I won't have to worry about windows.  I figure I can use my works image to install XP.

Voltaic Shock

---

### Post by Praill on 2007-02-28
VirtualBox is the way to go, since it's free. But VB doesnt yet support 3D acceleration if you need that :(
If you need 3D acceleration, I hear its *cha-ching* counter-part *cha-ching* VMWare can do it. But as you can tell from my sarcastic emotes, it costs money. You can, however, try it for 30 days to see if you like it. 
And there is a way to hack the free VMPlayer they provide to install windows. But thats a no no :)

---

### Post by Marious on 2007-02-28
Can't say that I have tried that software your talking about but you should be able to run it in Wine just fine with out having to have XP installed.

From WineHQ: "Wine does not require Microsoft Windows." (Yay Wine!)

But then again there are some programs that just don't run properly under Wine so the previous poster has given you good advice as to some of the other alternatives. Now it will run a bit slower since it is being virtually ran and not natively from an XP installation but even if you install XP in Wine it will be the same. If it does not require to be super fast then you should be fine. Enjoy Ubuntu I certainly am, I don't even log onto my XP partition I just run Ubuntu, but I do have 2 machines. And as far as MySQL well it runs just fine in Ubuntu, but I'm not sure if you are required to run both from the virtual platform more then likely you will have to but others can let you know if that is the case.

Marious

---

### Post by Voltaic Shock on 2007-02-28
Thanks for the advice.  I mainly do web programming ASP.NET.  I have used Ubuntu in the past before and enjoyed it a lot.

I am worried about installing it on my laptop right now and loosing my WindowsXP.  I have Ubuntu 6.10 running in VMWare right now with 10 GB.

Voltaic Shock

---

### Post by etank on 2007-02-28
Try dual booting the machine then. Take the same 10G and create a new partition to install Ubuntu in.

---

### Post by jvc26 on 2007-02-28
> **Marious said:**
> but even if you install XP in Wine it will be the same. 

Installing XP in wine? You can install apps but not the OS. You'd have to virtualise the OS.
Il

---

### Post by Voltaic Shock on 2007-02-28
> **etank said:**
> Try dual booting the machine then. Take the same 10G and create a new partition to install Ubuntu in.

I will try that, how much can I trust GParted?

Can I run GParted on windows and foramt the drive there?

Voltaic Shock

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-02-28
> **Voltaic Shock said:**
> I will try that, how much can I trust GParted?

Can I run GParted on windows and foramt the drive there?

Voltaic Shock

Indeed -- See below...

[http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html](http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

If you have a copy of partition magic laying around, that should do the trick as well. You can however trust GParted... It works great! 

Good Luck!

---

### Post by Voltaic Shock on 2007-02-28
> **k|d<FuNkY>FrY said:**
> Indeed -- See below...

[http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html](http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

If you have a copy of partition magic laying around, that should do the trick as well. You can however trust GParted... It works great! 

Good Luck!

Thanks for the Info I will try this out.

Voltaic Shock

---

### Post by GoatTuber on 2007-02-28
Has anyone tried [ReactOS]("http://www.reactos.org") under VirtualBox? That should allow you to run Windows apps from a *WindowsXP compatible* environment, without having to buy a Windows license. I think I'll put this on my list of things to do tonight.

---

### Post by veloce on 2007-02-28
> **Voltaic Shock said:**
> I was wondering if I can install VS 2003/2005 on Ubuntu under Wine or use VMWare to install XP and then install them that way.

I have to have VS 2003/2005 for work purposes along with SQL Server (it pays my bills - :P)

I am trying to swich over to Ubuntu but still rely on Windows for some apps.

Voltaic Shock

I bit the bullet and formatted my Dell Laptop's harddrive and installed Ubuntu and VMWare Server. All my personal files were transferred to from a usb drive backup.  

  I then created a win xp + Office vm using  the backup disks. I had to reactivate these products as I had "changed my hardware".  Today I am installing SQL Server Express on the vm.  

I'm not a gamer so haven't noticed any graphic performance issues from the lack of 3D acceleration.

---

### Post by Voltaic Shock on 2007-03-02
> **veloce said:**
> I bit the bullet and formatted my Dell Laptop's harddrive and installed Ubuntu and VMWare Server. All my personal files were transferred to from a usb drive backup.  

  I then created a win xp + Office vm using  the backup disks. I had to reactivate these products as I had "changed my hardware".  Today I am installing SQL Server Express on the vm.  

I'm not a gamer so haven't noticed any graphic performance issues from the lack of 3D acceleration.

I am just dual booting for now and mounted the windows partion in Ubuntu.  Let me know how SQL Server works out.

Voltaic Shock

---

### Post by DAaaMan64 on 2007-03-24
> **GoatTuber said:**
> Has anyone tried [ReactOS]("http://www.reactos.org") under VirtualBox? That should allow you to run Windows apps from a *WindowsXP compatible* environment, without having to buy a Windows license. I think I'll put this on my list of things to do tonight.


Try out tinyXP you won't get compatibility with ReactOS.  TinyXP runs great, but yeah you have to have an XP license to use it. :(

---

### Post by veloce on 2007-03-25
> **Voltaic Shock said:**
> I am just dual booting for now and mounted the windows partion in Ubuntu.  Let me know how SQL Server works out.

Voltaic Shock

SQL Server express has installed fine and is working well for local use.  I have yet to try using it to access a remote server, but it is running well.  Performance is okay, I haven't had a chance to do any benchmarking against running it natively.

---

### Post by rich.bradshaw on 2007-03-26
reactOS is pretty much unusable at the moment I would say...

---

### Post by rude_lee on 2007-03-26
im wat can i use to run microsoft office under edgy with out having to install windows xp because i want to take away windows from my hardrive altogether im also a total noob please dont cus me out

---

### Post by veloce on 2007-03-26
If you **really** do not want windows on your hard drive, then your only alternative would be "wine".  I don't use it, but there is sure to be a howto around somewhere.

However, if you want to run ms office properly, I would still recommend installing windows in a virtual machine (I use vmware server).

If you really want to get away from ms products, why use ms office at all?  open office is at least as functional.

---

### Post by Thisbetom on 2007-03-27
Hey,

I just switched over fully to UBUNTU, but I want to figure out how to get VS2005 or Visual Web Developer on it.  Did you ever figure it out using WINE or did you need VMWare?

Thanks,
-Tom
(First Post... NIOYCE)

---

