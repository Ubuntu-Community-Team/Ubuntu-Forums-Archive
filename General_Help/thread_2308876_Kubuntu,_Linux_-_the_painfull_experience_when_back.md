---
title: "Kubuntu, Linux - the painfull experience when backing up onto USB drives"
date: 2016-01-06
forum: General Help
---

### Post by richlion2 on 2016-01-06
Hello, 

I am on the latest Kubuntu version. I think the problem I have is not new and we've been stuck with this for some time. I don't think this may be an Ubuntu problem, rather something around the Linux Kernel. 

I have a problem running backups of a 500GB drives into an external 2TB portable USB drive. However, not only portable, any external USB drive - USB 2.0 and 3. When I start the copy process using Dolphin Copy/Paste method the process starts and I can still use the system for a while. This can be on a powerfull 4-Core system. Copying small amounts of data does not present any problem. However when copying large amounts of data the whole system stalls, almost grinds to a halt. I can close all my applications and I can barely navigate in the system. I have 2 PC computers and at least 2 laptops, one is a powerfull 17" Acer, another one is the newest Toshiba ultrabook with and SDD and I consider it super fast. The same thing on all of them, the backup reaches aprox 50% completion and the system grinds to a halt. I left one such process to run over night. I came back this morning and the copy should have finished, yet the "notification" systray applet showed 16 pending operations, no progress bar and I had to press CTRL+ALT+DEL to initiate a shutdown process and that took me 30 minutes. Can someone explain where the problem is? I know that the Linux OS uses some good caching techniques and attempts to use the whole computers memory during the backup/copy process. This is rather an unacceptable situation, because half way through a backup process I cannot use the system at all - any web browsing, checking emails becomes impossible. It's like the copy process is hijacking my computer. I don't know what can be done. Is there any way to reduce the amount of memory is used during such a copy operation? What other methods can I use to backup 500+ GB of my files without having my OS resources saturated? Is this a Linux kernel design problem? Am I the only one who has this kind of an experience? It's easy to replicate it, so is this never tested? 

I would appreciate some hints. Thanks. 

Regards.
Richard

---

### Post by buzzingrobot on 2016-01-06
Are you trying to copy 500GB of files in a single operation? Try breaking it up into smaller chunks.  

If the 2TB drive is not permanently attached, and if it holds existing data, KDE may be trying to index it.  KDE wants to index any drive for its desktop search function unless it's been excluded from indexing in System Settings.  This includes external drives when they are attached, I believe. Indexing a large amount of data, on any OS, can be resource-demanding.

---

### Post by HermanAB on 2016-01-06
There is a USB bug that keeps coming back.  The bug that keeps on giving.

You need to use ionice with the copy process - so you need to use the command line.

---

### Post by mastablasta on 2016-01-06
yes, check for indexing.

as for ionice workarround - why do it "simple" (solve the bug) & automatic in the OS, when you can complicate it for the users...

never saw this kind of error since USB 1 in windows...

---

### Post by SeijiSensei on 2016-01-06
Do you have the same problems if you use rsync from the command prompt?

---

### Post by leunam12 on 2016-01-06
rsync is the man. I have never had any problems with it unless there is some kind of problem with the drive(s)
```
rsync -avP /source/directory/ /destination/directory
```
This example will copy all the files in the source directory to the destination directory. If there are existing files in the destination with the same name than in the source only the files that have a newer date/time stamp are transferred.

---

### Post by richlion2 on 2016-01-08
> **leunam12 said:**
> rsync is the man. I have never had any problems with it unless there is some kind of problem with the drive(s)
```
rsync -avP /source/directory/ /destination/directory
```
This example will copy all the files in the source directory to the destination directory. If there are existing files in the destination with the same name than in the source only the files that have a newer date/time stamp are transferred.

This seems like a decent workaround solution, I shall try that. 

On the other hand, I find it awkward that I have to take control of a simple process. To me how I copy 500GB to a USB drive should be simple. Then people suggest switching off indexing, then copying in chunks, yes, I can do all that, I don't mind using the BASH console. All that is fine, but if there is a bug with USB, then I'll be watching for fixes. To me, as I said at the beginning of the thread, this is not a new problem, it has existed over the past few years regardless of the distro, for examle until 1 year ago I was using Sabayon/gentoo - similar problem. To me it looks like a flaw in the concept somewhere around the kernel and how to report it. Linus? 

I will also try without indexing and see if I can eliminate that function.  I'll post the result.

When it comes to memory: my memory usage at the beginning of my session looks like this: Skype, Firefox, Chromium, Thnuderbird -  I have aprox. 1,5GB free (out of 4GB). When I add 1 or 2 prgrams I have about 400MB left in the system. That still should be enough to perform a backup/copy and any KDE indexing should not be hijacking my system. To me it's a bug, as simple as that. I dont blame Ubuntu here, so don't get me wrong. 

Thanks everyone, you are most kind and helpful.
Richard.

---

