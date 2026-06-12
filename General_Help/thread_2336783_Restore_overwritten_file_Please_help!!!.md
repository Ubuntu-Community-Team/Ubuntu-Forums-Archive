---
title: "Restore overwritten file? Please help!!!"
date: 2016-09-11
forum: General Help
---

### Post by karhulitos on 2016-09-11
Hi,

I am desperate. I humbly request fellow Ubunteers guruish help!

Here's the story and bit of background:
- I have done few web radio shows with my friends along the years. I record the shows on the streaming client PC to create podcasts.
- soundcard->darkice->icecast is the basic setup. Darkice does a local dump file (mp3) while it streams to icecast. I use this file to create the podcasts.
- In yesterday's show we had one network outage which we didn't even notice nor the listeners of our show
- however, I learned just today that darkice overwrites the dump file if it loses its connection to icecast ([http://www.freelists.org/post/darkice/FWD-Dump-file-resets,1](http://www.freelists.org/post/darkice/FWD-Dump-file-resets,1))
- out of our 7h show the network outage happened at 6:03 leaving us with only 57 minutes of saved stream

QUESTION: is it possible to find and recover a ~500MB file, or the biggest part of it after it has been overwritten with same name and with 55MB of data?
I'm not a noob but no guru either but surely am willing to try! Will buy a beer to the person who can help me find the lost data.

DETAILS:
- Ubuntu Studio 14.04
- etx4 (250G capacity /~240G free)
- after file overwritten PC started once using the HDD where the missing data is
- now it's off until I find find some guidance what to do next

Please help!

Kind Regards, Timo

---

### Post by Bucky Ball on 2016-09-11
I'd probably give [System Rescue CD]("http://www.system-rescue-cd.org/SystemRescueCd_Homepage") a go. It has testdisk and photorec on it. You might be able to dig it out with [photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

You can use testdisk to recover the whole partition, but not sure that's what you're after. 

You've done the right thing not using the drive. Boot only from bootable media like CD/DVD or USB if possible. You can create a USB of SRCD and boot from that, check things with photorec.

Good luck.

(PS: System Rescue CD also has Gparted and some other handy things on it. I always have a copy on USB within reach. :))

---

### Post by karhulitos on 2016-09-11
> **Bucky Ball said:**
> I'd probably give [System Rescue CD]("http://www.system-rescue-cd.org/SystemRescueCd_Homepage") a go. It has testdisk and photorec on it. You might be able to dig it out with [photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

I will give Photorec a try!

---

### Post by dragonfly41 on 2016-09-11
I would just like to add that although testdisk and photorec are excellent tools there are other forensic tools to try if testdisk/photorec fail ...

e.g. scalpel ...

```

SCALPEL(1)                Digital Forensics Solutions               SCALPEL(1)


NAME
       scalpel  - Recover files or data fragments from a disk image using file
       type-specific patterns


SYNOPSIS
       scalpel [-b] [-c <config file>] [-d] [-e] [-h]  [-i  <file>]  [-n]  [-o
       <dir>] [-O] [-p] [-q <clustersize>] [-r] [-V] [-v] [FILES]...


DESCRIPTION
       Recover  files  from  a disk image or raw block device based on headers
       and footers specified by the user.


       -b     Carve files even if defined  footers  aren't  discovered  within
              maximum  carve  size  for file type [foremost 0.69 compat mode].
              This option may help when fragmentary evidence  is  useful,  but
              will increase the number of false positives.


       -c file
              Chooses which configuration file to use. If this option is omit&#8208;
              ted, then "scalpel.conf" in the current directory is  used.  The
              format  for  the  configuration file is described in the default



```


Here is one summary of tools ...

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

and another ....

[http://www.gfi.com/blog/top-20-free-digital-forensic-investigation-tools-for-sysadmins/](http://www.gfi.com/blog/top-20-free-digital-forensic-investigation-tools-for-sysadmins/)

But don't expect instant results.   Often you have to make overnight runs to recover data.

And remember that you will need an empty drive or partition into which any recovered data can be saved after a forensic run.  
 It can be frustrating if you have arrived at the point of recovering files but you forgot that you need to save them somewhere.

---

### Post by Bucky Ball on 2016-09-11
> **dragonfly41 said:**
> It can be frustrating if you have arrived at the point of recovering files but you forgot that you need to save them somewhere.

Is that the voice of experience we hear? Ouch! :| ;)

---

### Post by karhulitos on 2016-09-11
> **dragonfly41 said:**
> 
e.g. scalpel ...

Thanks, I will not give up just yet. Photorec recovered plenty of mp3s & oggs but just not the one I'd expect. Seems that photorec is pretty decent if you have a deleted file case.
I just wonder how will etx4/hdd behave when
- 500MB file written
- then 50MB file written with same name
Will the write start at the very beginning of the 500MB file? (= so I have 450MB somewhere lurking which is not detected as mp3/ogg)

---

### Post by dragonfly41 on 2016-09-11
As you now have found recovery tools can recover files ... but in your scenario (as I understand) you have one massive 500 MB file which has been overwritten by a smaller file of 50 MB.

So the question is how can you recover a file from a remaining fragment of the file (i.e. the 450 MB end "fragment" of file not yet overwritten).

I have no experience in recovery of  mp3/ogg.
But researching this topic I found this ...

[http://www.dslrfilmnoob.com/2013/08/06/fixing-corrupted-audio-files-vlc/](http://www.dslrfilmnoob.com/2013/08/06/fixing-corrupted-audio-files-vlc/)

which says ...

> At the end of the file the recording the file is marked with header information that&#8217;s *appended* to the file. 

This suggests to me that you might have two metadata blocks buried in your 500 MB.

(a) one at the end of the overwritten file
(b) one at the end of the smaller (50 MB) file which overwrote the above.

Also in that article is a link to the format of *.wav files.

[https://blogs.msdn.microsoft.com/dawate/2009/06/23/intro-to-audio-programming-part-2-demystifying-the-wav-format/](https://blogs.msdn.microsoft.com/dawate/2009/06/23/intro-to-audio-programming-part-2-demystifying-the-wav-format/)

If you research this approach (but aiming at Linux and not Windows) you might be able to fathom the structure of the chunk to search for using a tool such as scalpel.

But as I make clear, I am *guessing* about the approach to use to recover partially overwritten wav.


I guess that testdisk/photorec will not help you much and you need to look for chunks in the 500 MB file.  Find any "signatures" to search for using a string search process which can process such as large file (500 MB).

If the data is important it might be prudent to clone it and work on recovery of the cloned file.


[COLOR=#b22222]**[Later Edit]**[/COLOR]

I'm adding this example of an MP3 recovery tool ... Easus is usually a reliable source ...

[http://www.easeus.com/resource/recover-mp3-files.htm](http://www.easeus.com/resource/recover-mp3-files.htm)

---

### Post by karhulitos on 2016-09-12
Hi DragonFly,

I _really appreciate_ your expertise on this and all your guesses are valuable hints for me. Thank You.
I yesterday used photorec's "whole partition" option which I though would find my lost file after "free space" didn't.
Giving a second thought to my latter try I think it should have resulted in finding the 2. write valid and undeleted 55MB version of the "stream.mp3".

I need to find out now if photorec is supposed to find all mp3's whether they're deleted or not on filesystem level if "whole partition" is selected.

I'll proceed to scalpel only after I've exhausted and understood all capabilities photorec should offer.

[edit] Photorec manual says "from the unallocated space only (available for ext2/ext3/ext4, FAT12/FAT16/FAT32 and NTFS). With this option only deleted files are recovered." As I did 2nd pass with whole partition I should now have at least the 55MB file recovered in my USB stick. I didn't find it yesterday with my watery eyes. Will doublecheck later.
So this would leave me thinking photorec's mp3 detection is not regocnizing correctly the file darkice produces. I may still have a chance..

---

### Post by Habitual on 2016-09-12
[r-linux]("http://www.r-tt.com/free_linux_recovery/Download.shtml") because sometimes it takes more than 1 tool?

---

### Post by dragonfly41 on 2016-09-12
Be clear about what photorec (and other like recovery tools) can and cannot do.

If you have a partition holding hundreds of files with different file extensions and you inadvertently overwrite 10% of the partition then chances are that photorec will find the files in the area of partition not overwritten.

However in your case you don't have a corpus of hundreds or thousands of files.

You have *one* file (250 MB in size) which has been partially overwritten by a smaller 50 MB file.

*I doubt that Photorec will recover the damaged 250 MB file.   ... [corrected typo]*

So the forensic approach has to be &#8220;how can I recover a partially overwritten mp3 file?&#8221;

This is a new field to me so I narrowed the search down to questions of that ilk.

I found this which looks promising.

[https://digital-forensics.sans.org/blog/2009/04/06/recovery-of-mp3s-using-regex/](https://digital-forensics.sans.org/blog/2009/04/06/recovery-of-mp3s-using-regex/)

(Note that the reference to Foremost also applies to Scalpel which is derived from Foremost).

The author in above article writes ...

> [COLOR=#292929]I decided to try to recover the data by extracting every mp3 frame from the media and to stitch them all together in order as found.[/COLOR]

This &#8220;stitching&#8221; is analogous to the old time splicing of mag tapes.


So my suggestion (and I'm learning more about mp3 forensics as I write this) is to understand the structure of the single file(s) which you have.

Then see how parts can be &#8220;stitched&#8221; together.

In your shoes I would replay history by simulating events that occurred but compressing the timescale to about 60 seconds to generate example files for forensic analysis.

I would write a bash script to do the following:

(1) start recording a fresh stream

(2) take a copy of the mp3 after say 30 seconds of recording > testdump1.mp3

(3) simulate an outage which causes an overwrite of your master.mp3.

(4) continue recording for a further 30 seconds (thus overwriting your master.mp3 as you describe in your first post)

(5) take a second copy of mp3 > testdump2.mp3

(6) stop recording


Now you have two *small *files for forensic analysis.

The question is how to stitch these fragments together.

The author refers to using a hex editor such as ...

[http://www.hhdsoftware.com/free-hex-editor](http://www.hhdsoftware.com/free-hex-editor)

This has to be a hex editor which can load very large files.

....

Another useful site I found is here ...

[http://asecuritysite.com/forensics/mp3](http://asecuritysite.com/forensics/mp3)


....

And I found this usage of scalpel .. when searching &#8220;can a partial mp3 be recovered&#8221;


[http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel](http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel)

> [COLOR=#333333]Scenario 1 involves a household without TV with at least one young child. The father has accidentally deleted the child&#8217;s favorite &#8220;Sandmann&#8221; episodes, which were recorded from ARD Mediathek over several days. Deprived of the show, the child expresses disappointment in the usual loud and unmistakable way.[/COLOR]


But note again, this scenario is recovery of *deleted* files .. not *overwritten* files.



[P.S.]

This hex editor apparently works in Ubuntu on "huge files".

[http://www.wxhexeditor.org/](http://www.wxhexeditor.org/)

---

### Post by karhulitos on 2016-09-12
Thanks Habitual, will give it a try later. Now I'm onto why aren't the properly existing (not deleted or overwritten) darkice created mp3 streams not detected by PhotoRec.

---

### Post by Habitual on 2016-09-12
No worries.
You have options. They may not be apparent, but they're there.
Hope it goes well.

---

### Post by karhulitos on 2016-09-12
> **dragonfly41 said:**
> 
*I doubt that Photorec will not recover the damaged 250 MB file.*

I kind of agree with you. One thing I just cannot understand: why didn't PhotoRec find the perfectly playable 55MB file which is existing using whole partition (incl. non deleted ones) search?
I need to understand this first.

I am speachless about your suggestions. It'll take rest of the week to try all options. I truly owe you guys multiple beers.

---

### Post by dragonfly41 on 2016-09-12
You might need to tweak photorec  ... from the manual

[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

[COLOR=#252525]To recover more files, it is possible to [/COLOR][add your own custom signatures to PhotoRec]("http://www.cgsecurity.org/wiki/Add_your_own_extension_to_PhotoRec")[COLOR=#252525].[/COLOR]

[http://www.cgsecurity.org/wiki/Add_your_own_extension_to_PhotoRec](http://www.cgsecurity.org/wiki/Add_your_own_extension_to_PhotoRec)

---

### Post by karhulitos on 2016-09-13
I sent my two test files *) to PhotoRec's forum and the author confirmed both are detectable thus recoverable. I'm confused. PhotoRec did recover hundreds of files and I listened perhaps one hundred from different parts of the recovery and no hits to my Saturday's show. I will try R-Linux today.



*)
Friday test stream dump by darkice day before real show
[http://www.railers.fi/audio/rpdr2.mp3](http://www.railers.fi/audio/rpdr2.mp3)
[http://www.railers.fi/audio/rpdr2.ogg](http://www.railers.fi/audio/rpdr2.ogg)

---

### Post by dragonfly41 on 2016-09-13
A suggestion .. photorec didn't find your Saturday recording because it was not *deleted*? 

Incidentally these tools I found when searching might be useful .. when you find the files to "splice".

[http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php)

[http://mp3wrap.sourceforge.net/](http://mp3wrap.sourceforge.net/)

---

### Post by karhulitos on 2016-09-13
Progress!! R-Linux's raw data detection picked up an 1,6GB ogg and it played the show's first 5 minutes. Why? No idea but I'm not complaining. Mentally I had already let go the first 57 minutes as I thought the overwrite action would have started from the beginning of the Saturday file completely wiping the first 57 minutes' bytes off the disk.
I did have two streams, an ogg and a mp3 both dumping to file. I don't care which one I can recover but ogg should even be slightly better.
The file itself is way too big than expected so I smile only inwards until all 7h found..:D Will come back to tell if all minutes were found. R-linux is now running the recovery over night so I should have all mp3 or ogg blocks I have ever had on that box. Maybe some stitching ahead but that's ok just if all data recovered.

A big Thank You to you guys already now as I would have probably given in without your support!

---

### Post by Bucky Ball on 2016-09-14
Persistence is the name of the game around here so you're right on target! Well done, sounds like you're getting somewhere. :)

---

### Post by Habitual on 2016-09-14
> **Bucky Ball said:**
> Persistence is the name of the game around here so you're right on target! Well done, sounds like you're getting somewhere. :)
Mad Props. Good job and well done.

---

### Post by karhulitos on 2016-09-20
After a lengthy restore process &#8211; listening and searching fragments of my show out of 250GB of OGG stream files &#8211; I have come to the end. Out of the 7h stream I lost approximately 45mins. The restore process returned tens of 1,9 - 3,2GB files along with one nearly 50GB file which had only 10 secs of some odd FX sound. Rest were smaller files, apparently Ubuntustudio's sounds. The bigger files were indeed of my shows stream, each file having the same bigger part but starting or ending from a little bit different position than earlier.
The lost parts were 3 sections in between the whole stream and one ~10 minutes chunk had changed place in time in the bigger 3GB files. So the errors weren't in the beginning or the end of file but basically anywhere. I still deem the whole work success as most was secured.

One oddity to mention was that I couldn't find a single tune of my show in the mp3 restored files. Few older recordings were found which were deleted on purpose. Funny. Perhaps OGG had something different in its signature that R-Linux was able to detect. And it did detect a bit too much like the 10sec 50GB OGG file.
Later thinking I realized Photorec might have been able to restore the same OGG files too. I remember seeing the 50GB file but couldn't open any of them with Audacity. It was R-Linux's first restore file (0000.ogg) which raised my hopes as it was playable by Audacity and contained almost all of the show. The rest tens of big OGG files weren't playable by Audacity but I noticed that VLC's Convert function was able to read/drop the illegal OGG headers when converted to WAV. After that I was able to see and listen all OGG files and search missing parts. I kind of knew that I wouldn't find any more missing parts as the first 0000.ogg had almost all. But of course I needed to browse all files to keep my sanity.. after all it only took one week. :D

Looking the positive side I found a dramatic error in my Icecast config which didn't allow more than ~30 concurrent listeners. The real trigger for this mess was either our 4G link breaking or icecast process eating up all memory &#8211; perhaps due to my misconfiguration or a bug. I noticed 3 days after the show icecast having a memory leak as it was OOM'ed by kernel. Did Icecast suffering from memory shortage or link breaking trigger the file overwrite by Icecast client Darkice remains a mystery as system didn't write any logs during the show night. Perhaps syslogd and others got OOMed as well..

Thanks again guys, you're all champs! Will buy you beers when you come to Finland.

---

### Post by Bucky Ball on 2016-09-21
In the absence of a 'resolved' option, please mark the thread as solved to help others. This will not close the thread to further discussion. Thanks.

---

