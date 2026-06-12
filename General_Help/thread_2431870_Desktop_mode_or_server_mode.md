---
title: "Desktop mode or server mode?"
date: 2019-11-23
forum: General Help
---

### Post by josephchrzempiec on 2019-11-23
Hello I'm till farely new to linux and trying to understand a few thing as i go along. But the questions i have is for KVM in ubuntu. I'm trying to setup a few virtual machine's for me and my borthers to play some games. 

(1) So i was wondering would it be better to do this in desktop or in server for ubuntu?

(2) second question is for remote desktop sense all VM will be windows what remote program to use to get the best performance so there not much of a bottle neck when using this?
My internet connection is 100MB download 100MB upload and from my system to my router is gigabit connected so I'm hopeing that part is okay. I know remote desktop of an kind takes very little to a lot of bandwidth needed so I'm trying to make sure I'm okay with i guess you would call it lagging or slow down of any kind.  my brothers both of them have the same internet connection they have 30MB download and 15MB upload but in different locations and different networks.


I'm just curious what would be the best way to precede at this is. I have in the past used a windows program called virtualbox and another. but recently i have tried it again and it was really bad. I know most games need GPU. and i do have 3 GPU attached to the system all the same ones. But For right now my thing is to focusing on is getting started and taking it one step at a time.

I'm asking this great community how should i start and where should i start at. as well any great ideas on to improving what i do know now please let me know thank you.


Joseph

---

### Post by CatKiller on 2019-11-23
> **josephchrzempiec said:**
> Hello I'm till farely new to linux and trying to understand a few thing as i go along. 

Desktop. 

The server image doesn't have things added, it has things taken away, like any kind of graphical user interface. If you're an experienced Linux user running a particular machine for a particular purpose then you don't need those things and you already know how to install them if you do; if you're a new user trying to figure things out and learn as you go then you do need those things.

---

### Post by josephchrzempiec on 2019-11-23
Hello catkiller Thank you for that information. I didn't know that I'm still kind of new to linux i have only really played around with it learning as i go around.But now I'm learning a lot as time goes by. Understanding it is a whole new challenge to me.

---

### Post by TheFu on 2019-11-23
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) will save you time in the long run. 

Unix skills build on prior skills, so many advance things require a base level of skill and understanding.  This is needed so as you follow pages of instructions, you'll recognize where those pages don't apply anymore.  Linux is crazy flexible, so there is usually 50-500 different ways to solve any issue.  That means any instructions will need to be tailored for your system and the setup.

It isn't like Windows where you can find a set of images, point-n-click and be done.

---

### Post by josephchrzempiec on 2019-11-23
Helo TheFu i undertand that is why Im here to learn. and figure out the problems i have and see what i learn in the process.

---

### Post by jetsam on 2019-11-23
Just an opinion...

I picked up the Unix command line back in the dial up internet days when some of the better internet providers just dumped you at a terminal and let you figure it out from there.  Unix For The Impatient was a good book on how to navigate the command line, and it's surprisingly still relevant today because the command line changes so slowly.

I recommend you give server mode a chance.  Just be willing to install a desktop if you get too frustrated or think it would help save you time.  It's easy to install a desktop in the server editions... it's literally a few "sudo apt-gets" away.

---

