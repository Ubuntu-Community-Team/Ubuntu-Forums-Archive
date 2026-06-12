---
title: "Ubuntu 22.04 installed in August 2022 fails to start."
date: 2023-04-01
forum: General Help
---

### Post by euphorbialand on 2023-04-01
I installed Ubuntu 22.04 on Lenovo Yoga 13 in August 2022. It worked great initially now it started acting out. Sometimes it does not start up. It stays on the Lenovo splash screen with the options F2 and  F12. So I have to force close and start again. Eventually the system starts but I cannot be sure when it happens and one day it might not work at all. Eventually computer opens but then the mouse stopped working. So now I need to use touchpad which I am not used to. I turned it off because when typing the cursor would jump up and down. Now I had to turn it on and I hate it. I read lots of stuff on google on the subject but nothing really directly referred to my case. One of things I did was to repair file system but it did not help. Most of instructions referer to situation when it does not start up at all. I am not a pro on ubuntu and I prefer to use applications rather than terminal unless there are no other options. I installed ebook editor, easy tag for mp3, gscan2pdf, kmymoney. I might have installed some other apps but I don't remember all of them. Maybe one of them caused it. I am not going back to Windows now matter what. 
I can still use the computer for now. But I never know whether it will work the next time. 

Any suggestions? Thanks in advance. Euphorbialand

---

### Post by TheFu on 2023-04-01
Check the system logs for errors and warnings.  Google "ubuntu log files" for how.  Hopefully, it isn't a hardware issue, but I fear there are a few of those based on the problem descriptions.

**Always, always, check the system logs first.  Always.**

---

### Post by euphorbialand on 2023-04-01
I found it in activities. But. I really don't know what to make of it. These are just important messages. System messages are really long. 

7:50:10 PM gdm-session-wor: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
 7:50:04 PM systemd: Failed to start Application launched by gnome-session-binary.
 7:50:03 PM gdm-session-wor: gkr-pam: unable to locate daemon control file
 7:49:44 PM gnome-session-b: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
 7:49:43 PM bluetoothd: Failed to set mode: Failed (0x03)
 7:49:40 PM kernel: blacklist: Problem blacklisting hash (-13)
 7:49:39 PM kernel: x86/cpu: VMX (outside TXT) disabled by BIOS

---

### Post by euphorbialand on 2023-04-01
Touchpad also works at random. Sometime it works sometimes it doesn't.  Now I have only touch screen and keyboard. I am thinking about reinstalling the system unless someone gives me other suggestions. I am entry level user so it is hard for me fix the problem on my own other than reinstalling the system.

---

### Post by TheFu on 2023-04-02
> **euphorbialand said:**
> I found it in activities. But. I really don't know what to make of it. These are just important messages. System messages are really long. 

7:50:10 PM gdm-session-wor: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
 7:50:04 PM systemd: Failed to start Application launched by gnome-session-binary.
 7:50:03 PM gdm-session-wor: gkr-pam: unable to locate daemon control file
 7:49:44 PM gnome-session-b: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
 7:49:43 PM bluetoothd: Failed to set mode: Failed (0x03)
 7:49:40 PM kernel: blacklist: Problem blacklisting hash (-13)
 7:49:39 PM kernel: x86/cpu: VMX (outside TXT) disabled by BIOS

Session stuff isn't important.
Does your mouse use bluetooth?

The system messages are where issues will be.  You should scan them for errors/warnings (or use a tool), then READ each, carefully.

I still fear this is a hardware problem, based on the description. Reinstalling the OS can't fix hardware problems.  If you boot into a "Try Ubuntu" environment (use a USB flash drive) and everything works, then I'd believe it is a configuration issue, not hardware.

---

### Post by euphorbialand on 2023-04-02
I scanned system messages. No errors, no warnings in it. I have USB mouse. You were right about hardware. The mouse failed. I replaced the mouse with another USB mouse and it works. This is the last thing i suspected. Touchpad still does not work but I don't need it as long as mouse works. Maybe also hardware problem. Computer is 10 years old but with I7 processor. Very fast and with touch screen. 

But I still have problem that it does not always boot up. It started acting approx. a month ago. Recently I installed and unintalled few accounting applications and then uninstalled after trying.  Like Grucash, HomeBank and KMyBank. On some of them there is description "Potentially unsafe, third party application".  But they were recommened on sites that looked trustworthy. 
Is it possible that broken mouse caused failed boot up?

