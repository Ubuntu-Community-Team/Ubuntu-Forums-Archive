---
title: "Trim test produces highly fragmented file"
date: 2014-10-13
forum: General Help
---

### Post by Cbhihe on 2014-10-13
[SIZE=1]*This is a cross-post from 5 days ago on askubuntu.com for which I got 0 answer.*[/SIZE] 

I ran the [TRIM test]("http://askubuntu.com/questions/162476/how-to-check-if-trim-is-working-for-an-encrypted-volume/457642#457642") proposed by [frostschutz]("http://unix.stackexchange.com/users/30851/frostschutz") and also found [here]("http://wiki.ubuntuusers.de/SSD/TRIM/Testen"). 
The high fragmentation of the result 1MB file is unexpected. How can that be ?  
**Background:**
My one and only storage device /dev/sda is a Samsung 500GB SSD. It is "TRIM-ready" and the kernel comes with an fstrim executable in /etc/cron.weekly. I nevertheless wanted to run the test, say, out of curiosity. The test produced a 1MB file, trim.test, filled with the y alpha character.

  Following the file creation, I checked the file's exact position on disk:  
```
> cd / 
> yes | sudo dd iflag=fullblock bs=1M count=1 of=trim.test 
> sudo filefrag -s -v trim.test 
Filesystem type is: ef53 
Filesystem cylinder groups approximately 177 
File size of trim.test is 1048576 (256 blocks of 4096 bytes)  
ext:       logical_offset:          physical_offset:      length:     expected:   flags:
0:       0..            15:     2816076..     2816091:      16:                    merged    
1:      16..            31:      170064..      170079:      16:        2816092:    merged    
2:      32..            63:      170848..      170879:      32:         170080:    merged    
3:      64..           127:      168269..      168332:      64:         170880:    merged    
4:     128..           255:      170112..      170239:     128:         168333:    merged,eof
trim.test: 5 extents found, perfection would be -1 extent
```

Adding the lengths of each extent, everything comes up to 256 blocks. 
Things check, but _why is the file so incredibly fragmented ?_

---

### Post by tgalati4 on 2014-10-13
How full is the disk?

```
df -h
```

Perhaps there was system activity going on during your file write which threw data over 5 places on the disk.

It could also be a hardware issue such that the wear-leveler is having to work extra hard.  What prompted you to perform these tests?  Are you getting strange disk behavior?  Is your system slowing down randomly?  Is it much slower now than when you installed fresh?

---

### Post by Cbhihe on 2014-10-13
The disk is 1 month old and its usage is:
         [TABLE]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]size (kB)[/TD]
