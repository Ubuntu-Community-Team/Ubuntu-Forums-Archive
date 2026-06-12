---
title: "Moved /home and lost all user settings!!"
date: 2007-04-05
forum: General Help
---

### Post by visctrix on 2007-04-05
I followed Carthik's guide ([here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")) to move /home to its own partition. I think I did it very carefully, but I had a couple of major problems.

I am left with an apparently clean new version of Ubuntu having (temporarily I hope) lost all my desktop modifications, my Firefox bookmarks, my Thunderbird emails, and all other user-related settings (although they are saved and retrievable).

I'm hoping that the problem and the solution are here: 
[LIST]
[*]the old_home folder contains two directories, 'visctrix' and 'suna' (my friend)
[*]the new home contains the contents of 'visctrix'
[/LIST]

Will the solution be to 'move' (?) the contents of the new home into a subdirectory called visctrix? If so how do I do this properly? I've been using Ubuntu for two years now, but don't often have to do this sort of thing and I want to make sure I get some proper advice first.

TIA for any help.

---

### Post by solar george on 2007-04-05
What do you get if you do an ```
ls -a 
``` in your new /home/visctrix?

Have you deleted you old /home?

---

### Post by visctrix on 2007-04-05
Some new folders and files seem to have been created by the system in a new folder at /home/visctrix

The old /home/visctrix is now at /old_home and a full copy of it is in the current /home directory

---

### Post by visctrix on 2007-04-05
Bumping this as it's a simple question but I do need help.

When I copied the files to the new partition I used
```
$cd /home/
$find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/
```
Do I need to go through this again or will a simple mv do it?

Thanks

---

### Post by visctrix on 2007-04-06
Ok, having slept on it, what about this as a potential solution?
[LIST=1]
[*]rename /home/visctrix to /home/old_visctrix (because /home/visctrix seems to have been automatically generated when I logged in - the fresh install bit)
[*]create an empty folder called visctrix $ mkdir /home/visctrix
[*]unmount /home (but how do I do this properly - see below)
[*]then $ sudo mount /dev/hde7 /home/visctrix
[/LIST]

The reason being that I've already copied all the files across, but the new mount point seems to be wrong.

The question, how do I unmount /home?
[LIST]
[*]I would guess $ sudo umount /home
[*]but maybe $ sudo umount /dev/hde7  ??
[/LIST]

Then I can edit fstab appropriately (**or should I just edit fstab and reboot and forget all the above steps?**)

Thanks

---

### Post by visctrix on 2007-04-07
Original post in General Help [here]("http://ubuntuforums.org/showthread.php?t=402429").

