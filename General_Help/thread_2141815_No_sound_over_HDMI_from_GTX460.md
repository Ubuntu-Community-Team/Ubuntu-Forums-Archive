---
title: "No sound over HDMI from GTX460"
date: 2013-05-03
forum: General Help
---

### Post by Tbone2010 on 2013-05-03
Hi all, here's my issue.  When I run aplay -l, I get the built-in Intel stuff, which is routed to the front panel of my desktop.  I don't care about that.  I'm trying to get my sound to be carried over HDMI to my TV/monitor.

I used this command: 
```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
```
and got this output:
```
Sound cards recognized by the system:00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
01:00.1 Audio device [0403]: NVIDIA Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
01:00.1 Audio device [0403]: NVIDIA Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
01:00.1 Audio device [0403]: NVIDIA Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)

```

So it looks like ALSA should recognize my card, but somehow doesn't.

Running this command 
```
[COLOR=#333333][FONT=UbuntuMono]cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo alsa force-reload; sudo lshw -C sound[/FONT][/COLOR]
```
hangs at the last line of this:```
Advanced Linux Sound Architecture Driver Version k3.8.0-19-generic.
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xfbff8000 irq 51
  1:        : sequencer
  2: [ 0- 2]: digital audio capture
  3: [ 0- 1]: digital audio playback
  4: [ 0- 1]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 2]: hardware dependent
  8: [ 0]   : control
 33:        : timer
00-02: HDA Codec 2
00-00: ALC892 Analog : ALC892 Analog : playback 1 : capture 1
00-01: ALC892 Digital : ALC892 Digital : playback 1 : capture 1
00-02: ALC892 Analog : ALC892 Analog : capture 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192


Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for zach: 
rm: cannot remove ‘/etc/asound.conf’: No such file or directory
rm: cannot remove ‘/home/zach/.pulse’: No such file or directory
rm: cannot remove ‘/home/zach/.asound*’: No such file or directory
rm: cannot remove ‘/home/zach/.pulse-cookie’: No such file or directory
Get:1 http://security.ubuntu.com raring-security Release.gpg [933 B]
Hit http://archive.canonical.com raring Release.gpg                                                                    
Get:2 http://security.ubuntu.com raring-security Release [40.8 kB]                                                     
Hit http://archive.canonical.com raring Release                                                                        
Hit http://archive.canonical.com raring/partner Sources                                                                
Hit http://archive.canonical.com raring/partner amd64 Packages                                                         
Get:3 http://security.ubuntu.com raring-security/main Sources [4,100 B]                                                
Hit http://archive.canonical.com raring/partner i386 Packages                                                          
Get:4 http://security.ubuntu.com raring-security/restricted Sources [14 B]                                             
Get:5 http://security.ubuntu.com raring-security/universe Sources [14 B]                                               
Get:6 http://security.ubuntu.com raring-security/multiverse Sources [14 B]                                             
Get:7 http://security.ubuntu.com raring-security/main amd64 Packages [7,065 B]                                         
Get:8 http://security.ubuntu.com raring-security/restricted amd64 Packages [14 B]                                      
Get:9 http://security.ubuntu.com raring-security/universe amd64 Packages [2,991 B]                                     
Get:10 http://security.ubuntu.com raring-security/multiverse amd64 Packages [14 B]                                     
Get:11 http://security.ubuntu.com raring-security/main i386 Packages [6,886 B]                                         
Get:12 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]                                      
Ign http://archive.canonical.com raring/partner Translation-en_US                                                      
Get:13 http://security.ubuntu.com raring-security/universe i386 Packages [3,302 B]                                     
Ign http://archive.canonical.com raring/partner Translation-en                                                         
Get:14 http://security.ubuntu.com raring-security/multiverse i386 Packages [14 B]                                      
Hit http://security.ubuntu.com raring-security/main Translation-en                                                     
Hit http://security.ubuntu.com raring-security/multiverse Translation-en                                               
Hit http://security.ubuntu.com raring-security/restricted Translation-en                                               
Hit http://security.ubuntu.com raring-security/universe Translation-en                                                 
Ign http://security.ubuntu.com raring-security/main Translation-en_US                                                  
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US                                            
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US                                            
Ign http://security.ubuntu.com raring-security/universe Translation-en_US                                              
Hit http://repo.steampowered.com precise Release.gpg                                                                   
Hit http://us.archive.ubuntu.com raring Release.gpg                                                                    
Get:15 http://us.archive.ubuntu.com raring-updates Release.gpg [933 B]                                  
Get:16 http://us.archive.ubuntu.com raring-backports Release.gpg [933 B]                                            
Get:17 http://extras.ubuntu.com raring Release.gpg [72 B]                                                           
Hit http://repo.steampowered.com precise Release                                                                  
Hit http://us.archive.ubuntu.com raring Release                                                          
Get:18 http://us.archive.ubuntu.com raring-updates Release [40.8 kB]                                                   
Hit http://repo.steampowered.com precise/steam Sources                                                           
Hit http://extras.ubuntu.com raring Release                                                                      
Get:19 http://us.archive.ubuntu.com raring-backports Release [40.8 kB]                                                 
Hit http://extras.ubuntu.com raring/main Sources                                                                       
Hit http://us.archive.ubuntu.com raring/main Sources                                                                   
Hit http://repo.steampowered.com precise/steam amd64 Packages                                           
Hit http://us.archive.ubuntu.com raring/restricted Sources                                                             
Hit http://us.archive.ubuntu.com raring/universe Sources                                                               
Hit http://extras.ubuntu.com raring/main amd64 Packages                                                                
Hit http://us.archive.ubuntu.com raring/multiverse Sources                                                             
Hit http://us.archive.ubuntu.com raring/main amd64 Packages                                                            
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages                                                      
Hit http://extras.ubuntu.com raring/main i386 Packages                                                  
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages                                         
Hit http://repo.steampowered.com precise/steam i386 Packages                                            
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages                                                      
Hit http://us.archive.ubuntu.com raring/main i386 Packages                                                             
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages                                                       
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                                                         
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages                                                       
Hit http://us.archive.ubuntu.com raring/main Translation-en                       
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en                                       
Hit http://us.archive.ubuntu.com raring/restricted Translation-en                                       
Hit http://us.archive.ubuntu.com raring/universe Translation-en                                                        
Get:20 http://us.archive.ubuntu.com raring-updates/main Sources [7,219 B]                                              
Get:21 http://us.archive.ubuntu.com raring-updates/restricted Sources [14 B]                                           
Get:22 http://us.archive.ubuntu.com raring-updates/universe Sources [925 B]                                            
Get:23 http://us.archive.ubuntu.com raring-updates/multiverse Sources [14 B]                                           
Get:24 http://us.archive.ubuntu.com raring-updates/main amd64 Packages [12.8 kB]                                       
Get:25 http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages [14 B]                                    
Get:26 http://us.archive.ubuntu.com raring-updates/universe amd64 Packages [6,315 B]                                   
Get:27 http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages [14 B]                                    
Get:28 http://us.archive.ubuntu.com raring-updates/main i386 Packages [12.7 kB]                                        
Ign http://extras.ubuntu.com raring/main Translation-en_US                                                             
Get:29 http://us.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]                                     
Get:30 http://us.archive.ubuntu.com raring-updates/universe i386 Packages [6,576 B]                                    
Get:31 http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages [14 B]                                     
Ign http://extras.ubuntu.com raring/main Translation-en                                                                
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en                                                    
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en                                              
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en                                              
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en                                                
Get:32 http://us.archive.ubuntu.com raring-backports/main Sources [14 B]                                               
Get:33 http://us.archive.ubuntu.com raring-backports/restricted Sources [14 B]                                         
Get:34 http://us.archive.ubuntu.com raring-backports/universe Sources [2,107 B]                                        
Get:35 http://us.archive.ubuntu.com raring-backports/multiverse Sources [14 B]                                         
Get:36 http://us.archive.ubuntu.com raring-backports/main amd64 Packages [14 B]                                        
Ign http://repo.steampowered.com precise/steam Translation-en_US                                                       
Get:37 http://us.archive.ubuntu.com raring-backports/restricted amd64 Packages [14 B]                                  
Get:38 http://us.archive.ubuntu.com raring-backports/universe amd64 Packages [2,937 B]                                 
Get:39 http://us.archive.ubuntu.com raring-backports/multiverse amd64 Packages [14 B]                                  
Ign http://repo.steampowered.com precise/steam Translation-en                                                          
Get:40 http://us.archive.ubuntu.com raring-backports/main i386 Packages [14 B]                                         
Get:41 http://us.archive.ubuntu.com raring-backports/restricted i386 Packages [14 B]                                   
Get:42 http://us.archive.ubuntu.com raring-backports/universe i386 Packages [2,944 B]                                  
Get:43 http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages [14 B]                                   
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en                                                  
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en                                            
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en                                            
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en                                              
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                                                         
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US                                                   
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US                                                   
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US                                                     
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US                                                 
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US                                           
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US                                           
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US                                             
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US                                               
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US                                         
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US                                         
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US                                           
Err http://ppa.launchpad.net raring Release.gpg                                                                        
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Hit http://ppa.launchpad.net raring Release.gpg                                                                        
Ign http://ppa.launchpad.net raring Release                                                                            
Hit http://ppa.launchpad.net raring Release                                                                            
Hit http://ppa.launchpad.net raring/main Sources                                                                       
Hit http://ppa.launchpad.net raring/main amd64 Packages                                                                
Hit http://ppa.launchpad.net raring/main i386 Packages                                                                 
Err http://ppa.launchpad.net raring/main Sources                                                                       
  404  Not Found
Err http://ppa.launchpad.net raring/main amd64 Packages                                                                
  404  Not Found
Err http://ppa.launchpad.net raring/main i386 Packages                                                                 
  404  Not Found
Ign http://ppa.launchpad.net raring/main Translation-en_US                                                             
Ign http://ppa.launchpad.net raring/main Translation-en                                                                
Ign http://ppa.launchpad.net raring/main Translation-en_US                                                             
Ign http://ppa.launchpad.net raring/main Translation-en                                                                
Fetched 204 kB in 15s (13.5 kB/s)                                                                                      
W: Failed to fetch http://ppa.launchpad.net/undistract-me-packagers/daily/ubuntu/dists/raring/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)


W: Failed to fetch http://ppa.launchpad.net/undistract-me-packagers/daily/ubuntu/dists/raring/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/undistract-me-packagers/daily/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/undistract-me-packagers/daily/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
H/W path       Device      Class       Description
==================================================
                           system      P55-USB3 ()
/0                         bus         P55-USB3
/0/0                       memory      128KiB BIOS
/0/4                       processor   Intel(R) Core(TM) i5 CPU         760  @ 2.80GHz
/0/4/a                     memory      64KiB L1 cache
/0/4/b                     memory      8MiB L2 cache
/0/1a                      memory      8GiB System Memory
/0/1a/0                    memory      4GiB DIMM 1600 MHz (0.6 ns)
/0/1a/1                    memory      DIMM [empty]
/0/1a/2                    memory      4GiB DIMM 1600 MHz (0.6 ns)
/0/1a/3                    memory      DIMM [empty]
/0/100                     bridge      Core Processor DMI
/0/100/3                   bridge      Core Processor PCI Express Root Port 1
/0/100/3/0                 display     GF104 [GeForce GTX 460]
/0/100/3/0.1               multimedia  GF104 High Definition Audio Controller
/0/100/8                   generic     Core Processor System Management Registers
/0/100/8.1                 generic     Core Processor Semaphore and Scratchpad Registers
/0/100/8.2                 generic     Core Processor System Control and Status Registers
/0/100/8.3                 generic     Core Processor Miscellaneous Registers
/0/100/10                  generic     Core Processor QPI Link
/0/100/10.1                generic     Core Processor QPI Routing and Protocol Registers
/0/100/1a                  bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1a.1                bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1a.2                bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1a.7                bus         5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1b                  multimedia  5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                  bridge      5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c/0                storage     JMB363 SATA/IDE Controller
/0/100/1c/0.1              storage     JMB363 SATA/IDE Controller
/0/100/1c.1                bridge      5 Series/3400 Series Chipset PCI Express Root Port 2
/0/100/1c.1/0  eth0        network     RTL8111/8168 PCI Express Gigabit Ethernet controller
/0/100/1c.2                bridge      5 Series/3400 Series Chipset PCI Express Root Port 3
/0/100/1c.2/0              bus         uPD720200 USB 3.0 Host Controller
/0/100/1d                  bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.1                bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.2                bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.3                bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.7                bus         5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                  bridge      82801 PCI Bridge
/0/100/1f                  bridge      5 Series Chipset LPC Interface Controller
/0/100/1f.2                storage     5 Series/3400 Series Chipset 4 port SATA IDE Controller
/0/100/1f.3                bus         5 Series/3400 Series Chipset SMBus Controller
/0/100/1f.5                storage     5 Series/3400 Series Chipset 2 port SATA IDE Controller
/0/101                     bridge      Core Processor QuickPath Architecture Generic Non-Core Registers
/0/102                     bridge      Core Processor QuickPath Architecture System Address Decoder
/0/103                     bridge      Core Processor QPI Link 0
/0/104                     bridge      Core Processor QPI Physical 0
/0/105                     bridge      Core Processor Integrated Memory Controller
/0/106                     bridge      Core Processor Integrated Memory Controller Target Address Decoder
/0/107                     bridge      Core Processor Integrated Memory Controller Test Registers
/0/108                     bridge      Core Processor Integrated Memory Controller Channel 0 Control Registers
/0/109                     bridge      Core Processor Integrated Memory Controller Channel 0 Address Registers
/0/10a                     bridge      Core Processor Integrated Memory Controller Channel 0 Rank Registers
/0/10b                     bridge      Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
/0/10c                     bridge      Core Processor Integrated Memory Controller Channel 1 Control Registers
/0/10d                     bridge      Core Processor Integrated Memory Controller Channel 1 Address Registers
/0/10e                     bridge      Core Processor Integrated Memory Controller Channel 1 Rank Registers
/0/10f                     bridge      Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
/0/1           scsi0       storage     
/0/1/0.0.0     /dev/sda    disk        128GB OCZ-VERTEX4
/0/1/0.0.0/1   /dev/sda1   volume      350MiB Windows NTFS volume
/0/1/0.0.0/2   /dev/sda2   volume      53GiB Windows NTFS volume
/0/1/0.0.0/3   /dev/sda3   volume      41GiB EXT4 volume
/0/1/0.0.0/4   /dev/sda4   volume      24GiB EXT4 volume
/0/2           scsi1       storage     
/0/2/0.1.0     /dev/sdb    disk        1TB ST31000528AS
/0/2/0.1.0/1   /dev/sdb1   volume      931GiB Windows NTFS volume
/0/3           scsi3       storage     
/0/3/0.0.0     /dev/cdrom  disk        DVD-RAM writer
total 0
crw-rw---T+  1 root audio 116, 33 May  3 17:02 timer
crw-rw---T+  1 root audio 116,  1 May  3 17:02 seq
crw-rw---T+  1 root audio 116,  2 May  3 17:03 pcmC0D2c
crw-rw---T+  1 root audio 116,  3 May  3 17:03 pcmC0D1p
crw-rw---T+  1 root audio 116,  4 May  3 17:03 pcmC0D1c
crw-rw---T+  1 root audio 116,  6 May  3 17:03 pcmC0D0c
crw-rw---T+  1 root audio 116,  7 May  3 17:03 hwC0D2
crw-rw---T+  1 root audio 116,  8 May  3 17:03 controlC0
drwxr-xr-x   2 root root       60 May  3 17:03 by-path
drwxr-xr-x   3 root root      240 May  3 17:03 .
crw-rw---T+  1 root audio 116,  5 May  3 17:16 pcmC0D0p
drwxr-xr-x  15 root root     4320 May  3 17:19 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3b] (rev 06)
00:1a.1 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3e] (rev 06)
00:1a.2 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3f] (rev 06)
00:1a.7 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b36] (rev 06)
00:1d.1 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b37] (rev 06)
00:1d.2 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b38] (rev 06)
00:1d.3 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b39] (rev 06)
00:1d.7 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
02:00.0 SATA controller [0106]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 02)
02:00.1 IDE interface [0101]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 02)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c51] (rev 04)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
3f:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
3f:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
3f:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
3f:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
3f:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
3f:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
3f:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
3f:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
3f:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
3f:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
3f:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 002: ID 046d:c066 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
/usr/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/by-path:    zach       2069 ..c.. bash
dpkg-query: no path found matching pattern *bin/slmodemd*
[    0.000000] No AGP bridge found
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [mem 0x000f5620-0x000f562f] mapped at [ffff8800000f5620]
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.165828] perf_event_intel: CPU erratum AAJ80 worked around
[    0.221062] ACPI: No dock devices found.
[    0.249145] pci_bus 0000:3f: No busn resource found for root bus, will use [bus 3f-ff]
[    0.256774] pnp: PnP ACPI: found 13 devices
[    0.522010] audit: initializing netlink socket (disabled)
[    0.522018] type=2000 audit(1367600547.416:1): initialized
[    0.574696] libphy: Fixed MDIO Bus: probed
[    0.587459] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.587541] hub 1-0:1.0: USB hub found
[    0.603417] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.603497] hub 2-0:1.0: USB hub found
[    0.603664] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.603731] hub 3-0:1.0: USB hub found
[    0.603839] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.603899] hub 4-0:1.0: USB hub found
[    0.604000] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.604058] hub 5-0:1.0: USB hub found
[    0.604154] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.604212] hub 6-0:1.0: USB hub found
[    0.604306] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.604365] hub 7-0:1.0: USB hub found
[    0.604463] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.604522] hub 8-0:1.0: USB hub found
[    0.604616] usb usb9: New USB device found, idVendor=1d6b, idProduct=0001
[    0.604674] hub 9-0:1.0: USB hub found
[    0.605046] usb usb10: New USB device found, idVendor=1d6b, idProduct=0002
[    0.605109] hub 10-0:1.0: USB hub found
[    0.608236] usb usb11: New USB device found, idVendor=1d6b, idProduct=0003
[    0.608309] hub 11-0:1.0: USB hub found
[    0.617918] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.292254] usb 1-6: New USB device found, idVendor=05e3, idProduct=0608
[    1.292911] hub 1-6:1.0: USB hub found
[    1.720300] usb 5-1: New USB device found, idVendor=046d, idProduct=c066
[    2.521366] type=1400 audit(1367614950.404:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=538 comm="apparmor_parser"
[    2.521865] type=1400 audit(1367614950.404:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
[    2.522146] type=1400 audit(1367614950.404:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=538 comm="apparmor_parser"
[    2.525251] lp: driver loaded but no devices found
[    2.536799] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    2.546720] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[    2.679736] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[    2.693397] snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
[    2.834532] input: HDA Intel MID Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    2.834600] input: HDA Intel MID Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    2.834752] input: HDA Intel MID Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    2.834796] input: HDA Intel MID Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    2.834837] input: HDA Intel MID Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    2.834878] input: HDA Intel MID Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    2.834920] input: HDA Intel MID Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    2.834966] input: HDA Intel MID Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    2.835423] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    2.930130] type=1400 audit(1367614950.812:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=937 comm="apparmor_parser"
[    2.930221] type=1400 audit(1367614950.812:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=935 comm="apparmor_parser"
[    2.930459] type=1400 audit(1367614950.812:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=935 comm="apparmor_parser"
[    2.930573] type=1400 audit(1367614950.812:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=937 comm="apparmor_parser"
[    2.930745] type=1400 audit(1367614950.812:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=937 comm="apparmor_parser"
[    2.932324] type=1400 audit(1367614950.816:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=934 comm="apparmor_parser"
[    3.632604] IP: [<ffffffffa0b33820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[    3.632997] Modules linked in: snd_hda_codec_hdmi bnep rfcomm bluetooth binfmt_misc(F) snd_hda_codec_realtek snd_hda_intel(+) coretemp kvm_intel snd_hda_codec kvm snd_hwdep(F) joydev(F) snd_pcm(F) ppdev(F) hid_generic gpio_ich snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) parport_pc(F) snd_rawmidi(F) snd_seq(F) usbhid snd_seq_device(F) hid snd_timer(F) snd(F) soundcore(F) i7core_edac nvidia(POF) mac_hid lpc_ich microcode(F) serio_raw(F) edac_core lp(F) parport(F) pata_acpi r8169 pata_jmicron ahci(F) libahci(F)
[    3.634684] Pid: 442, comm: modprobe Tainted: PF          O 3.8.0-19-generic #30-Ubuntu Gigabyte Technology Co., Ltd. P55-USB3/P55-USB3
[    3.634788] RIP: 0010:[<ffffffffa0b33820>]  [<ffffffffa0b33820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[    3.635612] Process modprobe (pid: 442, threadinfo ffff880210ba4000, task ffff880210b51740)
[    3.636586]  [<ffffffffa0ab6186>] snd_hda_codec_configure+0x146/0x440 [snd_hda_codec]
[    3.636694]  [<ffffffffa00822f0>] azx_probe_continue+0x3a0/0x4f0 [snd_hda_intel]
[    3.636800]  [<ffffffffa00808b0>] ? azx_attach_pcm_stream+0x1e0/0x1e0 [snd_hda_intel]
[    3.636906]  [<ffffffffa0081cb0>] ? azx_halt+0x30/0x30 [snd_hda_intel]
[    3.636985]  [<ffffffffa00806d0>] ? azx_pcm_trigger+0x580/0x580 [snd_hda_intel]
[    3.637090]  [<ffffffffa0081810>] ? azx_runtime_suspend+0x30/0x30 [snd_hda_intel]
[    3.637195]  [<ffffffffa007e670>] ? azx_pcm_free+0x50/0x50 [snd_hda_intel]
[    3.637276]  [<ffffffffa008279a>] azx_probe+0x35a/0x940 [snd_hda_intel]
[    3.637357]  [<ffffffff8137b4cb>] local_pci_probe+0x4b/0x80
[    3.637433]  [<ffffffff8137b7f1>] pci_device_probe+0x111/0x120
[    3.637511]  [<ffffffff81455717>] driver_probe_device+0x77/0x230
[    3.637664]  [<ffffffff814558d0>] ? driver_probe_device+0x230/0x230
[    3.638272]  [<ffffffffa008901e>] azx_driver_init+0x1e/0x1000 [snd_hda_intel]
[    3.641139] RIP  [<ffffffffa0b33820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
sudo: /etc/init.d/sl-modem-daemon: command not found
	Release Date: 08/10/2010
		Serial services are supported (int 14h)
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: P55-USB3
	Serial Number:  
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: P55-USB3
	Serial Number:  
	Manufacturer: Gigabyte Technology Co., Ltd.
	Serial Number:  
	Manufacturer: Intel
	Serial Number:  
	Port Type: Serial Port 16450 Compatible
	Port Type: Serial Port 16450 Compatible
	Manufacturer:  
	Serial Number:  
	Manufacturer:  
	Serial Number:  
	Manufacturer:  
	Serial Number:  
	Manufacturer:  
	Serial Number:  
snd_seq_dummy          12798  0 
snd_hda_codec_hdmi     36913  2 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          61623  1 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
usbhid                 47074  0 
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
hid                   101002  2 hid_generic,usbhid
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer

```

