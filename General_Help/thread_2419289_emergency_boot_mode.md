---
title: "emergency boot mode"
date: 2019-05-19
forum: General Help
---

### Post by d_t_s2 on 2019-05-19
So I've messed with my pc latest Ubuntu and added a internal HDD. It was not being recognised so I've followed some script to make it work - apparently! Trouble is I've buggered it all up. Now I can't boot at all. As far as I am aware I've only changed the fstab. 
Obviously I do not know what I'm doing!! I only tend to use terminal in nessesity 
Can you help me revert back to working? 
Urgent help required. Thanks

---

### Post by oldfred on 2019-05-19
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by d_t_s2 on 2019-05-19
I have tried boot repair but cannot obtain it. 
I have 14.04 on cd but no other versions!

Can I re-repair the fstab from emergency boot?

---

### Post by oldfred on 2019-05-19
If running 14.04 then that is your problem. It has reached EOL - end of life.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Repositories are closed, so you do not get updates.

Best just to install 18.04 or maybe 16.04.

If fstab is issue, you may be able to mount it can edit it in live installer. Or you may have to chroot into it, but best to use current versions.

---

### Post by d_t_s2 on 2019-05-19
> **oldfred said:**
> 
If fstab is issue, you may be able to mount it can edit it in live installer. Or you may have to chroot into it, but best to use current versions.
I'm sure it is just etc/fstab that I inadvertently changed. Can I revert back? Could I disconnect the new drive? I have no other pc to obtain a live usb.

---

### Post by oldfred on 2019-05-19
Can you boot to terminal using recovery mode?
Then:
sudo nano /etc/fstab
Arrow down and put # (comment) at beginning of error.
Any time you edit fstab, you always run this to make sure no errors. If it just returns then ok. If not you have to fix error before rebooting.
sudo mount -a
That remounts per updated fstab.

---

### Post by DuckHook on 2019-05-19
> **d_t_s2 said:**
> &#8230;I have 14.04 on cd but no other versions!&#8230;
> **d_t_s2 said:**
> I'm sure it is just etc/fstab that I inadvertently changed. Can I revert back? Could I disconnect the new drive? I have no other pc to obtain a live usb.
[LIST=1]
[*]Although past EoL, your CD of 14.04 should be able to start in LiveCD mode.
[*]From there, mount your main HDD.
[*]You should be able to navigate into your root /etc/fstab and edit it.
[*]Don't make things worse by changing things willy-nilly. Go in with a written plan of what changes you wish to make, and record all of your steps.
[*]This time, make a backup of fstab first before working on it, so you can at least get back to the same starting point to try again if things don't work out.
[*]In addition to oldfred's advice, do not make changes to fstab unless you first:
[LIST=i]
[*]backup all of your important data, and
[*]have a current LiveUSB or other means with which to recover.
[/LIST][/LIST]

---

### Post by d_t_s2 on 2019-05-20
I've tried all the above. Thanks. No joy. Partly because I do not know my error.  I cannot boot into 14.04
However I have disconnected both new drives leaving original I still have emergency boot mode and can load into grub. Recovery mode overwritten by emergency mode. I get all 'ok' apart from Failed to mound Drive3- which is the root of the problem.  
If the can obtain an utd live cd usb would this be able to determine the cause and repair without losing my documents etc. Not worried about system settings and apps etc.?

I'm Not very good here at command line! 
Thanks

---

### Post by dino99 on 2019-05-20
/etc/fstab needs to match 'sudo blkid' output

---

### Post by DuckHook on 2019-05-20
You've put yourself in a bad place, but I'm just stating the obvious.

[LIST]
[*]I still don't understand why you cannot boot a LiveCD session with your CD of 14.04. It should be as simple as changing the boot order in your BIOS so that it boots from CD as the first device. But you say for some odd reason that you can't do this, so that's out.
[*]You state that you have no access to any other computer, not even a friend's, so can't download and spin a LiveUSB either, so apparently, that's also out.
[*]You're not well-versed with the command line, and yet are stuck with the very primitive environment of GRUB busybox. So it is almost impossible for you to fix anything from there.
[/LIST]
You are basically stating that there is no way out for yourself.

Following are instructions for a last-gasp try, failing which, I can only suggest that you take your box into a shop that knows something about Linux and pay them to fix things for you. While they are at it, they should first copy off all of your important data to an external storage device so that you have a proper data backup.

Instructions for last try:

[LIST=1]
[*]Make sure all other HDDs are disconnected. The only one that should (and it **must**) be connected is the one with your original OS.
[*]This assumes you have no other OS on this HDD, it boots from the first partition of the first drive and you don't have the boot partition separate from your root partition—in other words, it is a standard install. If this is not the case, then *do not* use the following instructions.
[*]When you are confronted with the busybox shell, type in the following, taking care to type exactly:
[*]```
set root=(hd0,1)
```
[*]```
linux /vmlinuz root=/dev/sda1
```
[*]```
initrd /initrd.img
```
[*]```
boot
```
[*]If you can now boot into your OS, hurrah. But before celebrating too much, fix your fstab properly, following advice already given in prior posts.
[/LIST]
I know this is an awful time to remind you of good computing habits but others also read these threads, so:

[LIST=1]
[*]Never change system files without having a proven alternate way of booting up and recovering if something goes wrong.
[*]Do not change critical system files without first making a backup copy.
[*]Have a good backup strategy for your data so that any system crash is at most an annoyance.
[/LIST]

