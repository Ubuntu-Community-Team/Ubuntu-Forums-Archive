---
title: "Installation S.M.A.R.T"
date: 2015-10-09
forum: General Help
---

### Post by dex3 on 2015-10-09
Hey guys long story short I was formatting my drive.. and now when I boot my computer I get a s.m.a.r.t error.. I' have installed Ubuntu onto the drive.. I boot the computer I get the screen with S.M.A.R.T.. I press enter.. Ubuntu boots up.. it comes up with an error saying "Ubuntu 14.04 Has experienced an internal error, executablepath /usr/bin/signon-ui.. As well as more errors keep popping up (internal error).. I am unable to access firefox.. it seems as if Ubuntu isn't properly installed to the drive.. Is there anyway I can fix my S.M.A.R.T error.. I've done some googling and it suggests that my drive has failed.. but this didn't happen until I started formatting/partitioning my drive.

---

### Post by Bashing-om on 2015-10-09
dex3; Yuk ...

Tough call, one must isolate to either a hardware problem or a software issue.

If it were me I would run the full barrage of SMART's tests. Making sure it is not hardware.
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)
[https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results](https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results)
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)

If the hard drive is good, then the next is to wipe that drive ... 'dd' will do that .
Verify the .iso download file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
And once the .iso is burned, verify that burn:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Then I would next partition the hard drive for my use case and 

RE-install 'buntu .
[INDENT][INDENT][INDENT]been there
[INDENT][INDENT][INDENT]done that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-09
dex3; Hey ;

Check that you have the tool installed:
issue terminal command:
```

dpkg -l smartmontools

```

Then I will walk you through using the tool to examine the hard drive(s).

Show us what we are working with:
Post back the outputs - Between Code Tags - the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We will see what 
[INDENT][INDENT]tale gets told
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-09
ubuntu@ubuntu:~$ dpkg -l smartmontools
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  smartmontools  <none>       <none>       (no description available)
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f220

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968517631   484257792   83  Linux
/dev/sda2       968519678   976771071     4125697    5  Extended
/dev/sda5       968519680   976771071     4125696   82  Linux swap / Solaris

Disk /dev/sdb: 31.4 GB, 31379685376 bytes
255 heads, 63 sectors/track, 3815 cylinders, total 61288448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02a68386

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    61288447    30643200    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MK5061GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4225MB  extended
 5      496GB   500GB  4225MB  logical   linux-swap(v1)


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 31.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.4GB  31.4GB  primary  fat32        boot, lba

---

### Post by Bashing-om on 2015-10-09
dex3; Hey, yeah ..

We can do this .. code tags help a bunch .. please read and heed and use:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Retaining formatting promotes readability . When you read as much "code" on a day as we do ... sure does help !

OK .. moving on along.. the tool is presently not installed.
Install the tool:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install smartmontools

```

Once installed now we look.
execute in terminal:
```

sudo smartctl -a /dev/sda

```
post the command and it's output here and we get a quick summary of what the hard drive's condition is.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-09
dex3; Hey ...

I have outside chores to get done. I will return and check your progress in about 3 hours .

see ya

---

### Post by oldos2er on 2015-10-09
Backup your data now if you haven't already.

---

### Post by dex3 on 2015-10-09
Hey so remember I am on ubuntu because of the flash drive.. so is installing stuff even possible? As I said above when I boot onto ubuntu from the HDD I cannot access the web browser.. I'm am on ubuntu through the flash drive.. at any rate I tried installing the tools that you suggested.. it gave me an error, I tried installing again and now it says ```
  dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

---

### Post by Bashing-om on 2015-10-09
dex3; Yeah ..

I did not realize you were on a USB thumb drive. But one can still be able to install the application. However, if you do not have persistence enabled the install will not persist a reboot. The update/upgrade/install process may have run you our of memory causing the error ??

But less hassle to work from the install .
What results if you boot to grub's boot menu -> advanced options -> recovery -> resume normal boot ?

Does this get you a usable desktop ( degraded graphics is expected) ?