I moved /home to its own partition following [Carthik's instructions]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"). I ended up losing all my user settings - email, desktop, bookmarks, even my screen resolution changed. I've been using Ubuntu for two years so a lot has been lost. Of course everything has been backed up, but I don't know how to restore it... I'm obviously not an absolute beginner but I don't usually do system stuff like this so I feel like one today!

I think(?) the problem is that instead of copying everything in [FONT="Courier New"]/home[/FONT] to [FONT="Courier New"]/newhome[/FONT] I actually seem to have copied [FONT="Courier New"]/home/visctrix[/FONT] to [FONT="Courier New"]/newhome[/FONT] so now that [FONT="Courier New"]/newhome[/FONT] has become [FONT="Courier New"]/home[/FONT] all the old paths are wrong (I hope you follow this).

I've tried to unmount [FONT="Courier New"]/home[/FONT] and start again, but [FONT="Courier New"]/home[/FONT] is already in use and can't be unmounted...

I'm tempted to edit the following line in fstab:
```
/dev/hde7 	/home 		ext3 	nodev,nosuid 	0 	2
```
to read:
```
/dev/hde7 	/home/visctrix 		ext3 	nodev,nosuid 	0 	2
```
Can I just do this and reboot and everything will be ok? I know editing fstab can be risky though and I don't want to risk my system more at this point.

Thanks in advance for any advice.

---

### Post by Bias on 2007-04-07
Certainly worth trying however when I mess with fstab I make a duplicate entry in the file, comment out the original and then change the copied line, this makes it easier to go back.

Nick.

---

### Post by moore.bryan on 2007-04-07
> **visctrix said:**
> I think(?) the problem is that instead of copying everything in [FONT=Courier New]/home[/FONT] to [FONT=Courier New]/newhome[/FONT] I actually seem to have copied [FONT=Courier New]/home/visctrix[/FONT] to [FONT=Courier New]/newhome[/FONT] so now that [FONT=Courier New]/newhome[/FONT] has become [FONT=Courier New]/home[/FONT] all the old paths are wrong (I hope you follow this).

*how would /newhome get renamed to /home?*

---

### Post by visctrix on 2007-04-07
Brian - you need to see Carthik's tutorial (linked in my first post) which explains that.

Bias - I tried it, and was left unable to boot into anything but the failsafe terminal! Now have to use my laptop to get advice from the forum (glad I finally can do this or I would be stuck!)

Any other suggestions? Now I might need help using the failsafe terminal to get me out of my new predicament!!

---

### Post by moore.bryan on 2007-04-07
[I]it seems like there's a step missing from cathik's tutorial... it never tells you to rename /newhome to /home, but it has you adding it to your fstab.  you should be able to add this to your fstab to make it all work:
```
/dev/hde7     /newhome     ext3     nodev,nosuid     0     2
```[/I]

---

### Post by visctrix on 2007-04-07
Thanks Brian, but I'm not sure that's right for this reason: /newhome was a temporary mount point for my new partition /dev/hde7 so really /newhome didn't properly exist. The tutorial says create /mnt/newhome, mount /dev/hde7 to /mnt/newhome, copy /home to /newhome, unmount /newhome, move /home to /old_home, create a new /home, then mount /dev/hde7 to the new /home. Even if /newhome does still exist, it would be the same as /home - both have /dev/hde7 mounted to them.

There are a few things I could do now:
[LIST]
[*]try your suggestion, try to mount /newhome
[*]move /old_home back to /home (restore old setup)
[*]try to finish what I started and make it work (my preferred option)
[/LIST]
Apart from a solution to the third option, I need to work out how to edit fstab from the terminal. I've typed $ sudo vim /etc/fstab and I have it open in the window but I've never used vim before and it's a strange new thing to try to learn in extremis... :-)

---

### Post by visctrix on 2007-04-07
Ok, I've learnt how to basically use vim, I've edited fstab to comment out the new line I tried and uncomment the previous entry.

Now I'm back with the problem I started this thread with, but I don't have any idea of the solution... :confused:

---

### Post by moore.bryan on 2007-04-07
*could you post your fstab?*

---

### Post by visctrix on 2007-04-07
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde3 -- converted during upgrade to edgy
UUID=8357f578-9033-40d1-bdf7-2e5a247353ba / ext3 defaults,errors=remount-ro 0 1
# /dev/hde5 -- converted during upgrade to edgy
UUID=770eff5f-96d7-4475-a4ae-bae3eff3a3fe none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb        /media/usb1     auto    rw,user,noauto  0       0
#Added by winmac_fstab utility
# /dev/hde1 -- converted during upgrade to edgy
UUID=1BE6-2B74 /media/0040GB040Disk040(hde1) vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by visctrix 7 November 2005 
# /dev/hdf1 -- converted during upgrade to edgy
UUID=7021281d-272f-4111-b5f9-741bc22800c1 /media/hdf1 reiserfs defaults 0 0
# /dev/hde6 -- converted during upgrade to edgy
UUID=36f9e607-98aa-4c01-85a2-846031a440f3 /media/hde6 reiserfs defaults 0 0
#Added by visctrix 5 April 2007
/dev/hde7 	/home 		ext3 	nodev,nosuid 	0 	2
#Added by visctrix 7 April 2007
#/dev/hde7 	/home/visctrix	ext3 	nodev,nosuid 	0 	2
# /dev/hde7 -- converted during upgrade to edgy
# UUID=de291e6d-c6ff-405a-8736-5625c7ba187a /media/hde7 ext3 defaults,errors=remount-ro 0 1

```

[Note I also commented out the last line on 5 April which I am unsure about, but the problem occurred initially before I was able to edit fstab so this should be unconnected with it. Also it seems the the convert during upgrade to edgy was simply because /dev/hde7 was an empty and unmounted partition that was just mounted in /media]

Thanks

---

### Post by moore.bryan on 2007-04-07
[I]okay, let me try to understand what you're after.  you want to separate your /home into a separate partition so it will be consistent between reinstalls, so you followed the directions on that thread and your home isn't located; correct?

try this as your fstab:
```

# /etc/fstab: static file system information.
#
# <file system>     <mount point>     <type>     <options>     <dump>     <pass>
proc    /proc     proc     defaults     0     0
#/dev/hde3
UUID=8357f578-9033-40d1-bdf7-2e5a247353ba /     ext3     defaults,errors=remount     0     0
#/dev/hd5
UUID=770eff5f-96d7-4475-a4ae-bae3eff3a3fe     none     swap     sw     0     0
/dev/hda     /media/cdrom0     udf,iso9660     user,noauto     0     0
/dev/hdc     /media/cdrom1     udf,iso9660     user,noauto     0     0
/dev/fd0     /media/floppy0      auto     rw,user,noauto      0     0
/dev/sda     /media/usb0     auto     rw,noauto     0     0
/dev/sdb     /media/usb1     auto     rw,noauto     0     0
#/dev/hde1
UUID=1BE6-2B74     /media/0040GB040Disk040(hde1)     vfat     rw,user,fmask=0111,dma
#/dev/hdf1
UUID=7021281d-272f-4111-b5f9-741bc22800c1     /media/hdf1     reiserfs     defaults
#/dev/hde6
UUID=36f9e607-98aa-4c01-85a2-846031a440f3     /media/hde6      reiserfs      defaults
#/dev/hde7
UUID=de291e6d-c6ff-405a-8736-5625c7ba187a     /home     ext3     defaults     0     2

```[/I]

---

### Post by visctrix on 2007-04-07
Thanks Brian, you seem to be thinking hard for me :-)

Main problem - now X.org is broken so I can only boot into the command line.

I spotted a typo in the new fstab line 7 - hd5 instead of hde5 - and I've corrected this but it doesn't solve the problem.

I've tried to $ sudo mv /etc/fstab /etc/fstab_bm so that I can then restore my fstab backup, but I get a message that says mv: cannot move [......] : Read-only file system

What next? Should I auto-reconfigure X? it seems I'm in danger of fixing something that shouldn't be broken...

How can I restore my fstab backup?

Thanks

---

### Post by moore.bryan on 2007-04-07
[I]well, if you got it to boot, you're on the right track.  when you get to the cli, is your /home correct?  if so, you just need to reconfigure xserver...
```
sudo dpkg-reconfigure xserver-xorg
```
i'm not sure how to copy back your old /home because you'd have to unmount the partition it's on...
[/I]

---

### Post by visctrix on 2007-04-07
Ok, I did that, and now not only do I have the same problem, but now I don't even get to the command line - just a flashing cursor on a blank screen

The message I get is "Could not start the X server ... due to some internal error. ... this display will be disabled. Please restart GDM when the problem is corrected."

I press enter for OK and get the flashing cursor on a blank screen.

Wouldn't I have been better trying to restore the previous fstab as I asked in my last post? Have you or anyone else got any suggestions as to how to do that as sudo doesn't seem to work?

---

### Post by moore.bryan on 2007-04-07
[I]after you dpkg-reconfigure, were there any error messages?  the best way to replace your old /home is to copy back the /old_home to /home and comment out the new partition in fstab.  something along these lines should work:
```
sudo rm -rf /home
sudo mv /old_home /home
```
if that doesn't work, maybe someone else would have a better idea.  you've seemed to have followed all the steps in the post to a tee; not sure why it isn't working for you.  try back-tracking and making sure every suggestion was followed...
[/I]

---

### Post by dreadlord_chris on 2007-04-07
> **visctrix said:**
> Bumping this as it's a simple question but I do need help.

When I copied the files to the new partition I used
```
$cd /home/
$find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /mnt/newhome/
```
Do I need to go through this again or will a simple mv do it?

Thanks

I'd bet [dollars to donuts]("http://dictionary.cambridge.org/define.asp?key=dollars*1+0&dict=I") you did all this while logged in to your normal user account. You can only work with files you have permission to access. In this case that would mean ***only the files in your personal home directory** (/home/visctrix)* would be moved to the new location. Since your intention was to move **everything** in /home/, you needed to sudo that find command...

---

### Post by visctrix on 2007-04-07
I felt sure there must be some simple underlying explanation - and that makes perfect sense Chris.

Thanks for the lesson, I hope I learn from it :-)

---

