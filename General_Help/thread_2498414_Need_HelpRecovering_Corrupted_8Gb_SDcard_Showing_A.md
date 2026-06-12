---
title: "Need HelpRecovering Corrupted 8Gb SDcard Showing As 32Mb"
date: 2024-06-12
forum: General Help
---

### Post by typos1 on 2024-06-12
I was in a rush and forgot to unmount my sdcard from my Android device. 

Now if I put it in any Android device its recognised and needs formatting, in ******* its given a drive name but ******* also says it needs formatting. Trying to repair it with ******* using CHSK reports that is cant be done because its RAW data. 

Ubuntu doesnt see it, nor do Gparted or Disks. FSCK and TESTDISK do see it but they say its 32Mb when the card is actually 8Gb. 

I ve used photorec before but I cant see it helping if it can only see 32Mb of the card plus I just read something on the ubuntu's site that says they can only be used if the drive can be mounted.

I ve spent the last 2 days reading more pages online than I can remember, but nothing I can see will help because its recognised only as 32Mb and I havent found anyone with the same reduced size situation and everything I ve found relating to sdcards showing as incorrect size is related to fake cards and reformatting to show the correct size. Something in this closed thread : [https://ubuntuforums.org/showthread.php?t=2307719](https://ubuntuforums.org/showthread.php?t=2307719) says using the "clean" command in DISKPART but I dont want to risk that either.

I cant even fast reformat it and then try and recover data because it will only be 32Mb . . . I think but I dont want to risk it without help.

I m stuck, help !

---

### Post by dragonfly41 on 2024-06-12
Sad story. This is one thread I found to compare notes. Writes about a possible "crack" in card..

[https://raspberrypi.stackexchange.com/questions/61895/sd-card-showing-as-30-mb-on-a-32-gb-card-cant-format-cant-create-a-partition](https://raspberrypi.stackexchange.com/questions/61895/sd-card-showing-as-30-mb-on-a-32-gb-card-cant-format-cant-create-a-partition)


P.S. added note .. above thread refers to this ..

[https://www.sdcard.org/downloads/formatter/](https://www.sdcard.org/downloads/formatter/)

Windows only.

---

### Post by typos1 on 2024-06-12
Thanks for the reply. 

Yes I found some stuff about cracks too, but it seems unlikely in this case because I m pretty sure it was me not unmounting it before removing it (even though I have occasionally done this before without problems).

I just finally found something else relating to sdcards suddenly having a reduced capacity which also suggested using "clean" in diskpart on *******, then reformatting and the correct capacity is restored. He reformatted it with diskpart too and gave the warning that it could take a long time, so presumably it was overwriting the disc, which I deffo dont want to do.

So so far my best option seems to use "clean" in diskpart on ******* and then try it and if its still 32Mb then format it the quick way (ie not overwriting data) in Disks on ubuntu, then try and recover my data.

Was hoping someone could give me a more certain thing to do because I really want be able to recover this data.

Edit: just noticed that my spelling of windows with a "ze" replacing the "ws" at the end has been completely asterixed out !!

---

### Post by dragonfly41 on 2024-06-12
Best I can think of before signing off for today.
Search "forensics SDcard" or other with "forensic".

[https://www.forensicfocus.com/forums/general/sd-card-forensics/](https://www.forensicfocus.com/forums/general/sd-card-forensics/)

P.S. ... also found this ...

[https://www.quora.com/I-have-an-SD-card-of-16GB-but-its-showing-only-30-MB-and-Windows-is-also-unable-to-format-it-What-should-I-do](https://www.quora.com/I-have-an-SD-card-of-16GB-but-its-showing-only-30-MB-and-Windows-is-also-unable-to-format-it-What-should-I-do)


P.P.S.  This is a good find.

[https://www.cleverfiles.com/howto/recover-corrupted-sd.html](https://www.cleverfiles.com/howto/recover-corrupted-sd.html)


P.P.P.S (overnight)

[Just learned at this site]("https://www.partitionwizard.com/disk-recovery/does-formatting-an-sd-card-delete-everything.html") that formatting "the quick way" as you suggest does not necessarily wipe data (which I would be concerned about).* If you take that risk* then it is possible that testdisk might then be used to recover data. But what a risk. Next time ensure backups and n+1 redundancy plan in place.

---

### Post by typos1 on 2024-06-13
Thanks.

Actually I dont want to use the clean command in windows/diskpart because it cleans it by writing zeros to the device.

I ve already made an image of the card but its only 32Mb because thats how much storage is showing as available.

I can find how to restore the original size, I know how to search for lost data, but I cant find anyone with a similar problem or anything that allows me to restore the original size and get the lost data back. Well I found one thing that said that in the headline but then contradicted itself in the actual text.

I do have a partial backup, just had not got around to adding the extra files to the backup.

---

### Post by dragonfly41 on 2024-06-13
"Rules 1 and 2" in this thread seem worth remembering.

[https://superuser.com/questions/854588/fix-sd-card-that-cannot-be-formatted](https://superuser.com/questions/854588/fix-sd-card-that-cannot-be-formatted)

---

