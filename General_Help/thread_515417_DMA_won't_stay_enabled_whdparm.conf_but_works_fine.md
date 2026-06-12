---
title: "DMA won't stay enabled w/hdparm.conf but works fine started by hand"
date: 2007-08-01
forum: General Help
---

### Post by Terry of Astoria on 2007-08-01
(edit: I discovered my hard drive was going bad . . .)

DMA won't stay enabled w/hdparm.conf but works fine started by hand


I have Feisty which has been upgraded all the way from Breezy. I love this machine and I'm giving it to a friend now. While checking everything out and preparing it, I discovered that **DMA won't stay enabled for my /dev/hda. **  I have a /dev/hdd too, and it automagically is already DMA-enabled. 
 
I already posted in this thread, but no response in two days, and my friend wants his Ubuntu -
 [http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive](http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive)
 Please, bear with me:
```

me@maestro:~$ sudo hdparm -I /dev/hda |grep ‘DMA:’
Password:
me@maestro:~$ 

```
++(There's no response.) OK. So I tried the suggestion beneath, "- To view all the information about your drive run: sudo hdparm –I /dev/hda"
```

me@maestro:~$ sudo hdparm –I /dev/hda
–I: No such file or directory
me@maestro:~$ 

```

++OK, maybe use a hyphen instead of a dash. . .
```

me@maestro:~$ sudo hdparm -I /dev/hda

/dev/hda:

ATA device, with non-removable media
        Model Number:       WDC WD400BB-53AUA1                      
        Serial Number:      WD-WMA6R2202166
        Firmware Revision:  18.20D18
Standards:
        Supported: 5 4 3 
        Likely used: 6
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   78165360
        device size with M = 1024*1024:       38166 MBytes
        device size with M = 1000*1000:       40020 MBytes (40 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 40
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *  
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
                Automatic Acoustic Management feature set
Security: 
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
        Integrity word not set (found 0xa53e, expected 0x100a5)
me@maestro:~$ 


```

OK yes it is a Western Digital Caviar drive. The post says setting multiple sector count can slow them down.
-Also What is a "Integrity word not set (found 0xa53e, expected 0x100a5)"
And according to the post, the star by udma5 means we can use udma5.

Now here is the funny part. here we go, set DMA on from CLI:
```

me@maestro:~$ sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
me@maestro:~$ 

```
And it works. Disk access is about ten times as fast as before issuing the command.
So, still following [http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive](http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive) ,
I try to set it to stay on after booting by editing /etc/hdparm.conf and adding 

```

/dev/hda {
        dma = on
        }

```


Since I have no scsi or sata drives, I can't use the other options. Anyway DMA continues to REFUSE to be enabled upon reboot . . .
Until I enable it by hand again as I described above.
Any thoughts?

Current output of hdparm before hand-enabling DMA [after enabling, DMA is listed as 1 (on)]: 
```

me@maestro:~$ hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78165360, start = 0
me@maestro:~$ hdparm /dev/hdd

/dev/hdd:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488397168, start = 0
me@maestro:~$ 


```

I thought of making a script to run the enabling command after boot, but I thought that's what /etc/hdparm is . . .
I don't want to make my friend type something every time he wants to move files to his flash drive . . . :-)
:) ( I want regular old ascii smilies for Christmas, along with WORLD PEACE - whatever . . .) 
;-)
:)
:-)

---

### Post by Terry of Astoria on 2007-08-02
Is anything wrong?
```

## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -s Turn on/off power on in standby mode
#poweron_standby = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

/dev/hda {
        dma = on
        }
```

---

### Post by squaregoldfish on 2007-11-11
Try the following and see if it works:

sudo update-rc.d hdparm defaults

The hdparm startup script is what reads the hdparm.conf file, but it doesn't seem to be enabled by default.

Steve.

---

### Post by kerry_s on 2007-11-11
i put mine in /etc/rc.local.

---

### Post by Terry of Astoria on 2007-11-12
I discovered my drive was about to die. It's all fixed now.

---

