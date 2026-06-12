---
title: "How to search my database"
date: 2020-09-26
forum: General Help
---

### Post by satimis on 2020-09-26
Hi all,

Configuration of PC
HD-1 - SSD running OS
HD-2 - WD for data storage

1)
What will be the shell script to search HD-2 only for files, including their paths, which contain e.g. "build web server on VM of VirtualBox" ?

2)
What will be the shell script to search complete PC for files, including their path, which contain e.g. "build web server on VM of VirtualBox" ?

Thanks in advance.

Regards

---

### Post by dragonfly41 on 2020-09-27
Install ripgrep from here

[https://github.com/BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep)

Use a ripgrep command to locate files containing your exact pattern or regex expression.

Where possible narrow down search to a known directory or path.

Further filter ripgrep output by* appending* pipe and grep to ripgrep command.
[COLOR=#008000]| grep <filterpattern> [/COLOR]

---

### Post by The Cog on 2020-09-27
I would install silversarcher-ag for that. "apt show silversearcher-ag".
the actual executable is "ag". e.g. 
```
ag /mnt/hd2 "build web server on VM of VirtualBox" 
ag / --ignore /mnt/hd2 "build web server on VM of VirtualBox"
```

---

### Post by dragonfly41 on 2020-09-27
Studying published benchmarks (ripgrep vs. ag vs. others) might be useful.

[https://blog.burntsushi.net/ripgrep/](https://blog.burntsushi.net/ripgrep/)

---

### Post by The Cog on 2020-09-27
> **dragonfly41 said:**
> Studying published benchmarks (ripgrep vs. ag vs. others) might be useful.

[https://blog.burntsushi.net/ripgrep/](https://blog.burntsushi.net/ripgrep/)

That's a very interesting read. I suggested ag because it's the one I know, and I am often surprised how fast it is. I will have to give rg a try.
ripgrep is also in the ubuntu repos.

---

### Post by scorp123 on 2020-09-27
> **satimis said:**
>  What will be the shell script to search HD-2 only for files, including their paths, which contain e.g. "build web server on VM of VirtualBox" ?

Are you even sure that there are Virtualbox VM's outside of your home directory??

Per default Virtualbox places all VM's into a sub-directory within your home folder called "VirtualBox VMs". So all VM's that you created will reside here:
```
/home/YourUser/VirtualBox\ VMs

```

If your system is not a multi-user system (e.g. a server and there are other users working on it) and you don't know how to change Virtualbox's default save location, chances are all your VM's are still there in the default save location.

Also, we could ask Virtualbox directly to list all VM's it knows about. Command examples from my system:

```

> VBoxManage list vms

"OS Project 2019" {cf837fb6-cf63-4dfc-86b2-3ec2d554c00f}
"New Wiki Final" {f441224a-f3a5-4de9-80dc-46ebd399874c}
"Old Wiki" {b8b89961-c363-4176-8a50-dfda7f7b95d4}
"Windows 2016 AD Server" {b0e13f95-6543-3067-8875-1ee94e2b9a6c}
"ThinClient OS Candidate 2020" {6581a4b5-727f-4bac-9d76-24b3bcdf4673}
"Budgie 20.04" {261269ac-23dd-4234-9193-47f1edb8d57e}

```

We can also ask Virtualbox to print out the details it knows about the VM's it sees, e.g. :

```

> VBoxManage showvminfo "Budgie 20.04"

Name:                        Budgie 20.04
Groups:                      /Private VMs
Guest OS:                    Ubuntu (64-bit)
UUID:                        261269ac-23dd-4234-9193-47f1edb8d57e
Config file:                 /home/adm/VirtualBox VMs/Private VMs/Budgie 20.04/Budgie 20.04.vbox
Snapshot folder:             /home/adm/VirtualBox VMs/Private VMs/Budgie 20.04/Snapshots
Log folder:                  /home/adm/VirtualBox VMs/Private VMs/Budgie 20.04/Logs
Hardware UUID:               261269ac-23dd-4234-9193-47f1edb8d57e
Memory size                  4096MB
Page Fusion:                 disabled
VRAM size:                   128MB
CPU exec cap:                100%
HPET:                        disabled
CPUProfile:                  host
Chipset:                     piix3
Firmware:                    BIOS
Number of CPUs:              1
PAE:                         disabled
Long Mode:                   enabled
Triple Fault Reset:          disabled
APIC:                        enabled
X2APIC:                      enabled
Nested VT-x/AMD-V:           disabled
CPUID Portability Level:     0
CPUID overrides:             None
Boot menu mode:              message and menu
Boot Device 1:               Floppy
Boot Device 2:               DVD
Boot Device 3:               HardDisk
Boot Device 4:               Not Assigned
ACPI:                        enabled
IOAPIC:                      enabled
BIOS APIC mode:              APIC
Time offset:                 0ms
RTC:                         UTC
Hardware Virtualization:     enabled
Nested Paging:               enabled
Large Pages:                 disabled
VT-x VPID:                   enabled
VT-x Unrestricted Exec.:     enabled
Paravirt. Provider:          Default
Effective Paravirt. Prov.:   KVM
State:                       powered off (since 2020-09-01T22:08:01.000000000)
Graphics Controller:         VMSVGA
Monitor count:               1
3D Acceleration:             disabled
2D Video Acceleration:       disabled
Teleporter Enabled:          disabled
Teleporter Port:             0
Teleporter Address:
Teleporter Password:
Tracing Enabled:             disabled
Allow Tracing to Access VM:  disabled
Tracing Configuration:
Autostart Enabled:           disabled
Autostart Delay:             0
Default Frontend:
VM process priority:         default
Storage Controller Name (0):            IDE
Storage Controller Type (0):            PIIX4
Storage Controller Instance Number (0): 0
Storage Controller Max Port Count (0):  2
Storage Controller Port Count (0):      2
Storage Controller Bootable (0):        on
Storage Controller Name (1):            SATA
Storage Controller Type (1):            IntelAhci
Storage Controller Instance Number (1): 0
Storage Controller Max Port Count (1):  30
Storage Controller Port Count (1):      1
Storage Controller Bootable (1):        on
IDE (1, 0): Empty
SATA (0, 0): /home/adm/VirtualBox VMs/Private VMs/Budgie 20.04/Snapshots/{764965d6-2514-45bf-afdf-599ad981738d}.vdi (UUID: 764965d6-2514-45bf-afdf-599ad981738d)
NIC 1:                       MAC: 08002775065D, Attachment: Bridged Interface 'enp2s0f0', Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
NIC 2:                       disabled
NIC 3:                       disabled
NIC 4:                       disabled
NIC 5:                       disabled
NIC 6:                       disabled
NIC 7:                       disabled
NIC 8:                       disabled
Pointing Device:             USB Tablet
Keyboard Device:             PS/2 Keyboard
UART 1:                      disabled
UART 2:                      disabled
UART 3:                      disabled
UART 4:                      disabled
LPT 1:                       disabled
LPT 2:                       disabled
Audio:                       enabled (Driver: PulseAudio, Controller: AC97, Codec: AD1980)
Audio playback:              enabled
Audio capture:               disabled
Clipboard Mode:              disabled
Drag and drop Mode:          disabled
VRDE:                        disabled
OHCI USB:                    disabled
EHCI USB:                    disabled
xHCI USB:                    enabled

USB Device Filters:

Index:                       0
Active:                      yes
Name:                        Realtek 802.11ac NIC
VendorId:                    2357
ProductId:                   0106
Revision:
Manufacturer:
Product:
Remote:                      0
Serial Number:

Bandwidth groups:  <none>

Shared folders:<none>

Capturing:                   not active
Capture audio:               not active
Capture screens:             0
Capture file:                /home/adm/VirtualBox VMs/Private VMs/Budgie 20.04/Budgie 20.04.webm
Capture dimensions:          1024x768
Capture rate:                512kbps
Capture FPS:                 25kbps
Capture options:

Guest:

Configured memory balloon size: 0MB

Snapshots:

   Name: Snapshot 1 (UUID: a1310cac-adab-44e2-b7fe-af7d1a6d8bf6)
   Description:
Fresh install + patched + vboxguest-additions installed
      Name: Snapshot 2 (UUID: d4c5a498-a1ad-4283-867a-3a09066b1174)
      Description:
vboxguest-additions installed + screen set to 1440x900
         Name: Snapshot 3 (UUID: d4ac9981-118e-4c37-bb47-c4f7a91f9ff7) *
         Description:
rtl88xxau module compiled + installed via dmks. Working OK.

```


Unless there are multiple users on your system chances are all your VM's are still inside your home.
If there are multiple users on your system (e.g. it's a server and people log in remotely) chances are their VM's are inside their homes.

If you have reasons to assume the VM's might be elsewhere (a shared "/data" directory that's shared between users maybe?) then you will have to tell us more about that setup. Or you will indeed need to search for those VM's.

---

### Post by satimis on 2020-09-29
> **scorp123 said:**
> Are you even sure that there are Virtualbox VM's outside of your home directory??
.........
Hi scorp123,

Lot of thanks for your detail advice and time spent to help me.

I only need searching the database on my PC
- not searching the data on VMs
- not searching the database via VMs on LAN, local network

Regards

---

### Post by satimis on 2020-10-04
> **dragonfly41 said:**
> Install ripgrep from here

[https://github.com/BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep)

Use a ripgrep command to locate files containing your exact pattern or regex expression.

Where possible narrow down search to a known directory or path.

Further filter ripgrep output by* appending* pipe and grep to ripgrep command.
[COLOR=#008000]| grep <filterpattern> [/COLOR]
Hi,

Thanks for your advice.  I have ripgrep installed but still can't resolve how to use it.

For example - I expect to find a file/files on my database, containing duplicator, 2 part install and extract .zip on the file/files

What will be the command?

Thanks

Regards

---

### Post by satimis on 2020-10-04
> **The Cog said:**
> I would install silverserver-ag for that. "apt show silversearcher-ag".
the actual executable is "ag". e.g. 
```
ag /mnt/hd2 "build web server on VM of VirtualBsilversearcher-agox" 
ag / --ignore /mnt/hd2 "build web server on VM of VirtualBox"
```
Hi,

Thanks for your advice.

$ apt policy silverserver-ag
N: Unable to locate package silverserver-ag

It is not on repo

$ apt policy silversearcher-ag```

silversearcher-ag:
  Installed: (none)
  Candidate: 2.2.0-1/
  Version table:
     2.2.0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
```

silversearcher-ag is on repo

Regards

---

### Post by The Cog on 2020-10-04
My apologies. It's silversearcher-ag, not silverserver-ag. I will edit my post to correct that.
I read the article on ripgrep (post #4 above) and that looks pretty good too. I haven't tested a comparison personally though.

---

### Post by satimis on 2020-10-04
> **The Cog said:**
> My apologies. It's silversearcher-ag, not silverserver-ag. I will edit my post to correct that.
I read the article on ripgrep (post #4 above) and that looks pretty good too. I haven't tested a comparison personally though.
Hi,

Thanks for your advice.  I have silversearcher-ag installed.

$ which ag
/usr/bin/ag

but have no idea using it.  Suppose I need to search the PC for files containing "duplicator + 2 parts install + extract .zip" on the same file.  What command shall I run?

$ ag / "duplicator+2 parts install+extract .zip"```

ERR: Error stat()ing: duplicator+2 parts install+extract .zip
ERR: Error opening directory duplicator+2 parts install+extract .zip: No such file or directory

```

$ sudo ag / "duplicator+2 parts install+extract .zip"```

ERR: Error stat()ing: duplicator+2 parts install+extract .zip
ERR: Error opening directory duplicator+2 parts install+extract .zip: No such file or directory

```

The command didn't work.

Regards

---

### Post by dragonfly41 on 2020-10-04
With ripgrep you first navigate to the root folder to be searched then you can use the **pipe** feature ..

```
rg "duplicator" | rg "2 parts install" | rg "extract.zip"
```

This might be the same with ag.

Note that it is better to filter out unrequired file types.

---

### Post by satimis on 2020-10-04
> **dragonfly41 said:**
> With ripgrep you first navigate to the root folder to be searched then you can use the **pipe** feature ..

```
rg "duplicator" | rg "2 parts install" | rg "extract.zip"
```

This might be the same with ag.

Note that it is better to filter out unrequired file types.
Hi,

Thanks for your advice.

I expect to find the name of file/files, including its/their path, which contain following information;
duplicator
2 parts install
extract .zip

Performed following test;
$ cd /
$ sudo rg "duplicator" | sudo rg "2 parts install" | sudo rg "extract.zip"

The output is;```

....
proc/20956/task/20956/attr/fscreate: Invalid argument (os error 22)
proc/20956/task/20956/attr/keycreate: Invalid argument (os error 22)
proc/20956/task/20956/attr/sockcreate: Invalid argument (os error 22)
proc/20955/task/20961/fdinfo/7: No such file or directory (os error 2)
proc/20955/task/20961/fdinfo/8: No such file or directory (os error 2)
proc/20955/task/20961/attr/prev: Invalid argument (os error 22)
proc/20955/task/20961/attr/exec: Invalid argument (os error 22)
proc/20955/task/20961/attr/fscreate: Invalid argument (os error 22)
proc/20955/task/20961/attr/keycreate: Invalid argument (os error 22)
proc/20955/task/20961/attr/sockcreate: Invalid argument (os error 22)

```

continue and never finish

Regards

---

### Post by dragonfly41 on 2020-10-04
Try this to start off .. first cd to your target folder .. then run ..

[FONT=monospace][COLOR=#000000]```
rg -i "extract.zip" ./
```[/COLOR]
[/FONT]

---

### Post by TheFu on 2020-10-04
I'm loving the silversearcher-ag idea. Haven't looked at it, but plan to.

I've been using recoll for years. **recoll** is like google for your desktop. It has a GUI and requires indexing from time to time. I run new indexing via cron daily at 5am on the media storage system. That way, it is almost always current enough.  Recoll has a CLI interface too.  [https://en.wikipedia.org/wiki/Recoll](https://en.wikipedia.org/wiki/Recoll)  recoll is in the normal repos. It does need some configuration. Once the indexing finishes, it is FAST to return results.  It handles soundex searching too which can be a hassle for singular vs plural results.

---

### Post by satimis on 2020-10-05
> **dragonfly41 said:**
> Try this to start off .. first cd to your target folder .. then run ..

[FONT=monospace][COLOR=#000000]```
rg -i "extract.zip" ./
```[/COLOR]
[/FONT]
Performed following tests.  The 4TB harddrive for data storage is on /media/satimis/786a6a67...............08d5

$ cd /media/satimis/786a6a67...............08d5

1)
$ rg -i "extract.zip" ./```

Websites_Duplicator_20201004/Finance/Reynoldstocks_20200819_create_20200628/reynoldstocks/wp-content/plugins/duplicator/installer/dup-installer/ctrls/ctrl.s1.php
177:                    DUPX_Log::info("ERROR: Stopping install process.  Trying to extract without ZipArchive module installed.  Please use the 'Manual Archive Extraction' mode to extract zip file.");
```

2)
$ rg -i "extract zip" ./```

Websites_Duplicator_20201004/Finance/Reynoldstocks_20200819_create_20200628/reynoldstocks/wp-content/plugins/duplicator/installer/dup-installer/ctrls/ctrl.s1.php
177:                    DUPX_Log::info("ERROR: Stopping install process.  Trying to extract without ZipArchive module installed.  Please use the 'Manual Archive Extraction' mode to extract zip file.");
```

3)
$ rg -i "extract .zip" ./```

Websites_Duplicator_20201004/Finance/Reynoldstocks_20200819_create_20200628/reynoldstocks/wp-content/plugins/file-manager-advanced/readme.txt
32: * **Archives:** Archives create/extract (zip, rar, 7z, tar, gzip, bzip2)

```

On 3) ~/readme.txt file I couldn't find the xxx.zip file but the word "extract" is there.

Regards

---

### Post by dragonfly41 on 2020-10-05
Is your problem now solved?
On 4TB how long did the ripgrep operation take (roughly)?

---

### Post by satimis on 2020-10-05
> **dragonfly41 said:**
> Is your problem now solved?
Sorry, no.  I expect to search the file/files, including its/their path which contain the word "extract" and xxx.zip file (I have added its name in searching)
> On 4TB how long did the ripgrep operation take (roughly)?
About 5~6 mins.

Regards

---

### Post by dragonfly41 on 2020-10-05
Try just this..

rg -i extract ./

---

### Post by ActionParsnip on 2020-10-05
What mount point is being used for the 2nd file system that you want to search? (assuming this is /media/storage here (Yours may be different!!)) run:
```

cd /media/storage; sudo find . | grep -i something

```

---

### Post by satimis on 2020-10-06
> **ActionParsnip said:**
> What mount point is being used for the 2nd file system that you want to search? (assuming this is /media/storage here (Yours may be different!!)) run:
```

cd /media/storage; sudo find . | grep -i something

```

$ cd /media/satimis/786a6a67...........fe75cd0b08d5/; sudo find . | grep -i "extract .zip"
No output

$ cd /media/satimis/786a6a67...........fe75cd0b08d5; sudo find . | grep -i "extract .zip"
Also no output 

/media/satimis/786a6a67...........fe75cd0b08d5 is drive-2.  On it there are many folders and sub-folders.

Regards

---

### Post by dragonfly41 on 2020-10-06
You seem to have a <space> between "extract" and ".zip"

Probably why there are no matches .. with rg, ag, recoll or find.

Explore the regex methods in rg.

Or continuing with "find" try ..

[COLOR=#000000]cd /media/satimis/786a6a67...........fe75cd0b08d5/; sudo find . | grep -i "extract" | grep -i ".zip"

or

[/COLOR][COLOR=#000000]cd /media/satimis/786a6a67...........fe75cd0b08d5/; sudo rg -i extract ./ | grep -i .zip[/COLOR]

---

### Post by satimis on 2020-10-06
> **dragonfly41 said:**
> You seem to have a <space> between "extract" and ".zip"

Probably why there are no matches .. with rg, ag, recoll or find.

Explore the regex methods in rg.

Or continuing with "find" try ..

[COLOR=#000000]cd /media/satimis/786a6a67...........fe75cd0b08d5/; sudo find . | grep -i "extract" | grep -i ".zip"

or

[/COLOR][COLOR=#000000]cd /media/satimis/786a6a67...........fe75cd0b08d5/; sudo rg -i extract ./ | grep -i .zip[/COLOR]

$ cd /media/satimis/786a6a67.........fe75cd0b08d5/; sudo find . | grep -i "extract" | grep -i ".zip"```

./PC1A_Data_20181231_20201031/Satimis_Document_20181231_20201031/Misc_Drinks_n_Foods_20120531_20200930/Restaurant_Software_2017/TastyIgniter_20170808/Extract/TastyIgniter-master/system/libraries/Zip.php
```
Not listing the files which contains "extract" and ".zip"

$ cd /media/satimis/786a6a67.......fe75cd0b08d5/; sudo rg -i extract ./ | grep -i zip
It took about 6 mins to finish but with no output.

---

### Post by dragonfly41 on 2020-10-06
You can also try a GUI like SearchMonkey but it will be much slower than ripgrep.

[Later note added]

Here is another helpful blog on [ripgrep usage giving examples]("https://mariusschulz.com/blog/fast-searching-with-ripgrep").

---

