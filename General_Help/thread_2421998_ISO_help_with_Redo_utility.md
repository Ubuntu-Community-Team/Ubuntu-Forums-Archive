---
title: "ISO help with Redo utility"
date: 2019-06-30
forum: General Help
---

### Post by orthoducks on 2019-06-30
Is this an appropriate place to look for help with Redo? Which forum would be best?

I've been to the Redo forum of SourceForge, but no one is answering there.

---

### Post by #&amp;thj^% on 2019-06-30
Is there a technical question? or this just to ask if it's ok to ask here.

---

### Post by cruzer001 on 2019-06-30
I have not use Redo.  Clonezilla is my choice.

[https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

---

### Post by orthoducks on 2019-07-09
Yes, there's a question. I'll copy it from my unanswered post on the SourceForge forum.

I want to use Redo to clone a Windows 7/Ubuntu system disk. Can someone please tell me where I'm going wrong?
 
I booted Redo from a CD ROM that I burned from an image I downloaded  from SourceForge yesterday. [That was 6/27 -- yesterday when I originally posted this.] The computer had two 250 GB hard disks. One,  a Maxtor, contained the systems. The other, a Seagate, was empty. My  mission was to clone the Maxtor disk to the Seagate.

 Redo displayed a splash screen, then a screen with two buttons  labeled Back Up and Restore. Already this looked squirrely: I read  several web reviews that said Redo can clone disks, but cloning is a  copy operation -- neither a backup nor a restore. Where's the Clone or  Copy button?

 I decided that cloning was more like a backup than a restore, so I  clicked Back Up. Redo prompted me to select the source drive from a  list, and I selected the Maxtor. It then prompted me to select the  partitions to copy; I selected all (the default). Finally it prompted me  to select the destination drive from an [I]empty list.
[/I]
There are enough loose pieces here to make me wary of moving forward  without advice. Am I doing the right thing? Is Redo doing the right  thing?

---

### Post by mastablasta on 2019-07-10
i am a former user of redo.

the software i no longer developed or maintained. it is based on old 12.04 version of ubuntu and i believe partclone. not exactly sure about the last one. i wish someone would pick it up and at least bring it to Ubuntu 18.04 version. i know there are some attempts by the users, but it's not the same as if one did it properly. it was a simple program with a very nice GUI that every beginner could get along with.

for disk to disk cloning clonezilla is better option and is still developed. though the interface is kind of lame and more importantly poorly designed. so for GUI users it is not that friendly.

anyway print this guide out (if you don't have another PC), and follow it step by step. : [https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

this is how i cloned my old 120 GB (at least i think it was 120) WD black that was about to die to a new 1TB seagate. then i moved the windows partitions a bit (using mini tool partition wizard) and also created a new one.

---

### Post by orthoducks on 2019-07-15
Clonezilla is a nonstarter for me, but it seems to come up whenever I ask about Redo, so I'd better explain why.

When I first tried to solve this problem I concluded that Clonezilla was my best choice. I installed it. I read the documentation. Then I tried to use it. It asked a seemingly endless series of questions, some of which made me guess at answers, then it gave me a cryptic error message and stopped. I had no idea what was wrong or how to fix it. The documentation was no help. That, as far as I'm concerned, is the end of the road for Clonezilla.

You need to understand how I'm going to use whatever I end up choosing. I will clone my disk, and then I may never use the program again until I need to restore the clone, or if it's a bootable clone, clone it again *immediately* after the need to use it arises.

So the question is not whether I can learn to use Clonezilla. Given enough time and effort, I'm sure I can. The question is whether I can count on being able to use it immediately, under pressure, after ignoring it for months or years. It has demonstrated conclusively that I can't.

Now, returning to Redo: If its only disadvantages are that it's less powerful than Clonezilla and doesn't it have current support, those things carry little weight against the fact that (assuming I can get past the puzzling problems I described) it will provide the one capability I need, and Clonezilla won't.

I hope that as a former Redo user, you can offer me some help to make it meet my needs.

---

### Post by mastablasta on 2019-07-16
partclone, partimage ... they all have quite similar interface. you could explore those if the have any newer version.

i suggested clonezilla not because it is nice, but because it works. it has a terrible, terrible user interface. i used it two times so far (on windows OS drive and once on linux disk). 

i posted a link to step by step guide. you just follow that and it should work. it is no installed but ran from a live session (you burn the os to USB or CD and then boot from this media). the issue with clonezilla is that if you change your mind at certain step you need to star it form the beginning. that's where this disk-disk clone guide comes in handy. i am not sure where you get stuck. just make sure new disk is same or larger size than current disk.

following this guide is quite straight forward. so check out the guide and let me know where you get stuck.

redo was not made to clone bootable disks. however, you can clone partition, then add the boot sector later (if it's not part of the clone). i am not sure how this is done using UEFI or these new types of boots (hidden boot partitions on windows, secure boot etc.). also i am not sure redo even supports any of new UEFI hardware since it was made back in 2011. 

on MBR boot (old BIOS and not UEFI motherboard) and windows 7 you would boot from a repair CD and then restore the MBR.: [https://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](https://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

fixmbr or fixboot found in bootrec.exe are a few other options that might work from current boot:
[https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues](https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues)

---

### Post by orthoducks on 2019-07-24
I decided to give Clonezilla another chance. This is what happened.

I couldn't find my original Clonzilla CD, so I burned a new one. I used the ISO I downloaded last time, which I believe was dated 2016.

I got a bunch of "blk_update_request" errors on the DVD drive when I booted, followed by the message "overlayfs: missing 'workdir'." I can't prove these errors weren't legitimate, but the drive I used to read the CD has performed flawlessly in the past; so has the drive I used to burn it. Clonezilla appeared to start normally after the errors, but my confidence in it was already impaired.

I selected "local disk to local disk clone" and worked my way through the instructions you referred me to, this time without the multitude of obscure questions. The UI bore only a general similarity to the one described, though. Has this program's interface changed so much in three years?

When I told it to go, it copied the first two partitions. Then it said it couldn't copy the third one because *the destination partition was too small.*

Excuse me? It was supposed to be *cloning a disk.* If it complains about the size of a destination partition, it's copying partitions. If this were a commercial program, I'd have returned it right then. I'd invite the vendor to explain why I shouldn't file a complaint against them for false advertising.

It's not a commercial program, so I'll cut it more slack. But I am not pleased to learn that before I can say *clone the disk,* I'll have to find out the sizes of my source disk's partitions and duplicate them all on the destination.

I let it try to copy the rest of the partitions. At one point it displayed a bunch of messages about "not a FAT device." My source disk has no FAT partitions; the destination might. I gather it's complaining that some source partitions don't have the same format as the destination. That implies that I have to format all of the destination partitions, as well as create them.

When it was done, it displayed a multi-line message with no line breaks about powering off or rebooting, followed by a command prompt. I entered 'poweroff', one of the commands it suggested, and got the response "bus error." (Ubuntu and Windows 7 have no trouble powering this machine off.)

Conclusion: Assuming this program will copy my boot track and partitions correctly (we've established that it doesn't clone disks), I'll give it a grade of D+. That is not for its lack of niceness. As long as I can figure out how to run it, I don't care whether it's "nice." This is for its inability to do the one thing I want it for. With considerable extra effort I should be able to make it do something equivalent, but it will take a lot more setup than it should, which means a lot more risk of error, which is exactly what I'm trying to avoid.

I'm going to sleep on this. I may work with it some more, or I may drop it and buy Acronis, which I'm told is "nicer," which I hope means more usable as well as prettier.

---

### Post by mastablasta on 2019-07-24
yeah.... [https://sourceforge.net/p/clonezilla/discussion/](https://sourceforge.net/p/clonezilla/discussion/)

the interface says it all. :)


[LIST]
[*]The underlying GNU/Linux operating system was upgraded. This release is based on the Debian Sid repository (as of 2019/Jul/07).
[*]Deprecate Partimage, i.e. no more depending on Partimage. Since it's not in the Debian Buster repository. It's only recommended to install, not a required package.
[*]Package live-boot was updated to 1:20190627-drbl1, which uses ntfs-3g instead of kernel module ntfs.ko to mount the file system. Ref:
[/LIST]


maybe an older image with partimage?!

can this clonezilla guide help?: [https://www.dedoimedo.com/computers/clonezilla.html](https://www.dedoimedo.com/computers/clonezilla.html)

make sure the booted ClonezillaLive OS works properly.

---

### Post by orthoducks on 2019-07-25
mastablasta, the SourceForge link led to a page that lists three Clonezilla forums, each of which has many topics. It's not clear which one you're referring to.

Working backward from your comments, I think you found that Clonezilla uses PartImage for some of its operations, and recent releases of Linux come without PartImage, forcing Clonezilla to use alternative methods which may be less capable or reliable, unless PartImage is installed separately. Is that accurate? I may have gotten it entirely wrong. Since I'm running Clonezilla from a live CD, I don't understand how having PartImage or not could matter.

I'm still working with the software I installed before the two-year Linux hiatus that I'm now trying to end. My Clonezilla ISO is dated 20160210. My Ubuntu ISO is release 16.04.2. PartImage is not on it.

I examined both HDDs with PartEd. The number and sizes of the partitions are identical. The contents appear to be identical up to the last allocated partition (sda7/sdb7), which is NTFS on the source, about 50% full, and "unknown" on the destination. This suggests that my original assumption was right: Clonezilla won't work (at least without PartImage) unless the two disks' partitions are compatible (they are) and identically formatted (they're not). I'm going to format the destination's sdb7 and see if that makes Clonezilla happier, but I won't get to it tonight.

I haven't read the Clonezilla guide you suggested but I skimmed part of it. It insists that I should run in expert mode because it gives me more control, which conflicts with my reason for wanting to use the program at all. It mentions a "savedisk" command, apparently available only in expert mode, which clones a disk. But I'm skeptical that "clone" means the same thing to Clonezilla as it does to me, and I'm skeptical that savedisk will actually do more than the beginner mode operations I'm trying to use now.

---

### Post by mastablasta on 2019-07-25
yes it look slike paid version of cloning software is the way to go then.

the help forums might be able to troubleshoot your issue.

yes, i was thinking that since you have windows 7 and likely BIOS machine, you might be able to use an older version of the program or partimage. i am not sure how well one can even boot an older kernel OS on new UEFI PC.

i used disk to disk clone of windows NTFS drive with partitions. i cloned it from failing smaller drive to new 1 Tb drive and it all all worked well. the clone was completed, then i stretched the NTFS partitions. i just followed the cloning guide and it all worked out as it was supposed to. not sure why it doesn't work for you, but to troubleshoot this you should ask Clonezilla community and their devs. if you are sure that feature is not working, report a bug, so they can resolve it and improve it. that's who opensource software works. not everyone is a developer. most are just users (who are sometimes also testers) and who report bugs so that those with knowledge can fix them

there isn't that much backup software that do disk to disk. 
[https://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software](https://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software)

could mondo rescue be used?

---

