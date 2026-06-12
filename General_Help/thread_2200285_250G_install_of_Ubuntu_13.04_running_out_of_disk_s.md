---
title: "250G install of Ubuntu 13.04 running out of disk space - but less than 6Gs on it"
date: 2014-01-18
forum: General Help
---

### Post by tamccullough on 2014-01-18
Hi.

Hopefully someone can help me out here. I recently rolled back to 13.04 because of problems.
Messed up a hard drive in the process.

Now I am trying to recover files with Testdisk from that hard drive.

Recently though, the OS is telling me I am low on disk space, when there is 230G of free space.

For some reason, the Disk Analyser thinks that I am low on space within some of the folders that I have been putting recovered files into. It shows that these folders are at 100% capacity!

Very confused.

I have never used the Cinnamon desktop in Ubuntu and just recently installed it. Could that be part of the problem?

---

### Post by Frogs Hair on 2014-01-18
13.04 loses support in about two weeks and you might not want put in the effort trouble shooting it.  If 13.10 is problem 12.04 LTS might be a better option until 14.04 LTS  is released in April.

---

### Post by grahammechanical on 2014-01-18
Please tell us the exact message that the OS is giving when the OS tells you that you are low on disk space? What partitions do you have on that hard disk and what are their sizes? Where are you copying those recovered files to? A USB memory stick? Or a partition on another hard drive? Or a partition on the same hard drive?

Disk Usage Analyser always shows the / folder as 100.0% usage. Folders are of variable size to allow files to be stored in them. The size of the / folder is a total of all the file sizes in all the folders under the / folder. Disk Usage Analyser measures the size of every item in every folder under the / folder and presents those sizes as a percentage of the total size of all the items in the / folder. So, the percentage of the / folder that is used will always be 100%.

Right now I am running a version of Ubuntu in a partition that File Manager tells me is 36.8 GB capacity and that the partition is 17.4 GB used and 17.5 GB free. Disk Usage Analyser tells me that the size of the / folder is 17.3 GB and Usage is 100%. If I add some files by installing an application then the size of the / folder will increase and it will still be at 100% usage. If I remove an application the size of the / folder will decrease but it will still be 100% usage.

So, we come down to the message that the OS is giving warning you that the disk/partition is full. What is that message exactly?

Regards.

---

### Post by tamccullough on 2014-01-18
Hi guys. Looks like I must not have hit submit on my reply to you Frogs Hair. I mentioned that I rolled back from 13.10 to 13.04 due to what I believe were graphics problems associated with MIR. I'm a low level user though, so what do I know.

grahammechanical - so the strange thing is that 13.04 is installed to a 250GB hard drive, using all available space on the install. I am recovering directly to my Documents folder (or so I believe - testsdisk is doing it automatically) so there should be zero issue about space. I'm only searching for .zip type files, so there should be no more than 6 GB found regardless.

The message if I remember correctly is that testdisk has stopped because of low disk space, and a pop up states that I am running low on disk space.

Maybe it's related to the fact that testdisk is only searching for a specific file type. I figure this might be one of those problems that not many people have ever encountered because I'm doing something that is not often done.

---

### Post by deadflowr on 2014-01-18
Off topic, but did you install MIR?

---

### Post by Frogs Hair on 2014-01-18
> Frogs Hair. I mentioned that I rolled back from 13.10 to 13.04 due to what I believe were graphics problems. I didn't want you to put too much effort into a release that was about to reach end of life , but using 13.04 is your choice . Deadflowers question is important because Mir was not stable on 13.10 and not installed by default.

---

### Post by tamccullough on 2014-01-18
> **Frogs Hair said:**
> I didn't want you to put too much effort into a release that was about to reach end of life , but using 13.04 is your choice . Deadflowers question is important because Mir was not stable on 13.10 and not installed by default.

Interesting. Then I guess it was never installed.

Which makes me wonder what the issue was. None of theses flavours worked on this system - Ubuntu 13.10, UbuntuGnome 13.10 and linux mint 16 - all had the same problem. Freezing at the log in screen. So my assumption was that it was a graphic issue based around what I thought was the adoption of MIR.

So I grabbed Ubuntu 13.04 and installed it here, and absolutely no issues. Besides this current disk space problem.

So - No I never installed MIR myself. Sorry.
I know how it offends me when my windows friends make assumptions about linux. It must be annoying for high end users to hear similar sort of assumptions from guys like myself.

---

### Post by tamccullough on 2014-01-18
How about this...

Could it be my fault - because of how I am using testdisk?

Testdisk automatically creates locked folders within the directory that it is run out of. In order for me to remove those dirs I have used the chown command on the testdisk file folder. Could that be causing the progam itself to mistakenly detect a lack of space on the disk?

---

### Post by deadflowr on 2014-01-18
> [COLOR=#000000]I know how it offends me when my windows friends make assumptions about linux. It must be annoying for high end users to hear similar sort of assumptions from guys like myself.[/COLOR]

It doesn't bother most of us;), linux is a fast moving environment.
Things can change quickly. Ubuntu and mir are a prime example.
It was being pushed as the new display server, but when it was decided to hold it off, a lot of users didn't know, so...

On topic though, thinking about the disk usage analyzer, what were the biggest folders listed?
Disk Usage Analyzer lists from highest usage to lowest, you can usually easily see what folders are bigger than expected.
I never worry about the 100% thing, it just means 100% of the USED space, and not the overall space.
If that makes sense.

---

### Post by tamccullough on 2014-01-18
Well, the disk analyser says that it could not scan the folder "/" or some of the folders it contains - Permission denied

But it does show that the home folder with - Usage 54.0%, Size 6.5 GB - as the biggest. Followed by usr with - Usage 31.2%, Size 3.9 GB and some others.

I think I need to give testdisk another go. Maybe I need to reinstall the OS? Currently running testdisk on another system with the hard drive that I am trying to recover from. I need my .ora files from the last week.

---

### Post by tamccullough on 2014-01-18
Ok. So it may be a testdisk thing.

I'm currently running and monitor it right now on another machine. I've got the disk analyser and system monitor up and running as it looks for .zip files. It looks that it might create one large file on the machine as it searches.  Currently it hasn't found any zip files.

But while it is working it is creating a .sxw file that continues to bulk up. At the moment it is 82 GB. The disk I am trying to recover from is 500 GB and I am working with a 250 GB hd. So I think it must have made a temp file that it discarded after it was forced to stop.

It seems to me to be like that murder problem. Guy is murdered with an icicle, which melts, leaving detectives wondering what he was killed with!

---

### Post by Bashing-om on 2014-01-18
tamccullough;
Perhaps now it is time to break out some CLI tools and get a look at what is:
Terminal Codes:
```

sudo fdisk -lu ##if the partitioning is msdos else; gdisk
sudo parted /dev/sda unit s print
df -h
df -i
cd /
sudo du -sx * | sort -n

```
If you need to drill down further (du -sx), use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.

These will leave no doubt about the disk space usage.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

