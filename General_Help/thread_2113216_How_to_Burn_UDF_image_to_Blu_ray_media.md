---
title: "How to Burn UDF image to Blu ray media"
date: 2013-02-06
forum: General Help
---

### Post by MakOwner on 2013-02-06
I have done this before, I can't remember the command line paramters to cdrecord.  I worte them down. Somewhere.  If I could remember where I put it, I could probably remember the command lime parameters...

I hace created a 25GB UDF image of data that I want to write to blank BDR media.
 
I'm using schilly's cdrecord.  I know cdrecord supports writing to BD, but after googling all afternoon I can't find a single complete command line example. :/


Is 

```

cdrecord -v speed=2 driveropts=burnfree -dao bigdata.udf

```

sufficient?

---

### Post by MakOwner on 2013-03-10
Hello?  Anyone around?

---

### Post by cariboo on 2013-03-11
Moving this thread to General Help may get you an answer quicker, than in Server Discussions.

---

### Post by meteorrock on 2013-03-11
You can try to use Nero linux 4.0 . Or use "K3b" an advanced linux burning program for a GUI solution. In the command line you can burn "UDF"  files with "UDF tools" installed through the command line. K3B, a burning image program that you can install from the apt-get or through 'ubuntu' software,  will recognize that UDF file for your blu ray with the tools installed below. Unless you like to fiddle in the command line to burn "UDF" blu ray files. I like the command line, but if there is a GUI solution, why not use it? Screw 'wine'. If we wanted windo$e we would be using it along with "IMGburn."   Native linux tools, bro. 

    Select the file-system tab in K3B and burn your "data" DVD or blu ray as a UDF in the options of that program after installing the tools below. De-select "Joliet" and the "Rock ridge" options as these are for DVD playback only with the "Video TS" and the "Audio TS" for those files on a  standard DVD player for playback.

  For Bluray you will use UDF only.  This also applies with "BDMV" and the "CERTIFICATE" folders that you demux or muxed with TsMuxeR , for those  .mkv files from the net, for blu ray playback on a standalone blu ray player.   Burn that image to a regular DVD if its under 4.7  GB for the blu ray hack that you are born to do. HAIL Pirates and torrent users. =)  If you are using a burnable blu ray disk, it will pop up as such in your "K3B." it will burn up to 50 GB on that app to a blank blu ray disk. Ignore the pop ups on "K3B" saying it will not play under windo$e with "Joliet" and "Rock Ridge" filesystems disabled in that app.  

```
sudo apt-get update
```

```
  apt-get install udftools
```

For more information on blu ray burning I got a thread over in linux mint at this link here. [http://forums.linuxmint.com/viewtopic.php?f=90&t=122314](http://forums.linuxmint.com/viewtopic.php?f=90&t=122314)

---

### Post by MakOwner on 2013-03-11
Thanks for the reply.
I already have the udftools installed. I'm not trying to duplicate a BD disk or even put video on one - I'm trying to offload some binary files from spinning disk to BD media.  
I really only use CLI tools for most of this - on the machine where I'm setting this up I have the MATE desktop, and in order to load k3b (which I like, don't get me wrong) you have to load tons and tons of KDE libraries and desktop enviornment stuff just to get one application working.  It's the last resort at this point. I have had k3b working in the past, but using it with cdrkit is dodgy at best.Not a k3b issue if you ask me.

So, anyway - at this point I can create my 24GB UDF image, write data to it mounted via loopback.
I can checksum the data before and after the copy and I get identical results.
I can read the data back from the mounted UDF image no problem, and it compares successfully.

The problem arises when burining the UDF image to bluray.

And the worst bit is I have a stack of blurays over here beside me that I have done successfully in the past, and I can't locate the file where I wrote down the steps.  (maybe I should have put it on one of the BD disks!)
After the burn, when I attempt to remount th emedia, I get these errors (tons of the read/sense errors and then at the end):

