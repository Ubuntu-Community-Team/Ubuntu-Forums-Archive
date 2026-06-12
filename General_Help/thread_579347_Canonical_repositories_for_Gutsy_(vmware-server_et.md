---
title: "Canonical repositories for Gutsy (vmware-server etc)"
date: 2007-10-18
forum: General Help
---

### Post by hollymcr on 2007-10-18
Now that Gutsy is here, are Canonical repos with (eg) vmware-server packages on their way?

I have a shiny new Gutsy server I need to put VMWare on to, and I'd rather stick with the repos if I can.

---

### Post by b20963a2 on 2007-10-18
It was in the "commercial" repo under Feisty, perhaps you can find the same for Gutsy?

---

### Post by FredB on 2007-10-18
VMWare server is not available right now. There is Virtual Box available, but no 64 bits guest OS support, nor USB :(

---

### Post by zccopwrx on 2007-10-18
yeah, it would be nice to have my VMs back, my vmware-server install no longer functions since I upgraded to Gutsy :(

---

### Post by Robby89 on 2007-10-18
Any ideas on when the package will be in the repo? I don't really want to install it from the binary, but if its not anytime soon I will

---

### Post by hollymcr on 2007-10-18
I wouldn't be surprised if the Feisty builds work; I upgraded a couple of PCs from 7.04 to 7.10 which had VMWare Server installed and they still work, I just can't install afresh.

I'm not at work now to try this, but I would suggest downloading the .deb from 
    [http://archive.canonical.com/pool/main/v/vmware-server/](http://archive.canonical.com/pool/main/v/vmware-server/)
.. and letting Ubuntu install it, it should pick up any dependencies (I assume the server kernel modules are still in the normal repos otherwise my upgrades wouldn't have worked).

NB: I have found out already that the commercial repos are being replaced by partner repos, and I note that the Canonical repos are already there in the default sources (not sure if they're enabled by default), but from what I can tell they only currently include Opera. There's also a "hardy" repo there too (for 8.04?) which also contains Opera only.

Maybe the actual builds are provided by the partner, ie we're waiting on VMWare not Canonical. Presumably when (if?) it does arrive we'll get 1.04 rather than 1.03.

---

### Post by Robby89 on 2007-10-18
That is most likely the case as VMWare isn't free software. Hopefully we'll see a build soon.

---

### Post by dextur on 2007-10-19
Stopped working for me too, too bad I really need it. Can I downgrade back to feisty?

---

### Post by eric.rost on 2007-10-20
Installing from binary will work, but you need this file:
[URL="http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz"]
vmware-any-any-update114.tar.gz[/URL]

/edit to add:

That's crosslinked from this [thread]("http://ubuntuforums.org/showthread.php?p=3561274")

---

### Post by malachi on 2007-10-21
Download this file: [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

Unless you have customized where Firefox stores its downloads, it should end up on your desktop when finished. When complete, right-click the file and choose "Extract Here." There should be a folder called vmware-any-update or something similar.

Open a terminal by going to Applications > Terminal. Type in ```
cd Desktop/vmware-any-update
``` (Change the vmware-any-update to the actual name of the folder if necessary.) Type in ```
sudo ./runme.pl
```

Follow the directions given in the terminal. For the most part, you should only have to hit Enter to accept the default options. When it is complete, and asks you to run the configuration script, hit yes.

---

### Post by veloce on 2007-10-22
Malachi: you should make it clear that your solution only works if you have installed manually with a downloaded package from vmware.

If you have installed the package from the repositories, then vmware-config.pl does not exist and cannot be patched with the any to any patch.

For those of us who installed from the repository, our current choices are to wait for the repo to be updated or uninstall and install manually.

Cheers.

---

### Post by Loranga on 2007-10-23
I am in the same situation as you guys, maybe it is a good time to take a look at kvm-qemu? :)

---

### Post by TimeSInk on 2007-10-23
Veloce and Malachi: Any idea whether an uninstall and reinstall will allow access to an existing virtual machine?

Background: same error "Unable to change virtual machine power state" after an upgrade to Gutsy. I have an XP virtual machine running to allow me access to a proprietary ap here at work.

Thanks, dan

---

### Post by veloce on 2007-10-25
Sorry for the delayed response.

I uninstalled the version I had installed from the repository.

I then installed from a copy downloaded from VMWare.

All old vms working fine.

Traps:
uninstall is not complete: I needed to delete the folder:
/etc/vmware

I needed to enter the license key again (which of course I had forgotten to write down anywhere).

---

### Post by fjgaude on 2007-10-25
> **hollymcr said:**
> Now that Gutsy is here, are Canonical repos with (eg) vmware-server packages on their way?

I have a shiny new Gutsy server I need to put VMWare on to, and I'd rather stick with the repos if I can.

I downloaded the server package from vmware site, and it works fine in my 64-bit Gutsy box, full featured, except no USBs.

---

### Post by veloce on 2007-10-25
Did you have to tweak it at all to get it to run on 64 bit version?

You used to have to install some 32 bit stuff for vmware.

---

### Post by TimeSInk on 2007-10-26
Thank you, Veloce; I'll give that a try.

I think it is only appropriate that I don't try it until late on a Friday afternoon :) ...

---

### Post by fjgaude on 2007-10-26
> **veloce said:**
> Did you have to tweak it at all to get it to run on 64 bit version?

You used to have to install some 32 bit stuff for vmware.

No, I simply downloaded the server package from the VMware site, used the old free lisence number I got months ago, and followed the instructions to install. I then used my old 32-bit vmdk folder, placed in the /var/lib/vmware/Virtual Machines folder. Started the VMware and ran previous WinPro machine.

Seems to run just as fast on the 64- as on the 32-bit boxes.

---

### Post by lilian on 2007-10-30
Hi,

I am not sure to understand... I have upgraded from feisty to gutsy. Since I did the upgrade, vmware server doesn't work anymore.

Do you think I can install the package vmware-server/vmware-server_1.0.3-1_i386.deb from [http://archive.canonical.com/pool/main/v/vmware-server](http://archive.canonical.com/pool/main/v/vmware-server) ?

What about the vmware-server-kernel-modules ?

I know I can download the sources from vmware web site, but I don't want to install something not packaged.

Thank you
Lilian

---

### Post by janne_oksanen on 2007-10-30
I upgraded to Gutsy and to my disappointment found vmware-server missing from the repos. I suppose I can always go back and boot up my old kernel and it should work. I'd very much prefer it being in the repos though.

---

### Post by TimeSInk on 2007-10-30
Update: I uninstalled through Synaptic, installed the 1.04 package, then spent significant time trying to locate my old XP vmx! That done, things came right up with only the USB devices not showing so far. 

Note: this is on a 64 bit Intel proc machine.

---

### Post by fjgaude on 2007-10-30
> **lilian said:**
> Hi,

I am not sure to understand... I have upgraded from feisty to gutsy. Since I did the upgrade, vmware server doesn't work anymore.

Do you think I can install the package vmware-server/vmware-server_1.0.3-1_i386.deb from [http://archive.canonical.com/pool/main/v/vmware-server](http://archive.canonical.com/pool/main/v/vmware-server) ?

What about the vmware-server-kernel-modules ?

I know I can download the sources from vmware web site, but I don't want to install something not packaged.

Thank you
Lilian

You install actually a later version 1.0.4... the kernel modules are created when you run the install script that comes when you reinstall the downloaded package from VMware, using the same license number they gave you the first time around.

---

### Post by fjgaude on 2007-10-30
> **TimeSInk said:**
> Update: I uninstalled through Synaptic, installed the 1.04 package, then spent significant time trying to locate my old XP vmx! That done, things came right up with only the USB devices not showing so far. 

Note: this is on a 64 bit Intel proc machine.

They don't show on the 32-bit either... we will have to wait until someone finds out what is going on, who fixes what, etc.

---

### Post by TimeSInk on 2007-10-30
Over [here]("http://ubuntuforums.org/showthread.php?t=588225")...

All up and showing...

---

### Post by fjgaude on 2007-10-30
> **TimeSInk said:**
> Over [here]("http://ubuntuforums.org/showthread.php?t=588225")...

All up and showing...

Man, thank you, what a relief... wonder why they were commented-out by the Ubuntu team?

---

### Post by Loranga on 2007-11-07
So is VMWare server 1.0.4 now available for Gutsy?

---

### Post by fjgaude on 2007-11-07
Not in the repositories, as fas as I know. But you go to the VMware web site, download the compressed file, extract it to your home directory, install, follow directions. Usually just hit return for the defaults. Use the license number you originally had.

All works fine after you uncomment those four lines in the mountdevsubfs.sh file, as shown in other posts.

---

### Post by KRavEN on 2007-11-13
Okay, it's very easy to build your own debs for vmware server.  Only problem is they're not re-distributable.

Go here [http://www.weliveonline.net/blog/2007/10/17/install-vmware-on-debian/](http://www.weliveonline.net/blog/2007/10/17/install-vmware-on-debian/) and skip down to section 3.

I got vmware-package here: [http://ftp.stw-bonn.de/debian/pool/contrib/v/vmware-package/](http://ftp.stw-bonn.de/debian/pool/contrib/v/vmware-package/)

Also will need to apt-get install openbsd-inetd package before you start

Replace 3.4 and 3.5 with the following steps:

Get [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

make-vmpkg -s vmware-any-any-update114.tar.gz

dpkg -i vmware-any-any-kernel-source_114.0.19.0_all.deb
cd vmware-any-any
m-a -f -t -u `pwd` a-b vmware-any-any-kernel-source
dpkg -i vmware-any-any-kernel-modules-VERSION.deb

You will need to re-run the last 2 steps every time the kernel gets upgraded.

---

### Post by hollymcr on 2007-11-14
> **KRavEN said:**
> Okay, it's very easy to build your own debs for vmware server.  Only problem is they're not re-distributable.

Thanks for that, I'll give it a go and see how I get on. Got several machines that would have VM on if it were easy, but I don't want to install build tools on them all!

---

### Post by nilegard on 2007-11-16
I don't know if I'm posting this at the wrong forum since I built my vmware from source, but I found out that by running
```
sudo vmware-config.pl 
```
the script detected that my vmware-player wasn't compatible with my new (gutsy) kernel and tried to recompile the necessary modules. I simply accepted the default suggestions upon the following questions and in a matter of minutes I had my vmware image rolling.

Suppose this is pretty much the same as the previous post about the upgrade/any thing. Difference is I didn't dl anything...

---

### Post by prosper927 on 2007-11-22
i also would like to run vmware in linux gutsy for 64bit after futile attempts to run virtual box for quite some time... hope that someone could guide a newbie in ubuntu on how to do this since i tried to install it via synaptics and that there are required dependencies but is not going to be installed...:(

---

### Post by veloce on 2007-11-22
> **prosper927 said:**
> i also would like to run vmware in linux gutsy for 64bit after futile attempts to run virtual box for quite some time... hope that someone could guide a newbie in ubuntu on how to do this since i tried to install it via synaptics and that there are required dependencies but is not going to be installed...:(

There are plenty of installation instructions on this forum.  The ones you want follow this pattern:

[LIST=1]
[*]Download install package from vmware's site and get a license key at the same time.
[*]install dependencies (build-essential, xinetd and for 64bit the 32 libs - sorry can't remember the package name)
[*]run the vmware installation package.
[/LIST]

---

### Post by PhrankDaChickenGeek on 2007-12-27
Just a note-  The Canonical Commercial Repository with VmWare server works now:
```

deb http://archive.canonical.com/ubuntu gutsy partner

```

---