There are other options we can try ... either from the recovery console or from terminal, in order to get the tool installed and post the requested output.

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-09
When I boot Ubuntu from HDD it no longer gives me other options for booting.. it instead automatically boots to Ubuntu.. in which case I cannot access the web browser.. I have restarted my computer booted Ubuntu from my USB Drive.. ran the terminal again sudo apt-get install smartmontools.. asks me if its ok to install i say y.. then it says this..

  ```
 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   
  &#9474;                                                                         &#9474;   
  &#9474; Please select the mail server configuration type that best meets your       
  &#9474; needs.                                                                      
  &#9474;                                                                             
  &#9474;  No configuration:                                                          
  &#9474;   Should be chosen to leave the current configuration unchanged.            
  &#9474;  Internet site:                                                             
  &#9474;   Mail is sent and received directly using SMTP.                            
  &#9474;  Internet with smarthost:                                                   
  &#9474;   Mail is received directly using SMTP or by running a utility such         
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                    
  &#9474;  Satellite system:                                                          
  &#9474;   All mail is sent to another machine, called a 'smarthost', for            
  &#9474; delivery.                                                                   
  &#9474;  Local only:                                                                
  &#9474;                                                                             
  &#9474;                                 <Ok>                        
```

---

### Post by Bashing-om on 2015-10-09
dex3; Sorry;

That advisory is a new on on me . I have no idea of what is prompting that .
 we must continue to consider that you have a bad burn .

If you boot the USB drive, as soon as the bios screen clears depress a shift key -> language scree, escape key to accept the defaults -> boot options screen -> check disk for defects.
Run the check, will take some time to complete.

Does it complete with no errors ?

[INDENT][INDENT]else we are back to booting the install - one way or the other .
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-09
there are no disk defaults.. ive tried running terminal on install boot.. it gives error.. no log

---

### Post by Bashing-om on 2015-10-09
dex3; Well:
> 
there are no disk defaults.. i

I have to ask then what the liveUSB is ? Some other than ubuntu desktop ?

[INDENT][INDENT]now I really do not know
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-09
It's Ubuntu downloaded right from Ubunto Website? 

[IMG]http://s23.postimg.org/5xenmr1d7/Screenshot_from_2015_10_10_01_04_47.png[/IMG]

---

### Post by Bashing-om on 2015-10-09
dex3; Yepper;

Agreed that is a standard ubuntu desktop.
On that liveUSB there should be the "check disk for defects" option. You will have to interrupt the normal live boot process (maybe if UEFI ? then it is the escape key) and redirect the boot up to the boot options screen.

[INDENT][INDENT]we do need a firm foundation
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-09
Yeah I did check the disk for defects as you suggested earlier.. it said no errors have returned.

---

### Post by Bashing-om on 2015-10-09
dex3; K ,

That gives us some small measure of confidence that the install medium is good.
From that liveUSB, what now results:
```

sudo apt-get install smartmontools
sudi fdisk -lu
sudo smartctl -a /dev/sda

```
The 'fdisk' command to make sure the 500 Gig drive is still seen by the system as 'sda' to direct 'smartctl' to check the proper drive.

[INDENT][INDENT]progress made slowly
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-09
> **Bashing-om said:**
> dex3; K ,

That gives us some small measure of confidence that the install medium is good.
From that liveUSB, what now results:
```

sudo apt-get install smartmontools
sudi fdisk -lu
sudo smartctl -a /dev/sda

```
The 'fdisk' command to make sure the 500 Gig drive is still seen by the system as 'sda' to direct 'smartctl' to check the proper drive.[INDENT][INDENT]progress made slowly
[/INDENT]
[/INDENT]



Huh? Nothing has changed since you first asked me to run those lines.. I get the same message I did before? The one that you said you've never seen before? Again this from Linux on the USB.. not install.. because I can't run any terminal codes through HDD linux.. so again this is the message that popped up on terminal after the first line was entered.. Are you sure you dont want to try using google remote stream or something so that you can see what I am doing? 