And finally, here is the output of the alsa-info.sh script:
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.61
!!################################


!!Script ran on: Fri May  3 21:16:19 UTC 2013




!!Linux Distribution
!!------------------


Ubuntu 13.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 13.04" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 13.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      P55-USB3
Product Version:    
Firmware Version:  F8




!!Kernel Information
!!------------------


Kernel release:    3.8.0-19-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.8.0-19-generic
Library version:    1.0.25
Utilities version:  1.0.25




!!Loaded ALSA modules
!!-------------------


snd_hda_intel




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xfbff8000 irq 51




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: NVIDIA Corporation GF104 High Definition Audio Controller (rev a1)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1b.0 0403: 8086:3b56 (rev 06)
    Subsystem: 1458:a002
--
01:00.1 0403: 10de:0beb (rev a1)
    Subsystem: 1462:2381




!!Modprobe options (Sound related)
!!--------------------------------


snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: Realtek ALC892
Address: 2
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0892
Subsystem Id: 0x1458a002
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x2e 0x2e]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x1c 0x1c]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC892 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Control: name="SPDIF Phantom Jack", index=0, device=0
  Pincap 0x00000014: OUT Detect
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Out Front Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Out Surround Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011412: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Line Out CLFE Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016411: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Out Side Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012414: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c50: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=07, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=06, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Line Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181345f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=08, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Headphone Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Control: name="SPDIF Phantom Jack", index=1, device=0
  Pincap 0x00000014: OUT Detect
  Pin Default 0x014b6130: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Control: name="SPDIF In Phantom Jack", index=0, device=0
  Pincap 0x00000024: IN Detect
  Pin Default 0x01cb7170: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = Yellow
    DefAssociation = 0x7, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x2e 0x2e]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x25 0x0b
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw---T+ 1 root audio 116,  8 May  3 17:03 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  7 May  3 17:03 /dev/snd/hwC0D2
crw-rw---T+ 1 root audio 116,  6 May  3 17:03 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  5 May  3 17:03 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  4 May  3 17:03 /dev/snd/pcmC0D1c
crw-rw---T+ 1 root audio 116,  3 May  3 17:03 /dev/snd/pcmC0D1p
crw-rw---T+ 1 root audio 116,  2 May  3 17:03 /dev/snd/pcmC0D2c
crw-rw---T+ 1 root audio 116,  1 May  3 17:02 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 May  3 17:02 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  3 17:03 .
drwxr-xr-x 3 root root 240 May  3 17:03 ..
lrwxrwxrwx 1 root root  12 May  3 17:03 pci-0000:00:1b.0 -> ../controlC0




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 2: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [MID]