---

### Post by TheFu on 2023-04-02
> **euphorbialand said:**
>  
Is it possible that broken mouse caused failed boot up?

It depends on the BIOS settings.  I know for keyboards, if one isn't connected, many BIOSes will fail to boot unless the "Continue on Keyboard failure" is enabled in the BIOS.  One of my systems needs that to boot. No keyboard connected.
I don't do much with laptops. Any HID device (keyboard, mouse, touchpad) would be confused as a keyboard.

I think it is more likely that the boot issue is due to a failing HDD or bitrot.  If it were me, I'd check the SMART data on the drive, ensure there weren't any failures reported, before doing anything else.

Bitrot can be solved by doing regular backups, at least weekly, if not daily.  The effort in reading all the bits on the source HDD will cause the drive firmware to ensure bitrot doesn't occur.  Seems crazy, but doing backups means you will be less likely to need them. ;)

---

### Post by TheFu on 2023-04-02
> **euphorbialand said:**
> Like Grucash, HomeBank and KMyBank. On some of them there is description "Potentially unsafe, third party application".  But they were recommened on sites that looked trustworthy. 

GnuCash is in the normal repos. I don't know about the others.  Best to stay in with software in the repos.

---

### Post by euphorbialand on 2023-04-02
I made extended SMART DATA AND SELF TEST. It says that "disk is OK".

---

### Post by TheFu on 2023-04-02
> **euphorbialand said:**
> I made extended SMART DATA AND SELF TEST. It says that "disk is OK".

That summary is a default. It is the detailed, columns, with data that matter.  I've never seen SMART say the disk wasn't fine, even after it has 50% of the relocatable sectors used up.  The details matter.  Specifically check the attributes with "error" and "relocated" in their names.  You want to see '0' in the raw data column.

---

### Post by euphorbialand on 2023-04-02
Removed google link.

---

### Post by TheFu on 2023-04-03
> Unable to connect

An error occurred during a connection to drive.google.com. 

Our network blocks most of google, image sharing, file sharing and social network sites. Basically, if the primary goal of the company is to gather information on clients (paid or unpaid), then we block them.  Sorry.

But honestly, reading someone else's logs aren't really enjoyment for me.  I review 20+ system logs daily as part of my job.  Pair them down to the important parts only and post those here within *forum code tags*.  The easier you make it for others to help, the faster and better the answers will be.  I'm just being honest.

SMART data isn't long. The important parts are about 35 lines and easily posted here.  Text is always preferred over any wrapper.

Or wait for someone else to look. There are lots of people willing to look at full logs here.

---

### Post by euphorbialand on 2023-04-03
I am not sure how to interpret SMART results and what is the state of my hard drive. I understand the reason why Google is not accepted here. I will remove the link from my post. There are 7 columns. Last two columns "updates" is always online and "assesment" is always OK.
 I will type in lines with the values other than 0.

   Attribute                                   value                    normalized        t
Power cycle count 6722 93 0 93 old age
wear leveling count 459 87 17 87 prefail
used reserved blocks chip 180 94 10 94 prefail
used reserved blocks total 338 94 10 94 prefail
hreshold           worst           type
Judging from not zero values my hard drive might be in bad shape which would not be surprising for the 10 years old computer. 
Could you tell me what is the state of my hard drive based on these results?
And thank you for your assistance and valuable information. I didn't know that I could diagnose the system problems from the log and that I could also evaluate state of my drive using SMART test. 
So far my computer is at good behavior with a new mouse.

---

### Post by TheFu on 2023-04-03
The last column from the **smartctl** output is missing.  That's the most important column.  Also, without code tags, things don't line up and make it hard to read. If you are using a tool that doesn't provide the raw data for SMART, use the correct tool.  For every attribute, you can lookup what they mean by the number.

 _normalized threshold worst_ columns are nearly worthless to me.  The columns for SMART attributes should be:
```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   000    Pre-fail  Always       -       **0**
  5 Reallocated_Sector_Ct   0x0032   100   100   010    Old_age   Always       -       **0**
...
```

Don't worry about "prefail" or "old age".  If you run a smart test on a brand new drive, it will say the same.  NVMe SSD SMART data sorta sucks, but SATA SSDs follow the SATA SMART data, which can be very useful.

---