```
 Package configuration                                                           
                                                                                
  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   
  &#9474;                                                                         &#9474;   
  &#9474; Please select the mail server configuration type that best meets your       
  &#9474; needs.                                                                      
  &#9474;                                                                             
  &#9474;  No configuration:                                                          
  &#9474;   Should be chosen to leave the current configuration unchanged.            
  &#9474;  Internet site:                                                             
  &#9474;   Mail is sent and received directly using SMTP.                            
  &#9474;  Internet with smarthost:                                                   
  &#9474;   Mail is received directly using SMTP or by running a utility such         
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                    
  &#9474;  Satellite system:                                                          
  &#9474;   All mail is sent to another machine, called a 'smarthost', for            
  &#9474; delivery.                                                                   
  &#9474;  Local only:                                                                
  &#9474;                                                                             
  &#9474;                                 <Ok>                                        
  &#9474;                                         
```

---

### Post by oldos2er on 2015-10-10
Did you run ```
sudo dpkg --configure -a
```? 

I think for the mail server configuration you'd choose "Local only."

---

### Post by Bashing-om on 2015-10-10
dex3; Hey ....

Settle down, ( from your PM) .. and think your way through this, and keep in mind the end goal.
Your stated goal at this time is to run SMART on the hard drive. Not a problem. 

We can run these tests from either the liveUSB or from the install. You are the one doing the work. You tell us which method you want to do and we will guide you on how to do so.

[INDENT][INDENT]we can lead you to the water
[INDENT][INDENT][INDENT]but only you can drink it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-10
I'm running Ubuntu through the the flash drive... because the install on my HDD produces errors.. so yes what is the next step.

---

### Post by dex3 on 2015-10-10
> **oldos2er said:**
> Did you run ```
sudo dpkg --configure -a
```? 

I think for the mail server configuration you'd choose "Local only."

How would I select local only theres no way to select or type anything when this postfix configuration comes up

---

### Post by Bashing-om on 2015-10-10
dex3; Sorry;

Presently I am confused.

Can you boot the liveUSB or no ? I take it we will work for the time being from the liveUSB IF it is bootable.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-10
> **Bashing-om said:**
> dex3; Sorry;

Presently I am confused.

