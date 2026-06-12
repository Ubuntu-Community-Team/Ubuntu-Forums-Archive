---
title: "What is the point of a disk check every 30 mounts?"
date: 2007-06-13
forum: General Help
---

### Post by FRuMMaGe on 2007-06-13
I find it extremely annoying that Ubuntu deems it necessary to check my 160GB laptop hard-drive every 30 times I boot up.

Is there a way to stop this?  Or better yet, delay it until I can be bothered to do it at home?

---

### Post by jd65pl on 2007-06-13
[http://doc.gwos.org/index.php/ChangeDiskCheckFrequency](http://doc.gwos.org/index.php/ChangeDiskCheckFrequency)

---

### Post by jeroen.kurvers on 2007-06-13
You can use Bonager to pospone the check: [http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager]("http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager")

---

### Post by Sockerdrickan on 2007-06-13
Well 30 boots in Ubuntu is like 1 year :)

---

### Post by g8m on 2007-06-13
It's time to replace ext with a smarter filesystem that doesnt need that.

It's true that linux doesnt need that many reboots like a xp os, but that's changing too, after every kernel update I get a blue circle announcing that it needs a reboot.

Those checks were build in a time when 40mb was a big hard disk. It takes forever to check a 250Gb hardisk.

---

### Post by jimcooncat on 2007-06-13
> **g8m said:**
> It's time to replace ext with a smarter filesystem that doesnt need that.


I've been using reiserfs for my partitions for years with no apparant problems. If you use it for /boot, be sure to add the "notail" option. Be sure to read up on "badblocks" before switching to it (of course if you have bad blocks, you might want to retire that HD).

Update 4/29/08: John Dong (jdong) has enlightened me regarding the waning support of ReiserFS. The website of the developing company, Namesys, has now gone offline. OpenSUSE did have good reasons to stop using it as the default filesystem, and I wished I'd run across their reasoning earlier (link below). I'm reevaluating, and will probably start using Ext3 instead.

[http://blog.linuxoss.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/](http://blog.linuxoss.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/)

---

### Post by g8m on 2007-06-15
I know reiser is better. It was the default for suse for years, but even suse has reverted back to ext. Maybe zfs should be ported to linux?

---

### Post by jimcooncat on 2007-06-15
From Wikipedia:
> ReiserFS was the default file system in Novell's SUSE Linux Enterprise until Novell decided to move to ext3 on October 12, 2006[1], two days after principal author Hans Reiser was charged with the murder of his wife.

See, nothing to do with the technology. Sheer politics. DARPA (with my tax dollars) paid for much of the development. 

In the meantime, Hans is expected to sell the company (good luck with that with SUSE dropping them like a hot potato), and won't get a trail until this fall. See more of the soap opera (including the confessed serial killer ex-boyfriend!) at:
[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

I'm sticking with the product, and it looks as if it may be supported in the long run, even after this.

---

### Post by el mariachi on 2007-06-15
I'm not very informed about Linux filesystems, although I ran a check on Wikipedia ( I really didn't understand most of the stuff).

I currently use ext3 for all my partitions, I don't intend to change them, even if there's a better fs BUT, my older computer needs a new linux installation. SO.. can you put it in layman's terms the pros and cons of ext reiserFS and some other you find better than these two. And, if it depends on what my needs are, I'll say speed! (it's an old computer, who cares if it isn't safe, I ain't going to conduct classified research with it :P)

---

### Post by jimcooncat on 2007-06-16
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

When you get to step 5, choose "Manually edit partition table".

I can't seem to find some good screenshots for this -- if anyone can, please post a link!

You'll want to end up with something similar to this

```
/boot (100 Mb) : reiserfs with the "notail" option
/ (5 Gb): reiserfs
swap (512 Mb or (1.25 muliplied by the size of your RAM), whichever is larger): swap
/home (rest of your space): reiserfs
```

Pros:
[LIST]
[*] Speed, especially with small files. Ubuntu uses lots of small files. If you store email, use a Maildir, and your computer will reward you for using reiserfs with outstanding email reading and searching performance.
[*]  No forced disk check
[/LIST]

Cons:
[LIST]
[*]Doesn't check for bad blocks on the hard disk. You should manually run the "badblocks" program after installation (or preferably before, if you can figure out how to). If you have any, rethink about using reiserfs or dig deep in the docs on how to deal with it. Or chuck the disk.
[*]  No forced disk check unless you get a bad shutdown. Probably one should be done once a month, though I don't think to do it.
[*]  Separate /boot partition recommended with notail option.
[/LIST]

---

### Post by Old *ix Geek on 2007-06-16
> **Tux0r said:**
> Well 30 boots in Ubuntu is like 1 year :)
Not on a laptop! ;)

---

### Post by Sweet Mercury on 2007-06-17
> **Old *ix Geek said:**
> Not on a laptop! ;)

I second that!

I'm about a month into my Ubuntu experiment. and tonight marked the second time I was "forced" into a disk check on my laptop. Didn't help that I can't suspend the thing fully...

---

