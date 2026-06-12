---
title: "Why isn't rEFInd working?"
date: 2016-02-04
forum: General Help
---

### Post by helm10101 on 2016-02-04
**Final edit: rEFInd wasn't working because I tried installing it from Ubuntu Live USB, As soon as I installed Ubuntu and then rEFInd, it worked.

_________________________________________________________________________________________________________________________
Hi, 
I was suggested to install the rEFInd for a GUI for boot manager.
I just follow the instruction on the official rEFInd site:
[URL="http://www.rodsbooks.com/refind/installing.html"]http://www.rodsbooks.com/refind/installing.html:

[/URL]```
$ sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind
```

I did that through a live USB installation - not in an installed Ubuntu, but the terminal did show that it's been installed.
Please help me with the following, as I'm really frustrated:

1) Why now, I can't even find it anywhere? When I reboot, nothing appears.
2) Is rEFInd a real software? or some malware?
3) Why does Ubuntu tell me that it installs things but it never does? I mean, this package I installed, how do I know it has really been installed somewhere? I did find somewhere that you need to type "dpkg --get-selections", but refind does not appear on the least.

Thank you for any help

---

### Post by howefield on 2016-02-04
What is the output of the following command..

```
dpkg -l | grep refind
```

---

### Post by helm10101 on 2016-02-04
> **howefield said:**
> What is the output of the following command..

```
dpkg -l | grep refind
```

it shows:  refind                                        0.10.2-0ppa1                               amd64        boot manager for EFI-based computers

Actually, when I installed rEFInd through Ubuntu itself, rather than a live USB, it worked, and now it does show up at boot.

May I ask you, if I want to remove it, how can I do that? There is no documentation in the official rEFInd on how to remove it, which is quite suspicious, no?
Also, from some reason, rEFInd shows older openSUSE installation I had, and I deleted them.
How can I remove these boot options? These openSUSE don't even appear on the EFI Bios Boot options, so why do they appear on rEFInd?

I also followed this: [URL="http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi"]http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi :
[/URL]```
sudo apt-get install efibootmgr
sudo modprobe efivars
sudo efibootmgr 
sudo efibootmgr -b 5 -B 

```
and successfully removed openSUSE from the EFI boot entries, so how do they keep appearing on rEFInd?

Thank you !

---

### Post by helm10101 on 2016-02-04
Update: I managed to find the cause: from some reason, the opensuse folder appear on my boot/EFI folder:
[IMG]http://i.imgur.com/BcVWJSE.jpg[/IMG]
So I went inside opensuse folder and change the "opensuse.efi" to "opensuse" without extension.
Will it be safe to completely remove the opensuse folder?

Also, the last entry in REFIND Is a thing called "vmlinuz-4.2.0", is it safe to change the extension of this one as well? from .signed to something else? or remove this file? What is this vmlinuz anyway?

Here it is:

[IMG]http://i.imgur.com/48mcqYb.jpg[/IMG]

Thanks

**Edit: I edited refind.conf to not show this vmlinuz boot entry so everything is good.
At first I damaged the refind.conf so I copied the refind.conf-sample to it.
What if the refind.conf-sample would'nt have existed? Can I simply delete the refind.conf and refind will re-create it? or it's not doing so in refind?

---