### Post by euphorbialand on 2023-04-03
I lined it up in columns but after posting all columns got packed together. But I don't want to take more of your time. I will google for SMART info. I am sure everything is available if I spend enough time and I learn something in the process. As for the system problem I am almost sure that it was a broken mouse. I replaced mouse and I should be OK.
Once more thank you for your assistance and for your time to answer my questions.

---

### Post by TheFu on 2023-04-04
> **euphorbialand said:**
> I lined it up in columns but after posting all columns got packed together. But I don't want to take more of your time. I will google for SMART info. I am sure everything is available if I spend enough time and I learn something in the process. As for the system problem I am almost sure that it was a broken mouse. I replaced mouse and I should be OK.
Once more thank you for your assistance and for your time to answer my questions.

There's nothing to copy/pasting terminal output into these forums, then wrapping that output with 'code-tags'. No formatting changes are needed at all. If you were doing anything like that, you were doing it wrong, I'm sorry to say.  For example, the following took about 10 seconds, total:
```
NAME                                  SIZE TYPE FSTYPE      LABEL      MOUNTPOINT
nvme0n1                             465.8G disk                        
&#9500;&#9472;nvme0n1p1                            50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                           600M part ext4        boot       /boot
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9500;&#9472;vg00-swap                         4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                      35G lvm  ext4        root       /
  &#9500;&#9472;vg00-var                           55G lvm  ext4        var        /var
  &#9500;&#9472;vg00-home                          26G lvm  ext4        home       /home

```
Without code tags, it looks like this:
> NAME                                  SIZE TYPE FSTYPE      LABEL      MOUNTPOINT
nvme0n1                             465.8G disk                        
&#9500;&#9472;nvme0n1p1                            50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                           600M part ext4        boot       /boot
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9500;&#9472;vg00-swap                         4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                      35G lvm  ext4        root       /
  &#9500;&#9472;vg00-var                           55G lvm  ext4        var        /var
  &#9500;&#9472;vg00-home                          26G lvm  ext4        home       /hom
See the issue?

---

### Post by euphorbialand on 2023-04-04
I don't have smartctl column in SMART results.
 
As for the code tag I might be using it wrong. But it did not work. I went to "Go Advanced" clicked on hash tag at the beginning and the end of the text. Then edited text with lined up columns and it did not work. It came out the same way. 

