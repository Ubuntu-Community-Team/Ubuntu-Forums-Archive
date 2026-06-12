---
title: "Can't find any info that helps, updated ubuntu JellyJam and now it won't boot gui"
date: 2023-08-05
forum: General Help
---

### Post by nunchuckmadness on 2023-08-05
I ran the updater and it updated some things, I saw it working on gpu drivers then the screen went black and never came back after waiting. I restarted the computer and it only boots into the command terminal with a green background and :~$ 

I've been trying to get it back on my network to fix the gpu driver but I don't have any of the commands installed other search results say to use. Basically just a vanilla install I've been using for a few weeks for steam

I tried some things, simple commands to bring it up but I either didn't have the tools or I probably did it wrong.

But I think trying to change the state of anything isn't going to work because in trying to enable network manager is says it failed because the service is masked. 

I just need to get ethernet enabled, I'm sure I can fix it if I can sudo apt install a driver. 

22.04.2 gnu 6.2.0-26
Amd53600
Nvidia 1060

---

### Post by Bashing-om on 2023-08-05
nunchuckmadness - Hello

> 
boots into the command terminal with a green background and :~$

Does this mean you are local to the computer ?

If local - what shows:
```

lsb_release -a
sudo lshw -C display

```

See what we are working with ---- and
[INDENT]where we go from here[/INDENT]

---

### Post by nunchuckmadness on 2023-08-05
Yes, this is my home computer. 

lsb_release -a  says no lsb modules are available, then it lists the distro info, ubuntu 22.04.2 lts, jammy, etc

Sudo lshw -c display 
It detects the card

The only thing that looks unusual to me is the resolution, it says it's set to 1024x768, I wonder if that's it. My 55in (~140cm) TV probably can't do anything with that

Phys I'd. 0

Bus info. Pci@0000:08:00.0

Ver. a1

width. 64bit

Clock.33mhz

Capabilities. Pm msi pcie vgacontroller bushmaster calisthenics rom

Config. driver=Nvidia latency=0

Resources. irq:96 memory:f5000000-f5ffffff memory:e000000-effffff memory:f1ffffff ioport:e000(size=128) memory:c0000-dffff

*-graphics
Product. efi vga

Phys id. 1

Logical name. /dev/from

Capabilities. fb

Configuration. Depth=32 resolution=1024, 768

---

### Post by Bashing-om on 2023-08-05
nunchuckmadness; Well  ...

We can assume now that you are running Nvida for the graphic's chip.
So what is loaded ?
post back - copy and paste between code tags:
```

dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]see what tale gets told
[/INDENT]

---

### Post by nunchuckmadness on 2023-08-05
I'll try this when I get home. But sorry, I can't copy and paste from my computer, I'm on my phone.

---

### Post by Bashing-om on 2023-08-05
nunchuckmadness; Roger that :D

These things best done at the terminal.

If I am not here when you do get home - others here will assist.

[INDENT]all in this together
[/INDENT]

---

### Post by nunchuckmadness on 2023-08-05
Thank you, I did the earlier steps at home, but had to split. 

Will update

---

### Post by nunchuckmadness on 2023-08-06
I can see why you said to copy and paste. But I don't have the capability to copy it to my phone. I have no network on my computer either. 

There's multiple rc and ii entries, close to the bottom it says 

ii nvidia-firmware-535-535.86.05  ...   535.86.05-0ubuntu0.22.04.1

There are also 525 lines in every other entry

---

### Post by Bashing-om on 2023-08-06
nunchuckmadness; Hummmm ....

Think'n be a good idea to change our focus and see what is up with networking.
what  results:
```

ping -c3 8.8.8.8
ping -c3 google.com
ping -c3 127.0.0.1

```

as it is real tough to deal with fractured info.
Hopefully we can find a quick fix for networking.

[INDENT]what it takes
[/INDENT]

---

### Post by nunchuckmadness on 2023-08-06
8.8.8.8 says network is unreachable

Google.com says temp failure in name resolution

127.0.0.1 comes back with with a response of about .04 ms

I normally use a wifi adapter for regular use, but right now I have it hooked up to a bridged connection from my laptop. The internet on my laptop is working good.

I also tried earlier before posting to work with the .yaml file to get it onto the network following another forum post. I hope I didn't mess it up, I was very careful to follow the instructions, but couldn't do everything it asked because I don't have the right tools installed. Should we clean out the old .yaml files and write a new one where we can direct it to a dns ?

---

### Post by Bashing-om on 2023-08-06
nunchuckmadness; Uh Huh

Yaml files must be exact. We best see what your present file is !
Unfortunate for you - I do not run network manager thus I can not directly check all your files.
However, we can start the looking.
```

