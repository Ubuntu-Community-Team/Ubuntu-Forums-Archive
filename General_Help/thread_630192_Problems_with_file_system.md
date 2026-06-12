---
title: "Problems with file system"
date: 2007-12-03
forum: General Help
---

### Post by hraposo on 2007-12-03
I'v problems with my file system in one partitin. I run 2efsck -y during a nigth but when I boot, the system stops, a said that are probles with the file system. And the only way of continuing is to do CRT+D.
How I can solve this problem?
Is the command 2efsck -y correct to repair the file system? If not, what command?
There are any program to check and repais the file system?

---

### Post by Herman on 2007-12-03
The easiest way to run a file system check these days is to boot your Gutsy Gibbon Live CD, (Feisty or earlier won't do, it has to be Gutsy Gibbon), and go 'System'-->'Administration'-->'Partition Editor', and open GParted Partition Editor.
Then you right-click on the partition housing the file system you want to have the check run on. 
From the right-click menui, you select 'Check'.
Click 'Apply' on the toolbar.
Click 'Apply' in the confirmation box.
Wait while the file system check runs.
When it has finished don't forget to expand the window several times to see all the information about what happened.

That's it!

That will fix 99% of problems in most file systems without the user even knowing how to type a command at all.

If you still get the pause in booting even after running the file system check, the problem will most likely be that you have reformatted a partition or deleted a partion and forgotten to update your /etc/fstab file.
Our /etc/fstab files use UUID numbers to specify each file system now, so you might need to check your /etc/fstab file to make sure those are correct.

Here is a handy command to get a list of your file systems and their UUID numbers,
```
ls /dev/disk/by-uuid/ -alh
```Here are the commands to make a backup copy of your /etc/fstab file before editing it, just in case you or someone else reading this post might be new here,
```
sudo cp /etc/fstab /etc/fstab_backup
```And here's the command to open the file.
```
sudo gedit /etc/fstab
```Just compare the file system UUID numbers with the ones you got from the first command I posted here and make sure they correspond. If you see one that doesn't match, copy the one from the command and paste it over the offending UUID number in your /etc/fstab file to overwrite the obsolete number with the current UUID number for the file system currently in the partition.
Or maybe there's an extra number there from a partition you have deleted, if so, you can either delete the entry in /etc/fstab or at least comment it out by tying a # at the beginning of the line.
Save and exit the file.
Next time you reboot, your Ubuntu operating system should reboot like new again! 

For more information: [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm") 

Regards, Herman :)

---

