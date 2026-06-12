---
title: "help with grub (problem started after edgy)"
date: 2006-12-03
forum: General Help
---

### Post by ubuntu27 on 2006-12-03
Hello.
I helped installing Ubuntu to a friend's comp. The install was successful. 
But, the problem begun when we upgrade it to edgy from dapper.

He no longer can boot Windows. 

here is the: sudo fdisk -l


```
Disco /dev/sda: 80.0 GB, 80026361856 bytes

255 cabezas, 63 sectores/pista, 9729 cilindros

Unidades = cilindros de 16065 * 512 = 8225280 bytes



Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema

/dev/sda1               1        3693    29663991   83  Linux

/dev/sda2            3825        9728    47423880    f  W95 Ext'd (LBA)

/dev/sda3            3694        3824     1052257+  82  Linux swap / Solaris

/dev/sda5            3825        9728    47423848+   7  HPFS/NTFS



Las entradas de la tabla de particiones no están en el orden del disco
```


AND THIS IS THE result of "cat /etc/fstab"

```
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1 -- converted during upgrade to edgy

UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b / ext3 defaults,errors=remount-ro 0 1

# /dev/sda5 -- converted during upgrade to edgy

UUID=1E6C75506C7523A5 /media/windows2003 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/sda3 -- converted during upgrade to edgy

UUID=139cb531-9b19-4523-a057-cdf32d468f6b none swap sw 0 0

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


Any help please :)


AFTER WE'VE INSTALLED DAPPER (with Desktop CD), THERE WAS NO GRUB TO BEGIN WITH.

---

### Post by tristam77 on 2006-12-03
Hi,

add 
```
title		Microsoft Windows Server 2003
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
to /boot/grub/menu.lst

You could change the timeout value to 10

---

### Post by igknighted on 2006-12-03
GRUB is installed, otherwise Ubuntu wouldn't boot.  FSTAB only has to with mounting discs once Ubuntu is booted, so it really isnt relevant here.  I would be curious to see your /boot/grub/menu.lst file.  My first thought is that grub ndoesnt show the choices because Ubuntu defaults to a hidden grub menu... there should be a screen after the POST and before the Ubuntu splash that says to press escape for the GRUB menu.  If Windows is not on that menu, you will need to add it in the menu.lst file in a way similar to what tristam just posted.

---

### Post by bulldog on 2006-12-03
Yes curious indeed at you menu.lst.

If you manage to boot windows again in this configuration,I have to reconsider some assumptions I made..........:cool:

Still waiting for your menu.lst```
cat /boot/grub/menu.lst
```

[bookmarked this one]

---

