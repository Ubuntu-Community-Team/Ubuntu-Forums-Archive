---
title: "sudo"
date: 2005-10-24
forum: General Help
---

### Post by azuiden on 2005-10-24
i just recently installed 5.10

i currently have a wireless pci card that i have yet to intialize on my machine before it can become functional.

when attempting to load the INF's for ndiswrapper i realized that i couldn't sudo

it gave me the following error

sudo: unable to lookup ubuntu via gethostbyname()

a reboot does not fix this

and doing other commands does not give me any other result

---

### Post by mlomker on 2005-10-24
Boot up and select 'rescue' from the grub menu.  You can use **nano** to edit these two files in the /etc directory from the command prompt.  You must not have specified a hostname during setup or something...

Do this:
```

nano /etc/hostname
nano /etc/hosts

```

Ctrl-X, Y, Enter to save.  My host is mlomkernote, so make your files look similar to these:


```

mlomker@mlomkernote:/etc$ cat hostname
mlomkernote
mlomker@mlomkernote:/etc$ cat hosts
127.0.0.1       localhost.localdomain   localhost       mlomkernote

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by azuiden on 2005-10-25
i don't have a grub menu

i have a dedicated linux machine

and i did skip over setting a host name in the installation because i skipped over the network on accident i stopped and came back and i forgot where i was and hit cancel and go back too many times and took a guess

so anyway i can get root access to be able to write those files?

---

### Post by Whatsisname on 2005-10-25
why don't you have a grub menu?

linux needs to boot somehow, grub is not only used for dual boot systems. Whether you have it or not, have no fear.

Throw in your linux installation CD and go through the installation until you get  to the disk partitioner. Once there, hit escape a couple times until you get to the long installation menu. Scroll way to the bottom and there will be the option to drop to a shell. Select that, mount your harddrive partitions, then use nano to edit as the other poster specified. Unmount the partitions, then reboot and hopefully you'll be good to go.

[QUOTE=azuiden]i don't have a grub menu

i have a dedicated linux machine

and i did skip over setting a host name in the installation because i skipped over the network on accident i stopped and came back and i forgot where i was and hit cancel and go back too many times and took a guess

so anyway i can get root access to be able to write those files?[/QUOTE]

---

### Post by azuiden on 2005-10-25
ok i jsut realized that you have to push esc to access the grub menu for it to be able to work and get into recovery mode

and whatsisname's way will only allow me to change the installation because it doesn't nothing otherwise because i have everything already installed

---

### Post by dominicb on 2005-10-25
I used the default hostname which is ubuntu, and got the same error when trying to sudo something, ie sudo fails because it can't geethostbyname() for ubuntu. In /etc/hosts was only 127.0.0.1 localhost. I can't add ubuntu as a hostname because you need to sudo and I can't sudo because I can't gethostbyname().

Being a smart alec, I reinstalled and chose the hostname localhost. Lo and behold, when I want to sudo, it works fine. So being an idiot, i do this:

sudo hostname ubuntu

which works great, so I stretch a little with

sudo hostname bubuntu

which fails because sudo can't gethostbyname() for ubuntu.

Why is sudo trying to gethostbyname for my local hostname?

Anyway the fix above works fine. I've been into ubuntu about 3 hours and i'm already annoyed with sudo. I *like* knowing the root password. Now off to find out why my RT2500 wireless card isn't started.

---

