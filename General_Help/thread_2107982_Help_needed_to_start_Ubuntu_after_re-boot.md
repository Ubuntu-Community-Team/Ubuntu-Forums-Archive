---
title: "Help needed to start Ubuntu after re-boot"
date: 2013-01-23
forum: General Help
---

### Post by quantlinear on 2013-01-23
Hi to all, 

I have  experienced  a crash couple a days a go after I have manually shut down the system due to none-respond shut down from the Ubuntu interface( It has been happening almost every time I have tried to shut down the system from the interface which i has to re-set and then able to shut it down ) The Ubuntu is unable to upload,I have done few  reset & switched off the system manually few times too  in hope that  the system recover from the crash but that did`t  help. I have been receiving some codes as follow : 

-------------------------------------------- 

*Stopping anac(h)ronistic crom    [ok]
*Stopping anac(h)ronistic crom    [ok]
*Stopping anac(h)ronistic crom    [ok]
*Stopping enable remaining boot-time encrypted block devices [ok]

*stopping Mount filesystem on boot [ok]
*checking battery state ......  [ok]
*Stopping system V runlevel compatibility [ok]
*Starting CUPS printing spooler/server [ok]

-------------------------------------------------

*Stopping anac(h)ronistic crom                                    [ok]
*Stopping  save kernel messages                                   [ok]
*Starting anac(h)ronistic crom                                    [ok]
*Stopping anac(h)ronistic crom                                    [ok]
*Stopping enable remaining boot-time encrypted block devices      [ok]
*Stopping Mount filesystem on boot                                [ok]
* Checking battery state .............                            [ok]
*Stopping system v runlevel compatibility                         [ok]
*starting CUPS printing Spooler/server                            [ok]

-------------------------------------------------


I appreciate all your help to get this problem resolved as soon as possible. 
Thanks
M

---

### Post by oldfred on 2013-01-23
After any abnormal shutdown fsck is usually required. Run on all your ext partitions.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
If you have to force shutdown remember the elephants.
       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by quantlinear on 2013-01-23
Hi, 

Prior to the system crash, I was receiving several  messages that was asking me to increase the size of the partition. I have a 1 TB hard drive which it has been partitioned but I wasn't sure of how to increase the partition volume.do you think the system crash related to the lack of sufficient volume on the main partition that ubuntu  system was initially  installed ?

Regards, 

M

---

### Post by oldfred on 2013-01-23
If you got warning you have to immediately do some housecleaning. 

Did you download a lot of data, or is there a run away error message filling some log file?

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by quantlinear on 2013-01-24
Many Thanks for helping me to solve this problem. 

If you got warning you have to immediately do some housecleaning. (I wasnt sure how to do a house cleaning on Linux, Although I have installed an app similar to CCcleaner for linux. please advice any specific source that I could read on this subject 

 Did you download a lot of data, or is there a run away error message filling some log file?

I have been using linux for only 3 months ,so i am a newbie,Mainly I have  learned basic stuff by reading and watching video on Ubuntu from none-academic sources . 
 I didnt download any data personally,but I was receiving regular messages  "Available  UPDATE" which I have proceed as usual  , then recently there were new messages warning me to increase the size of the partition,meanwhile I was trying to find out how to increase the partition size,therefore  the issue was persisting until I was notified that I have ran out of space and unable to proceed with the USUAL UPDATE. Finally I experienced Shut down problem and then I have manually shut down the system. and then Ubuntu doesn't boot and I have received the codes ...........

Would it be possible to chat over skype? then it would be much easier to  fix the issues I have 

My skype id : strongbow707  

Many Thanks

---

### Post by Impavidus on 2013-01-24
Can you give us the output of this command:```
df -h
```In case you don't know, open a terminal (ctrl-alt-t), copy-paste the command and paste the output in a new post. Put it in code tags by selecting the lines and clicking the "#" button above the input field.

It will give us an overview of the partitions on your system and which one is full. It could be a boot partition, they are often small. Also try```
sudo du -s /var/log
```which will tell us whether any logs are filling your drives.

By the way, on my laptop SysRq is on the delete key.

---

### Post by quantlinear on 2013-01-24
@ Impavidus   

Thank you . 

Reply:

Code df-h , I have tried in anyway to get access to the terminal but I am unable. 

The code : sudo du  -s. / var/log 

I have managed to bring up the log-in page by pressing (Ctrl-alt-f3)

After logged-in . After entered the password 

Message: 8308. /var/log 

I will be attaching some screen shut which I have taken by a camera. 

I am stuck and can't make a sense of how to get access to Ubuntu interface. 

Would you able to add me on Skype : strongbow707 . I am in United Kingdom . 

Thanks .

---

### Post by quantlinear on 2013-01-24
Please find the attachment from the screen shut

---

### Post by quantlinear on 2013-01-24
Please find the attachment .

---

### Post by oldfred on 2013-01-24
You should be able to use your install DVD or flash drive to boot to a live mode. Then you can mount your partitions and remove some data.

From liveCD mount (either with terminal or with nautilus) your Linux partition(s) and run this:

sudo df -H
sudo fdisk -lu

If you want to you can use IRC.
[http://ubuntuforums.org/showthread.php?t=69068](http://ubuntuforums.org/showthread.php?t=69068)

---

### Post by quantlinear on 2013-01-24
@Alfred 
Hi, I have managed under your instruction by a little search on google and luck to get the live CD run on my PC .I have chose the " try Ubuntu " option ,also entered the codes as you stated : 

Sudo df   -h   ( refer to attached image) 
Sudo Fisk. - lu ( refer to attached image)


I am stuck again with not knowing where should I go from here , 

I have mentioned that  I am a newbie to Ubuntu, therefore sometimes I am unable to follow the instruction as they seems a bit direct at the issue  , while I am still trying to learn and understand Linux as a whole( used only windows previously) . Please give a bit more details on how to apply the stages, I hope that I am not look demanding but you are far more experienced than me on Linux system. 

I will try to go on free node IRC

Once more many thanks for your valuable help 

Thanks 

M

---

### Post by quantlinear on 2013-01-24
@Alfred 
Hi, I have managed under your instruction by a little search on google and luck to get the live CD run on my PC .I have chose the " try Ubuntu " option ,also entered the codes as you stated : 

Sudo df -h ( refer to attached image) 
Sudo Fisk. - lu ( refer to attached image)


I am stuck again with not knowing where should I go from here , 

I have mentioned that I am a newbie to Ubuntu, therefore sometimes I am unable to follow the instruction as they seems a bit direct at the issue , while I am still trying to learn and understand Linux as a whole( used only windows previously) . Please give a bit more details on how to apply the stages, I hope that I am not look demanding but you are far more experienced than me on Linux system. 

I will try to go on free node IRC

Once more many thanks for your valuable help 

Thanks 

M

---

### Post by oldfred on 2013-01-24
Please copy & paste terminal output to message. If long use # to add code tags. Use screen shots for gui output.

You did not mount sda1 & sda3 before runing the df -h. Is sda1 your / (root) or just a /boot partition. It does not look very large, but sda3 is huge.

Use nautilus & click on sda1 & sda3 from live install to mount them and rerun df -h.

If sda1 is / (root) you really need to make it larger. If you have separate /home in sda3, you only need 10 to 25GB for /. You can use gparted from live install to move partitions around. Or reinstall. 
If you have important data be sure to backup first.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by quantlinear on 2013-01-24
Please copy & paste terminal output to message. If long use # to add code tags. Use screen shots for gui output.

 You did not mount sda1 & sda3 before runing the df -h. Is sda1 your / (root) or just a /boot partition. It does not look very large, but sda3 is huge.

 Use nautilus & click on sda1 & sda3 from live install to mount them and rerun df -h.

 If sda1 is / (root) you really need to make it larger. If you have separate /home in sda3, you only need 10 to 25GB for /. You can use gparted from live install to move partitions around. Or reinstall. 
 If you have important data be sure to backup first.
-------------------------------------------------------------

@Alfred 

Do you Actually want me to install the ubuntu again ?

you did not mount sda1 & sda3 before runing the df -h. Is sda1 your / (root) or just a /boot partition. It does not look very large, but sda3 is huge.

REPLY: I am on the  option "try ubuntu" after. If I click install Ubuntu,then it gave me two options (erase ubuntu -  something else )  then i followed SOMETHING ELSE : 

so i have clicked on something else : then there is a installation type window 

Devive 
dev/dsa
dev/sda1/ext4    5498 MB 
dev/sda5
dev/dsa3 ext4    993203



I have clicked on CHANGE @ 
dev/sda1/ext4    5498 MB    But i am unsure what option on the "edit partition" i should choose , before click "ok" please refret to attached photo. 

this way ,after i could get access to my hardrive, then i can apply Gparted partition. but what I need urgently is to get access to my files on the OS that has been down for few days.

---

### Post by quantlinear on 2013-01-24
Please find the attachment

---

### Post by quantlinear on 2013-01-24
Image of the edit partition

---

### Post by oldfred on 2013-01-24
Gparted is not the installer, it is a separate application on the liveCD. But the installer has something similar to gparted in creating new partitions for your install.

If you have any data you want to save DO NOT reinstall.

Did you look at the links on using gparted?

If sda1 is your / (root) it is small at 5.5GB. You will have to regularly aggressively house clean if you want that small of a system partition. 
I normally install to 25GB including my /home but have all data in other data partitions. I use about 9GB of my 25GB root partition.

---

### Post by nothingspecial on 2013-01-24
We've been looking at this on IRC.

The live CD has been booted and the OP (quantlinear) cannot find his data in any of the partitions available in the sidebar of the file browser.

I have suggested fsck and testdisk/photorec

The OP's prime concern is the data.

---

### Post by quantlinear on 2013-01-24
Oldfred 

Hi, after this I had enough for today with Ubuntu, I must admit that i do enjoy the screw up immensely as it has thrown me all over the web and pointed me at many amazing sources & people .I  will start on it tomorrow again but some help will be most appreciated. 

--------------------------------------------------
The below instruction that I have burned  a CD of  knoppix lastnight ,I have inserted it to the drive as per instruction but I ended  up to have a menu with electronic voice as i have moved down from top to bottom of the menu (1-11), what I only could found interesting at the time ,It  was SHUT DOWN option , that was the only option which I happily took the initiative and clicked yes !! 
[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250) 

----------------------------------------------------------

It seems that I need to get a complete new installation from scratch but before that , desperately I would need to EXTRACT  the personal files from the hard drive. 

What do i have do from here to recover and then get a clean and professional Ubuntu installation which I will need some help with few links that explain know-how to put me straight back on the track. can you help please.   
 
A thousand Thanks for all your effort and support.

---

### Post by oldfred on 2013-01-24
I am not real familiar with Knoppix, but I think it includes testdisk and photorec.

Did they point you to the testdisk info on trying to recovery the partition?

       [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

            repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Only if testdisk does not find partition and show files will you need photorec as a last recourse. But that can be a long slow process. Lets see what testdisk finds.

---

### Post by quantlinear on 2013-01-30
Hi, Please find the copy of the GNU Parted below here, I am unsure what I should do from here. 

ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# sudo swapoff -a
root@ubuntu:~# sudo parted  /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) rescu START END                                                  
Error: Invalid number.                                                    
(parted) help
  align-check TYPE N                        check partition N for TYPE(min|opt)
        alignment
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on
        COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition
        table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on
        partition NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table,
        available devices, free space, all found partitions, or a particular
        partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START
        and END
  resize NUMBER START END                  resize partition NUMBER and its file
        system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition
        NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and
        copyright information of GNU Parted
(parted) 

Thank you.

---

### Post by oldfred on 2013-01-30
Parted is the command line version to edit partitions, gparted is the gui version which if lauching from command line not icon should be this:

gksu gparted

Do you want to edit partitions or recover data?

---

### Post by quantlinear on 2013-01-31
Thank you for your continuous effort to help me to solve this problem. 


first and foremost I need to recover my data and then I think ideally i need a fresh re-install with proper partitioning of the hard drive. 

I will be seeking advice  from yourself about fresh professional installation with secure user name & password , I hope that you don't mind :) 

Currently I am studying Cisco CCNA, I would like to learn much more on Linux security,virtual machine. 

Kind Regarsd, 

Mikael

---

### Post by oldfred on 2013-01-31
Does testdisk find old partition table(s)?

---

### Post by quantlinear on 2013-01-31
please find the attachment. unfortunately i am unable to get the "testdisk" working. i have made some screen shuts. I have followed the instruction but it seems that I couldn't get the result. i am still very confuse of how to retrieve my data from the hard disk. its getting very frustrating.

---

### Post by oldfred on 2013-01-31
testdisk is one word, but you have to install it first. Please go back and follow the step by step instructions on the testdisk site.

sudo apt-get install testdisk

sudo testdisk

---

