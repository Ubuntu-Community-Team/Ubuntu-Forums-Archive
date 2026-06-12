---
title: "Ubuntu not detecting Haiku OS"
date: 2015-11-10
forum: General Help
---

### Post by asifnaz on 2015-11-10
After installing Ubuntu I cant boot into Haiku OS 

```
asif@asif-desktop:~$ sudo fdisk -l
[sudo] password for asif: 

Disk /dev/sda: 19.4 GiB, 20847698432 bytes, 40718161 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2ad00380

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sda1  *          63 10233404 10233342  4.9G  b W95 FAT32
/dev/sda2       10233405 38957624 28724220 13.7G 83 Linux
/dev/sda3       38963198 40716287  1753090  856M  5 Extended
/dev/sda5       38963200 40716287  1753088  856M 82 Linux swap / Solaris

```


and

```
asif@asif-desktop:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
asif@asif-desktop:~$
```

I had Haiku on /dev/sda1 .Need your help

---

### Post by Mike_Walsh on 2015-11-10
I'd be surprised if anything **will** boot Haiku. 

I tried for months to get this thing to boot. Nothing would work. It always ended up either freezing.....or telling me it installed successfully; yet I could never locate it with gParted, or find it. Nothing would detect it; perhaps I was doing something wrong.

I have a bog-standard, middle of the road, Compaq Presario desktop PC, from about 10 years ago; round about the time that Haiku development began, as I recall. If you got it working, care to share?

By the way, I'd be very surprised if GRUB **would** detect it, as it runs, if memory serves, a totally unique file-system.....quite unlike anything else.

Incidentally, how did you install Ubuntu? Did you let the installer do its own thing, or did you use the 'Something Else' option, which allows you to specify exactly where you want it installed?

You're sure Haiku is even still on your system.....and hasn't been overwritten by your Ubuntu install?


Regards,

Mike. ;)

---

### Post by yancek on 2015-11-10
Interesting that using fdisk shows the Haiku partition as FAT32 but df -T shows correctly as befs

Grub will boot it.  I have Haiku installed on a 16GB flash drive and boot it from Grub Legacy with the following chainload entry.  Just modify it for Grub2.  Because of the type filesystem used, I expect that like windows it would need to be chainloaded which works for me.

> title Haiku
rootnoverify (hd1,0)
chainloader +1

Tested the entry below from Grub2 on Ubuntu and it booted.  First partition, second drive so if your Haiku is on sda1 change set root to hd0,1.  Got this from the Haiku forums

> menuentry 'Haiku {
set root=(hd1,1)
chainloader +1
}

I didn't try to install Haiku to a hard drive but the instructions on their site to install to a flash drive were pretty good.  df -T output for Haiku from another Linux system.

> /dev/sdc1      befs       15G  4.2G   11G  29% /media/haiku

---

### Post by mcgess on 2015-11-11
I can confirm yancek's solution works, with grub2 I added a file in /etc/grub.d

```
martin@martin-ThinkPad-T61:/etc/grub.d$ cat 50_haiku 
#! /bin/sh -e

echo "Adding Haiku entry" >&2
cat << EOF
menuentry "Haiku R1 alpha" {
    set root=(hd0,6)
    chainloader +1
}
EOF

```

Of course change hd0,6 to suit your setup and then sudo update-grub will create an entry to boot Haiku

---

### Post by asifnaz on 2015-11-12
Thank you **Yaneck and mcgess **for your help . I am not sure what to change in hd0,0 can you help me in this regards ..?

---

### Post by mcgess on 2015-11-12
Hi

Before you installed Ubuntu which operating systems did you have on your computer.
You now have

```
Device     Boot    Start      End  Sectors  Size Id Type
/dev/sda1  *          63 10233404 10233342  4.9G  b W95 FAT32
/dev/sda2       10233405 38957624 28724220 13.7G 83 Linux
/dev/sda3       38963198 40716287  1753090  856M  5 Extended
/dev/sda5       38963200 40716287  1753088  856M 82 Linux swap / Solaris

```

That looks like Ubuntu is installed on sda2 with swap on sda5 (in extended partition sda3)

You say you had Haiku on sda1, it should still be there (in a smaller partition)
You shouldn't need to change anything in sda1 (hd0,1)
Assuming you have grub2 you should have a linux directory /etc/grub.d which contains a collection
of scripts which tell grub2 how to create its own table. The scripts are run in numerical order
so one starting 08_ will produce grub entries closer to the top than a script numbered 50_

Using sudo to give you permissions create a file whose contents I gave earlier but using hd0,1
where I had hd0,6. The new file needs execute permission so


```
sudo chmod +x /etc/grub.d/your_file_name
sudo update-grub

```
and watch the output to check what entries are created

---

### Post by yancek on 2015-11-12
You can test this to verify that it works for you by simply putting the entry below in the grub.cfg file and saving it and rebooting.   Do not run update-grub as that will remove the entry.  Reboot.

```
menuentry 'Haiku {
set root=(hd0,1)
chainloader +1
} 			 		
```

If it boots follow the process outlined above by mcgess and go back to the grub.cfg file and delete the entry, if you want.

---

### Post by asifnaz on 2015-11-12
> **yancek said:**
> You can test this to verify that it works for you by simply putting the entry below in the grub.cfg file and saving it and rebooting.   Do not run update-grub as that will remove the entry.  Reboot.

```
menuentry 'Haiku {
set root=(hd0,1)
chainloader +1
}                      
```

If it boots follow the process outlined above by mcgess and go back to the grub.cfg file and delete the entry, if you want.
```

asif@asif-desktop:~$ sudo chmod +x /etc/grub.d/asif
[sudo] password for asif: 
asif@asif-desktop:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/asif: 1: /etc/grub.d/asif: martin@martin-ThinkPad-T61:/etc/grub.d$: not found
Adding Haiku entry
done
asif@asif-desktop:~$ 
```

and I added this in /etc/grub.d/asif

martin@martin-ThinkPad-T61:/etc/grub.d$ cat 50_haiku
#! /bin/sh -e

echo "Adding Haiku entry" >&2
cat << EOF
menuentry "Haiku R1 alpha" {
    set root=(hd0,1)
    chainloader +1
}
EOF
```

```

Irebooted but I dont see any grub slection menu at all . computer boots into Ubuntu directly .

---

### Post by mcgess on 2015-11-13
In my first post I pasted one line to few :( now you have pasted a bit to much ;)
The first line in your file should start #!

---

### Post by yancek on 2015-11-13
The error reported in your above output can be eliminated by following the steps outlined at the link below:

[URL="http://askubuntu.com/questions/475993/grub-update-warning-in-ubuntu-14-04"]http://askubuntu.com/questions/475993/grub-update-warning-in-ubuntu-14-04
[/URL]
The /etc/grub.d directory already has a file that exists specifically for this purpose.  It is 40_custom.  Just add the entry I posted earlier to that file by opening it in a text editor using sudo, then saving it and running sudo update-grub and rebooting.  You're making this more complicated than it needs to be.

---

### Post by asifnaz on 2015-11-14
Thank you Yaneck and mcgess . The Haiku OS entry has been made but I have to push escape to see grub menu , but it is not a big problem . I really appreciate your help

---