### Post by ubuntu27 on 2006-12-03
```
001. # menu.lst - See: grub(8), info grub, update-grub(8)
002. #            grub-install(8), grub-floppy(8),
003. #            grub-md5-crypt, /usr/share/doc/grub
004. #            and /usr/share/doc/grub-doc/.
005. 
006. ## default num
007. # Set the default entry to the entry number NUM. Numbering starts from 0, and
008. # the entry number 0 is the default if the command is not used.
009. #
010. # You can specify 'saved' instead of a number. In this case, the default entry
011. # is the entry saved with the command 'savedefault'.
012. # WARNING: If you are using dmraid do not change this entry to 'saved' or your
013. # array will desync and will not let you boot your system.
014. default		0
015. 
016. ## timeout sec
017. # Set a timeout, in SEC seconds, before automatically booting the default entry
018. # (normally the first entry defined).
019. timeout		3
020. 
021. ## hiddenmenu
022. # Hides the menu by default (press ESC to see the menu)
023. hiddenmenu
024. 
025. # Pretty colours
026. #color cyan/blue white/blue
027. 
028. ## password ['--md5'] passwd
029. # If used in the first section of a menu file, disable all interactive editing
030. # control (menu entry editor and command-line)  and entries protected by the
031. # command 'lock'
032. # e.g. password topsecret
033. #      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
034. # password topsecret
035. 
036. #
037. # examples
038. #
039. # title		Windows 95/98/NT/2000
040. # root		(hd0,0)
041. # makeactive
042. # chainloader	+1
043. #
044. # title		Linux
045. # root		(hd0,1)
046. # kernel	/vmlinuz root=/dev/hda2 ro
047. #
048. 
049. #
050. # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
051. 
052. ### BEGIN AUTOMAGIC KERNELS LIST
053. ## lines between the AUTOMAGIC KERNELS LIST markers will be modified
054. ## by the debian update-grub script except for the default options below
055. 
056. ## DO NOT UNCOMMENT THEM, Just edit them to your needs
057. 
058. ## ## Start Default Options ##
059. ## default kernel options
060. ## default kernel options for automagic boot options
061. ## If you want special options for specific kernels use kopt_x_y_z
062. ## where x.y.z is kernel version. Minor versions can be omitted.
063. ## e.g. kopt=root=/dev/hda1 ro
064. ##      kopt_2_6_8=root=/dev/hdc1 ro
065. ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
066. # kopt=root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro
067. 
068. ## default grub root device
069. ## e.g. groot=(hd0,0)
070. # groot=(hd0,0)
071. 
072. ## should update-grub create alternative automagic boot options
073. ## e.g. alternative=true
074. ##      alternative=false
075. # alternative=true
076. 
077. ## should update-grub lock alternative automagic boot options
078. ## e.g. lockalternative=true
079. ##      lockalternative=false
080. # lockalternative=false
081. 
082. ## additional options to use with the default boot option, but not with the
083. ## alternatives
084. ## e.g. defoptions=vga=791 resume=/dev/hda5
085. # defoptions=quiet splash
086. 
087. ## should update-grub lock old automagic boot options
088. ## e.g. lockold=false
089. ##      lockold=true
090. # lockold=false
091. 
092. ## altoption boot targets option
093. ## multiple altoptions lines are allowed
094. ## e.g. altoptions=(extra menu suffix) extra boot options
095. ##      altoptions=(recovery) single
096. # altoptions=(recovery mode) single
097. 
098. ## controls how many kernels should be put into the menu.lst
099. ## only counts the first occurence of a kernel, not the
100. ## alternative kernel options
101. ## e.g. howmany=all
102. ##      howmany=7
103. # howmany=all
104. 
105. ## should update-grub create memtest86 boot option
106. ## e.g. memtest86=true
107. ##      memtest86=false
108. # memtest86=true
109. 
110. ## should update-grub adjust the value of the default booted system
111. ## can be true or false
112. # updatedefaultentry=false
113. 
114. ## ## End Default Options ##
115. 
116. title		Ubuntu, kernel 2.6.17-10-386
117. root		(hd0,0)
118. kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro quiet splash
119. initrd		/boot/initrd.img-2.6.17-10-386
120. savedefault
121. boot
122. 
123. title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
124. root		(hd0,0)
125. kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro single
126. initrd		/boot/initrd.img-2.6.17-10-386
127. boot
128. 
129. title		Ubuntu, kernel 2.6.15-26-386
130. root		(hd0,0)
131. kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro quiet splash
132. initrd		/boot/initrd.img-2.6.15-26-386
133. savedefault
134. boot
135. 
136. title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
137. root		(hd0,0)
138. kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro single
139. initrd		/boot/initrd.img-2.6.15-26-386
140. boot
141. 
142. title		Ubuntu, memtest86+
143. root		(hd0,0)
144. kernel		/boot/memtest86+.bin
145. boot
146. 
147. ### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by ubuntu27 on 2006-12-03
A got Error22
after I've added 

```
title		Microsoft Windows Server 2003
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

to the menu.lst

```
114. ## ## End Default Options ##
115. 
116. title		Ubuntu, kernel 2.6.17-10-386
117. root		(hd0,0)
118. kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro quiet splash
119. initrd		/boot/initrd.img-2.6.17-10-386
120. savedefault
121. boot
122. 
123. title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
124. root		(hd0,0)
125. kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro single
126. initrd		/boot/initrd.img-2.6.17-10-386
127. boot
128. 
129. title		Ubuntu, kernel 2.6.15-26-386
130. root		(hd0,0)
131. kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro quiet splash
132. initrd		/boot/initrd.img-2.6.15-26-386
133. savedefault
134. boot
135. 
136. title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
137. root		(hd0,0)
138. kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=1fb4bed9-988b-419d-8cdd-92754e11c52b ro single
139. initrd		/boot/initrd.img-2.6.15-26-386
140. boot
141. 
142. title		Ubuntu, memtest86+
143. root		(hd0,0)
144. kernel		/boot/memtest86+.bin
145. boot
146. 
147. title		Microsoft Windows Server 2003
148. root		(hd0,5)
149. savedefault
150. makeactive
151. chainloader	+1
152. 
153. ### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by tristam77 on 2006-12-03
OK, you say one thing and paste another ;P
> 147. title		Microsoft Windows Server 2003
148. root		(hd0,5)
149. savedefault
150. makeactive
151. chainloader	+1

148 Should be either root (hd0,0), or root (hd0,4)

Grubs error 22 means "No such partition" as sda6 does not exist.

What happens when root (hd0,0) is used?

---

### Post by ubuntu27 on 2006-12-03
> What happens when root (hd0,0) is used?

When I put (hd0,0)

it simply dosn't give me any errors, intead it runs Ubuntu and not windows.


SEE attachment, so you could see how ti looks like from the gparted. (it seems different from the output of fdisk)

---

### Post by tristam77 on 2006-12-03
One should place the entries outside the "DEBIAN AUTOMAGIC KERNELS LIST" section, but that would not solve the problem.

You could add ```