[COLOR=#000000]Attribute                        value                    normalized            threshold           worst       type[/COLOR]
[COLOR=#000000]Power cycle count          6722                             93                   0                       93             old age [/COLOR]
[COLOR=#000000]wear leveling count 459 87 17 87 prefail[/COLOR]
[COLOR=#000000]used reserved blocks chip 180 94 10 94 prefail[/COLOR]
[COLOR=#000000]used reserved blocks total 338 94 10 94 prefail

[/COLOR]

---

### Post by TheFu on 2023-04-04
**smartctl** is the name of the program to use to get SMART data. The use of that tool is both in a few forum posts here and in the manpage for the command.

In post #14, I showed a few SMART attributes for a local disk here.  I run short tests weekly, since they are so easy and provide plenty of data.  I should run long tests monthly and setup a script to do that a few years ago, but didn't follow up to ensure those are working too.  Whenever there's a SMART error, I get an email from the system telling me about the error and how it changed from 0 to 2 or something like that.  smartmontools has lots of ways to monitor smart data for our disks.

'Code tags' work best here when copy/pasting terminal output.  This isn't a trick question.  Use them just like you'd use quote or bold tags. You should never be adding or removing spaces or typing anything specific - we wan the copy/pasted terminal text.  If it takes more than 10 seconds, then you are doing it wrong. This isn't trying to put a challenge to getting help, I'm just not good at explaining, I suppose.  There are lots of threads here where others request code-tags be used and provide a short how-to. Perhaps one of those will "click" for you?

---

### Post by euphorbialand on 2023-04-04
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292022&stc=1[/IMG]I found a link how to install and how to use smartctl. I hope this link is legitimate:
[https://linuxhint.com/install-and-configure-smartctl-on-ubuntu/](https://linuxhint.com/install-and-configure-smartctl-on-ubuntu/)
 and will not be rejected by this forum. 
If this is trustworthy site I will definitely follow instruction and install this application. I am careful with using terminal because I am afraid to crush the system. Could you confirm that this site is OK to follow?

As for the code tags, I did not copy results from the terminal. This SMART test was the result of running GUI "DISKS" application. So I just typed in results using spaces to line it up in columns. That is probably the reson why code tags did not work. I suppose it only works with pasted terminal contents. I attached my file I hope it worked. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292022&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292022&stc=1[/IMG]

---

### Post by TheFu on 2023-04-04
I use 
```
sudo $SMARTCTL -t short  /dev/nvme0n1

```
wait for the test to complete, then to get a report, use:
```
sudo smartctl -a  /dev/nvme0n1

```
The device file needs to be for the hole disk, not any partition.

*Gnome Disks* probably dumbs down the SMART output to a useless level. Not worth your time.

---

### Post by euphorbialand on 2023-04-04
This is a description of my device. after using  command "smartctl -h /dev/vda"

== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG MZMPC256HBGJ-000L1
Serial Number:    S112NEACA09408
Firmware Version: CXM13L1Q
User Capacity:    256,060,514,304 bytes [256 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
TRIM Command:     Available
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS T13/1699-D revision 4c
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue Apr  4 15:54:29 2023 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled



When I use test mode
stefania@stefania-Lenovo-IdeaPad-Yoga-13:~$ smartctl -t short /dev/vda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.19.0-38-generic] (local build)
 

/dev/vda: Unable to detect device type
Please specify device type with the -d option.
Use smartctl -h to get a usage summary


Following your command:
stefania@stefania-Lenovo-IdeaPad-Yoga-13:~$ sudo smartctl -t short /dev/nvme0n1
stefania@stefania-Lenovo-IdeaPad-Yoga-13:~$: command not found
Command 'sudo:' not found, did you mean:
  command 'sudo' from deb sudo (1.9.9-1ubuntu2.3)
  command 'sudo' from deb sudo-ldap (1.9.9-1ubuntu2.3)
Try: sudo apt install <deb name>

I don't know what else I could do.

---

### Post by TheFu on 2023-04-04
a) when posting terminal output, please, please, use code tags.
b) you have to know the correct device name on your system.  vda and nvme0n1 aren't likely correct.
c) If the sudo command isn't there, I have to ask are you even on Ubuntu? I can't imaging any ubuntu system working without it. Further, you can't manage a system without it.  I'm at a loss.

Could your default character set not include the latin alphabet?  I'm reaching here.   Maybe just open a new terminal window and try again.  But you need to know the correct device names.  I can't easily show you examples, because my storage isn't normal.  
If you will run and post the output from  this command, the device names should be clear:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
I'm sure there are a few GUI methods to get this same data, but those aren't trivial to copy/paste into these forums.

In the meantime, perhaps this reference would be helpful?  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Free, no-hassle download.

---

### Post by euphorbialand on 2023-04-04
1. I am using code tags before and after the code. I think I did not use it correctly. Maybe this time it will work.
2. sudo works all the time on my terminal. I installed different applications using this command. I installed smartctlr using sudo command. I don't know why it does not work in this case.
Here is your command: and the results.

stefania@stefania-Lenovo-IdeaPad-Yoga-13:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
```

Filesystem     Type  Size  Used Avail Use% Mounted on
dev/sda2      ext4  234G  192G   30G  87% /
/dev/sda1      vfat  511M  6.1M  505M   2% /boot/efi

```

Thanks for the link. I will look into it.

---

### Post by euphorbialand on 2023-04-04
The book is interesting. Although it is like learning DOS all over again. I hope I don't need most of the commands since I have GUI for most of functions. 
I did the command and the test was executed. The results are almost the same as on GUI test except that there is a first column with flag with hex value. Anyway. I learned a lot and I appreciate giving a crush cource on Ubuntu commands. 

```

$ sudo smartctl -t short /dev/sda1

```

```
== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Tue Apr  4 19:06:44 2023 PDT
Use smartctl -X to abort test.



```

I run the same test with SDA2
I retrieved them with this command:

```
[COLOR=#000000][FONT=monospace]sudo smartctl -a /dev/sda1[/FONT][/COLOR]
```

```

vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       13504
 12 Power_Cycle_Count       0x0032   093   093   000    Old_age   Always       -       6729
175 Program_Fail_Count_Chip 0x0032   100   100   010    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   100   100   010    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0013   087   087   017    Pre-fail  Always       -       459
178 Used_Rsvd_Blk_Cnt_Chip  0x0013   094   094   010    Pre-fail  Always       -       180
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   094   094   010    Pre-fail  Always       -       338
180 Unused_Rsvd_Blk_Cnt_Tot 0x0013   094   094   010    Pre-fail  Always       -       6190
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   070   043   000    Old_age   Always       -       30
195 Hardware_ECC_Recovered  0x001a   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   253   253   000    Old_age   Always       -       0
233 Media_Wearout_Indicator 0x003a   198   198   000    Old_age   Always       -       2464
234 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       0
235 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       163
236 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       294
237 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       459
238 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       338



```

---

### Post by TheFu on 2023-04-05
/dev/sda1
**That's the wrong device.** It is a partition, not the whole drive.
You need to use the whole disk, which is  /dev/sda
With some commands, you'd have just wiped the entire partition.  Be careful running commands as root.  Bad things can happen.

That drive appears to be an old SATA SSD.  I'd lookup what the 233-238 attribute IDs mean. That 233 seems a bit scary.
Have you really rebooted 6700 times?  That seems excessive, it is more than once a day, every day.

---

### Post by euphorbialand on 2023-04-05
Yes I boot a computer more than once a day. I only keep it on when I need it. I did the test on SDA instead o SDA1 and SDA2. 

```

D# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       13506
 12 Power_Cycle_Count       0x0032   093   093   000    Old_age   Always       -       6731
175 Program_Fail_Count_Chip 0x0032   100   100   010    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   100   100   010    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0013   087   087   017    Pre-fail  Always       -       459
178 Used_Rsvd_Blk_Cnt_Chip  0x0013   094   094   010    Pre-fail  Always       -       180
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   094   094   010    Pre-fail  Always       -       338
180 Unused_Rsvd_Blk_Cnt_Tot 0x0013   094   094   010    Pre-fail  Always       -       6190
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   068   043   000    Old_age   Always       -       32
195 Hardware_ECC_Recovered  0x001a   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   253   253   000    Old_age   Always       -       0
233 Media_Wearout_Indicator 0x003a   198   198   000    Old_age   Always       -       2464
234 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       0
235 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       163
236 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       294
237 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       459
238 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       338


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     13506         -
# 2  Extended offline    Completed without error       00%     13504         -
# 3  Short offline       Completed without error       00%     13504         -
# 4  Short offline       Completed without error       00%     13504         -
# 5  Short offline       Completed without error       00%     13504         -
# 6  Short offline       Completed without error       00%     13495         -
# 7  Extended offline    Completed without error       00%     13490         -
# 8  Extended offline    Completed without error       00%     13489         -


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

### Post by TheFu on 2023-04-05
Well, it appears that the version of smartctl you have is smart enough to recognize a partition and figure out the drive device.  Consider yourself lucky.  It wasn't always that way.

Did you look up the attribute meanings for 233+ attributes yet?  Those raw numbers could be completely unimportant OR they could say the drive will fail this week.

---

### Post by euphorbialand on 2023-04-06
234 - Percentage total program-erase count/maximum erase count
235 - Power fall backup health/POR, recovery count/good block count 

[https://www.micromat.com/product_manuals/drive_scope_manual_01.pdf](https://www.micromat.com/product_manuals/drive_scope_manual_01.pdf)

236 - 238 vendor specific

This is all I could find. Other sites don't even list these numbers. I don't worry about my hard drive. If it fails I have backups. Then I will either replace it or buy a new computer.

---

### Post by TheFu on 2023-04-06
Ok, we got sidetracked with the disk aspect.  Let's assume it is fine.
Have you booted an Ubuntu ISO from a USB Flash drive into "Try Ubuntu" mode and do the issues still happen?  That was suggested in post #5.  

While in that mode, you should run fsck on all native Linux file systems too. That would be 
```
sudo fsck -t ext4 /dev/sda2
```
If it finds issues, allow it to repair them.

if the drive is still on that same device.  Drives change letters sd**a**, sd**b**, sd**c**, sd**d**, based on discovery order at boot time, so after each boot, we have to check for the correct device name.  File systems usually are placed into partitions, so that adds a number after the drive device. Using the prior data posted, sda**2**.

Anyway, 2 more steps to try.  We're working this in order.

After those, I have other ideas for slow booting, but don't want to get too far ahead.

---

### Post by euphorbialand on 2023-04-06
I am fine with my computer for now. After I replaced a mouse my system is booting without problems. I don't want to do anything else about it according to saying "If it works don't fix it". I sure will get back to this forum or to you if I have issues down the road. For now I would consider my problem solved. 
Thank you for your time and effort to help me. I learned a lot in the process. I know how to test hard drive, I know that I can view logs to diagnose the problem before I ask for help, and I have a handout for Linux commands if I need to use it.

---

### Post by TheFu on 2023-04-06
To help the wider community, please use the "Thread Tools" button and mark this thread as "SOLVE" in the DB.

For slow booting slow issues without log errors/warnings and after the storage has been checked, run these 2 commands to gather information:

**inxi -bz**; this will show an overview of the hardware installed - helps others understand what you have so their expectations are set correctly.
**systemd-analyze critical-chain** ; this shows the dependencies in the boot process and how long each took.  There are many, many, many, things that Ubuntu will start at boot which are completely unnecessary. They, Canonical, has decided that making things easy is more important than making things fast.  Easy usually means "bloated", however.

For example, here's mine:
```
$ systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @4.193s
&#9492;&#9472;multi-user.target @4.193s
  &#9492;&#9472;postfix.service @4.191s +1ms
    &#9492;&#9472;postfix@-.service @2.047s +2.142s
      &#9492;&#9472;network-online.target @1.928s
[B]        &#9492;&#9472;NetworkManager-wait-online.service @1.705s +207ms
          &#9492;&#9472;NetworkManager.service @1.634s +70ms
[/B]            &#9492;&#9472;network-pre.target @1.633s
              &#9492;&#9472;ufw.service @1.078s +555ms
                &#9492;&#9472;local-fs.target @1.070s
**                  &#9492;&#9472;run-user-112-gvfs.mount @3.363s**
                    &#9492;&#9472;run-user-112.mount @2.711s
                      &#9492;&#9472;swap.target @780ms
                        &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\>
                          &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd3
```
I have no use at all for the bold'd lines.  I don't use them.  I would save over 4 seconds by preventing those things from booting.  Let's see if that actually works, since the real world isn't usually the same.  I removed both those dependencies .... 

```
$ systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @4.878s
&#9492;&#9472;multi-user.target @4.878s
  &#9492;&#9472;postfix.service @4.873s +4ms
    &#9492;&#9472;postfix@-.service @2.291s +2.581s
      &#9492;&#9472;network-online.target @2.278s
        &#9492;&#9472;systemd-networkd-wait-online.service @2.239s +33ms
          &#9492;&#9472;systemd-networkd.service @2.136s +101ms
            &#9492;&#9472;network-pre.target @2.132s
              &#9492;&#9472;ufw.service @1.403s +729ms
                &#9492;&#9472;local-fs.target @1.393s
                  &#9492;&#9472;run-user-112.mount @3.492s
                    &#9492;&#9472;swap.target @964ms
                      &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\x2>
                        &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\>

```
So, it is a little slower in the real world, but still fast compared to what most people would have, I expect.
**systemd-analyze blame** is another way to see what's taking a long time.
```
$ systemd-analyze blame 
2.581s postfix@-.service
2.234s munin-node.service
 729ms ufw.service
 711ms systemd-udev-settle.service
 440ms accounts-daemon.service
 434ms networkd-dispatcher.service
 355ms ubuntu-system-adjustments.service
 281ms gpu-manager.service
 281ms cups.service
 267ms avahi-daemon.service
 257ms systemd-logind.service
 253ms chrony.service
 241ms zfs-share.service
 226ms user@112.service
 221ms systemd-machined.service
 220ms libvirtd.service
...
```

The systemd-analyze tool has some very important caveats.  Definitely read the manpage to learn those. The output doesn't always mean what we think it does. That goes for me too. Programmers sometimes use incorrect names for what they are really showing.

Also remember that things that slow my system boots are very different from things that will slow other system boots. We have different hardware and our configurations are different. 

The speed of the disks being found (USB is slow) and ensuring that extra NIC ports are specifically "optional" is probably the two things I run into most often slowing boots on my systems.  Some systems here are on multiple networks and have extra, unused, ethernet ports. At boot time, the OS will try to connect those unused ports, until a timeout happens.  One system takes nearly 35 seconds to boot, but it has 10 disks connected and it runs a number of virtual machines which are part of the slowdown. Since I reboot about once every other week, it isn't a big deal.  I can get some tea while the reboot is happening. ;)

Can't remember if I posted this link, so here's a no hassle download: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  for the Linux Command Line.

---

### Post by euphorbialand on 2023-04-06
I marked this thread as solved. I don't have slow boot problem but I will keep in mind this information for the future reference. Since the thread is already showing on Google other people might benefit from your information as well.

---

