---
title: "Creating DVD Video iso"
date: 2005-07-26
forum: General Help
---

### Post by maol62 on 2005-07-26
I'm trying to create a iso out of a DVD Video structure that I have on my HDD.
It looks like this:

-------------------------------------------------------------------------
# ls -R Movie/
Movie/:
AUDIO_TS  VIDEO_TS

Movie/AUDIO_TS:

Movie/VIDEO_TS:
VIDEO_TS.BUP  VTS_01_0.BUP  VTS_01_1.VOB  VTS_01_3.VOB
VIDEO_TS.IFO  VTS_01_0.IFO  VTS_01_2.VOB
--------------------------------------------------------------------------

Then when I preform the mkisoft -dvd-video command (added the verbose option) I get the following answer:

------------------------------------------------------------------------------
# mkisofs -dvd-video -v -o movie.iso ./Movie
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs 2.01a34-unofficial-iconv (i686-pc-linux-gnu)
Scanning ./Movie
Scanning ./Movie/VIDEO_TS
Scanning ./Movie/AUDIO_TS
-------------------------------------------------------------------------------

and the CPU goes straight up to 100% and keeps on doing it until my patience says stop... I have waited 30 minutes and nothing more happens.

When I skip the -dvd-video option there aren't any troubles creating the iso but then I dont get the right layout where VIDEO_TS.IFO has the lowest number, when using the command 
# isoinfo -i movie.iso -l 

Anyone who have any ideas what could be wrong?

---

### Post by solatis on 2005-07-31
Have you tried using growisofs instead of mkisofs ?

growisofs uses mkisofs and dd if I'm not mistaken...

---

### Post by maol62 on 2005-07-31
It seems that is has something to do with the filesystem. Very strange. I still haven't removed Windows XP from my computer and when I performed this operation mentioned above, I first copied the folder from the NTFS-partition to my Resier-partition, then I performed the command that caused the processor burst. Now I have tried another way, I do exactly the same except from that I read the DVD-structure from the, in Ubuntu mounted, NTFS-partition. Then I finally get an error message:

----------------------------------------------------------------------------------------------------------
 # mkisofs -dvd-video -o /movie.iso /media/win_h/Movie
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: IFO is not of correct size aborting.
mkisofs: Unable to parse DVD-Video structures.
mkisofs: Unable to make a DVD-Video image.
----------------------------------------------------------------------------------------------------------
Now, this is not a normally created structure, it is created to dvd-structure by a bunch of windows software first converted from divx to dvd by DivxToDVD, then demultiplexed by Vobedit, then multiplexed (with subtitles added) by IFOedit. Finally once again, edited in IFOedit, this time just to paste the right colors for subtitles. And I think that the problem has something to do with IFOedit because the DVD-structure created by DivxToDVD works with mkisofs but not the final structure, created by IFOedit. Created with DivxToDVD the VTS_01_0.IFO file is aprox 50kB, and created with IFOedit it is aprox 85kB. So the main problem is certainly not a mkisofs problem, but still it was strange that I got no error message when doing the operation from Resier.

---

### Post by Jenda on 2005-08-26
All I get is:
> jenda@niniel:~$ dd if=/dev/dvd of=dvd.iso
dd: reading `/dev/dvd': Input/output error
1216+0 records in
1216+0 records out
622592 bytes transferred in 6.426452 seconds (96880 bytes/sec)
Can anyone please tell me what to do?

---

### Post by chipmonk010 on 2005-08-26
you need to get the dvd tree on your HD to make an iso, and to do this you need a ripping program like dvdbackup(see link) 
The dvd's encrytion will prevent you from making the iso in the normal single step, like your example. once the tree is on your HD u need to build the iso using a line like the following:

mkisofs -dvd-video -o /DVD_PROJECTS/homedvd.img /DVD_PROJECTS/HOMEDVD/

try this, u must use the -dvd-video switch in order for the files to be structured correctly. A dvd player reads from the center of the disk outward so the movie must be burned in this way, the dvd-video switch taks care of this. see also
[http://dvd.chevelless230.com/dvdbackup.html](http://dvd.chevelless230.com/dvdbackup.html)

Note: simpley copying the dvd file tree to your HD without a ripping program to decrypt it will NOT work the first post does not mention how the dvd tree was obtained. dvdbackup is great program u can get it from apt....u also need libdvdread and libdvdcss..

EDIT: didnt read the your second post....sry, sounds more like either the filesystem or the way the tree was made too me....but il leave all that stuff i typed up there....lol

---

### Post by Jenda on 2005-08-26
[QUOTE=chipmonk010]you need to get the dvd tree on your HD to make an iso, and to do this you need a ripping program like dvdbackup(see link) 
The dvd's encrytion will prevent you from making the iso in the normal single step, like your example. once the tree is on your HD u need to build the iso using a line like the following:

mkisofs -dvd-video -o /DVD_PROJECTS/homedvd.img /DVD_PROJECTS/HOMEDVD/

try this, u must use the -dvd-video switch in order for the files to be structured correctly. A dvd player reads from the center of the disk outward so the movie must be burned in this way, the dvd-video switch taks care of this. see also
[http://dvd.chevelless230.com/dvdbackup.html](http://dvd.chevelless230.com/dvdbackup.html)

Note: simpley copying the dvd file tree to your HD without a ripping program to decrypt it will NOT work the first post does not mention how the dvd tree was obtained. dvdbackup is great program u can get it from apt....u also need libdvdread and libdvdcss..

EDIT: didnt read the your second post....sry, sounds more like either the filesystem or the way the tree was made too me....but il leave all that stuff i typed up there....lol[/QUOTE]
 OK, mine seems to work now, for no apparent reason, but chipmonk:
Maybe you should specify *who* you're replying to, it might make it easier for the reader. (Quotes serve the purpose quite well...)

---

