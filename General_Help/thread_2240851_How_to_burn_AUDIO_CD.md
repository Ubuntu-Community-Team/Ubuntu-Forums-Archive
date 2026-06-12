---
title: "How to burn AUDIO CD?"
date: 2014-08-22
forum: General Help
---

### Post by mirec2 on 2014-08-22
Hi 
I'd like to burn a few audio cds, but I have just 20-30 broken ones... that's all. The songs are in MP3 format.
I tried: **K3b**, it stuck during burn process en about 30%, with message "cdrecord has no permission to open the device". Also tried convert the songs to the .wav format, but nothing changed, and slowest burn speed (8x), the same...
         **Brasero**, it stuck on "writing cd-text information", with the .wavs, same sh**.
        ** XFburn**, burnt it "succesfuly" but is unreadable...

I use commonly K3B to burn data CD/DVD, with data (movies) works well.
I'm on Ubuntu 14.04

I did not think, that burn an ordinary audio cd can be such big problem ...

Thanks

---

### Post by themightykhan84 on 2014-08-22
You could try burning through Rhythm Box.

---

### Post by mirec2 on 2014-08-22
If I press the button create audio cd, brasero will appear...

---

### Post by cbraxton on 2014-08-22
Are you trying to burn an actual audio CD to play in traditional-style CD players, or are you making a CD for an MP3-compatible player? It's an important difference.

I routinely use K3b to make audio CDs, but if I'm starting with MP3 files they need to be converted to WAV format first. I use a quick-and-dirty shell script for this:

```

#!/bin/sh

if [ ! -d wav ]; then
  echo "Creating wav subdir."
  mkdir wav
fi

for file in *.mp3
do
  echo '----------------------------------------'
  echo Processing $file...
  FNAME=`echo $file | cut -d . -f 1`
  mpg123 -w "wav/$FNAME.wav" "$FNAME.mp3"
  echo '----------------------------------------'
done

```