Card hw:0 'MID'/'HDA Intel MID at 0xfbff8000 irq 51'
  Mixer name    : 'Realtek ALC892'
  Components    : 'HDA:10ec0892,1458a002,00100302'
  Controls      : 53
  Simple ctrls  : 20
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 46 [72%] [-18.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 28 [61%] [12.00dB] [on]
  Front Right: Capture 28 [61%] [12.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]




!!Alsactl output
!!--------------


--startcollapse--
state.MID {
    control.1 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 64
        value.1 64
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Front Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 -6400
            dbvalue.1 -6400
        }
    }
    control.4 {
        iface MIXER
        name 'Surround Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Center Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 -6400
        }
    }
    control.6 {
        iface MIXER
        name 'LFE Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 -6400
        }
    }
    control.7 {
        iface MIXER
        name 'Center Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.8 {
        iface MIXER
        name 'LFE Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.9 {
        iface MIXER
        name 'Side Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 -6400
            dbvalue.1 -6400
        }
    }
    control.10 {
        iface MIXER
        name 'Side Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.11 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 64
        value.1 64
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.12 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.13 {
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.14 {
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.15 {
        iface MIXER
        name 'Rear Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.16 {
        iface MIXER
        name 'Rear Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.17 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.18 {
        iface MIXER
        name 'Line Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.19 {
        iface MIXER
        name 'Auto-Mute Mode'
        value Enabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.20 {
        iface MIXER
        name 'Front Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.21 {
        iface MIXER
        name 'Rear Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.22 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.23 {
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.24 {
        iface MIXER
        name 'Capture Volume'
        value.0 28
        value.1 28
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 46'
            dbmin -1600
            dbmax 3000
            dbvalue.0 1200
            dbvalue.1 1200
        }
    }
    control.25 {
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 46'
            dbmin -1600
            dbmax 3000
            dbvalue.0 -1600
            dbvalue.1 -1600
        }
    }
    control.26 {
        iface MIXER
        name 'Input Source'
        value 'Front Mic'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Front Mic'
            item.1 'Rear Mic'
            item.2 Line
        }
    }
    control.27 {
        iface MIXER
        name 'Input Source'
        index 1
        value 'Front Mic'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Front Mic'
            item.1 'Rear Mic'
            item.2 Line
        }
    }
    control.28 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.29 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.30 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.31 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.33 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'IEC958 Capture Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.35 {
        iface MIXER
        name 'Master Playback Volume'
        value 46
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 -1800
        }
    }
    control.36 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.37 {
        iface CARD
        name 'Line Out Front Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.38 {
        iface CARD
        name 'Line Out Surround Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.39 {
        iface CARD
        name 'Line Out CLFE Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.40 {
        iface CARD
        name 'Line Out Side Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.41 {
        iface CARD
        name 'Front Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.42 {
        iface CARD
        name 'Front Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.43 {
        iface CARD
        name 'Rear Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.44 {
        iface CARD
        name 'Line Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.45 {
        iface CARD
        name 'SPDIF Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.46 {
        iface CARD
        name 'SPDIF Phantom Jack'
        index 1
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.47 {
        iface CARD
        name 'SPDIF In Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.48 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access read
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
    control.49 {
        iface PCM
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.50 {
        iface PCM
        device 1
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.51 {
        iface PCM
        device 1
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.52 {
        iface PCM
        device 2
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.53 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
}
--endcollapse--




!!All Loaded Modules
!!------------------


Module
snd_hda_codec_hdmi
bnep
rfcomm
bluetooth
binfmt_misc
snd_hda_codec_realtek
snd_hda_intel
coretemp
kvm_intel
snd_hda_codec
kvm
snd_hwdep
joydev
snd_pcm
ppdev
hid_generic
gpio_ich
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
parport_pc
snd_rawmidi
snd_seq
usbhid
snd_seq_device
hid
snd_timer
snd
soundcore
i7core_edac
nvidia
mac_hid
lpc_ich
microcode
serio_raw
edac_core
lp
parport
pata_acpi
r8169
pata_jmicron
ahci
libahci




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D2/init_pin_configs:
0x11 0x99430140
0x12 0x411111f0
0x14 0x01014410
0x15 0x01011412
0x16 0x01016411
0x17 0x01012414
0x18 0x01a19c50
0x19 0x02a19c60
0x1a 0x0181345f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4005e601
0x1e 0x014b6130
0x1f 0x01cb7170


/sys/class/sound/hwC0D2/driver_pin_configs:


/sys/class/sound/hwC0D2/user_pin_configs:


/sys/class/sound/hwC0D2/init_verbs:




!!ALSA/HDA dmesg
!!--------------


[    2.679736] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[    2.693397] snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
[    2.696196] lp0: using parport0 (interrupt-driven).
[    2.834532] input: HDA Intel MID Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    2.834600] input: HDA Intel MID Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    2.834752] input: HDA Intel MID Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    2.834796] input: HDA Intel MID Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    2.834837] input: HDA Intel MID Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    2.834878] input: HDA Intel MID Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    2.834920] input: HDA Intel MID Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    2.834966] input: HDA Intel MID Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    2.835416] hda_intel: Disabling MSI
[    2.835423] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    2.875353] init: failsafe main process (861) killed by TERM signal
--
[    3.632479] BUG: unable to handle kernel paging request at ffff88021320ffe0
[    3.632604] IP: [<ffffffffa0b33820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[    3.632699] PGD 1c0e063 PUD df7ce067 PMD 21014a063 PTE 800000021320f161
[    3.632887] Oops: 0003 [#1] SMP 
[    3.632997] Modules linked in: snd_hda_codec_hdmi bnep rfcomm bluetooth binfmt_misc(F) snd_hda_codec_realtek snd_hda_intel(+) coretemp kvm_intel snd_hda_codec kvm snd_hwdep(F) joydev(F) snd_pcm(F) ppdev(F) hid_generic gpio_ich snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) parport_pc(F) snd_rawmidi(F) snd_seq(F) usbhid snd_seq_device(F) hid snd_timer(F) snd(F) soundcore(F) i7core_edac nvidia(POF) mac_hid lpc_ich microcode(F) serio_raw(F) edac_core lp(F) parport(F) pata_acpi r8169 pata_jmicron ahci(F) libahci(F)
[    3.634643] CPU 0 
[    3.634684] Pid: 442, comm: modprobe Tainted: PF          O 3.8.0-19-generic #30-Ubuntu Gigabyte Technology Co., Ltd. P55-USB3/P55-USB3
[    3.634788] RIP: 0010:[<ffffffffa0b33820>]  [<ffffffffa0b33820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[    3.634888] RSP: 0018:ffff880210ba5ac0  EFLAGS: 00010283
--
[    3.636515] Call Trace:
[    3.636586]  [<ffffffffa0ab6186>] snd_hda_codec_configure+0x146/0x440 [snd_hda_codec]
[    3.636694]  [<ffffffffa00822f0>] azx_probe_continue+0x3a0/0x4f0 [snd_hda_intel]
[    3.636800]  [<ffffffffa00808b0>] ? azx_attach_pcm_stream+0x1e0/0x1e0 [snd_hda_intel]
[    3.636906]  [<ffffffffa0081cb0>] ? azx_halt+0x30/0x30 [snd_hda_intel]
[    3.636985]  [<ffffffffa00806d0>] ? azx_pcm_trigger+0x580/0x580 [snd_hda_intel]
[    3.637090]  [<ffffffffa0081810>] ? azx_runtime_suspend+0x30/0x30 [snd_hda_intel]
[    3.637195]  [<ffffffffa007e670>] ? azx_pcm_free+0x50/0x50 [snd_hda_intel]
[    3.637276]  [<ffffffffa008279a>] azx_probe+0x35a/0x940 [snd_hda_intel]
[    3.637357]  [<ffffffff8137b4cb>] local_pci_probe+0x4b/0x80
--
[    3.638194]  [<ffffffff8137a6bc>] __pci_register_driver+0x4c/0x50
[    3.638272]  [<ffffffffa008901e>] azx_driver_init+0x1e/0x1000 [snd_hda_intel]
[    3.638353]  [<ffffffff8100215a>] do_one_initcall+0x12a/0x180
--
[    3.638744] Code: 0f 1f 00 4d 8b bc 24 c0 00 00 00 25 00 e0 00 00 c1 e8 0c 83 c8 01 49 63 17 83 c0 01 83 f8 10 48 8d 14 92 49 8d 14 d7 48 8d 72 08 <66> 89 5a 08 c7 46 08 02 00 00 00 0f 86 5b 02 00 00 48 8d 4e 18 
[    3.641139] RIP  [<ffffffffa0b33820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[    3.641280]  RSP <ffff880210ba5ac0>

```

I've been looking for what to do for about 2 days now.  Can someone point me in the right direction?

---

### Post by pqwoerituytrueiwoq on 2013-05-03
give this a try
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme) (most likely the fix you want)
if that does not work there is this
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

### Post by Tbone2010 on 2013-05-03
What exactly does this do? What problem is this supposed to fix?  It's not that I don't trust you, I just want to understand what's going on.

Edit: Now that I've run it, I see that it updates the kernel.  After rebooting, I get this:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This is a step in the right direction, but I'm still not there yet.  I've looked in alsamixer to make sure all of my channels are unmuted, but the problem lies with Pulse.  If I run ```
 pavucontrol 
``` it opens the window but says "connection to pulseaudio failed".  When I run ```
 pulseaudio 
``` in the terminal I get this output:```

W: [pulseaudio] sink.c: Default and alternate sample rates are the same.
E: [pulseaudio] module.c: Failed to load module "module-alsa-source" (argument: "device=hw:0,3"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

```


From this I gather that there is an error in /etc/pulse/default.pa, so here is what mine looks like: ```

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.


# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)


.nofail


### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav


.fail


### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore


### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties


### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
load-module module-alsa-sink
load-module module-alsa-source device=hw:0,3
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
# added to try to get sound working over Nvidia card HDMI
load-module module-alsa-sink device=hw:0,3,7,8,9


### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect use_ucm=0
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif


### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif


### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif


.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif


### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix


### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish


### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv


### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor


### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore


### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams


### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink


### Honour intended role device property
load-module module-intended-roles


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle


### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif


### Enable positioned event sounds
load-module module-position-event-sounds


### Cork music/video streams when a phone stream is active
#load-module module-role-cork


### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply


### Load DBus protocol
#.ifexists module-dbus-protocol.so
#load-module module-dbus-protocol
#.endif


# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.


### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system


### Register ourselves in the X11 session manager
#load-module module-x11-xsmp


### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif


load-module module-switch-on-port-available


### Make some devices default
#set-default-sink output
#set-default-source input



```

---

### Post by Tbone2010 on 2013-05-03
Ok, so I got it to play a test sound by commenting out a line I had put in /etc/pulse/default.pa to try to get it to recognize my sound device built-in to the graphics card, and changing the ```
load-module module-alsa-source device=hw:0,3
``` line to ```
load-module module-alsa-source device=hw:0,1
```.  However, I still have no sound when I play a video in YouTube.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
Then this is what you need: (1st code box)
[http://ubuntuforums.org/showthread.php?t=1926721&page=2#19](http://ubuntuforums.org/showthread.php?t=1926721&page=2#19)

The 1st link is a install/update checker for the mainline kernel, there have been issues with the raring kernel breaking hdmi audio since a 1wwek before it was released
on my desktop i have a high probability of not even being able to boot on the raring stock kernel, it also breaks my hdmi audio (i don't use it i stick with analog, hdmi sound is not worth the trouble, there is always something that does not work)

---

