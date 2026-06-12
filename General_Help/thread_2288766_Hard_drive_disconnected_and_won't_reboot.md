---
title: "Hard drive disconnected and won't reboot"
date: 2015-07-29
forum: General Help
---

### Post by John_Carver on 2015-07-29
Due to a mishap, the hard drive was physically disconnected (system was shut down) and now connected won't reboot.
Suggestions?  Thanks

---

### Post by yancek on 2015-07-30
The first thing to check is obviously that the connections are secure.  What OS are you running?  Is this the only operating system on the computer?  Do you have a Linux Live CD available?  Re-connected to the same port?

---

### Post by John_Carver on 2015-07-30
[QUOTE=yancek;13329986]

The first thing to check is obviously that the connections are secure.   Yes

What OS are you running?   xubunt 15.05

Is this the only operating system on the computer? I have ubunut 14.04 lts

  Do you have a Linux Live CD available? Yes and it can't find the hard drive

I can boot with a usb flash drive setup with startup disk creator but the image won't install

---

### Post by Bashing-om on 2015-07-30
John_Carver; Hello ,

We are here to help in your time of trouble.
yancek ask:
> 
Do you have a Linux Live CD available? 

Your reply:
> 
I can boot with a usb flash drive setup with startup disk creator but the image won't install

What is required here is a LiveDVD(USB) of the installed operating system. We will not install anything additional to that hard drive at this time. We just want to look at the situation.

To that end, boot up the liveDVD in "try ubuntu" mode to a termimal.

Post back the results - Between Code Tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
(lower case ells)
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

upfront. IF bios does not see that hard drive, there is nothing that can be done, at our level , until bios does recognize that drive.
If presently bios does not see the drive, change out the cables, and/or too change the controller port that is presently used .

[INDENT][INDENT]it all starts in bios
[/INDENT][/INDENT]

---

### Post by John_Carver on 2015-08-01
The last command shows: start 131k  end- 4048MB size 4068MB  type- primary  Flags- boot, hidden
It is difficult to transfer the screen on the live CD
I have taken a picture of the output if you can give me an email address to send it.

Appears  obvious the boot is hidden and i can't connect.
The question becomes how to find the hidden boot
Thanks for sticking with this.

---

### Post by Bashing-om on 2015-08-01
John_Carver; Hey ;

let's use our paste site to relay command outputs;
install the tool:
```

sudo apt-get install pastebinit

```
Now we can see these results by :
```

sudo parted -l | pastebinit

```
When the above is executed the result is a URL back to your terminal. Pass that URL back here to the thread and we can see that generated file that is now residing on the pastebin site .

However, the liveDVD has a browser , and should be no problem to copy and paste commands and outputs back into the thread.
I really want to see that complete output. And in between code tags to maintain formatting and readability.
Presently, we want to look at the hard drive(s), and what the partitioning info is.

[INDENT][INDENT]we work with 
[INDENT][INDENT][INDENT]what we have to work with
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by John_Carver on 2015-08-01
Here ya go

paste.ubuntu.com/11983510/

---

### Post by pqwoerituytrueiwoq on 2015-08-01
your hdd is not showing up, does the BIOS show it?
verify it is connected, if it is mechanical you can hear/feel it running if it has power
either the drive has failed or something is not connected (bad cable is possible)
*make sure the sata port it is connected to is enabled (assumes you are not using IDE ribbon cables)

---

### Post by John_Carver on 2015-08-01
solved the problem
the problem was me
sorry I put you through all of this
I had checked wiring before but had missed on it
Kinda like looking both ways before entering an intersection
I only looked one way this time

The scanner comments at the end of your thread about the scanner surprised me
I was having this problem and it was telling me I had a malformed command on xsane on my ASUS
Strange your comment was there

---

### Post by Bashing-om on 2015-08-02
John_Carver; Great !

In the end all that matters here is that there is resolution.
Pleasing that you provided the solution.
Please mark this thread solved:
(1st post -> thread tools)

[INDENT][INDENT]I look forward to our next adventure
[/INDENT][/INDENT]

---