This uses the program mpg123 to do the actual conversion, so that needs to be installed. I just run this in the directory where the MP3 files are located and it puts the converted files in a "wav" subdirectory. The converted files can then be used directly by K3b to create an audio CD by selecting "New Audio CD Project." (This script may have problems with some filenames. The ".mp3" needs to be in lower case and  I don't think it processes filenames with multiple "." characters in them properly. Feel free to improve it!)

---

### Post by ajgreeny on 2014-08-22
> **cbraxton said:**
> Are you trying to burn an actual audio CD to play in traditional-style CD players, or are you making a CD for an MP3-compatible player? It's an important difference.

[COLOR=#ff0000]I routinely use K3b to make audio CDs, but if I'm starting with MP3 files they need to be converted to WAV format first. I use a quick-and-dirty shell script for this:[/COLOR]

```

#!/bin/sh

if [ ! -d wav ]; then
  echo "Creating wav subdir."
  mkdir wav
fi

for file in *.mp3
do
  echo '----------------------------------------'
  echo Processing $file...
  FNAME=`echo $file | cut -d . -f 1`
  mpg123 -w "wav/$FNAME.wav" "$FNAME.mp3"
  echo '----------------------------------------'
done

```

This uses the program mpg123 to do the actual conversion, so that needs to be installed. I just run this in the directory where the MP3 files are located and it puts the converted files in a "wav" subdirectory. The converted files can then be used directly by K3b to create an audio CD by selecting "New Audio CD Project." (This script may have problems with some filenames. The ".mp3" needs to be in lower case and  I don't think it processes filenames with multiple "." characters in them properly. Feel free to improve it!)
Unless things have changed since I last burned an audio CD in xubuntu 12.04, I don't think what you say above (in red) is correct.  I have in the past burned audio CDs from just about every music file-type available, mp3, wav. flac, m4a, without ever converting to wav first, and I have used k3b, brasero, and xfburn to do it.

Just to double check, I have just finished burning an audio CD from some m4a files using xfburn with no problem, so perhaps the original poster needs to check that all the codecs needed are available on the machine, because as far as I'm aware, you need only make sure that you have the correct codecs and they should all burn to audio CD with no problem.

---

### Post by cbraxton on 2014-08-22
> **ajgreeny said:**
> Unless things have changed since I last burned an audio CD in xubuntu 12.04, I don't think what you say above (in red) is correct.  I have in the past burned audio CDs from just about every music file-type available, mp3, wav. flac, m4a, without ever converting to wav first, and I have used k3b, brasero, and xfburn to do it.

Interesting. I just tried directly dropping an MP3 file into a K3b audio CD project on my Xubuntu 12.04 system and the following diagnostic message pops up:

```

Problems adding files to the project.

Unable to handle the following files due to an unsupported format: ...

```

If I manually convert the MP3 to WAV first then of course there is no problem. (It's not a big deal, I have a fairly fast system and do the conversion on a RAM drive so it goes pretty quickly.)

---

### Post by Butthead on 2014-08-22
I have never had any problems burning audo CD's directly from MP3 files in K3b either (from version 8.04 on).  :confused:

---

### Post by ajgreeny on 2014-08-22
> **cbraxton said:**
> Interesting. I just tried directly dropping an MP3 file into a K3b audio CD project on my Xubuntu 12.04 system and the following diagnostic message pops up:

```

Problems adding files to the project.

Unable to handle the following files due to an unsupported format: ...

```

If I manually convert the MP3 to WAV first then of course there is no problem. (It's not a big deal, I have a fairly fast system and do the conversion on a RAM drive so it goes pretty quickly.)
You need the libk3b-extracodecs package installed; do you have it? It is not a dependency of k3b.

---

### Post by cbraxton on 2014-08-22
> **ajgreeny said:**
> You need the libk3b-extracodecs package installed; do you have it? It is not a dependency of k3b.

Thanks for the tip, I'll check it!

---

### Post by mirec2 on 2014-08-23
Hi

Yes I have these cocecs installed. Also can drop directly files in .mp3 format to the Audio cd proyect, burn proces start, but ends an about 30-40%. In K3b. Have no idea whats problem... with .wav is equal. Burning data, like movies, mp3, documents, games... are no problem, everything works great.

Yesterday I tried burn audio cd with brother's computer (win7 + nero burning rom) and there was no problem at all. At the first attempt.

Can be my burner broken only for audio cd? Or is it a question of cds? Now I only have Memorex CD-R 52x, 700MB, 80 min.

---

### Post by ajgreeny on 2014-08-23
> **mirec2 said:**
> Hi

Yes I have these cocecs installed. Also can drop directly files in .mp3 format to the Audio cd proyect, burn proces start, but ends an about 30-40%. In K3b. Have no idea whats problem... with .wav is equal. Burning data, like movies, mp3, documents, games... are no problem, everything works great.

Yesterday I tried burn audio cd with brother's computer (win7 + nero burning rom) and there was no problem at all. At the first attempt.

Can be my burner broken only for audio cd? Or is it a question of cds? Now I only have Memorex CD-R 52x, 700MB, 80 min.
Difficult to know what the problem is.  If you have all the codecs needed for decoding and encoding music it must be some other problem.  What does the log that is produced by k3b tell you at the end of a faulty burn?

---

### Post by mirec2 on 2014-08-26
Hi everybody.

Today I tried again, and failed. I tried to burn it to a CD-RW (for well known reasons...;) ). This it the K3b bug:
```

 [FONT=Monospace]Devices[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]TSSTcorp CDDVDW SH-S223C SB01 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
 [FONT=Monospace]
[/FONT]
 [FONT=Monospace]System[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]K3b Version: 2.0.2[/FONT]
 [FONT=Monospace]KDE Version: 4.13.3[/FONT]
 [FONT=Monospace]QT Version:  4.8.6[/FONT]
 [FONT=Monospace]Kernel:      3.13.0-34-generic[/FONT]
 [FONT=Monospace]
[/FONT]
 [FONT=Monospace]Used versions[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]cdrecord: 1.1.11[/FONT]
 [FONT=Monospace]
[/FONT]
 [FONT=Monospace]cdrecord[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]scsidev: '/dev/sr0'[/FONT]
 [FONT=Monospace]devname: '/dev/sr0'[/FONT]
 [FONT=Monospace]scsibus: -2 target: -2 lun: -2[/FONT]
 [FONT=Monospace]Linux sg driver version: 3.5.27[/FONT]
 [FONT=Monospace]Wodim version: 1.1.11[/FONT]
 [FONT=Monospace]SCSI buffer size: 64512[/FONT]
 [FONT=Monospace]Beginning DMA speed test. Set CDR_NODMATEST environment variable if device[/FONT]
 [FONT=Monospace]communication breaks or freezes immediately after that.[/FONT]
 [FONT=Monospace]TOC Type: 0 = CD-DA[/FONT]
 [FONT=Monospace]Driveropts: 'burnfree'[/FONT]
 [FONT=Monospace]Device type    : Removable CD-ROM[/FONT]
 [FONT=Monospace]Version        : 5[/FONT]
 [FONT=Monospace]Response Format: 2[/FONT]
 [FONT=Monospace]Capabilities   : [/FONT]
 [FONT=Monospace]Vendor_info    : 'TSSTcorp'[/FONT]
 [FONT=Monospace]Identification : 'CDDVDW SH-S223C '[/FONT]
 [FONT=Monospace]Revision       : 'SB01'[/FONT]
 [FONT=Monospace]Device seems to be: Generic mmc2 DVD-R/DVD-RW.[/FONT]
 [FONT=Monospace]Current: 0x000A (CD-RW)[/FONT]
 [FONT=Monospace]Profile: 0x002B (DVD+R/DL) [/FONT]
 [FONT=Monospace]Profile: 0x001B (DVD+R) [/FONT]
 [FONT=Monospace]Profile: 0x001A (DVD+RW) [/FONT]
 [FONT=Monospace]Profile: 0x0016 (DVD-R/DL layer jump recording) [/FONT]
 [FONT=Monospace]Profile: 0x0015 (DVD-R/DL sequential recording) [/FONT]
 [FONT=Monospace]Profile: 0x0014 (DVD-RW sequential recording) [/FONT]
 [FONT=Monospace]Profile: 0x0013 (DVD-RW restricted overwrite) [/FONT]
 [FONT=Monospace]Profile: 0x0012 (DVD-RAM) [/FONT]
 [FONT=Monospace]Profile: 0x0011 (DVD-R sequential recording) [/FONT]
 [FONT=Monospace]Profile: 0x0010 (DVD-ROM) [/FONT]
 [FONT=Monospace]Profile: 0x000A (CD-RW) (current)[/FONT]
 [FONT=Monospace]Profile: 0x0009 (CD-R) [/FONT]
 [FONT=Monospace]Profile: 0x0008 (CD-ROM) [/FONT]
 [FONT=Monospace]Profile: 0x0002 (Removable disk) [/FONT]
 [FONT=Monospace]Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).[/FONT]
 [FONT=Monospace]Driver flags   : MMC-3 SWABAUDIO BURNFREE [/FONT]
 [FONT=Monospace]Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R[/FONT]
 [FONT=Monospace]Drive buf size : 720896 = 704 KB[/FONT]
 [FONT=Monospace]FIFO size      : 12582912 = 12288 KB[/FONT]
 [FONT=Monospace]Speed set to 1764 KB/s[/FONT]
 [FONT=Monospace]pregap1: -1[/FONT]
 [FONT=Monospace]Track 01: audio   44 MB (04:23.16) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 02: audio   35 MB (03:33.72) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 03: audio   42 MB (04:11.45) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 04: audio   36 MB (03:35.06) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 05: audio   28 MB (02:47.05) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 06: audio   29 MB (02:56.36) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 07: audio   39 MB (03:53.60) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 08: audio   35 MB (03:31.33) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 09: audio   38 MB (03:47.12) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 10: audio   41 MB (04:08.06) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 11: audio   43 MB (04:17.13) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 12: audio   40 MB (03:58.26) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 13: audio   42 MB (04:12.40) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 14: audio   47 MB (04:43.13) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 15: audio   26 MB (02:35.46) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 16: audio   46 MB (04:34.84) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 17: audio   55 MB (05:27.13) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 18: audio   45 MB (04:29.22) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 19: audio   38 MB (03:50.89) no preemp swab copy[/FONT]
 [FONT=Monospace]Track 20: audio   39 MB (03:55.76) no preemp swab copy[/FONT]
 [FONT=Monospace]Total size:      795 MB (78:51.18) = 354839 sectors[/FONT]
 [FONT=Monospace]Lout start:      796 MB (78:53/14) = 354839 sectors[/FONT]
 [FONT=Monospace]Current Secsize: 2048[/FONT]
 [FONT=Monospace]ATIP info from disk:[/FONT]
 [FONT=Monospace]  Indicated writing power: 3[/FONT]
 [FONT=Monospace]  Reference speed: 6[/FONT]
 [FONT=Monospace]  Is not unrestricted[/FONT]
 [FONT=Monospace]  Is erasable[/FONT]
 [FONT=Monospace]  Disk sub type: High speed Rewritable (CAV) media (1)[/FONT]
 [FONT=Monospace]  ATIP start of lead in:  -11635 (97:26/65)[/FONT]
 [FONT=Monospace]  ATIP start of lead out: 359849 (79:59/74)[/FONT]
 [FONT=Monospace]  1T speed low:  4 1T speed high: 10[/FONT]
 [FONT=Monospace]  2T speed low:  4 2T speed high:  0 (reserved val  6)[/FONT]
 [FONT=Monospace]  power mult factor: 1 5[/FONT]
 [FONT=Monospace]  recommended erase/write power: 3[/FONT]
 [FONT=Monospace]  A1 values: 24 1A BC[/FONT]
 [FONT=Monospace]  A2 values: 26 B2 26[/FONT]
 [FONT=Monospace]Disk type:    Phase change[/FONT]
 [FONT=Monospace]Manuf. index: 3[/FONT]
 [FONT=Monospace]Manufacturer: CMC Magnetics Corporation[/FONT]
 [FONT=Monospace]Blocks total: 359849 Blocks current: 359849 Blocks remaining: 5010[/FONT]
 [FONT=Monospace]Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.[/FONT]
 [FONT=Monospace]Last chance to quit, starting real write in    2 seconds.[/FONT]
 [FONT=Monospace]   1 seconds.[/FONT]
 [FONT=Monospace]   0 seconds. Operation starts.[/FONT]
 [FONT=Monospace]Waiting for reader process to fill input buffer ... input buffer ready.[/FONT]
 [FONT=Monospace]Performing OPC...[/FONT]
 [FONT=Monospace]Sending CUE sheet...[/FONT]
 [FONT=Monospace]Writing pregap for track 1 at 337007[/FONT]
 [FONT=Monospace]Starting new track at sector: 337157[/FONT]
 [FONT=Monospace]Track 01:    0 of   44 MB written.[/FONT]
 [FONT=Monospace]Track 01:    1 of   44 MB written (fifo 100%) [buf  74%]   2.8x.[/FONT]
 [FONT=Monospace]Track 01:    2 of   44 MB written (fifo 100%) [buf  75%]  10.4x.[/FONT]
 [FONT=Monospace]Track 01:    3 of   44 MB written (fifo 100%) [buf  74%]  10.6x.[/FONT]
 [FONT=Monospace]Track 01:    4 of   44 MB written (fifo 100%) [buf  74%]  10.3x.[/FONT]
 [FONT=Monospace]Track 01:    5 of   44 MB written (fifo 100%) [buf  75%]  10.7x.[/FONT]
 [FONT=Monospace]Track 01:    6 of   44 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 01:    7 of   44 MB written (fifo 100%) [buf  74%]  10.6x.[/FONT]
 [FONT=Monospace]Track 01:    8 of   44 MB written (fifo 100%) [buf  75%]  10.3x.[/FONT]
 [FONT=Monospace]Track 01:    9 of   44 MB written (fifo 100%) [buf  75%]  10.6x.[/FONT]
 [FONT=Monospace]Track 01:   10 of   44 MB written (fifo 100%) [buf  75%]  10.3x.[/FONT]
 [FONT=Monospace]Track 01:   11 of   44 MB written (fifo 100%) [buf  82%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   12 of   44 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 01:   13 of   44 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   14 of   44 MB written (fifo 100%) [buf  82%]  10.3x.[/FONT]
 [FONT=Monospace]Track 01:   15 of   44 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   16 of   44 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 01:   17 of   44 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   18 of   44 MB written (fifo 100%) [buf  82%]  10.2x.[/FONT]
 [FONT=Monospace]Track 01:   19 of   44 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   20 of   44 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 01:   21 of   44 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   22 of   44 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 01:   23 of   44 MB written (fifo 100%) [buf  82%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   24 of   44 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   25 of   44 MB written (fifo 100%) [buf  75%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   26 of   44 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   27 of   44 MB written (fifo 100%) [buf  75%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   28 of   44 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   29 of   44 MB written (fifo 100%) [buf  75%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   30 of   44 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   31 of   44 MB written (fifo 100%) [buf  75%]  10.5x.[/FONT]
 [FONT=Monospace]Track 01:   32 of   44 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   33 of   44 MB written (fifo 100%) [buf  82%]  10.4x.[/FONT]
 [FONT=Monospace]Track 01:   34 of   44 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   35 of   44 MB written (fifo 100%) [buf  74%]  10.4x.[/FONT]
 [FONT=Monospace]Track 01:   36 of   44 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   37 of   44 MB written (fifo 100%) [buf  74%]  10.4x.[/FONT]
 [FONT=Monospace]Track 01:   38 of   44 MB written (fifo 100%) [buf  75%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   39 of   44 MB written (fifo 100%) [buf  74%]  10.3x.[/FONT]
 [FONT=Monospace]Track 01:   40 of   44 MB written (fifo 100%) [buf  82%]  10.1x.[/FONT]
 [FONT=Monospace]Track 01:   41 of   44 MB written (fifo 100%) [buf  74%]  10.4x.[/FONT]
 [FONT=Monospace]Track 01:   42 of   44 MB written (fifo 100%) [buf  74%]  10.0x.[/FONT]
 [FONT=Monospace]Track 01:   43 of   44 MB written (fifo 100%) [buf  82%]  10.3x.[/FONT]
 [FONT=Monospace]Track 01:   44 of   44 MB written (fifo 100%) [buf  74%]  10.6x.[/FONT]
 [FONT=Monospace]Track 01: Total bytes read/written: 46421424/46421424 (19737 sectors).[/FONT]
 [FONT=Monospace]Starting new track at sector: 356894[/FONT]
 [FONT=Monospace]Track 02:    0 of   35 MB written.[/FONT]
 [FONT=Monospace]Track 02:    1 of   35 MB written (fifo 100%) [buf  82%]  10.1x.[/FONT]
 [FONT=Monospace]Track 02:    2 of   35 MB written (fifo 100%) [buf  74%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:    3 of   35 MB written (fifo 100%) [buf  82%]  10.7x.[/FONT]
 [FONT=Monospace]Track 02:    4 of   35 MB written (fifo 100%) [buf  74%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:    5 of   35 MB written (fifo 100%) [buf  74%]  10.6x.[/FONT]
 [FONT=Monospace]Track 02:    6 of   35 MB written (fifo 100%) [buf  74%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:    7 of   35 MB written (fifo 100%) [buf  74%]  10.6x.[/FONT]
 [FONT=Monospace]Track 02:    8 of   35 MB written (fifo 100%) [buf  75%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:    9 of   35 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   10 of   35 MB written (fifo 100%) [buf  75%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:   11 of   35 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   12 of   35 MB written (fifo 100%) [buf  82%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:   13 of   35 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   14 of   35 MB written (fifo 100%) [buf  75%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:   15 of   35 MB written (fifo 100%) [buf  75%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   16 of   35 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 02:   17 of   35 MB written (fifo 100%) [buf  75%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   18 of   35 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 02:   19 of   35 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   20 of   35 MB written (fifo 100%) [buf  75%]  10.2x.[/FONT]
 [FONT=Monospace]Track 02:   21 of   35 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   22 of   35 MB written (fifo 100%) [buf  74%]  10.1x.[/FONT]
 [FONT=Monospace]Track 02:   23 of   35 MB written (fifo 100%) [buf  74%]  10.5x.[/FONT]
 [FONT=Monospace]Track 02:   24 of   35 MB written (fifo 100%) [buf  82%]  10.2x.[/FONT]
 [FONT=Monospace]Track 02:   25 of   35 MB written (fifo 100%) [buf  74%]  10.4x.[/FONT]
 [FONT=Monospace]Track 02:   26 of   35 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 02:   27 of   35 MB written (fifo 100%) [buf  74%]  10.4x.[/FONT]
 [FONT=Monospace]Track 02:   28 of   35 MB written (fifo 100%) [buf  74%]  10.2x.[/FONT]
 [FONT=Monospace]Track 02:   29 of   35 MB written (fifo 100%) [buf  74%]  10.7x.[/FONT]
 [FONT=Monospace]Track 02:   30 of   35 MB written (fifo 100%) [buf  74%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:   31 of   35 MB written (fifo 100%) [buf  74%]  10.6x.[/FONT]
 [FONT=Monospace]Track 02:   32 of   35 MB written (fifo 100%) [buf  82%]  10.2x.[/FONT]
 [FONT=Monospace]Track 02:   33 of   35 MB written (fifo 100%) [buf  74%]  10.6x.[/FONT]
 [FONT=Monospace]Track 02:   34 of   35 MB written (fifo 100%) [buf  74%]  10.3x.[/FONT]
 [FONT=Monospace]Track 02:   35 of   35 MB written (fifo 100%) [buf  74%]  10.7x.[/FONT]
 [FONT=Monospace]Track 02: Total bytes read/written: 37700208/37700208 (16029 sectors).[/FONT]
 [FONT=Monospace]Starting new track at sector: 372923[/FONT]
 [FONT=Monospace]Track 03:    0 of   42 MB written.[/FONT]
 [FONT=Monospace]Track 03:    1 of   42 MB written (fifo 100%) [buf  75%]  10.1x.[/FONT]
 [FONT=Monospace]Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error[/FONT]
 [FONT=Monospace]CDB:  2A 00 00 05 B3 AF 00 00 1B 00[/FONT]
 [FONT=Monospace]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=Monospace]Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00[/FONT]
 [FONT=Monospace]Sense Key: 0x3 Medium Error, Segment 0[/FONT]
 [FONT=Monospace]Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0[/FONT]
 [FONT=Monospace]Sense flags: Blk 0 (not valid) [/FONT]
 [FONT=Monospace]cmd finished after 4.678s timeout 200s[/FONT]
 [FONT=Monospace]/usr/bin/wodim: A write error occured.[/FONT]
 [FONT=Monospace]/usr/bin/wodim: Please properly read the error message above.[/FONT]
 [FONT=Monospace]write track data: error after 1778112 bytes[/FONT]
 [FONT=Monospace]Writing  time:   82.851s[/FONT]
 [FONT=Monospace]Average write speed  57.1x.[/FONT]
 [FONT=Monospace]Min drive buffer fill was 74%[/FONT]
 [FONT=Monospace]Fixating...[/FONT]
 [FONT=Monospace]Fixating time:   20.508s[/FONT]
 [FONT=Monospace]/usr/bin/wodim: fifo had 1544 puts and 1354 gets.[/FONT]
 [FONT=Monospace]/usr/bin/wodim: fifo was 0 times empty and 1345 times full, min fill was 98%.[/FONT]
 [FONT=Monospace]BURN-Free was never needed.[/FONT]
 [FONT=Monospace]
[/FONT]
 [FONT=Monospace]cdrecord command:[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=10 -sao driveropts=burnfree -useinfo -audio /tmp/kde-miro/k3b_audio_0_01.inf /tmp/kde-miro/k3b_audio_0_02.inf /tmp/kde-miro/k3b_audio_0_03.inf /tmp/kde-miro/k3b_audio_0_04.inf /tmp/kde-miro/k3b_audio_0_05.inf /tmp/kde-miro/k3b_audio_0_06.inf /tmp/kde-miro/k3b_audio_0_07.inf /tmp/kde-miro/k3b_audio_0_08.inf /tmp/kde-miro/k3b_audio_0_09.inf /tmp/kde-miro/k3b_audio_0_10.inf /tmp/kde-miro/k3b_audio_0_11.inf /tmp/kde-miro/k3b_audio_0_12.inf /tmp/kde-miro/k3b_audio_0_13.inf /tmp/kde-miro/k3b_audio_0_14.inf /tmp/kde-miro/k3b_audio_0_15.inf /tmp/kde-miro/k3b_audio_0_16.inf /tmp/kde-miro/k3b_audio_0_17.inf /tmp/kde-miro/k3b_audio_0_18.inf /tmp/kde-miro/k3b_audio_0_19.inf /tmp/kde-miro/k3b_audio_0_20.inf[/FONT]

```
 [FONT=Monospace]
[/FONT]

---

### Post by uRock on 2014-08-26
Please apply code tags in the above post. [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Thanks,
uRock

---

### Post by mirec2 on 2014-08-26
same tracks with brasero. 

This is where it **always** stuck. With CD-R or CD-RW.
[ATTACH=CONFIG]255852[/ATTACH]

is in Slovak, but en english is:
Writing audio CD
Writing CD-Text information.

---

