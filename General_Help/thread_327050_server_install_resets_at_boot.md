---
title: "server install resets at boot"
date: 2006-12-28
forum: General Help
---

### Post by paridoth on 2006-12-28
i am attempting to install ubuntu server edgy on my old compaq presario 5441 with an amd K6 450Mhz or so, 192 megs of ram, and onboard video. unfortunately after i go through the server install which works great, the computer restarts, gets to grub, grub counts down, and as soon as it finishes and starts to boot, before i even see anything on the screen, the computer resets, and it starts all over again. oddly enough after that i installed regular ubuntu 6.10 on the same computer and it works just fine. i'm not sure what to do, thanks for any help

PS i tried running it in recovery mode, same thing, and i ran a memtest and got no errors after about an hour of testing.

---

### Post by bernied on 2006-12-28
You can slow grub down a bit. If the menu is hidden, hit <ESC> to bring it up, then before it boots, select the default and hit 'e' to edit.

Then write down the commands (post here if you like). Then hit Enter or <ESC> again (sorry, can't remember which) to go back to the menu. Then hit 'c' for a command line, then try the cammands one by one, see how grub feels about them. You should be able to tell whether grub is happy or not, post any errors here. 

When you type in the 'kernel' command, leave out the 'quiet' option, as this will hide useeful information from you.

And the last command should be 'boot' - this is not necessary on a menu entry but is needed when booting manually in grub.

Hopefully this might give a bit more information.

---

### Post by paridoth on 2006-12-28
ok i edited the commands for the default entry, the only ones i could remove where quiet and splash, which i did, but i got the same results, a reset imediatly after "starting..." apears

here it is before i edited
```

root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386-server root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386-server
quiet
savedefault
boot

```

and then after

```

root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386-server root=/dev/hda1 ro
initrd		/boot/initrd.img-2.6.17-10-386-server
boot

```

---

### Post by bernied on 2006-12-29
I'm sorry, this makes no sense to me, it looks like it must be something about that particular kernel with that particular hardware. You know that a linux kernel can boot because you used one to install ubuntu. You could try some of the kernel paramaters that turn stuff off - like noacpi.

There's a huge list of them [here](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt), for example. Might be something specific to your machine though.

---

### Post by paridoth on 2006-12-30
turning stuff off doesnt really make sence to me iether though, because the desktop install should have had all the same stuff off, or even more so. i think what i am going to try to do is install edgy desktop, then uninstall X, gnome, and all the gui apps and see what happens, i mean if that works all i have to do is install the server apps i need and that should do it.

edit: started new thread on this
[http://www.ubuntuforums.org/showthread.php?p=1953245#post1953245](http://www.ubuntuforums.org/showthread.php?p=1953245#post1953245)

---

### Post by paridoth on 2007-01-01
wait i just got an idea from this wiki article
[https://help.ubuntu.com/community/Se...t=%28server%29](https://help.ubuntu.com/community/Se...t=%28server%29)
could i install the ubuntu server 6.10, then copy a desktop kernel and use the desktop kernel nstead of the "optimized" server kernel which i think is causing the problems?

---

### Post by bernied on 2007-01-01
You can try this, but the ubuntu kernels are heavily dependent on modules, so you need to have all the modules (which are specific to the kernel version) you're going to need as well. Could you not install the kernel and module packages using apt-get, so let ubuntu deal with the complexities?

You should be able to chroot into your ubuntu system from another linux (say a live cd).
You need to mount /proc /sys and /dev into the target before you chroot (and any other fancy partitioning that you might do on the server), so something like:
```
mkdir /mnt/tmpserver
mount -t [filesystem] /dev/[location of install] /mnt/tmpserver
cd /mnt/tmpserver
mount -t proc /proc proc
mount -t sysfs /sys sys
mount -o bind /dev dev
chroot ./
apt-get linux-image-generic
```
Does this help?

---

### Post by paridoth on 2007-01-01
i will try this from the ubuntu 6.10 live cd, but i have never done anything with chroot before, so ill have to read up on it a little, ill get back when i do

---

### Post by bernied on 2007-01-01
good, because I've probably left something out.

---

### Post by paridoth on 2007-01-02
ok i tried it, everything worked great, chroot worked perfect and everything, but i cant apt-get, looks like theres no internet conectivity after i chroot, the live cd has internet perfectly, but it looks like the chrooted environment doesnt have internet, as it said it couldnt find the kernel, and a apt-get update returns a bunch of errors about temporary failures resolving.

how can i get internet on the chrooted environment? or can i use the livecd's respos in the chrooted envirironment? or can i download the deb with the live cd then dpkg it in the chrooted environment?

---

### Post by bernied on 2007-01-02
It might be /etc/resolv.conf that's needed - see if it's in the install

And you can probably do the other things you said as well - just watch out for dependencies

---

### Post by paridoth on 2007-01-02
> **bernied said:**
> It might be /etc/resolv.conf that's needed - see if it's in the install
looks like i dont have one, could this be because i installed it when the computer wasnt conected to a network?
i have a resolv.conf, from another computer on the same network, can i use it?

edit: copied and pasted them over and its downloading the image now =)

---

### Post by bernied on 2007-01-03
> **paridoth said:**
> looks like i dont have one, could this be because i installed it when the computer wasnt conected to a network?
Exactly!

> **paridoth said:**
> edit: copied and pasted them over and its downloading the image now =)
Hooray!

You might want to manually check your /boot/grub/menu.lst file before rebooting - see that it's made an entry for a kernel (and initrd) with 'generic' in it. If not, it should look something like this:
```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro 
initrd          /boot/initrd.img-2.6.17-10-generic
boot
```

---

### Post by paridoth on 2007-01-03
it updated my menu.lst for me, and put the entry in, i chose it at boot, aanndd... it works! horay! the kernel boots and everything, but now i have a new problem -.-

at boot i get a message [```
    79.775771] sis630_smbus  0000:00:01.0: sis630 comp. bus not detected, module not inserted

```
it continues to boot, and finishes, i login, but have no network connection on the server, ifconfig returns only lo.

i'm guessing this has something to do with installing the generic kernel because when it was chrooted it had Internet, and a network connection.

---

### Post by bernied on 2007-01-03
hmmm, i'm not convinced that sis630_smbus is for your network adaptor.

Before you get carried away, just check whether 
```
ifconfig -a
```
shows the interface
If it does, then it's just the networking you've got to configure, see if you can do it through the system menu.

---

### Post by bernied on 2007-01-03
but if you don't have a gui desktop (does the server edition have a desktop installed?), then start with /etc/network/interfaces - there should be an entry for lo and an entry for the network interface, probably eth0, something like:
```
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
```
or, alternatively,
```
auto eth0
iface eth0 inet dhcp
```

You might also want to check the output from dmesg for references to eth:
```
dmesg | grep eth
```

---

### Post by paridoth on 2007-01-03
yup there was no entry for eth0 in the interfaces file, this is the last time i install a server without a network during install -.- working good now, thanks for your help =D

---

### Post by bernied on 2007-01-03
happy to help - learnt a thing or two myself

---