### Post by Tadaen_Sylvermane on 2019-11-23
> [COLOR=#000000]if you're a new user trying to figure things out and learn as you go then you do need those things.[/COLOR][COLOR=#000000]

i disagree. one should learn a system the way it's meant to be used i believe. if you are running a server then learn to run a server. besides from what i've seen over the years trying to run gui apps as sudo or root for server stuff only makes things worse or more difficult.

the command line isn't hard, it's very simple actually. just a different way of thinking. if you are going to put the effort into learning it, then learn it the right way the first time. you will be using the command line in your gui anyway. might as well keep the system as stable as possible and not bother with it in the first place.[/COLOR]

---

### Post by TheFu on 2019-11-23
There are lots of opinions.  Here's mine.

Between the desktop or server question, the answer is "it depends."  Will you physically sit behind the system daily or not?  Are their plans to move the setup into a cloudy provider or remote location?  Will other users only have remote access or will they walk over and sit behind the system so you want to see what they will be going through?

If the paying users are all remote, then it should be a server without any GUI installed.
If the paying users are all local, then it should be a desktop with an appropriate GUI installed.

Almost everything that a server install can accomplish can be done on a desktop. Loading server packages is extremely common. Using server-style networking is very common.  The kernels are the same regardless of which image is installed server or desktop.

If you are really new, the learning curve for a server is extremely steep.  It will be frustrating if your only computer knowledge is with GUIs.  I'd install a desktop if that were me and have a nicer environment, but try to use the shell for most things that don't directly require using a GUI.  For example, almost all file management and permissions should be handled by the shell.  GUIs are almost always 10x slower for that stuff.

As for KVM stuff.  
Prepare for disappointment if using a remote connected to a graphical environment running a game is the goal.  Spice is the fastest protocol and isn't secure enough alone to be used over the internet.  On a fast wired LAN, might be able to watch  video with it, but there are much better solutions for remote video playback.

Spice is really quite good for typical office applications, on the same LAN.  For internet remote desktops, x2go is the best method, but it isn't for heavy graphical games. More for playing cards or sudoku. There are Spice and x2go clients for the major desktop OSes.

Tuning performance for a hypervisor is a non-trivial effort, completely dependent on the hardware and skills of the person doing that task.  I've been using hypervisors since the 1990s and KVM since 2010.  If there will be multiple VMs running concurrently, then getting to best performance overall is about sharing the available resources efficiently and NOT allowing any single VM or host to take too much.
For more about that, [https://blog.jdpfu.com/slowVbox](https://blog.jdpfu.com/slowVbox) ... if you follow those general concepts for any hypervisor, you'll have a faster experience than most.
As for KVM-specific tuning, [https://blog.jdpfu.com/2012/07/30/improving-kvm-performance](https://blog.jdpfu.com/2012/07/30/improving-kvm-performance) is mostly valid, though I'd push towards using block storage to the VM if I were writing that article again.  If fast NVMe storage is used in x4 mode and only run a few VMs, then none of the storage stuff matters too much except that virtio will always use fewer resources than other options.  
Also, be aware that Windows eats VM resources for some reason.  At first, Windows guests seem to be fine, but within a few hours, they start using most of 1 vCPU for some reason. Eventually, CPU use will drop, until some background process kicks it back up again.  The best answer I've found is to limit the number of vCPUs to any Windows guest to 2.  This number gets the multi-core Windows installed version, allows changing the number of vCPUs later to be 2 or more, but doesn't provide unnecessary vCPUs when they aren't known to be needed. 

Some people prefer to use a CLI interface to create VMs.  I do not.  I use a GUI that is similar to virtualbox, but for almost any hypervisor guest setup.  I run it from a desktop that isn't on the hypervisor itself. As many network protocols on Unix systems do, it supports using ssh as a tunnel and ssh for authentication.  virt-manager is the name of the GUI. It leverages libvirt.  On the remote hypervisor, qemu-kvm and libvirt run, so basically, the remote server without any GUI has a GUI interface running on a local workstation.  There must be 500 youtube videos on setting this up.  I've given about 5 presentations to different computer groups about it over the last decade.

Anyway, work through TLCL book for about 200 pages, then setup ssh between all your different machines, and after that is done, look for solutions which leverage ssh like libvirt, x2go, rsync, sftp, and pretty much every Unix backup tool made.  If you use ssh, you'll want to setup ssh-keys so passwords are never used for authentication after the initial connection, 1-time only.

And don't forget to have the appropriate amount of fun with this stuff.

---

### Post by josephchrzempiec on 2019-11-23
Hello all thank you very much for the reply back I'm learning a lot here. I'm not new new to linux it's self i have ran simple things like apache server for websites for a friend i helped installed on his system as well as ftp server and a few other things. I have also used ubuntu desktop and still using it. I'm fairly new as in programming different things that are in programming. Right now all i did in terminal is pretty much cut and paste code and lines. I'm only just recently learning what each command does. 

My problem is yes running virtual machines with KVM using windows 10 vm for video play back, gaming and just browsing if it is better to run it in a ubuntu desktop mode or the server mode would be better to run something like this. I didn't know about spice or hypervisor it's self. i'm now looking into this.

---

### Post by TheFu on 2019-11-23
> **josephchrzempiec said:**
> Hello all thank you very much for the reply back I'm learning a lot here. I'm not new new to linux it's self i have ran simple things like apache server for websites for a friend i helped installed on his system as well as ftp server and a few other things. I have also used ubuntu desktop and still using it. I'm fairly new as in programming different things that are in programming. Right now all i did in terminal is pretty much cut and paste code and lines. I'm only just recently learning what each command does. 

My problem is yes running virtual machines with KVM using windows 10 vm for video play back, gaming and just browsing if it is better to run it in a ubuntu desktop mode or the server mode would be better to run something like this. I didn't know about spice or hypervisor it's self. i'm now looking into this.

We don't know what the intent is.
> If the paying users are all remote, then it should be a server without any GUI installed.
If the paying users are all local, then it should be a desktop with an appropriate GUI installed.

Remote access to Win10 for video playback, gaming, and multimedia browsing will probably suck. Nothing you can do about that.  For now, on linux, getting good graphics performance is tied to actually running the program ON the same system where the good GPU is located.  

19.10 has some new, experimental VM+GPU stuff inside it, but I wouldn't consider that stable.  19.10 support will end in July.

---

### Post by SeijiSensei on 2019-11-23
> **TheFu said:**
> Spice is the fastest protocol and isn't secure enough alone to be used over the internet.
Would running it over an OpenVPN tunnel make it secure enough?

I've not tried having VMs (I use VirtualBox) talk directly to my graphics adapter. I understand it's possible, but it takes some work. Gaming on an emulated video adapter will likely be very disappointing.

---

### Post by TheFu on 2019-11-24
> **SeijiSensei said:**
> Would running it over an OpenVPN tunnel make it secure enough?

I've not tried having VMs (I use VirtualBox) talk directly to my graphics adapter. I understand it's possible, but it takes some work. Gaming on an emulated video adapter will likely be very disappointing.

A full VPN is safe, assuming it isn't misconfigured or leaking metadata like DNS. Probably secure enough.
  I've been unable to get ssh-tunnels to work for spice.  Spice uses different channels for USB, audio, video and a few other connections, which is why 1 ssh-tunnel doesn't work.  I think the normal setup, like the way oVirt on RHEL does it, is using TLS connections around each of the channels.  I've not gotten that working either, but I haven't tried very hard.  Generally, I use x2go into the company server LAN to get a fast remote desktop (no video or audio playback when off LAN), and use vinagre for rdp or vnc connections into Windows on the LAN.  For Linux systems on the same LAN, I'll just use the remote x2go server like my desktop with X11 ssh forwarding.
```
laptop --> x2go --> Linux desktop --> RDP --> Windows desktop 
```
Oddly, this makes the Windows desktop performance faster than using a VPN into the network and running RDP or VNC directly from the laptop to the Win-Desktop.  x2go efficient compression matters.

vbox supports dedicated GPU passthru [https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough) .  
ESXi w/ vSphere, Xen and KVM do too, but it is usually non-trivial to setup.  I didn't find any official guides for it, but lots of blogs claiming success.  KVM instructions are 15 pages and every new kernel means working through the setup again. My low-end GPUs don't work. Seems only the $180+ GPUs get any support for PCI passthru.

Intel was/is working on GVT-g which will allow fast context switching between VMs and host desktops under KVM. I haven't seen mention of it working for other hypervisors and the demos from 2 yrs ago at an intel conference lasted just a few minutes before crashing. GVT-g only works with Intel GPUs. In theory.   
[https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide](https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide)  Looks like they support Xen.  But have also moved the CPU to 5th-7th-gen. That means none of my Intel systems work. 4 are too old and one is too new. ;(

Sorry for the OT stuff.

There's something included in 19.10 gnome and wayland that should help linux-to-linux desktops.

---

