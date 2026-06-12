---
title: "Virtual Machine to rid myself of Windows dual boot"
date: 2007-04-06
forum: General Help
---

### Post by Rizlaw on 2007-04-06
I've been using Ubuntu 6.10 for a few weeks now and intend to update to 7.04 on April 18th when it's released. However, I still need to dual boot to Windows XP Pro for certain Windows apps and printers that I can't get to work well in Codeweaver's version of Wine. I would like to get rid of Windows, but I have a few questions that maybe someone can help with:

1. I use two printers, which Ubuntu sees and installs drivers for (Brother PT-9500PC and Dymo Labelwriter 330 Turbo). I can't use either printer in Ubuntu because I need to run specific Windows programs to get the printing I need. Specifically, in Windows, I use Stamps.Com's software to print special mailing labels/stamps on the Dymo printer. Stamps.Com has no linux version of the software.

On the Brother PC-9500 label printer, I have a similar problem. Brother has no linux version of their label printing software.

I tried installing the Windows software into Codeweaver's version of Wine, I couldn't get the software or drivers the software needs, to install properly.

I have used Synaptic Package Manager to install "glabels" which is supposed to work with Dymo label printers, but it really isn't an answer for printing my special Stamps.Com labels.

Does anyone know of a linux solution?

2. I have read a little about VMware's VMplayer. I understand that it allows you to run Windows within Linux. I have also downloaded the HOWTO on VMware from the Ubuntu documentation pages. However, after installing VMPlayer, can you then install Windows programs that run on the Windows XP Pro virtual machine just like you would in Windows running natively. VMWare's website doesn't, as least to me, make it clear whether you can install and run Windows programs within their virtual machine environment. I'm trying to understand what the "limitations" are, if any, before I try to install VMPlayer. I am thinking that maybe I can get VMPlayer to run XP and the few Windows programs and printers I need, so that I can get rid of dual booting between XP and Ubuntu.  Any opinions, suggestions, recommendations would be appreciated.

---

### Post by tgm4883 on 2007-04-06
a virtual machine is just that.  You still need a license to run windows (which I assume you have) and just install windows inside the virtual machine.  As far as I have seen Windows doesn't even know that it is installed on a virtual machine.

Keep in mind that you need to create a virtual machine to use it on vmplayer. (and you can't create a virtual machine on vmplayer).  You first need to create one on vmware-workstation.

To elaborate a little further...

vmware runs an operating system on top of an operating system.  You basically start the virtual machine (which boots up like a computer) and then install programs inside of it....

I am doing a horible job of explaining this right now.  

In order to use vmplayer, you need an already built virtual machine.

If you don't have a virtual machine, you need vmware-workstation

There is a vmware-server, but i haven't looked into that.

Yea, this is horrible, hope someone else comes along.  Im on the verge of deleting this whole thing

---

### Post by jimbob on 2007-04-06
I was able to build a virtual machine for VMware-player by using EasyVMX and didn't need VMware-workstation  using EasyVMX:
   
    [http://easyvmx.com/easyvmx.shtml](http://easyvmx.com/easyvmx.shtml)

However after looking at them both I prefer VirtualBox by InnoTek.  It seems easier to use and has some nicer features like automatic mouse-over, etc.

   [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by spankymasterc on 2007-04-06
Dude i will help you with Vmworksation 6.0 beta :D it works awsome trust me and i have instructions that i have written so if you are interest pm or what ever :D

---

### Post by jimbob on 2007-04-06
I haven't tried this but it is possible to make a virtual machine (VM) from your existing XP installation.

Here is the link if you want to try it:

[http://www.howtoforge.org/vmware_converter_windows_linux](http://www.howtoforge.org/vmware_converter_windows_linux)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by hikaricore on 2007-04-06
One thing you may want to keep in mind, is that if hardware does not work under linux, it will not work under a virtual machine.

I'm also not too sure about printers working properly under a vm.

p.s. virtualbox is lighter weight and easier to install.  virtualbox has ubuntu/debian packages on their site.

---

### Post by spankymasterc on 2007-04-06
Dude dont do the above tried it to much complications if u need help trust me i will get you going and get your apps working i have windows xp and mac ox 10.4.7 installed on the vmware and they work great :D

---

### Post by carusoswi on 2007-04-08
Ok, so what do I do?
I downloaded that converter, but it won't run.
I donwloaded VMWare player.
It is looking for a virtual machine file.
I downloaded that other program mentioned above, EasyVMX, my package installer handled it, but, I cannot find it in my applicatons menu.

I feel a bit stupid, but, I guess that's the only way you can learn.

Advice would be most appreciated.

Thanks.

Caruso

---

### Post by Rizlaw on 2007-04-08
> **spankymasterc said:**
> Dude dont do the above tried it to much complications if u need help trust me i will get you going and get your apps working i have windows xp and mac ox 10.4.7 installed on the vmware and they work great :D

I've been mulling this over and looking at the different VM software and it seems you may be correct and VMware is the way to go. So a few questions before proceeding with your offer of help.

1. If I don't like what I see after installing VMPlayer can it be easily uninstalled from Ubuntu without messing up my installation?

2. I downloaded and installed VM Converter on my Windows XP partition and ran the wizard to create the magic file needed for VMPlayer. I aborted because I was confused about what it was asking me to do and VMware's user's guide totally failed to answer my concerns. I was under the impression that I only needed to select the active partition on which Windows XP Pro was installed (i.e. C:\). However, the wizard pops up a warning when I do this and says that I haven't selected an active OS partition --- that if I continue, the image I create won't boot in VMPlayer.  If I select two other hard discs (one of which is a linux ext3 formatted hard disc, the other an ntfs data drive) it then will allow me to create a usable image. I don't understand, why I need to add these additional hard disc drives to the image when they have no Windows OS on them, and one of the drives (linux ext3 drive) has nothing to do with Windows?  Now, I know that I don't need to use VM Converter, but I thought it would make life easier if I could just clone my existing XP installation and load that image into VMPlayer instead of having to create a new image of XP from scratch and then reinstall all my needed Windows software and drivers to see if this experiment will work. What are your thoughts?

3. A HOWTO written by "Altonbr" in the Ubuntu Tutorials section, has, what looks like a simple 9 step guide to installing VMPlayer. Is this worth following, or do you have an easier and better solution?

---

### Post by reswob on 2007-04-12
This is just a comment to let you know that I'm seeing that problem as well when I used converter.

I put that question out on the VMWare forums but I have not gotten an answer yet.

---