[TD="align: left"]used (kB)[/TD]
[TD="align: left"]available (kB)[/TD]
[/TR]
[TR]
[TD="align: left"]/dev/sda5[/TD]
[TD="align: right"]23122388[/TD]
[TD="align: right"]7160312[/TD]
[TD="align: right"]14780796[/TD]
[/TR]
[TR]
[TD="align: left"]/dev/sda1[/TD]
[TD="align: right"]43008988[/TD]
[TD="align: right"]27291336[/TD]
[TD="align: right"]15717652[/TD]
[/TR]
[TR]
[TD="align: left"]/dev/sda2[/TD]
[TD="align: right"]464808[/TD]
[TD="align: right"]68668[/TD]
[TD="align: right"]371718[/TD]
[/TR]
[TR]
[TD="align: left"]/dev/sda7[/TD]
[TD="align: right"]11892384[/TD]
[TD="align: right"]1686824[/TD]
[TD="align: right"]9594796[/TD]
[/TR]
[TR]
[TD="align: left"]/dev/sda6[/TD]
[TD="align: right"]374647512[/TD]
[TD="align: right"]50341944[/TD]
[TD="align: right"]305267928[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: right"]453136080[/TD]
[TD="align: right"]86549084[/TD]
[TD="align: right"]345732890[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: right"]19%[/TD]
[TD="align: right"]76%[/TD]
[/TR]
[/TABLE]

/dev/sda3 is swap and /dev/sda4 is the logical made of /dev/sd{5,6,7}... Sooo very empty  !!
And the syst had no activity to speak of, except for running usual services on a Desktop and listening to a number of ports. Nothing else.
> What prompted you to perform these tests?  
Sheer curiosity, since I knew that my SSD was trim-ready ... my cat likes to live dangerously...
> Are you getting strange  disk behavior? 
No
 > Is your system slowing down randomly?  
No
> Is it much slower  now than when you installed fresh?
No

As I said I am stumped by the fact that such a test produced a heavily fragmented 1Gb file, particularly on a pretty sparsely filled SSD that is trim-ready. It makes no sense to me. Hence my question.  

Can you explain about the "wear-leveler" ?

---

### Post by rbmorse on 2014-10-13
Does it even matter if a file on an SSD is "fragmented"?

---

### Post by Cbhihe on 2014-10-13
Yes, it does. 

There is quite a bit of literature on that and quite a few posts on UF and AU on the subject.

 In fact in a context like the one I described, my 1GB file _**should not**_ be fragmented for the reasons spell out above. Fragmentation on a SSD will dramatically and ramdomly slow down your read accesses. SSDs fare much worse than regular HDs when it comes to fragmentation. That is the reason TRIM exists. 
Look [here]("http://wiki.ubuntuusers.de/SSD/TRIM") if you're confy with German and [here]("http://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/?PageSpeed=noscript") if English is your church. Those two refs will give you some perspective.

TRIM & fragmentation gurus of the world, unite ! ...  and jump in the discussion. ;)
Cheers,

---

### Post by rbmorse on 2014-10-13
The link (English) explains why TRIM is important (clear before write). I understand that.  It doesn't say anything about fragmentation, or why a fragmented file should be a problem on a device where electro-mechanical factors (rotation latency, head repostitioning latency) do not come into play.

---

### Post by Cbhihe on 2014-10-14
Thanks @[[COLOR=#000000]rbmorse[/COLOR]]("http://ubuntuforums.org/member.php?u=82") for questioning my misplaced certainties. I was utterly wrong.
 
I got confused reading about TRIM (mainly) and seeing that posts and Wikis also made frequent reference to  fragmentation, in fact mostly establishing a difference between the two issues:
   - fragmentation of files in many different write-areas (using not contiguous physical blocks in the SSD) 
   - the use of TRIM, to prepare already used physical blocks for new writes, without the need to actually re-read them immediately before the data-write occurs, the which approximately halves the write process on previously written blocks. 
Both aspects are the source of legitimate questions about SSD storage R/W performance, hence the fact they often arise together in writings or questions, however they are distinct in nature.

I will explain a bit hereafter, so others may benefit from my snooping around. 
This may be slightly off topic (I think what follows belongs to the _*Hardware*_ section of UF) but hopefully it will serve to close this thread.

TRIM is only distantly related to the process of **wear-leveling** (WL)  (thanks, @[[COLOR=#000000]tgalati4[/COLOR]]("http://ubuntuforums.org/member.php?u=241895") for bringing that up in #2). 
WL is essentially meant to distribute block-writes over an SSD's free/available/unreserved block space. 
WL aims at making the number of read-writes (the limiting parameter that defines the life span of SSDs) as *physically uniform* as possible over the SSD. There are two WL modes: static and dynamic. [INDENT][SIZE=1]*This [wiki]("http://de.wikipedia.org/wiki/Solid-State-Drive#Vorteile_und_Einsatzgebiete") (in German, sorry!) specifies write-cycle counts may increase 100 fold for static and 25 fold for dynamic WL as compared to the same hardware with WL turned off. *[/SIZE]
[/INDENT]
 Understandably when an SSD starts being used, WL has a limited effect on how files are distributed and hence fragmented. That is because blocks that were never used before are available pretty much anywhere on the drive volume. In that respect the bigger the SSD volume, the greater its life span for given conditions of use. However this changes rapidly with increasing number of R/W, increases in R/W frequency, increasing file sizes (large files use up more space), all with respect to the size of the SSD itself or rather to the ratio of free to written blocks in the SSD volume. [SIZE=1][I][INDENT]This actually may be a case to :
- place the Linux swap, /tmp and /var on a HHD,while the rest of the OS may live on happily on the SSD. 
- no make partitions too small o[SIZE=1]n a[I]n SSD. For instance if swap is recommended to be twice your SDRAM size (or whatever they are), make it 4 times. I don't know whether my arythmetic is right, but if I understand well what I read, this will also simply double your SWAP SSD's blocks' life span. 
Further insight is welcome. This is all new to me.[/I][/SIZE]
[/INDENT]
[/I][/SIZE]  After that ill-defined initial phase, WL will in fact indirectly contribute to file **fragmentation**, in order to achieve its prime objective of optimized distribution of written blocks throughout the SSD. It is because internal data management in this case is fundamentally different  from that of HDD in its assignment o sectors to non-volatile flash memory cells and their corresponding blocks ("flash blocks"). The uptake is that a large file may be fragmented a thousand times over and not lead to any performance decline for the SSD.

Meanwhile **TRIM** prepares flash blocks for any upcoming new write. It pre-conditions once written cells for a new write by erasing pertinent cells and starting garbage collection when needed. Pre-conditionning applies to cells/blocks were at least once written and freed at a later stage. Blocks are freed when the file whose data they contained was  modified and moved elsewhere. In that sense TRIM keeps an eye on the distribution map of newly freed (and at least once used) cells as they are being low-level managed by the WL controller. 

So ! Frag is not important, but TRIM IS important provided the SSD is TRIM ready. 4 or five famous and reliable brand names provide TRIM capable SSDs today and you should ask for those and only for those when you go shopping. If you have read this thread from the beginning you know the name of at least one of those reputable brands. 

 
_**Conclusion**_:Fragmentation is effectively not important for SSDs because it does not slow down their data R/W access time. SSDs [do not need]("http://intelstudios.edgesuite.net/idf/2010/sf/aep/SSDS003/SSDS003.html") (<- Intel's talk requires Flash) nor do they benefit from defragmentation.
In fact, users of , especially Windows 7, should turn their automatic defragmentation jobs off in Windows, if they have replaced their original HDD with an SSD. Not doing so will decrease the life span of their SSDs. Regular/standard SDD's storage clean-up and administration [should not include defrag]("http://helpdeskgeek.com/featured-posts/should-you-defrag-an-ssd/") unless their objective is to perform a kind of slow motion terminal burn test on their brand new SSD.

---

### Post by sammiev on 2014-10-14
> **Cbhihe said:**
> Thanks @[[COLOR=#000000]rbmorse[/COLOR]]("http://ubuntuforums.org/member.php?u=82") for questioning my misplaced certainties. I was utterly wrong.
 
I got confused reading about TRIM (mainly) and seeing that posts and Wikis also made frequent reference to  fragmentation, in fact mostly establishing a difference between the two issues:
   - fragmentation of files in many different write-areas (using not contiguous physical blocks in the SSD) 
   - the use of TRIM, to prepare already used physical blocks for new writes, without the need to actually re-read them immediately before the data-write occurs, the which approximately halves the write process on previously written blocks. 
Both aspects are the source of legitimate questions about SSD storage R/W performance, hence the fact they often arise together in writings or questions, however they are distinct in nature.

I will explain a bit hereafter, so others may benefit from my snooping around. 
This may be slightly off topic (I think what follows belongs to the _*Hardware*_ section of UF) but hopefully it will serve to close this thread.

TRIM is only distantly related to the process of **wear-leveling** (WL)  (thanks, @[[COLOR=#000000]tgalati4[/COLOR]]("http://ubuntuforums.org/member.php?u=241895") for bringing that up in #2). 
WL is essentially meant to distribute block-writes over an SSD's free/available/unreserved block space. 
WL aims at making the number of read-writes (the limiting parameter that defines the life span of SSDs) as *physically uniform* as possible over the SSD. There are two WL modes: static and dynamic. [INDENT][SIZE=1]*This [wiki]("http://de.wikipedia.org/wiki/Solid-State-Drive#Vorteile_und_Einsatzgebiete") (in German, sorry!) specifies write-cycle counts may increase 100 fold for static and 25 fold for dynamic WL as compared to the same hardware with WL turned off. *[/SIZE]
[/INDENT]
 Understandably when an SSD starts being used, WL has a limited effect on how files are distributed and hence fragmented. That is because blocks that were never used before are available pretty much anywhere on the drive volume. In that respect the bigger the SSD volume, the greater its life span for given conditions of use. However this changes rapidly with increasing number of R/W, increases in R/W frequency, increasing file sizes (large files use up more space), all with respect to the size of the SSD itself or rather to the ratio of free to written blocks in the SSD volume. [SIZE=1][I][INDENT]This actually may be a case to :
- place the Linux swap, /tmp and /var on a HHD,while the rest of the OS may live on happily on the SSD. 
- no make partitions too small o[SIZE=1]n a[I]n SSD. For instance if swap is recommended to be twice your SDRAM size (or whatever they are), make it 4 times. I don't know whether my arythmetic is right, but if I understand well what I read, this will also simply double your SWAP SSD's blocks' life span. 
Further insight is welcome. This is all new to me.[/I][/SIZE]
[/INDENT]
[/I][/SIZE]  After that ill-defined initial phase, WL will in fact indirectly contribute to file **fragmentation**, in order to achieve its prime objective of optimized distribution of written blocks throughout the SSD. It is because internal data management in this case is fundamentally different  from that of HDD in its assignment o sectors to non-volatile flash memory cells and their corresponding blocks ("flash blocks"). The uptake is that a large file may be fragmented a thousand times over and not lead to any performance decline for the SSD.

Meanwhile **TRIM** prepares flash blocks for any upcoming new write. It pre-conditions once written cells for a new write by erasing pertinent cells and starting garbage collection when needed. Pre-conditionning applies to cells/blocks were at least once written and freed at a later stage. Blocks are freed when the file whose data they contained was  modified and moved elsewhere. In that sense TRIM keeps an eye on the distribution map of newly freed (and at least once used) cells as they are being low-level managed by the WL controller. 

So ! Frag is not important, but TRIM IS important provided the SSD is TRIM ready. 4 or five famous and reliable brand names provide TRIM capable SSDs today and you should ask for those and only for those when you go shopping. If you have read this thread from the beginning you know the name of at least one of those reputable brands. 

 
_**Conclusion**_:Fragmentation is effectively not important for SSDs because it does not slow down their data R/W access time. SSDs [do not need]("http://intelstudios.edgesuite.net/idf/2010/sf/aep/SSDS003/SSDS003.html") (<- Intel's talk requires Flash) nor do they benefit from defragmentation.
In fact, users of , especially Windows 7, should turn their automatic defragmentation jobs off in Windows, if they have replaced their original HDD with an SSD. Not doing so will decrease the life span of their SSDs. Regular/standard SDD's storage clean-up and administration [should not include defrag]("http://helpdeskgeek.com/featured-posts/should-you-defrag-an-ssd/") unless their objective is to perform a kind of slow motion terminal burn test on their brand new SSD.

+1 and thanks for the great read! =d>

---

### Post by tgalati4 on 2014-10-14
When you dig into the details, you get insight into behavior.  Because using swap slows your system down tremendously, there is really not a penalty using a spinning hard disk for swap.  But putting swap on an SSD can cause extensive wear and shorten the life or slow down the SSD's overall performance.  

Because there are several makers of SSD and their controllers are all different, making general statements about trim, fragmentation, and write performance is difficult.  How does RAID5 affect SSD performance?  Does using RAID make sense with SSD's?   How about encryption?  Should only a few directories be encrypted or the entire root partition, or the entire disk drive?  There seems to be a consensus of using both spinners and SSD's for a linux installation.  That way you can use the best features of both.

Use what works.  If your disk slows down in a year, you will know what to look for.

---