Can you boot the liveUSB or no ? I take it we will work for the time being from the liveUSB IF it is bootable.
[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


Yes I am on Linux through the LiveUSB now.

---

### Post by Bashing-om on 2015-10-10
dex3; Great !

OK ,, in terminal install the tool:
Execute terminal command:
```

sudo apt-get install smartmontools

```
and now run the check for hard drive problems:
execute terminal commands:
```

sudo fdisk -lu
sudo smartctl -a /dev/sda

```
where the output of 'fdisk'  should confirm that 'sda' is the target 500 Gigs hard drive for 'smartctl' to operate on.

Post the output back here if you need help to understand the conditions.

[INDENT][INDENT][INDENT]small steps
[/INDENT][/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-10
> **Bashing-om said:**
> dex3; Great !

OK ,, in terminal install the tool:
Execute terminal command:
```

sudo apt-get install smartmontools

```
and now run the check for hard drive problems:
execute terminal commands:
```

sudo fdisk -lu
sudo smartctl -a /dev/sda

```
where the output of 'fdisk'  should confirm that 'sda' is the target 500 Gigs hard drive for 'smartctl' to operate on.

Post the output back here if you need help to understand the conditions.
[INDENT][INDENT][INDENT]small steps
[/INDENT]
[/INDENT]
[/INDENT]




my friend were going back in circles... when I run "sudo apt-get install smartmontools" terminal presents me the follow code below with a purple background
```
 Package configuration                                                           
                                                                                
  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   
  &#9474;                                                                         &#9474;   
  &#9474; Please select the mail server configuration type that best meets your       
  &#9474; needs.                                                                      
  &#9474;                                                                             
  &#9474;  No configuration:                                                          
  &#9474;   Should be chosen to leave the current configuration unchanged.            
  &#9474;  Internet site:                                                             
  &#9474;   Mail is sent and received directly using SMTP.                            
  &#9474;  Internet with smarthost:                                                   
  &#9474;   Mail is received directly using SMTP or by running a utility such         
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                    
  &#9474;  Satellite system:                                                          
  &#9474;   All mail is sent to another machine, called a 'smarthost', for            
  &#9474; delivery.                                                                   
  &#9474;  Local only:                                                                
  &#9474;                                                                             
  &#9474;                                 <Ok>                                        
  &#9474;                                        
```

---

### Post by Bashing-om on 2015-10-10
dex3; K;

So we have a network configuration issue.

What results when you choose the " No configuration: " option ?

Can you presently access the internet ? We find out the internet condition from the return of terminal commands:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
the result should be similar to mine:
```

sysop@1404mini:~$ ping -c3 8.8.8.8
<snip>
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
<snip>

sysop@1404mini:~$ ping -c3 ubuntu.com
<snip>
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
<snip>

```

Got to have the tools, and must have internet to get the tools.

[INDENT][INDENT]trails, troubles and tribulations
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-10
There is no way for me to press no configuration.. i selected shift f2.. which brought up my options.. i highlighted "no configuration" then i scrolled down and highlighted ok and pressed enter.. in which case it brought me back to the same screen i was seeing before. My internet is fine?

```
 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

ubuntu@ubuntu:~$ ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=49 time=242 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=49 time=129 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=49 time=128 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 128.316/166.638/242.095/53.359 ms 
```

---

### Post by Bashing-om on 2015-10-10
dex3; Nope !

I must disagree that there are no networking problems .
Ping to goggle's DNS server you get no reply ( "  0 received, 100% packet loss " ).
However, I can not explain why a ping to ubuntu does complete. It will take someone with greater networking skills than I possess to work through this condition .

Having never encountered the system request " Postfix Configuration " I do not have the experience to advise.

[INDENT][INDENT]this time, I just do not know
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-10
> **Bashing-om said:**
> dex3; Nope !

I must disagree that there are no networking problems .
Ping to goggle's DNS server you get no reply ( "  0 received, 100% packet loss " ).
However, I can not explain why a ping to ubuntu does complete. It will take someone with greater networking skills than I possess to work through this condition .

Having never encountered the system request " Postfix Configuration " I do not have the experience to advise.
[INDENT][INDENT]this time, I just do not know
[/INDENT]
[/INDENT]



Can we not google screen cast or a different casting program so you can see what I am talking about?

---

### Post by Bashing-om on 2015-10-10
dex3; Sure;

I will look at anything that you present. But in this context of network configuration, I do not know of any help presently I can provide.

Is the interface wired or WIFI ?

[INDENT][INDENT]I do not know everything
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-11
> **Bashing-om said:**
> dex3; Sure;

I will look at anything that you present. But in this context of network configuration, I do not know of any help presently I can provide.

Is the interface wired or WIFI ?
[INDENT][INDENT]I do not know everything
[/INDENT]
[/INDENT]



It's on wifi.. I've tried two different networks.. i don't think it has anything to do with the network more so with linux..

---

### Post by Bashing-om on 2015-10-14
dex3; Shheessh ;


Well, as I have no experience with WIFI and am weak to say the least in networking and none with the experience have responded in this thread; open a new thread in this regard to gain the attention of those who do have the knowledge.

Until such time as you can download the smartmontools suite we are dead in the water.
Once the tools are installed, we can continue in this thread.

[INDENT][INDENT]A know-It-All
[INDENT][INDENT][INDENT][INDENT]I am not
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2015-10-14
Dex3 . . . if you have internet as it seems you do, why don't you try to install the "smartmontools" application via the Ubuntu Software Center (using live session) versus the terminal?   It's the same program, and if the internet is working, it should install.  I'm curious if it will throw the same error as your terminal install command as it seems wrong that you're getting email client install errors versus in the first place, as you're not installing a mail client or server?    (unless there's an email component to the smart tools??)

Also, you should be able to install any browser (FF, Chromium) via the USC also . . It would work for your present "session" which is all you need at this point.

Frankly, if it were me, what I would try to do is this:

>   From the Live usb-flashstick session, I would save off all important files/data (to another flashstick or to space on the same flashstick, or to the cloud),
(note, you should open nautilus in live session and it should be able to see all your existing drives, partitions, etc.)
>   I would (from another PC if possible), download and burn a new Ubuntu install image to another usb-flashstick,
>   Then, do a full re-install back to same partition (and reformatting that partition as part of the install process may clear up disk(s) issue).

---

### Post by dex3 on 2015-10-14
> **Geoffrey_Arndt said:**
> Dex3 . . . if you have internet as it seems you do, why don't you try to install the "smartmontools" application via the Ubuntu Software Center (using live session) versus the terminal?   It's the same program, and if the internet is working, it should install.  I'm curious if it will throw the same error as your terminal install command as it seems wrong that you're getting email client install errors versus in the first place, as you're not installing a mail client or server?    (unless there's an email component to the smart tools??)

