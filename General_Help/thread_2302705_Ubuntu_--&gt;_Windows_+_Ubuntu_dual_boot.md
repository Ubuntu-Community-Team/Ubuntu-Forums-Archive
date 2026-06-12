---
title: "Ubuntu --&gt; Windows + Ubuntu dual boot"
date: 2015-11-12
forum: General Help
---

### Post by james181 on 2015-11-12
Hey guys, new time Ubuntu-er here and I've got a couple questions. This laptop I am currently using has been through a lot and it recently had a hard drive failure. On the new hard drive, I had some technicians install Ubuntu instead of windows (thought I could just jump right in). I (kinda) regret this decision but was wondering what steps I have to take in order to uninstall this version of ubuntu, reinstall windows, and then REinstall ubuntu while windows is back on my machine to just have a dual boot setup. This may or may not be because I cant play Fallout 4 on this Laptop. 

Thank you guys for any help you can provide! 

James

---

### Post by yancek on 2015-11-12
I don't know that you would need to format the Ubuntu partitions.  I think current windows installers allow you to select a partition.  I haven't installed windows for years so I'm not sure about this.

When you boot the windows installation medium, check to see if you can do that.  Otherwise, just format the partition with a windows filesystem and leave some space for Ubuntu.  Which release of windows are you using and are you using UEFI/GPT on it?

---

### Post by oldfred on 2015-11-12
In addition, post this:
sudo parted -l

---

### Post by james181 on 2015-11-12
> **yancek said:**
> I don't know that you would need to format the Ubuntu partitions.  I think current windows installers allow you to select a partition.  I haven't installed windows for years so I'm not sure about this.

When you boot the windows installation medium, check to see if you can do that.  Otherwise, just format the partition with a windows filesystem and leave some space for Ubuntu.  Which release of windows are you using and are you using UEFI/GPT on it?

So basically I would need to figure out how to uninstall Ubuntu, find or buy a new windows key, then partition my drive to allow space for ubuntu? Im very new to the technical aspect of computers and messing with settings gives my anxiety so I dont think this will be an easy process for me but I'll try and keep you guys updated. Im trying to use Windows 7 btw (I think thats what you were asking).

James

---

### Post by james181 on 2015-11-12
> **oldfred said:**
> In addition, post this:
sudo parted -l

Sorry to sound like an idiot but what does this do/at what point in my process would I do this

James

---

### Post by oldfred on 2015-11-12
That will show your existing partitions, so we can make better suggestions.

From either your install or a live install you can go to the terminal and copy & paste command into terminal.

---

### Post by yancek on 2015-11-12
> So basically I would need to figure out how to uninstall Ubuntu,

No.  Ubuntu is an operating system not an application so there is no "uninstall", you simply format the partition.  The first step if you are going to use windows 7 is to boot the installation DVD and start the setup and see if it recognizes various partitions.  The problem is that naming conventions are different in windows vs. Linux.  What you see as C in windows could be any primary partition, usually it is installed at the beginning of the drive and might need a boot partition. 

If you have the windows DVD from another computer which you are no longer using, you should be able to use it on another computer.  Not sure what the process is with this as I haven't installed windows in over 10 years but you would likely need to contact them.

Next step, post the output of the command suggested above.

---