title Microsoft Windows Server 2003 part 5
root (hd0,5)
savedefault
makeactive
chainloader +1

```
and choose that option after POST

When those choices in the GRUB boot menu do not boot Ubuntu you could proceed with the following.

Warning, you could end up with an unbootable system or lose all data!
I suggest reinstalling the windows bootloader with the recovery console (run fixmbr) and 
[reinstalling grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). This is timeconsuming and not trivial; I suggest printing out the instructions.

---

### Post by bulldog on 2006-12-03
The reason I'm curious if windows will start in this configuration is the fact that I always presumed windows should be on the first primary partition.

By my knowing it should be so because windows writes the boot files on the first partition.

In this case it can't be done because it's an ext3 partition.

Reinstalling GRUB won't work because GRUB is fine as it is.
fixmbr and fixboot will not work either,at least I think so,but you can give it a try.
You will over write GRUB in that case,so to boot ubuntu again you'll have to install GRUB from the live cd.

---

### Post by tristam77 on 2006-12-03
> **bulldog said:**
> By my knowing it should be so because windows writes the boot files on the first partition.


Windows can be on any partition. The Master Boot Record ([MBR]("http://en.wikipedia.org/wiki/Mbr")) is separate from the partitions and has some code pointing to where to boot from.

It is however recommanded to leave an operating system on the partition you installed it on, especially with linux (think of fstab...)

---

### Post by bulldog on 2006-12-03
> **tristam77 said:**
> Windows can be on any partition. The Master Boot Record ([MBR]("http://en.wikipedia.org/wiki/Mbr")) is separate from the partitions and has some code pointing to where to boot from.

It is however recommanded to leave an operating system on the partition you installed it on, especially with linux (think of fstab...)

Well,I don't agree to that one without a fight :D 
For instance if you have installed win98 on the c:\ partition and you want to install windowsXP,you can install XP anywhere you want because it can write it's boot files to the c:\ partition.

But as said,I can be wrong on this,so I follow this thread to see if windows will boot again.

Maybe OP can take a look at the windows partition from within ubuntu and check if there are some file listed.
boot.ini--NTDETECT.COM--ntldr.

---

### Post by ubuntu27 on 2006-12-03
Thank you guys.
The guy (the owner of the comp)

Is already tired of trying everything tha t I have told him to do.

I have changed all the (hd0,x) 

and, even tried

sudo aptitude install grub (thinking grub wasn't installed)

, We've tried also to restore the GRUB, using the desktop CD.

I've tried every how-to on the web. 

Anyway,

We decided to re-install Ubuntu again.
Hope that will restore the GRUB. :)


PS: HE HAS TWO HARD DRIVES.

---

### Post by bulldog on 2006-12-03
Stop!
If you have two hdd's try to boot from the other disk by changing it in the BIOS.
The change that GRUB is on the other disk is very likely!!

Why didn't you say he had two hard disks? this is important info you have to give!!

Why didn't we see the second hdd in any of your postings?

---

### Post by ubuntu27 on 2006-12-03
> **bulldog said:**
> Stop!
If you have two hdd's try to boot from the other disk by changing it in the BIOS.
The change that GRUB is on the other disk is very likely!!

Why didn't you say he had two hard disks? this is important info you have to give!!

Why didn't we see the second hdd in any of your postings?


Sorry about that :( 
forgot to metnion about the HD.

ANyway, he just reinstalled UBuntu


He couldn't run WIndows again.


EDIT:  He says that he actually dosn't have two HD. Just one.

OMG! He is so mad. I feel like our friendship is at the stake... :(


He want to unistall UBuntu now. 
IS there a way to do that?

---

### Post by bulldog on 2006-12-03
Well sorry about that.

But I think I will not reconsider my presumptions,that if windows isn't on the first primary,you should have a small partition at the beginning of your disk for the windows bootfiles.

I can only advice to copy any valuable data from the disk and start from scratch,installing windows on the first primary.
Then install ubuntu.

Uninstall ubuntu is done by formatting the partitions.
But windows will not boot,in case he think so.
You can try to format the first partition to NTFS or FAT32 and run the windows install disk into the recovery mode and do a fixboot and fixmbr.
Maybe you can windows get running again if you do so.

---

### Post by ubuntu27 on 2006-12-03
> **bulldog said:**
> Well sorry about that.

But I think I will not reconsider my presumptions,that if windows isn't on the first primary,you should have a small partition at the beginning of your disk for the windows bootfiles.

I can only advice to copy any valuable data from the disk and start from scratch,installing windows on the first primary.
Then install ubuntu.

He dosn't have a CD burner. O I don't know how can he backup his files...
Any, web-backup solutions, maybe?

Maybe, he could move the windows partition to the left (to the first)...
I seriously don't have idea.

---

### Post by bulldog on 2006-12-03
Read my previous post I have edit some info you can try.

To get to the recovery console,
Boot the windows install cd and let it run till you get three options.
1:Install windows
2:Repair a windows install
3:Exit without installing

Choose option 2 (R) you will go to a console where your windows is listed.
You have to provide the admin password if there's any.
Than type fixboot and enter and type than fixmbr and enter again.
You'll get a warning but ignore it.

Than exit the cd and try to boot the hdd into windows.

Good Luck.

---

### Post by ubuntu27 on 2006-12-03
> **bulldog said:**
> Read my previous post I have edit some info you can try.

To get to the recovery console,
Boot the windows install cd and let it run till you get three options.
1:Install windows
2:Repair a windows install
3:Exit without installing

Choose option 2 (R) you will go to a console where your windows is listed.
You have tp provide the admin password if there's any.
Than type fixboot and enter and type than fixmbr and enter again.
You'll get a warning but ignore it.

Than exit the cd and try to boot the hdd into windows.

Good Luck.

Thank you.

BUt, he dosn't have WIndwos CD

---

### Post by bulldog on 2006-12-03
> **ubuntu27 said:**
> Thank you.

BUt, he dosn't have WIndwos CD

Well you can download the resue cd which can do the same but you need a cd burner.
Take a look here maybe it can help you out,

[http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector](http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector)

---

### Post by ubuntu27 on 2006-12-03
> **bulldog said:**
> Well you can download the resue cd which can do the same but you need a cd burner.
Take a look here maybe it can help you out,

[http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector](http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector)

Thank you bulldog.

He dosn't even have a CD Burner... :( 
And, no, he canot buy it. It's too expensive over there.

---

### Post by frying_fish on 2006-12-03
Firstly:

Windows CAN be installed on ANY partition in a system.  I have previously had windows main partition as the 7th partition on a device (yes there was an extended one in between it and the other primary partitions)  so that is not an issue.

the "C:\" stuff is just what windows will want to think, windows can install itself to what it classes as D:\ or E:\ or WHATEVER:\  its all the same to it.

Secondly,  try and run the windows fixboot stuff from a rescue cd to see if you can get windows to boot.  If that works then go and re-install grub from the desktop cd using the wiki guide for grub recovery.


Thirdly, make sure you have all the partitions correctly setup within grub.

---

### Post by bulldog on 2006-12-04
> **frying_fish said:**
> Firstly:

Windows CAN be installed on ANY partition in a system.  I have previously had windows main partition as the 7th partition on a device (yes there was an extended one in between it and the other primary partitions)  so that is not an issue.

the "C:\" stuff is just what windows will want to think, windows can install itself to what it classes as D:\ or E:\ or WHATEVER:\  its all the same to it.

Secondly,  try and run the windows fixboot stuff from a rescue cd to see if you can get windows to boot.  If that works then go and re-install grub from the desktop cd using the wiki guide for grub recovery.


Thirdly, make sure you have all the partitions correctly setup within grub.

Thank you frying_fish,maybe you should read and understand the topic?
There's no windows cd,there's no cd burner,and the first partition is now the fifth and will not boot.
All you suggest is tryed and **not** working.

And your statement'windows will boot from any partition' I heard before,but nobody can tell me how.
Maybe you can?I'm very curious about how it's done.

Thanks in advance.

---

### Post by ubuntu27 on 2006-12-04
Thanks to all of you guys&girls.

So far, we still haven't fixed the problem yet.

If you have any tip, or any ideas, that will be helpful. Don't hesitate :)

Thank you!

---

### Post by bulldog on 2006-12-04
Send you an email but look at this topic you should be able to alter the boot.ini file in the windows partition,so you can boot windows again.

And with a little luck you should be able to create a boot floppy for your windows.

[http://ubuntuforums.org/showthread.php?t=310906](http://ubuntuforums.org/showthread.php?t=310906)

---