Also, you should be able to install any browser (FF, Chromium) via the USC also . . It would work for your present "session" which is all you need at this point.

Frankly, if it were me, what I would try to do is this:

>   From the Live usb-flashstick session, I would save off all important files/data (to another flashstick or to space on the same flashstick, or to the cloud),
(note, you should open nautilus in live session and it should be able to see all your existing drives, partitions, etc.)
>   I would (from another PC if possible), download and burn a new Ubuntu install image to another usb-flashstick,
>   Then, do a full re-install back to same partition (and reformatting that partition as part of the install process may clear up disk(s) issue).

HI I tried through ubuntu software centre.. it downloads and then when it goes to install it makes ubuntu software centre black and white and just hangs there nothing else seems to be happening? Also guys I tried installing windows 10 now onto the HDD and it gets almost all the way through and then errors.. windows 10 says its possible to install but that there are S.M.A.R.T errors and that I Should backup the HDD etc.. I am now looking at the HDD on ubuntu live session and I see that there are all windows folders program files folder etc.. any more suggestions guys?

---

### Post by Bashing-om on 2015-10-14
dex3; Hey ...

Best I can say , as others say also, is to start all over from scratch.
Burn another DVD or USB.
From this new live environment we try and download the tool to check the hard drive.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-14
> **Bashing-om said:**
> dex3; Hey ...

Best I can say , as others say also, is to start all over from scratch.
Burn another DVD or USB.
From this new live environment we try and download the tool to check the hard drive.
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]



Hey so i did another install.. this time i've installed chronium since it is still giving me errors when trying to run firefox.. so I've installed smartmontools and this is what I got out of terminal running the lines you suggested in earlier posts.. 

```
 Disk /dev/sda: 500.1 GB, 500107862016 bytes255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022ee8


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968517631   484257792   83  Linux
/dev/sda2       968519678   976771071     4125697    5  Extended
/dev/sda5       968519680   976771071     4125696   82  Linux swap / Solaris
dex@dex-HP-ProBook-4430s:~$ sudo parted -l
Model: ATA TOSHIBA MK5061GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4225MB  extended
 5      496GB   500GB  4225MB  logical   linux-swap(v1)

```

---

### Post by Bashing-om on 2015-10-14
dex3; K,

That tells us that a linux distro is installed to the 1st hard drive - in this case sda - and I see nothing obvious wrong with the partitioning.

Now to the original question of this thread, From the liveUSB that has smartmontools installed to, run terminal command:
```

sudo smartctl -a -d ata /dev/sda

```
To display detailed SMART information for a SATA drive. Will take a while to complete the test .

Post the result back here and we have a look.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-14
> **Bashing-om said:**
> dex3; K,

That tells us that a linux distro is installed to the 1st hard drive - in this case sda - and I see nothing obvious wrong with the partitioning.

Now to the original question of this thread, From the liveUSB that has smartmontools installed to, run terminal command:
```

sudo smartctl -a -d ata /dev/sda

```
To display detailed SMART information for a SATA drive. Will take a while to complete the test .

