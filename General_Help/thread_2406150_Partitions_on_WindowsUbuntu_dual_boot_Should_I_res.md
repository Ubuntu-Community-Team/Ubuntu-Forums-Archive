---
title: "Partitions on Windows/Ubuntu dual boot: Should I resize, if so, how?"
date: 2018-11-16
forum: General Help
---

### Post by Richard_York on 2018-11-16
[SIZE=2]I've installed Ubuntu 18LTS to dual-boot with Windows10 on this machine,[/SIZE][SIZE=2] with help received here,[/SIZE][SIZE=2] and so far it's working well.

Intel i5-2400
Asus P8Z68-V LX Mainboard
8GB Kingston HyperX DDR3
Graphics card,  NVIDIA GT 710/REV 1.0
320GB Hard Disk

Windows was pre-installed. We use Ubuntu nearly all the time, and Windows only to update the SatNav, and a couple of other things which won't work with Ubuntu. So Windows really only needs space enough to keep it working well. There will be very little stored in its MyFiles section.

With very limited understanding I rather blindly followed instructions, (either [https://www.techsupportpk.com/2018/05/how-to-install-ubuntu-1804-desktop-dual-boot-with-windows-10.html](https://www.techsupportpk.com/2018/05/how-to-install-ubuntu-1804-desktop-dual-boot-with-windows-10.html) or one very like it),  to shrink a partition and create a new one, while still on Windows, for Ubuntu to live in. Because the "how-to" page I followed suggested 40GB I used that.

Now I'm wanting to migrate from our old machine our "MyDocuments" files, plus years of Firefox Thunderbird emails, and I belatedly realise this isn't all going to fit in that 40GB, and that it would make much more sense for Ubuntu to access as much disc as possible.

Here's an image of the current disc partition looked at in Windows:
[ATTACH=CONFIG]281647[/ATTACH]

Here's the screenshot of the same disc looked at on Gparted in Ubuntu
[ATTACH=CONFIG]281646[/ATTACH]
Right-clicking for "properties" on my Home folder gives me this:
[ATTACH=CONFIG]281648[/ATTACH]


I blandly assumed Ubuntu would find and install itself into that 40 (which turned into 39.6 for some reason) GB and all would be well.

1st question - My understanding isn't up to working out where Ubuntu actually is residing, do these shots tell you where it is?
2nd - Am I right to now realise that MyDocs files are also going to need to live in that same partition, and that I'm going to need to grow it?
3rd - I'm finding conflicting advice by simply searching for "can I resize a partition having installed Ubuntu 18?" - can I resize it without having to lose everything & start all over again, with re-installation from scratch?
4th - if so, how?

This, [https://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/](https://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/)   from 2012, seems clear that I can't resize while I'm using the partition, which I take to mean, while I'm using Ubuntu. I don't know if that still holds in 2018. Assuming it does, and that resizing would help, could I make that resize while the machine was open in Windows instead, so saving myself the re-installation?

Sorry for a string of queries in one post, but it seemed better than making multiple threads!

Thanks for help, especially any in very simple steps.
 



[/SIZE]

---

### Post by Impavidus on 2018-11-16
1: Your Ubuntu is indeed installed in the 40GB partition. The gparted screenshot shows that it's an ext4 partition with mountpoint /. The slight confusion over the size comes from the difference between GB and GiB. A GiB is slightly larger than a GB and both partitioning tools use GiB, although the Windows tool mislabels it as GB.

2: You could put your documents into that partition, but you don't have to. You could instead make yet another partition. In fact, it's recommended that if you reserve more than about 40GB for Ubuntu, you keep separate partitions, one for the operating system, the other for your documents. Some people make even more partitions, but for a beginner a root partition and a /home partition would be perfect.

3: You can resize a partition, but you can't do so while the system installed on that partition is running.

4: You can resize it while running a live disk – the same one you used to install Ubuntu. Windows can't handle Linux partitions.

But my suggestion is something different. Make a /home partition.

First use Windows tools to defrag the big Windows partition, then use Windows tools to shrink it to about 50GB. Shrink it to the left. Reboot Windows to let it run all its filesystem checks. Then boot Ubuntu. Normally I'd use a live disk, but this can be done from the installed system. Create a big ext4 partition in the unallocated space between the Windows partition and the Ubuntu root partition. Then migrate your /home directory to this new partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You'll end up with partition of 200GB for your documents and one of 40GB for the operating system and applications. The latter is rather large, but it's probably not worth the effort of shrinking it.

---

### Post by Richard_York on 2018-11-16
Thank you. This gives me hope! De-fragging in progress as I write, on another machine. Not sure how to defragment a specified partition in Windows, but it can do the whole thing while it's at it.

Just to check before I re-size the wrong thing,  is the partition to shrink the third one along, labelled "C", 258.43 size, in the Windows partition image I showed? 

I take it that shrinking the 40GB current Ubuntu partition would probably stretch my abilities beyond their limits?

---

### Post by oldfred on 2018-11-16
Shrinking a partition normally is very easy & quick. But then your space would be at end of drive and you could only use that by moving the Linux partition. Moving partitions has higher risk, since it has to copy all data from one place to another, usually part by part. And then any interruption, power failure, forced stop, will totally corrupt partition.

Always have good backups of all installed systems before any partition changes.  Then if things go sideways, you can easily (with Linux) reinstall  & restore data.
Otherwise you become one of the many who do not backup and post how to try to recover data, often only some recoverable, if any is.

---

### Post by Richard_York on 2018-11-17
I've backed up on Ubuntu, then created the new, so far un-allocated, partition while on Windows. The Disk Manager dialogue box offered that I could shrink the Windows partition lower than 50GB, so I did - I'm wondering now if I should have stuck with the recommended 50GB? Should I re-size before moving on, or should this be OK, given our minimal use of Windows? Here's what GParted shows now.
[ATTACH=CONFIG]281664[/ATTACH]

Post#2  then says "Create a big ext4 partition in the unallocated space between the Windows partition and the Ubuntu root partition." I can find various "how to" pages all with different ways of doing this, too many to list here, but generally warning of dire consequences of getting it wrong. I can't evaluate which to use. What method would you recommend, please?

Thanks for your patience. I'll get there in the end :smile:

---

### Post by oldfred on 2018-11-17
I would also suggest keeping Windows at 50GB.
Windows NTFS wants 30% free or it starts to slow down. And at 10% free a defrag can take forever. Your about 20% so it will work, but a few updates or saving of files may fill that.

You use gparted from live installer to change partitions, normally.
Since gpt and only creating in unallocated space, you may be able to do it on gparted.
The little key icons show mounted partitions and those cannot be changed, or why live installer is normally required. With MBR any mounted partition prevents changes, but I have created a partition in unallocated space with a partition mounted on my gpt partitioned drive.

---

### Post by Richard_York on 2018-11-17
OK, Windows C partition is now approx 50GB - I find the GiB/GB confusion indeed confusing, but it's within points of 50.

OldFred, I'm sorry, I'm not yet up to understanding from the rest of your post what my next step should be - if I'm still following post #2 here, I'm looking to make my space into ext4 partition, unsure how.

Thanks for continuing help.

---

### Post by oldfred on 2018-11-17
In gparted, click on the unallocated and new should be an option. Then you can create a partition. It defaults to the entire space, so if you want more than one partition you have to resize. You then have to click on green check mark at top to actually complete changes.
If it does not work from inside your install then you have to to use live installer or create a gparted live flash drive from its ISO. 

       [URL="http://gparted.sourceforge.net/faq.php"]http://gparted.sourceforge.net/faq.php
      [/URL]
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
    [URL="http://gparted.sourceforge.net/faq.php"]
[/URL]

---

### Post by Richard_York on 2018-11-17
Reassuring - GParted indeed gives me that option on creating the new partition. As in:
[ATTACH=CONFIG]281665[/ATTACH]

* Am I to make it a primary or a logical partition? 

* I realise from the GParted tutorial link given that naming is critically significant - given my set up, as in image on post #5 here, what name should I give?

* And do I need to alter the given suggestion in "Align to" ?

* I'm guessing the label is less critical, so calling it something I recognise like Ubuntudata would hopefully be OK?

Sorry to ask for every step - having got this far I'm reluctant to lose it all by haste.

---

### Post by oldfred on 2018-11-17
Alignment is vital for SSD & new 4K drives. Older drives less so.
I like to label all partitions, but it is more important for those partitions I only mount occasionally so I know what they are. Otherwise they mount with UUID which I have no idea what the are.
With gpt all partitions are the same or in effect primary.

I do not have Windows but several Ubuntu installs:

```
fred@Bionic-Z170N:~$ lsblk -f
NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                         
&#9500;&#9472;sda1 vfat   ESP      D966-440A                            /boot/efi
&#9500;&#9472;sda2 ext4   xenial   5c1e1a3f-261f-4da5-a0c2-8f479b3039de 
&#9500;&#9472;sda3 ext4   ISO      ab916e15-8a74-4d6e-a0b1-32718a505dc7 /media/fred/ISO
&#9492;&#9472;sda4 ext4   bionic   c29fc361-ea05-420b-b919-850aeef65dd4 /
sdb                                                         
&#9500;&#9472;sdb1 vfat   ESP_B    F496-1330                            
&#9500;&#9472;sdb2 ext4   bionic_b 06cdd4fd-6a03-4880-9021-7febff21e4b1 
&#9500;&#9472;sdb3 ext4   ISO_b    c395f36d-5e02-4913-a904-e336054b2eff 
&#9500;&#9472;sdb4 ext4   backup_b dd4e4a2e-4785-4441-91b0-28234b98e625 /mnt/backup
&#9500;&#9472;sdb5 ext4   cosmic   75f5141c-8bab-4168-8855-4bf000406680 
&#9500;&#9472;sdb6 ext4   data     f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7 swap            3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9492;&#9472;sdb8 ext4   disco    507e4c47-28a0-49c6-bd59-364ba137e207 /media/fred/disco

```

---

### Post by Richard_York on 2018-11-17
So calling it /dev/sda6, since sda 1 to 5 are already taken, would be right, I think?   And from what that tutorial says, more than 4 makes it logical rather than primary, so these seem like the answers to go for. 
At 7 yrs old I'm guessing my drive counts as older.
Hope I have this right now!

---

### Post by Richard_York on 2018-11-17
[ATTACH=CONFIG]281667[/ATTACH]
So far so good - result.
Now I'm starting on instructions at  [https://help.ubuntu.com/community/Pa...ng/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")    in post#2 here.
Finding uuid was fine, that's copied and saved. 
I get: 
/dev/sda6: UUID="3b55d810-a3ca-4dd0-9738-4394ee52dac4" TYPE="ext4" PARTLABEL="UbuntuData" PARTUUID="18969055-7f6b-45c0-b79f-4964ec70f636"
  
Now I'm quickly moving out of my depth.
Next instruction is:
[ATTACH=CONFIG]281668[/ATTACH]

I made the mistake of not realising all three lines at "Setup fstab" had to by typed before anything happened, but having done this, I get
[ATTACH=CONFIG]281669[/ATTACH]
and a text editor page showing 
[ATTACH=CONFIG]281670[/ATTACH]
I can't align  the instructions....
 _*[starts]*_

3.  Open the original fstab in a text editor: 
sudo gedit /etc/fstab  and add these lines into it 
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /media/home    ext3          defaults       0       2  and replace the "????????" with the UUID number of the intended /home partition.
NOTE:   In the above example, the specified partition in the new text is an  ext3, but if yours is an ext4 partition, you should change the part  above that says "ext3" to say "ext4", in addition to replacing the ???'s  with the correct UUID.

_*[ends]*_

....with what I've got in that text editor. Given that I hope I've supplied as much as possible here, I'd really appreciate an idiot's guide to the this, please.
Or have I simply gone in so far over my depth it isn't going to work for me?

---

### Post by oldfred on 2018-11-17
Run this first:
lsblk -f

That should show UUID of your new /home partition. You will replace the ??? with that UUID.
And most partitions are ext4, so change the type to ext4 from ext3 in example.

UUID=3b55d810-a3ca-4dd0-9738-4394ee52dac4   /media/home    ext4          defaults       0       2

Besure to follow all steps and if errors post back.

---

### Post by Richard_York on 2018-11-17
Ok, running lsblk -f confirmed that the new UUID is, as you copied in, 
3b55d810-a3ca-4dd0-9738-4394ee52dac4     That's good.

Where I'm still stuck is trying to identify which bits go where, in the text editor page which comes up.
Here's the image I posted earlier - having followed the instructions, the same page just popped up now:[ATTACH=CONFIG]281672[/ATTACH]

I'm sorry to be so dense, but don't want to louse up now, and to my inexperienced eyes it's not looking as straightforward as the example given. 
So I have to check before I move on.

Main question: I am not sure whether I simply add the line you typed - "3b55d810-a3ca-4dd0-9738-4394ee52dac4/media/home ext4 defaults 0 2" to the file as a stand-alone line, (if so, as a new line at the end?),  or if I need to replace some of the file as it stands in the text editor.

If I just add this line at the end, that's easy. If I have to edit what's already there I have more questions!

---

### Post by oldfred on 2018-11-17
You just add it to the bottom.

And one of next commands is this:
And running this to remount using edited fstab should return nothing. If an error, you have to fix it before rebooting.
sudo mount  -a

---

### Post by Richard_York on 2018-11-17
Something needs fixing, it appears.
I added the line in. Wasn't sure if it needs a  #  to start or not, so tried both ways.
Here's what I ended up with.
[ATTACH=CONFIG]281675[/ATTACH]
And here's what the Terminal showed during my attempts.
[ATTACH=CONFIG]281676[/ATTACH]
It's late where i live - I'll come back for the next round tomorrow. Thanks for your patience.

---

### Post by oldfred on 2018-11-17
The # is for comments or to remove temporarily a line. You do not want hashtag.

You have a space at beginning of line, not sure what that does, but computers are very particular. Try without space.

The instructions had you create the mount point first. Before remounting from fstab.
#4 
sudo mkdir /media/home

---

### Post by hennmann on 2018-11-17
oldfred? Why is GParted always suggested? What is wrong with the partitioning tool within the Ubuntu installation?

---

### Post by oldfred on 2018-11-17
I happen to prefer gparted. Seems easier somehow, or gives more info.
If you wanted gpt with BIOS boot you had to use gparted.

Otherwise you can use the partitioning tool in the installer.

---

### Post by Impavidus on 2018-11-18
> **Richard_York said:**
> So calling it /dev/sda6, since sda 1 to 5 are already taken, would be right, I think?   And from what that tutorial says, more than 4 makes it logical rather than primary, so these seem like the answers to go for. 
At 7 yrs old I'm guessing my drive counts as older.
Hope I have this right now!No, your drive uses GPT partitioning, so it counts as a newer drive. But all went well.

> **Richard_York said:**
> Something needs fixing, it appears.
I added the line in. Wasn't sure if it needs a  #  to start or not, so tried both ways.

There's a sort of informal standard that there are comment characters, usually # or %. Whenever you encounter a file that has, interspersed with lines of code, some lines of natural language starting with one of these characters, you can safely assume those are comment characters. Every line starting with a comment character is ignored by the program interpreting the file, so those lines are comments, just to make the file more readable to the humans editing it or to temporarily disable a particular line.

I now realise there one thing in that tutorial that's not exactly as it should be. It occasionally instructs you to run```
sudo gedit /etc/fstab
```Running gedit (or any other GUI application) with sudo and no other precautions may have some unpleasant consequences, although generally not hard to fix. There are several alternatives, like```
sudo -H gedit /etc/fstab
```temporarily using root's home directory, or```
sudo nano /etc/fstab
```using the terminal-based nano editor instead of gedit. As usual in terminal applications, there's no mouse in nano. Just use the keyboard and ctrl+x to save and close.

---

### Post by Richard_York on 2018-11-18
Thanks for all these. 

On opening up the computer this morning, I see there's now a 224GB  Volume icon on the desktop, which on opening has nothing in the folder, so that'll be my new partition, I take it.

I next followed Oldfred's advice in post #17 and removed the space at the beginning of the line I added to the text editor, after running       sudo gedit /etc/fstab   in the Terminal - before I saw Impavidus' post #21.

I have saved the file but not done anything else with it yet.

So next I should go to #4 in the instructions I have, from Impavidus' post #2, and as Oldfred says, run 
sudo mkdir/media/home, then hopefully continue on from there exactly copying the steps,    is that right?

Impavidus, when (if!) I eventually work down to "Preparing fstab for the  switch" in those instructions, which of the two lines you offer as  alternatives to "sudo gedit /etc/fstab"  would I find easier to work with?

I confess to several overnight moments of losing all confidence and thinking it might be easier to cut my losses and simply make a fresh clean install of Ubuntu18, but since we're making progress here I'm inclined to carry on, and hope I don't hit too many more hurdles! I'm already looking down at the bit in "Check copying worked" where it says ".... you may find differences but hopefully it should be obvious which you can ignore"  ... I'll save that for when we get there.

---

### Post by Impavidus on 2018-11-18
> **Richard_York said:**
> 
On opening up the computer this morning, I see there's now a 224GB  Volume icon on the desktop, which on opening has nothing in the folder, so that'll be my new partition, I take it.Yes, that's it.
> So next I should go to #4 in the instructions I have, from Impavidus' post #2, and as Oldfred says, run 
sudo mkdir/media/home, then hopefully continue on from there exactly copying the steps,    is that right?Right, but don't forget the space between mkdir and /media/home. I assume it was a typo in your post.
> Impavidus, when (if!) I eventually work down to "Preparing fstab for the  switch" in those instructions, which of the two lines you offer as  alternatives to "sudo gedit /etc/fstab"  would I find easier to work with?Both should be easy, but if you've never used the nano text editor before, I suggest you try```
sudo -H gedit /etc/fstab
```
> I confess to several overnight moments of losing all confidence and thinking it might be easier to cut my losses and simply make a fresh clean install of Ubuntu18, but since we're making progress here I'm inclined to carry on, and hope I don't hit too many more hurdles! I'm already looking down at the bit in "Check copying worked" where it says ".... you may find differences but hopefully it should be obvious which you can ignore"  ... I'll save that for when we get there.
There's a first time for everthing when learning Linux. When you succeed, you'll have gained a lot of confidence.

---

### Post by Richard_York on 2018-11-18
That's encouraging. 

I tried going from the instructions #4, with space in place, when the terminal's response was that the  /media/home   directory      already existed, as on the image below.
So I tried the next few instructions, thinking that if it existed presumably I'd made more progress than I'd realised -  but end up with the following when I copied in
sudo diff -r /home /media/home -x ".gvfs/*"
[ATTACH=CONFIG]281688[/ATTACH]
The theme of "no such directory exists" continues for dozens of lines beneath this.

---

### Post by oldfred on 2018-11-18
Did you have Firefox open when you did the copy?
It looks like it did not copy some of the locked files or new files that get created in Firefox after copy but by use of Firefox.

Do you have lots of data in your 224GB volume now?

---

### Post by Richard_York on 2018-11-18
I did have Firefox open, yes, so I could copy instructions into the terminal.

And yes again, opening that 224GB volume has two main folders, one called lost+found, the other called richard, with all the expected MyDocs type folders in there.
I'd not put any documents into the Documents yet, other than copying my Firefox profile across from the old computer: "Properties" tells me that 1.6GB is used including "(some contents unreadable)".

Should I empty the whole volume  and redo the copying operation without Firefox open? (I can read instructions from my laptop)

---

### Post by oldfred on 2018-11-18
Rsync (depending on settings) will just copy whatever had changed, no need to erase & totally redo.

This is what I use to copy to another drive. The excludes file is separate and includes a long list of temporary, cache, and other folders that do not need to be copied.
rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

---

### Post by Impavidus on 2018-11-19
The worst thing that can happen from keeping firefox open during rsync is that you may lose a few minutes of browsing history. The "(some contents unreadable)" refers to the contents of lost+found. Nothing to worry about, this is expected.

---

### Post by Richard_York on 2018-11-19
I copied in "rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup" from post#26  
Other than an error message, not a lot happened. So I tried going round the loop again, using the "Check copying worked" instruction to type 
sudo diff -r /home /media/home -x ".gvfs/*"

Here's the start of what's showing on my Terminal[ATTACH=CONFIG]281697[/ATTACH]
It continues for about 5 miles. I'll leave it open for now, in case copying more to show here would help, but there is truly a vast amount of it.
It starts with Firefox references, but moves on to a whole range of stuff.

I'm sorry, I seem to have got dug in here for a while!

I just saved the contents of the terminal in case I need to show any of them here. It runs to 20 pages.
It ends up with:
diff: /home/richard/snap/gnome-system-monitor/current/.themes: No such file or directory
 diff: /media/home/richard/snap/gnome-system-monitor/current/.themes: No such file or directory
 richard@LizardsDesktop:~$     rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup  
 rsync: failed to open exclude file mybackup_excludes.lst: No such file or directory (2)
 rsync error: error in file IO (code 11) at exclude.c(1178) [client=3.1.2]
 richard@LizardsDesktop:~$ 
 richard@LizardsDesktop:~$     rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup  
 rsync: failed to open exclude file mybackup_excludes.lst: No such file or directory (2)
 rsync error: error in file IO (code 11) at exclude.c(1178) [client=3.1.2]
 richard@LizardsDesktop:~$ 
 richard@LizardsDesktop:~$ 
  

It's always possible I can ignore all this, but am holding for now, waiting further feedback.

---

### Post by oldfred on 2018-11-19
My example was my copy of /home to a backup partition. You do not have a backup partition mounted so every file would be an error. And you do not have the excludes file, so that will be another error.

It was meant as an example of other parameters, not something to run, sorry if confusing.

---

### Post by Richard_York on 2018-11-19
Oops, sorry, my lack of understanding. I did wonder, but didn't know what else to type.

OK, to move on, unless I've wrecked the process thereby:   do I now just pick up from the next stage of those instructions at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)  ?
If so, I think my next move will be "Preparing fstab for the switch". I'll await confirmation this time before jumping in too hastily.

---

### Post by Impavidus on 2018-11-19
I don't know if anything peculiar is going on with those snaps, whether they require any special handling. I don't really think so. Anyway, each following step is simply reversible.

Note that the steps "Moving /home into /old_home" and "Reboot or Remount all" must be done immediately after another. Doing anything inbetween that attempts to access your home directory may have funny consequences.

---

### Post by Richard_York on 2018-11-19
Thanks - warning noted, so I'll leave that to tomorrow for a clear run.

---

### Post by Richard_York on 2018-11-20
I believe it's all worked now. Here's what I get in GParted:

[ATTACH=CONFIG]281707[/ATTACH]
with "Home" firmly appearing in the right place.

If it falls over I'll come back and ask more, meanwhile very many thanks to those of you who helped here.

---

### Post by Impavidus on 2018-11-21
Great.

When everything works fine, you can delete /old_home. You can also mark this thread as solved.

---

