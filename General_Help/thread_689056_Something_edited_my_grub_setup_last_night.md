---
title: "Something edited my grub setup last night"
date: 2008-02-06
forum: General Help
---

### Post by ubnewbie2 on 2008-02-06
Today, I turned on my computer and grub gave an error 15 "File Not Found"

I discovered it was trying to use (hd1,0).  I manually changed this to (hd0,0) and the computer booted.

I checked the date on /boot/grub/menu.lst and found it had been changed last night about 2200 hours.  All I did last night at that time was to install the updates for ubuntu that were pending, and shutdown.

So I have corrected the menu.lst file and updated grub, BUT I am really concerned that something like this can happen.:mad:

---

### Post by kesman on 2008-02-06
Last night's updates included kernel updates, which update your grub list also. Dunno why it went wrong with you, mine worked perfectly. These things CAN happen, but it's always good to remember that things are fixable most of the times.

---

### Post by ubnewbie2 on 2008-02-06
I see.  Well thanks for that info.  I'll be a little more careful when updating the kernel  :-)  not that there is anything I could have done differently.

---

### Post by logos34 on 2008-02-06
Make sure **'groot**' reads (hd0,0) also.

---

### Post by marvotron on 2008-02-06
same here, yesterdays updates rewrote my menu.lst to change my root from hd(0,0) to hd(0,2)

bit of a shock when restarting and im told 'cant mount selected partition'

its only a 5 minute fix when you know what you are doing but the least i would expect is a warning from the upgrade advising me that the boot loader is being changed and being able to review the changes.

not a nice way to start the day.

---

### Post by jonnan on 2008-02-06
How odd - I dualboot with XP (For games - I'm weak. <sob> I'm so ashamed . . ) so my linux partition is 0,1, and it always reverts to 0,0 when one of these updates goes through. But it was not originally a dual boot machine - I repartitioned with the gparted cd to make the NTFS partition.

Just out of curiosity - has everyone else edited the partitions since the original install? 

Because I had rather assumed that 0,0 was just a default that was being reverted to, but since other people revert to other configurations, that implies there is an original backup file being restored when these kernal updates go through. 

If so, then there's definitely a backup file that can be edited - get that and this won't recur again with the next kernal update.

Of course, I have no idea where this backup file *is* - any ideas?

Jonnan

---

### Post by ubnewbie2 on 2008-02-06
> **jonnan said:**
> How odd - I dualboot with XP (For games - I'm weak. <sob> I'm so ashamed . . ) so my linux partition is 0,1, and it always reverts to 0,0 when one of these updates goes through. But it was not originally a dual boot machine - I repartitioned with the gparted cd to make the NTFS partition.

Just out of curiosity - has everyone else edited the partitions since the original install? 

Because I had rather assumed that 0,0 was just a default that was being reverted to, but since other people revert to other configurations, that implies there is an original backup file being restored when these kernal updates go through. 

If so, then there's definitely a backup file that can be edited - get that and this won't recur again with the next kernal update.

Of course, I have no idea where this backup file *is* - any ideas?

Jonnan


Mine has changed - a  lot.  I removed an old IDE drive that it used to boot from.

---

### Post by ubnewbie2 on 2008-02-06
> **logos34 said:**
> Make sure **'groot**' reads (hd0,0) also.

I don't understand.  My menu.lst file has this

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```


but that's all commented. How can something in comments effect an update?

---

### Post by chrisccoulson on 2008-02-06
> **ubnewbie2 said:**
> I don't understand.  My menu.lst file has this

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```


but that's all commented. How can something in comments effect an update?

The bottom line isn't really commented. The lines with only a single # are used by update-grub to automagically populate all your grub entries. You need to change it so it looks like:
```
# groot=(hd0,0)
```

---

### Post by gcastell on 2008-02-06
Is this the reason why my menu.lst was changed? it seems to me as updating the Kernel will reset the menu.lst to default values, am I correct?

---

### Post by mcduck on 2008-02-06
> **gcastell said:**
> Is this the reason why my menu.lst was changed? it seems to me as updating the Kernel will reset the menu.lst to default values, am I correct?

Yes. When new kernel version is added to the Grub menu the menu.lst file is recreated, and everything between lines "### BEGIN AUTOMAGICK KERNEL LIST" AND "END DEBIAN AUTOMAGICK KERNEL LIST" is rewritten, using the settings configured in the default options section in the beginning of this "automagick" area.

So, if you make any changes to your boot options you also need to make them to default settings section, and if you add any extra operating systems to the menu they have to be either before or after the "automagick" section.

This is actually documented in the menu.lst file..  ;)

---

### Post by shmengie on 2008-02-06
i keep a copy of my preferred menu.lst in my docs folder. anytime the kernel updates, i just copy it back to boot/grub.

---

### Post by gcastell on 2008-02-06
> **mcduck said:**
> Yes. When new kernel version is added to the Grub menu the menu.lst file is recreated, and everything between lines "### BEGIN AUTOMAGICK KERNEL LIST" AND "END DEBIAN AUTOMAGICK KERNEL LIST" is rewritten, using the settings configured in the default options section in the beginning of this "automagick" area.

So, if you make any changes to your boot options you also need to make them to default settings section, and if you add any extra operating systems to the menu they have to be either before or after the "automagick" section.

This is actually documented in the menu.lst file..  ;)

So all I have to do was to read the manual? that's crazy! :lolflag::lolflag:

---

### Post by jonnan on 2008-02-06
> **gcastell said:**
> So all I have to do was to read the manual? that's crazy! :lolflag::lolflag:

Whoa - reading the documentation? What kind of forum is this anyway?!?!

Ah well, the good news is  my brilliant deduction was right. The bad news is that I would have known this months ago if I had just read the file all the way through. +1 brilliant deduction, -5 completely unnecessary - <sigh>. Such is my life - <G>.

Jonnan

---