---

### Post by d_t_s2 on 2019-05-20
Thanks duckhook I appreciate and agree with your honest opinion!! . I have used ubuntu for decades on a 'windows esk' type interface. Loving the simplicity and self sufficiency and using software center for apps I need. Works fine. Upgrades itself Then I get out of my depths trying to fix/add something following Google!! And end up here. My ex employer kept me alive once or twice but no longer available! 
I don't want to revert back to windows. Not even duel boot! 
If I can find the right help and fix the monumental cokup I'll keep out of code! Promise.
 I have a copy of latest live software coming Wednesday. So I will try that beforehand. Slight misunderstanding of 14.04 I tried bios boot but when attempting to boot into it - it could not load kernels??
I will try a live boot on Wednesday and cross fingers. 
All drives disconnected bar OS HDD. 
When you say fix fstab, how do I know what's messed up intially? 
Thanks again.

---

### Post by DuckHook on 2019-05-21
> **d_t_s2 said:**
> …I'll keep out of code!On the contrary, I would encourage you to take up what you call "code". Well, the command line at any rate. Knowing how to find your way around the command line can be a life-saver. It is also endlessly fascinating, if you are of that disposition.

FWIW, I don't code. Couldn't code to save my life. I know enough about bash, a few carefully chosen utilities, globbing and regex to get some simple stuff done, but the rest is experience, web research, help from more knowledgeable forum members and an intense curiosity about how Linux works. That's all.

Example: it isn't that hard to get to the point where you understand the various parts of fstab. Once you get there, it loses its ability to trip you up because your understanding allows you to manipulate its elements confidently. Instead of blindly following recipes that you find on the net, you can parse each element of that recipe to decide if it makes sense, has been rendered obsolete, is dangerous, etc.

> When you say fix fstab, how do I know what's messed up intially?At this point, you don't because you didn't keep an original copy around to study and compare things to. However, fstab really isn't that complicated. It's a simple text file that tells the system where to find your disk. It follows a set of conventions. And while to the uninitiated it looks like gobbledegook, each line and each part of each line has a meaning that isn't that hard to decipher if you approach it systematically.

Once your LiveBoot media arrives and you can run a LiveUSB session, post back to this thread and we should be able to help you reconstruct a working fstab.

One last observation: rather than let this incident sour you on the command line, it would be better to think of it as a learning opportunity: learn how to set up a VM running a containerized instance of Ubuntu. Use this disposable VM to do your experimenting. If you mess it up, roll back to a good previous snapshot and correct your mistake from the point where you messed up. You will be comfortable with system files and the command line before you know it.

---

### Post by d_t_s2 on 2019-05-21
Thanks DH most informative. The usb is currently in progress and I will collect in the morning. I assume that I boot into a try ubuntu option. I also found [https://downfromthetrees.typepad.com/blog/2012/05/how-to-use-an-ubuntu-livecd-to-fix-a-broken-fstab-file.html](https://downfromthetrees.typepad.com/blog/2012/05/how-to-use-an-ubuntu-livecd-to-fix-a-broken-fstab-file.html) which cuts the jargon out. 
I appreciate your time and help and if you can advise further much appreciated. I will keep you informed of the outcome. 

Just an afterthought, would it be easier to reinstall on a new HDD but still be able to access documents etc on original boot drive or will it still pose an issue? Documents etc are most important thing to save! (But not backup! ;( )

---

### Post by DuckHook on 2019-05-21
The steps in the link you posted are accurate. I'm not going to quibble about the slightly different way I would handle it. The steps in that tutorial will work. The only question mark is what the new contents of your fstab should be. We will get to that when the time comes.

---

### Post by d_t_s2 on 2019-05-22
Right I'm in Live USB and found the fstab file. As per instructions. I do not know a working script. What next?

---

### Post by oldfred on 2019-05-22
Post this in code tags.
copy of fstab
lsblk -f

Easy to use code tags in forum's advanced editor and # icon.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by d_t_s2 on 2019-05-22
Thankyou to you all for your patience with me and my lack of understanding.
I received the live usb today and flashed this to one of the new drives. From there I followed your advice to NEW fstab file. Took a photo. Disconnect new drive and plugged original drive back in and from emergency boot screen Su / nano/fstab deleted 15 lines of gobbledegook then rewrote the text from photo replacing UUID. 
This appears to have solved the situation. Currently upgrading to 18.10  so hopefully fixed. 
Thankyou all again. 

One other minor issue I have a dual boot screen now from my previous attempts with my 14.01 cd - that didn't work. How do I remove these?

---

### Post by d_t_s2 on 2019-05-22
I couldn't ```
 code 
```  as this is all being done on my phone!

Oh perhaps I can! Thanks again all

---

### Post by DuckHook on 2019-05-22
See?

You were actually able to get back to a working fstab without further handholding from any of us. You are already on your way to being able to deal with system files.

BTW:

[LIST=1]
[*]It is probably too late, but why upgrade to 18.10? 18.04 is stable and LTS while any standard release means the upgrade treadmill.
[*]I hope you backed up your data this time before upgrade.
[*]Don't know what you mean by dual boot screen. Two entries in GRUB? At any rate, start a new thread for new problems.
[/LIST]
Good Luck and Happy Ubuntuing!

---

### Post by d_t_s2 on 2019-06-08
Thank you all for your help. Auto Backup enabled. No idea how to recover from backup, but hopefully never need it again! Thread Closed!

---