Post the result back here and we have a look.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Hi just to clarify I am running Ubuntu from the HDD itself not liveusb.. smartmontools is installed onto ubuntu HDD not liveusb..
```
 === START OF INFORMATION SECTION ===Model Family:     Toshiba 2.5" HDD MK..61GSY[N]
Device Model:     TOSHIBA MK5061GSYN
Serial Number:    619LT73MT
LU WWN Device Id: 5 000039 351a023a3
Firmware Version: MH000C
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed Oct 14 21:38:32 2015 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.


General SMART Values:
Offline data collection status:  (0x86)	Offline data collection activity
					was aborted by the device with a fatal error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (  73)	The previous self-test completed having
					a test element that failed and the test
					element that failed is not known.
Total time to complete Offline 
data collection: 		(  120) seconds.
Offline data collection
capabilities: 			 (0x51) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 109) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0027   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0023   100   100   002    Pre-fail  Always       -       2337
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2515
  5 Reallocated_Sector_Ct   0x0033   001   001   010    Pre-fail  Always   FAILING_NOW 2047
  7 Seek_Error_Rate         0x002f   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       7609
 10 Spin_Retry_Count        0x0033   150   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1866
183 Runtime_Bad_Block       0x0032   100   100   001    Old_age   Always       -       2
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
185 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       65535
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       32474
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       7
189 High_Fly_Writes         0x003a   100   100   001    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   061   049   040    Old_age   Always       -       39 (Min/Max 32/40)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       575
192 Power-Off_Retract_Count 0x0022   100   100   000    Old_age   Always       -       7405681
193 Load_Cycle_Count        0x0032   069   069   000    Old_age   Always       -       311332
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       277
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0


SMART Error Log Version: 1
ATA Error Count: 32822 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.


Error 32822 occurred at disk power-on lifetime: 7608 hours (317 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 c2 0f 47 1f 60  Error: WP at LBA = 0x001f470f = 2049807


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 40 70 c0 68 c0 40 00      00:47:47.218  WRITE FPDMA QUEUED
  61 40 68 80 63 c0 40 00      00:47:47.210  WRITE FPDMA QUEUED
  61 40 60 40 5e c0 40 00      00:47:47.204  WRITE FPDMA QUEUED
  61 40 58 00 59 c0 40 00      00:47:47.181  WRITE FPDMA QUEUED
  61 08 50 e8 1f c4 40 00      00:47:47.173  WRITE FPDMA QUEUED


Error 32821 occurred at disk power-on lifetime: 7608 hours (317 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 b2 0f 47 1f 60  Error: UNC at LBA = 0x001f470f = 2049807


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 b0 08 47 1f 40 00      00:47:43.785  READ FPDMA QUEUED
  61 08 a8 10 1f c5 40 00      00:47:43.781  WRITE FPDMA QUEUED
  61 50 a0 c0 1e c5 40 00      00:47:43.766  WRITE FPDMA QUEUED
  61 d8 98 00 fa 1d 40 00      00:47:43.743  WRITE FPDMA QUEUED
  61 08 90 b8 1e c5 40 00      00:47:43.697  WRITE FPDMA QUEUED


Error 32820 occurred at disk power-on lifetime: 7608 hours (317 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 4a 0f 47 1f 60  Error: WP at LBA = 0x001f470f = 2049807


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 30 58 b8 f1 14 40 00      00:45:08.213  WRITE FPDMA QUEUED
  61 10 50 b8 f9 4a 40 00      00:45:08.211  WRITE FPDMA QUEUED
  60 08 48 08 47 1f 40 00      00:45:08.138  READ FPDMA QUEUED
  61 40 40 00 e9 00 40 00      00:45:08.138  WRITE FPDMA QUEUED
  61 40 38 40 ee 00 40 00      00:45:08.138  WRITE FPDMA QUEUED


Error 32819 occurred at disk power-on lifetime: 7608 hours (317 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 ea 0f 47 1f 60  Error: WP at LBA = 0x001f470f = 2049807


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 f0 38 65 c4 40 00      00:45:05.020  WRITE FPDMA QUEUED
  60 08 e8 08 47 1f 40 00      00:45:04.986  READ FPDMA QUEUED
  61 a8 e0 90 64 c4 40 00      00:45:04.985  WRITE FPDMA QUEUED
  61 08 d8 e8 7b 44 40 00      00:45:04.966  WRITE FPDMA QUEUED
  61 38 d0 88 f1 14 40 00      00:45:04.919  WRITE FPDMA QUEUED


Error 32818 occurred at disk power-on lifetime: 7608 hours (317 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 32 0f 47 1f 60  Error: WP at LBA = 0x001f470f = 2049807


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 50 38 38 64 c4 40 00      00:45:01.471  WRITE FPDMA QUEUED
  60 08 30 08 47 1f 40 00      00:45:01.337  READ FPDMA QUEUED
  61 08 28 18 c9 44 40 00      00:45:01.337  WRITE FPDMA QUEUED
  61 08 20 20 c8 44 40 00      00:45:01.337  WRITE FPDMA QUEUED
  61 40 18 00 c9 00 40 00      00:45:01.337  WRITE FPDMA QUEUED


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%      7598         0
# 2  Short offline       Completed: unknown failure    90%      7598         0
# 3  Short offline       Completed: unknown failure    90%      7598         0
# 4  Short offline       Completed: unknown failure    90%      7583         0
# 5  Short offline       Completed: unknown failure    90%      7582         0
# 6  Short offline       Completed: unknown failure    90%      7581         0
# 7  Short offline       Aborted by host               90%      1747         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by Bashing-om on 2015-10-14
dex3; Yuk !

The SMART status do say that drive is history in this configuration.

It is possible that the drive "might" be repurposed as a data disk.
One can play with 'badblocks' and/or zero'n out the drive with 'dd' and repartition. I would never ever trust this drive for production use again !

Pull your data off this drive and replace it ... now !
> 
Drive failure expected in less than 24 hours. SAVE ALL DATA.


[INDENT][INDENT]nothing else can be said
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-14
> **Bashing-om said:**
> dex3; Yuk !

The SMART status do say that drive is history in this configuration.

It is possible that the drive "might" be repurposed as a data disk.
One can play with 'badblocks' and/or zero'n out the drive with 'dd' and repartition. I would never ever trust this drive for production use again !

Pull your data off this drive and replace it ... now !
[INDENT][INDENT]nothing else can be said
[/INDENT]
[/INDENT]


Hi this whole S.M.A.R.T errors all happened when I formatted and partitioned the drive.. are we sure that there isn't anything else we can do to try and fix the HDD when there may not be anything wrong? I don't think it will fail in 24 hours.. After all I am currently running Ubuntu off of the HDD and am able to install applications etc.

---

### Post by Bashing-om on 2015-10-14
dex3; Welp;

This:
> 
192 Power-Off_Retract_Count 0x0022   100   100   000    Old_age   Always       -       7405681

All these sectors are marked as bad:
> 
 5 Reallocated_Sector_Ct   0x0033   001   001   010    Pre-fail  Always   FAILING_NOW 2047

and it keeps trying to move these bad sectors :
> 
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       277

says to me that you have controller problems. That drive is not usable at this time in this configuration. 
If you power that drive down ( unplug all cables) plug it back into a different sata port ; clear CMOS on the mainboard ; and power all back up ;Then run the SMART tests once more and see if that makes a difference. Still failing, wipe the disk and re-partition .Run SMART once more; You might be able to use that drive as a data disk for temporary storage means. My system is too important to me to risk it on a uncertain hard drive(s). All drives fail - all of them .. it is but a matter of time.

[INDENT][INDENT]just what I would do
[/INDENT][/INDENT]

---

### Post by dex3 on 2015-10-15
> **Bashing-om said:**
> dex3; Welp;

This:

All these sectors are marked as bad:

and it keeps trying to move these bad sectors :

says to me that you have controller problems. That drive is not usable at this time in this configuration. 
If you power that drive down ( unplug all cables) plug it back into a different sata port ; clear CMOS on the mainboard ; and power all back up ;Then run the SMART tests once more and see if that makes a difference. Still failing, wipe the disk and re-partition .Run SMART once more; You might be able to use that drive as a data disk for temporary storage means. My system is too important to me to risk it on a uncertain hard drive(s). All drives fail - all of them .. it is but a matter of time.
[INDENT][INDENT]just what I would do
[/INDENT]
[/INDENT]


I feel like its fixable just cant figure it out.. but one more question so If I get another HDD, the s.ma.r.t check will go away?

---

### Post by Bashing-om on 2015-10-15
dex3; Yepper;
Ya  got the right of it :
> 
I feel like its fixable just cant figure it out.. but one more question so If I get another HDD, the s.ma.r.t check will go away?

If no errors are reported nothing will be generated.
Replacing that hard drive is a got to be done thing .. then one can investigate what might be possible with that old drive. Even with hardware issues, it is fixable . However the cost is extremely high, particularly so IF the repair must be done in a a "clean room" . Relatively speaking, a new drive is cheap .

The chances of 'fixing' the present drive and keeping the data on that drive is very very low ! Only time effort and testing will ever show if there is any possibility to re-purpose that drive. Bite the bullet and replace it and be done with it.

[INDENT][INDENT]That is what I think
[/INDENT][/INDENT]

---