```

Mar 10 16:23:45 dale kernel: [540740.809751] sr 3:0:0:0: [sr0] CDB:
Mar 10 16:23:45 dale kernel: [540740.809754] Read(10): 28 00 00 17 7f fa 00 00 01 00
Mar 10 16:23:45 dale kernel: [540740.809769] end_request: I/O error, dev sr0, sector 6160360
Mar 10 16:23:45 dale kernel: [540740.809795] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=1540090, location=1539816
Mar 10 16:23:45 dale kernel: [540740.809800] UDF-fs: error (device sr0): __udf_read_inode: (ino 1540090) failed !bh
Mar 10 16:23:51 dale udisksd[1899]: Cleaning up mount point /media/dale/RMS_MP3_2012_Q4 (device 11:0 is not mounted)
Mar 10 17:22:30 dale kernel: [544265.049288] UDF-fs: warning (device loop0): udf_load_vrs: No anchor found
Mar 10 17:22:30 dale kernel: [544265.049295] UDF-fs: Rescanning with blocksize 2048
Mar 10 17:22:30 dale kernel: [544265.051315] UDF-fs: INFO Mounting volume 'TEST_IMAGE_NAME', timestamp 2013/03/10 15:23 (1e98)
Mar 10 17:52:49 dale kernel: [546083.898166] UDF-fs: warning (device loop0): udf_load_vrs: No anchor found
Mar 10 17:52:49 dale kernel: [546083.898175] UDF-fs: Rescanning with blocksize 2048
Mar 10 17:52:49 dale kernel: [546083.916571] UDF-fs: INFO Mounting volume 'TEST_IMAGE_NAME', timestamp 2013/03/10 15:23 (1e98)

```


The disk will sometimes mount and you can get a directory listing but corrupiton is obvious.

I think my problem is this - but I can't find anything anywhere to confirm this:
By default mkudffs creates a blocksize of 4096 on a UDF filesystem.  
cdrecord by default burns with a blocksize of 2048.

I'm creating a UDF filesystem/image built with a blocksize of 2048 and I'm going to burn it in the hopes that it works, since I can't find any supporting docs that spell this out.
 



> **meteorrock said:**
> You can try to use Nero linux 4.0 . Or use "K3b" an advanced linux burning program for a GUI solution. In the command line you can burn "UDF"  files with "UDF tools" installed through the command line. K3B, a burning image program that you can install from the apt-get or through 'ubuntu' software,  will recognize that UDF file for your blu ray with the tools installed below. Unless you like to fiddle in the command line to burn "UDF" blu ray files. I like the command line, but if there is a GUI solution, why not use it? Screw 'wine'. If we wanted windo$e we would be using it along with "IMGburn."   Native linux tools, bro. 

    Select the file-system tab in K3B and burn your "data" DVD or blu ray as a UDF in the options of that program after installing the tools below. De-select "Joliet" and the "Rock ridge" options as these are for DVD playback only with the "Video TS" and the "Audio TS" for those files on a  standard DVD player for playback.

  For Bluray you will use UDF only.  This also applies with "BDMV" and the "CERTIFICATE" folders that you demux or muxed with TsMuxeR , for those  .mkv files from the net, for blu ray playback on a standalone blu ray player.   Burn that image to a regular DVD if its under 4.7  GB for the blu ray hack that you are born to do. HAIL Pirates and torrent users. =)  If you are using a burnable blu ray disk, it will pop up as such in your "K3B." it will burn up to 50 GB on that app to a blank blu ray disk. Ignore the pop ups on "K3B" saying it will not play under windo$e with "Joliet" and "Rock Ridge" filesystems disabled in that app.  

```
sudo apt-get update
```

```
  apt-get install udftools
```

For more information on blu ray burning I got a thread over in linux mint at this link here. [http://forums.linuxmint.com/viewtopic.php?f=90&t=122314](http://forums.linuxmint.com/viewtopic.php?f=90&t=122314)

---

