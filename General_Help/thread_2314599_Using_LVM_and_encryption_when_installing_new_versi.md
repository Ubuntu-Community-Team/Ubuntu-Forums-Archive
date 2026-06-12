---
title: "Using LVM and encryption when installing new version of Ubuntu"
date: 2016-02-22
forum: General Help
---

### Post by Tom_Carr on 2016-02-22
What are the advantages and disadvantages of installing LVM and encryption when installing a new version of ubuntu?

I am a low tech user.  I install a new version of ubuntu every 2 years and then mostly use just the browser and office suite.  I almost always use the GUI and almost never go into the terminal.

---

### Post by sudodus on 2016-02-22
+ If you are travelling with a laptop computer, LVM and encryption will make it much harder for a thief to read the content of your computer.

- If you forget the passphrase, LVM and encryption will make it much harder for you to read the content of your computer (almost impossible, unless you have big resources).

- If the system is damaged, LVM and encryption will make it harder for you to read the content of your computer. So it is more important to backup your data regularly.

-o-

Do you really need LVM and encryption? There are so many other security issues. See this link

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Tom_Carr on 2016-02-22
Thanks.  I didn't even understand that LVM was about security.  

I looked at the BasicSecurity link.  I have done the basics except

[COLOR=#333333][FONT=Ubuntu Beta]3. enable the firewall (sudo ufw enable) without further tweaks;
I thought it was  already set up automatically.

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]5. keep Java (both openJDK and Oracle Java) disabled by default in your browser, and only enable it when needed;
Not sure how to do that


[/FONT][/COLOR]

---

### Post by TheFu on 2016-02-22
To many to list.  What have you read that you have questions about?

Generally, 
* LVM adds complexity AND capability AND flexibility.
* Encryption isn't all or nothing - there are 3 major options and each has good and bad points, so it depends on which you choose.

For portable devices, I use both LVM and dm-crypt.  For physical systems that don't move, I don't bother with encryption, but still use LVM.  For virtual machines, I don't use LVM - for me LVM is done at the hostOS layer on the real hardware, not inside a virtual machine, though I do know really smart people who I respect that use LVM inside AND outside of VMs.  Of course, for learning how to use LVM commands and playing around, doing that stuff inside a VM is a great idea.

Flexibility is the main reason to use LVM.  Not having to reboot to resize partitions is nice. Nearly immediate file system creation is nice, so not having to wait 10 minutes is the savings. Being able to add more storage to a specific LV while the file system it sits on is being used is nice.  With that flexibility, comes some added complexity. How much? Hard to say and depends on your comfort level.  It also depends on the file system you use.  btrfs or zfs don't make sense with LVM, but ext4 and LVM fit together nicely.

If you want whole drive encryption, using LVM actually makes things easier for a few different reasons than trying to do this encryption without it. Mainly because the encryption can be done under LVM, so 1 huge partition gets unlocked, but the LVM splits it up into LVs to be used for swap, /, /home, /var, .... whatever you desire.  If you do HOME directory encryption only, well, I stopped doing that after feeling and reading about performance issues. Plus, HOME directory encryption made doing backups too hard.  There is another way to encrypt everything - I've never used it.

Back in 2002, I was new to using LVM and did some stupid stuff which resulted in 80% of my data being lost.  I wasn't doing backups then and got what I deserved.  With encryption, backups are mandatory - bad things can happen and data loss is the result without backups.  That issue all those years ago got me "backup religion" to the point that I don't worry about having to reload any of the 10 systems here.  All have at least 30 days of versioned backups - some have 120 days.  I sleep much better now.

Worth it to you? I can't say.  Review the LVM and encryption pages on help.ubuntu.com then ask some questions.

---

### Post by Dennis N on 2016-02-22
From my ordinary user experience, I found LVM to be useful in combining two small partitions into one larger data partition:

```
P1 Data		20gB
P2 Ubuntu	25gB
P3 		30gB
```

Here with all standard partitions I was stuck with an existing too-small P1 for data storage. I wanted to combine space there with P3. Using LVM was the solution.

Skipping the details here, with LVM, P1+P3 can combine into a single LV (Logical volume), that appears to Ubuntu as a single device you can format with a file system, mount in fstab and use. It was fairly easy to do, and worth learning.

I am no expert on LVM (far from it), and that's the only way I have used it. Without encryption.

---

### Post by sudodus on 2016-02-22
> **Tom_Carr said:**
> Thanks.  I didn't even understand that LVM was about security.  

I looked at the BasicSecurity link.  I have done the basics except

[COLOR=#333333][FONT=Ubuntu Beta]3. enable the firewall (sudo ufw enable) without further tweaks;
I thought it was  already set up automatically.

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]5. keep Java (both openJDK and Oracle Java) disabled by default in your browser, and only enable it when needed;
Not sure how to do that


[/FONT][/COLOR]

LVM is a tool used to make LUKS encryption work (LVM is not about security itself, it is a second layer of the partition, a Logical Volume Mapper, and is useful for several purposes). See the following link

[Logical Volume Manager (Linux)](https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

---

### Post by Tom_Carr on 2016-02-23
For me, LVM seems like it might be useful.  Encryption is not important for my needs.

Is there any reason not to check LVM when you do an install?

---

### Post by oldfred on 2016-02-23
Another post on pros/cons:

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)

---

### Post by TheFu on 2016-02-23
LVM can be useful for making encryption easier, but definitely is NOT required.  It is possible to encrypt at the partition level and completely ignore LVM.

Great link Oldfred!  I've been hit by the 2nd bullet in the "cons" list myself.  The 2nd-to-last bullet is also true - any non-default LVM setup with encryption for Ubuntu installs is basically useless.  Just trying to resize the swap partition broke the install here.  Other distros have much better LVM support during installation. They allow anything I could think of to be created.

LVM brings capabilities and features at the cost of added complexity. Only you can decide whether that complexity is worth it or not.  Asking  specific questions might get better answers.

---

### Post by Tom_Carr on 2016-02-23
Thanks for the info and the links.  I will not use LVM for now because of the added complexity.  I don't really need it.  Maybe at some time in the future I will dig more into the details.  I will close the thread.  Thanks again.

---