cat /etc/netplan/01-network-manager-all.yaml

```
and make sure !
The desktop install -not SERVER - should be this:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```
This - even to the tab/spaces - must be exact !

[INDENT]longest journey -- starts with the 1st step
[/INDENT]

---

### Post by nunchuckmadness on 2023-08-08
Okay the fille looks like that

---

### Post by Bashing-om on 2023-08-08
nunchuckmadness; 

Ok next up is:
```

ls -al /run/systemd/network/

```
do you see similar:
10-netplan-enp4s0.network
where *my* interface is known as "enp4s0" - yours may well be different.
Mine looks like:
```

[Match]
Name=enp4s0

[Network]
DHCP=ipv4
LinkLocalAddressing=ipv6

[DHCP]
RouteMetric=100
UseMTU=true

```

also is the symbolic link present:
```

ls -al /etc/resolv.conf

```

such as my result:
```

lrwxrwxrwx 1 root root 39 Apr  3  2018 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

```

[INDENT]looking for that goof - somewhere
[/INDENT]

---

### Post by nunchuckmadness on 2023-08-08
ls -al /run/systemd/network/ 

Comes back with no such file in directory 

ls -al /etc/resolv.conf

Looks like yours.

---

### Post by TheFu on 2023-08-08
Just an idea.

For all these commands, you can send the output to a file, then copy the files to a USB flash drive, then connect that to your laptop and post the files here.

For example, 
```
$ cp /etc/netplan/01-network-manager-all.yaml /media/FLASH_DRIVE_NAME/
```

For commands, just use the redirection of stdout to a file:
```
$ name-of-command -options -more-options **[COLOR="#FF0000"]>[/COLOR]** /media/FLASH_DRIVE_NAME/command-out
```

And if you'll put the command and output between forum code tags, like I did above, it is easier to read for us. We are used to monospaced fonts. It also means you don't need to format any of the output from the terminal/console.

There's a system-info script which you can grab on your laptop, put onto the flash drive, copy over to your HOME on the Ubuntu system and run.  The output from that command can be copied back to the flash drive, posted here (code tags please), and then we won't have to ask for specific piece of information.  [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) is where to get it and has instructions for running it.  It is a good tool to have on any Linux system for troubleshooting.

---

### Post by nunchuckmadness on 2023-08-08
How do I use my USB? I have no graphical interface, no mouse or windows, I only have a green screen with the terminal

---

### Post by TheFu on 2023-08-08
> **nunchuckmadness said:**
> How do I use my USB? I have no graphical interface, no mouse or windows, I only have a green screen with the terminal

If it were me, I'd use the **mount** command with specific options based on the file system on the USB partition and the current device name, which can change.  But that is probably another rabbit-hole that you don't want to go into if you don't have that knowledge already.  OTOH, if you boot off a flash drive into a *Try Ubuntu* environment, then you will have a GUI and can connect a different flash drive to the system to copy off the files using a GUI.

Fixing booting issues is easiest for the widest possible boot issues from a Try Ubuntu environment.  Also, you can add the PPA for boot-repair, install it, then run it from that Try Ubuntu environment and probably upload the information since networking will probably work too.

---

### Post by Bashing-om on 2023-08-08
nunchuckmadness; Well !

Triple check that " /run/systemd/network/ " does not exist - typo ?
as:
at boot-time netplan 'renders' a systemd-networkd config in /run/systemd/network/ - check there are files in there. If not, then [color=red]there is no active network config[/color].
 netplan is a configuration generator, for either NetworkManager, or systemd-networkd.
  the idea is to create a config in /etc/netplan that is then applied automatically to whichever service manages network connections [/etc/netplan/config.yaml] - network manager -> /etc/netplan/01-network-manager-all.yaml
If you tell Netplan to use NetworkManager, all interface configuration control is handed off to the GUI interface on the desktop.

[INDENT]which way did he go, George
[/INDENT]

---