### Post by Cappy on 2007-06-17
File recovery may prove much harder on ReiserFS if somehow your partition table gets deleted or something. I don't think any open source recovery tools support it. It is well known that trying to recover data off of a ReiserFS may corrupt it further.

I'm not saying it is impossible, but there is some added risk that should be taken into consideration before switching.

---

### Post by el mariachi on 2007-06-17
I don't know if this is right but, when you delete a file (from the trash bin [paper hell for me:D] ), doesn't the file get permanently erased, that is, it's written over with zeros? This in an ext3 fs.

---

### Post by happy-and-lost on 2007-06-17
I quite like the disk checks. I'm a bit paranoid about my laptop's HDD, and having regular checks means that if the drive begns to fail, it should be spotted early and give me enough time to rescue my data.

---

### Post by Cappy on 2007-06-17
> **el mariachi said:**
> I don't know if this is right but, when you delete a file (from the trash bin [paper hell for me:D] ), doesn't the file get permanently erased, that is, it's written over with zeros? This in an ext3 fs.

"Undeletion

Unlike ext2, ext3 zeroes out block pointers in the inodes of deleted files. It does this to simplify read-write access to the filesystem when the journal is being replayed after an unclean mount. This, however, effectively prevents files from being undeleted. The user's only recourse is to grep the hard drive for data known to signal the start and end of the file. This provides slightly more secure deletion than ext2, which can be either an advantage or a disadvantage."

So no, not perm erased. It can still be recovered with say, a file recovery utility or a skilled user with grep. The file itself is not zeroed-out, only your "way to find it" is.

I think that it also means if you have a large file and a piece of another file is between the pieces of that large file ... that if you delete both files and then attempt to recover the larger file it will also pick up the smaller piece inside of it since there are no inodes. The reason for this is inodes contain the pointers to each part of a file. If one file is binary and the other is text or they are completely different file types a good file recovery should be able to pick them apart.

Another thing is that the inode (and the file, of course) will not actually be deleted until all programs accessing it are stopped. Windows can't do this, that is why you have to reboot your computer when you install stuff in Windows [so that it can install it on boot].

While I was searching on ReiserFS I also came across this website:
[http://www.linuxquestions.org/linux/answers/Hardware/ReiserFS_Data_Recovery_Tips](http://www.linuxquestions.org/linux/answers/Hardware/ReiserFS_Data_Recovery_Tips)

It shows you how to grep for deleted files ^^ I'm gonna try to grep for text on my own hard drive now =P

I also know the awesome program "mc" (midnight commander) can undelete files. I'm not sure how well it works but it is capable of it.

Another is one called "testdisk" (sudo apt-get install testdisk). testdisk actually recovers partitions but it has a program that is installed with it called "photorec" that can recover deleted files also.

---

### Post by el mariachi on 2007-06-17
Thanks cappy! it solved my doubt ;)

---

### Post by Ocxic on 2007-06-17
> **g8m said:**
> It's time to replace ext with a smarter filesystem that doesnt need that.

It's true that linux doesnt need that many reboots like a xp os, but that's changing too, after every kernel update I get a blue circle announcing that it needs a reboot.

Those checks were build in a time when 40mb was a big hard disk. It takes forever to check a 250Gb hardisk.


obviously, that goes for everyone, a reboot is the only way to get the current running kernel, out of memory and load the new one. thats comlpetly acceptible to me, what i hate is haveing to reboot, after installing my eathernet driver, then again for the graphic driver, and yet again for my chipset drivers, and then yet again another 5-8 time during the windows update.

---

### Post by g8m on 2007-06-18
> **Ocxic said:**
> obviously, that goes for everyone, a reboot is the only way to get the current running kernel, out of memory and load the new one. thats comlpetly acceptible to me, what i hate is haveing to reboot, after installing my eathernet driver, then again for the graphic driver, and yet again for my chipset drivers, and then yet again another 5-8 time during the windows update.

To be honest, those reboots during install, or when you change hostname or something like that never bothered me much. How often do you install? I've spoken to those linux die-hards while bragging that there system was up for a year or more. So they probably arent up-to-date with kernel-security-fixes. I did have a redhat install on-line  for 230 days a long time ago, while bragging about it during a thunderstorm, the electricty went down...

I don't mind shutting a pc down when I'm not using it. It's mainly a desktop for me, and only if the desktop is allive I need the server processes. So a couple times a monty I have to sit fsck out (several harddisks).

---

### Post by hessiess on 2007-06-18
i use this computer for wrighting stuff in lessons at school. ditched windows for this after it started taking 10 min to boot. ubuntu is perfect untill it has to do one of its disk checs. then it also takes to min to boot! it gets turend on and off atlest 6 times pur day

---

### Post by orb9220 on 2007-06-18
Yep annoying for me since mine says after 30boots but I know it is more like 10-15 boots so I change it to 50 with a  **sudo tune2fs -c 50 /dev/hdd1** and am happy with that setting.

---

### Post by 9a3eedi on 2007-06-27
actually.. I still don't understand. Isn't ext3 a journalling filesystem? if so, then why does it need to check the whole hard disk again and again? Can't it just read the journal?

---

