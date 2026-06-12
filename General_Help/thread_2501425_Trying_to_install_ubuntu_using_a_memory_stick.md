---
title: "Trying to install ubuntu using a memory stick"
date: 2024-10-06
forum: General Help
---

### Post by jgw on 2024-10-06
I just thought to let this go.  I have figured out, after wasting an entire day, that I have to hve the sdd to install to on my machine when I start and then make sure I boot from the memory stick.  Other than that nobody need reply to anything unless its to point out that I am not particularly intelligent.  I thought I had read that I had to install the target sometime later than initial start.  I was flat out wrong.

I have created a memory stick which, in theory, will install ubuntu into a machine.  I will be using a 1tb ssd as the main drive for the system.  Here is what I have been doing.  I put the memory stick (startup system stick) into the machine.  The machine itself has no drives, other stick, etc. on or in it.  I pull the power on the machine and then plug it back in and start it.  After I turn on the machine, after a little bit of time, the system asks me what I want to do.  I press the one that asks whether I want to try or install ubuntu.  I press that I want to try.  That takes me to another screen.  I then run gparted and that is where I am running into problems.  After checking me when starting gparted I have it on the screen.  It shows me what is hooked up on the machine.  I have tested this a lot.  gparted tells me that /dev/sda/ 29.30 gib and  /dev/sdb/ 29.30 gib It tells me whether I have an ssd attached or not!  I have tried to delete them, find them, etc. and have no idea what its all about.  I have no idea why or where they comes from.  I do know that, if I have a 1tb ssd attached that it should know its there.  It happens no matter when the ssd in installed.  I have stopped at this point because it makes no sense to me.   this is approximately where I tell it to start with an a 1tb ssd but its not there.  Oh, Just to make sure I also connected some ssd's with something on them and that worked just fine showing me that my connections with the ssd tests were just fine.

So, I skipped that and moved directly to installing ubuntu.  There were some more questions, etc.  Then it asked me where to install and my choice was, as far as I could tell the 31gb memory stick (which was doing all of this stuff as well).  That was crazy.  It completely ignored the 1tb ssd.   I think one of them would have actually started to boot but I was just making sure that my connection with them was real and powered.  I am tempted to let it install but the only thing, besides the 1tb ssd is the memory stick.  if I let it go I will then have a memory stick with ubuntu on it I think.

For some reason the ssd's that I am trying to put ubuntu on are not being seen by the machines.  When I goto the try place I can then run programs and one that I ran, Disks, did not show the ssd's as being loaded.  That being the case my question becomes whether or why that cannot happen.  I am going to take another machine apart and put that ssd on and see if I can just make it run.

I took an sdd, from another machine, plugged it in, turned it on and it came right up!  For some reason its just not finding the sdd's to be installed but when they have been they work just fine.  Seems I am unable to install Ubuntu!  

Anyway, given my history I tend to believe that I have done something that makes no sense.  I would be grateful for any thoughts..........

Thoughts?

---

### Post by dragonfly41 on 2024-10-07
I will try to read between the lines.
So you get to the point where you can “Try Ubuntu”.
Now at that stage Ubuntu is running on your LiveUSB in memory. You can use that as a beach head to look around your SSD's and install. But first setting up partitions as below.

Correctly you have installed GParted.

One step to take in your target installation SSD is to use GParted to create several partitions.

I suggest that it might help in understanding if in LiveUSB you capture screenshots of Gparted and post here. 
A picture is worth a thousand words.  You can then post your gParted windows in your Ubuntu discussion to allow contributors here have more visibility of how many alligators are in your alligator pit.

There are various way of configuring Live USB to have tools preinstalled.

One is to use Cubic to preinstall any diagnostic tools such as GParted, Flameshot, notes Editor such as CherryTree. At least that is my approach but optional.

But that approach might be an overkill.

[https://www.reddit.com/r/linuxquestions/comments/hujwfi/are_installed_programs_retained_in_a_live_usb/](https://www.reddit.com/r/linuxquestions/comments/hujwfi/are_installed_programs_retained_in_a_live_usb/)

One person in above discussion suggested creating two partitions in your LiveUSB. One for the installation of Ubuntu. The other for application downloads you might wish to launch.

We shall continue assuming that these extras are not installed. So we have to explain in text what are the settings in GParted.

Now the target SSD has to be arranged. 

When I use GParted to view my SSD (holding desktop Ubuntu) I see ..

GParted - Edit - View - Device - Partition

To the right is a drop down menu showing all [devices] - not partitions yet

It might look like

/dev/sda
/dev/sdb
/dev/sdc

Now in my case /dev/sda is SSD device where I have Windows 10 (dual boot) tucked away.

And /dev/sdb is another SSD device where I have Ubuntu 22.04.

And /dev/sdc is where I have another Ubuntu installation.

I use an external USB 3.0 docking bay to hold multiple SSD's in dual caddies. Again optional.

Choose the target [device] where you wish to install Ubuntu when in LiveUSB you later commit to “Install Ubuntu” instead of "Try Ubuntu".

Now this target SSD device has to be configured with [partitions].

The Tabs in the GParted Window  (I have pivoted them below) read:

Partition
Name
Filesystem
Mount Point
Size
Used
Unused
Flags

The first [partition] /dev/sdc1 (for example depending on number and configuration  of devices) should be 

Partition        /dev/sdc1
Name             EFI System
Filesystem        fat32
Mount Point
Size            500MBS
Used            ---
Unused        ---
Flags            boot, esp


Note that boot flags are inserted into this first bootable partition in the [device]


The second [partition] /dev/sdc2 (for example depending on number and configuration  of devices) might be 




Partition        /dev/sdc2
Name        Ubuntu 22.04 LTS
Filesystem        ext4
Mount Point    /
Size            878.91GiB
Used            605.90GiB
Unused        273.01GiB
Flags                

The third optional [partition] /dev/sdc3 (for example depending on number and configuration  of devices) might be 


Partition        /dev/sdc3
Name        Ubuntu 22.04 DATA
Filesystem        ext4
Mount Point    /media/xxx/xxxxxxx (custom path to mounted Data)
Size            878.91GiB
Used              14.86GiB
Unused        864.04GiB
Flags                


Note: The above settings are examples only from my setup and will vary depending on size of SSD device and if it is split into multiple partitions of different sizes.

---

### Post by bobunderwood99 on 2024-10-07
Since you (hopefully) were in the habit of removing/replacing SSDs with the power on I suggest you may have one or more fried SSDs and one or more fried M.2 slots on your motherboards.

---

### Post by yancek on 2024-10-07
It isn't clear to me that you have the 1TB drive you want to install TO plugged in when you boot Ubuntu.  Is it?  If you can boot Ubuntu from the usb, get to the Desktop and open a terminal and copy/paste the command below there and post the output here which should provide some useful details.

```
sudo parted -l
```

---

### Post by dragonfly41 on 2024-10-08
How was this issue solved?

---

