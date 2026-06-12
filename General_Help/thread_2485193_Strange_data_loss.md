---
title: "Strange data loss"
date: 2023-03-22
forum: General Help
---

### Post by llantones on 2023-03-22
[FONT=-moz-fixed]Hello everybody: 
My work laptops come with Ubuntu 20.04 and a very strange thing happened  to a colleague of mine (I'm asking here because I think what happened  doesn't depend on the distribution): he was working with Filezilla and  suddenly he lost all the data (I think it's regardless that you were  working with Filezilla) from your home folder and it appeared as newly  installed. However, the rest of the operating system continued to  function without problems. 

He is a person that I trust hasn't done anything "weird". The laptop is  a Dell Latitude 3510 Intel i3 with a 256 GB SSD M.2 PCIe NVMe drive. The  entire system is installed on a single partition with ext4. 

After the disaster I recovered the data with Photorec and sorted by  extension, but since most of the filenames are lost the solution is  partial. In addition, many project files, which are located in folders,  are scattered by extension, and it is very difficult to restore such data. 

This is something that hasn't happened to me in 20 years of intensive  use of GNU/Linux. I would understand it with a mechanical drive if it  had taken a hit running but with SSDs I don't understand it. 

I did not find any bad sectors with the badblocks command. I checked  with fsck and it fixed quite a few entries but no lost+found files  showed up. Gnome-disk-utility tells me that the disk is ok and  smartmontools tells me that it can't look at the log. Memtest also did  not give any faults in RAM memory. 

Just in case anyone has any idea what might have happened. 

Thanks and regards 
[/FONT]

---

### Post by TheFu on 2023-03-22
>  Just in case anyone has any idea what might have happened. 
No clue, but .... 

Don't run badblocks on SSDs.

Filezilla has had some issues. Is there any reason not to use a normal Linux file manager instead?  After all, most of them support sftp:// URLs once the ssh-client package is installed.  Can't really see any need for filezilla on a Linux system.

If the systems were running a volume manager, you could create rotating hourly snapshots as a fallback point.  btrfs, zfs, and LVM2 support that.  They'd also help with the clearly missing backup of the data that is needed.

---

### Post by oldfred on 2023-03-22
Have seen similar where /home is a separate partition and if that partition does not mount, it creates a new /home inside / with defaults.
You said it only had one partition?

It might be possible to have copied something over /home/$USER or changed name of user in /home, so new /home created?

Years ago I lost some files, used Photorec. Took weeks to compare the many copies of some files with last backup. Some files were saved multiple times so many copies of each file. I now make first line of every text file or most other files I create, a comment that is the file name.

Even more years ago, using XP, I liked to click & drag files or even folders. Somewhere I dragged a file or folder over an essential Windows folder. Major corruption and lots of effort to attempt to repair. Or be careful clicking & dragging in GUI.

---

### Post by llantones on 2023-03-24
I have never had a problem with filezilla or any other ftp client.

---

### Post by TheFu on 2023-03-24
> **llantones said:**
> I have never had a problem with filezilla or any other ftp client.
You mean besides the complete lack of reasonable security with the plain FTP protocol, of course.
[https://security.stackexchange.com/questions/12494/how-can-i-prevent-my-ftp-from-being-hacked](https://security.stackexchange.com/questions/12494/how-can-i-prevent-my-ftp-from-being-hacked)

---

### Post by llantones on 2023-03-24
I mean only unjustified loss of data

---

### Post by TheFu on 2023-03-24
> **llantones said:**
> I mean only unjustified loss of data

Ah ... I doubt filezilla is directly responsible.

There was a time when a specific filezilla version wouldn't xfer files to any of my systems.  Research showed they'd picked up the wrong version of a library and it took about 6 months for the fix. In the meantime, I switched to using a better tool for my needs.  On MS-Windows clients, there seem to be 2 popular choices - FileZilla and WinSCP.  In the end, I just drastically reduced the workflows that need MS-Windows.  I'm down to 2 left - financial tracking and taxes. For everything else, no MS-Windows needed any longer.  Getting from 10 things to 2 took about a decade.  Of course, we all have different needs.

---

### Post by dragonfly41 on 2023-03-24
[COLOR=#000000][FONT=-moz-fixed]> After the disaster I recovered the data with Photorec and sorted by extension, but since most of the filenames are lost the solution is partial. In addition, many project files, which are located in folders, are scattered by extension, and it is very difficult to restore such data.

[/FONT][/COLOR]Having just read this, an idea popped into my head.
Not yet tested this but I've got it in the back of my mind.
If you use PhotoRec (I have not used this for a very long time) you wil have many files to try to recover.
Now since many will be text we can use a method of concordance analysis to reorder recovered unnamed text files.
We do this by placing all of the PhotoRec recovered “corpus” into a Recovery directory.
We now install AntConc which is a powerful tool for  text concordance analysis.
There is also an online service [SketchEngine]("https://ubuntuforums.org/ROOT--SketchEngine_419.html") but it is not free.
I use both AntConc abd [SketchEngine]("https://ubuntuforums.org/ROOT--SketchEngine_419.html") for various text projects.
We import all or groups of recovered fies in ~/Recovery folder and t then apply AntConc (desktop)  or [SketchEngine]("https://ubuntuforums.org/ROOT--SketchEngine_419.html") (cloud)
[https://www.laurenceanthony.net/software/antconc/](https://www.laurenceanthony.net/software/antconc/)
AntConc keeps everything in your desktop which you might consider for sensitive text analysis
We can skim through the “word” list to see key words which should trigger some recovery plan. In fact to automate this process we can use scripting. Not just bash scripting but automation scripting.
We can also add multiple words in complex concordance searches.


Create corpus
Scan corpus for words or word pair
Specify how to route matching files int folders.

Of course you will not recover file names. But based on this experience, it is a good idea to add the filename and filepath  into metadata at file head (as comment) and then these "words" will be listed in concordance analysis.


Do remember that this is a spur-of-the-moment and unproven idea.
And this does not address your question: "what happened?"

---

### Post by TheFu on 2023-03-24
> **dragonfly41 said:**
>  Having just read this, an idea popped into my head.
Not yet tested this but I've got it in the back of my mind. 

That's a good idea.

Most media file types have this information inside them.  Use exiftool to grab it.  Should work for video, audio, and image files (not raw).  A little egrep and the file name from the metadata is easily available, at least for my mkv, ogg, mp3, and jpg/png files.

For office documents, most will have a template with keywords inside the text. Use doctotext, pdftotext, xlstotext, to get that output and at least get project numbers grouped even if the filenames aren't immediately known.  That assumes the metadata isn't updated in the file headers.  Might be as easy as trying exiftool again.

```
$ exiftool  The_Linux_Command_Line-William_Shotts_1364.pdf 
ExifTool Version Number         : 12.40
File Name                       : The_Linux_Command_Line-William_Shotts_1364.pdf
Directory                       : .
File Size                       : 2.0 MiB
File Modification Date/Time     : 2020:05:30 11:15:54-04:00
File Access Date/Time           : 2020:05:30 11:15:54-04:00
File Inode Change Date/Time     : 2020:06:02 10:40:55-04:00
File Permissions                : -rw-rw-r--
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.5
Linearized                      : No
Page Count                      : 555
Language                        : en-US
[B]Title                           : The Linux Command Line
Author                          : William Shotts
[/B]Creator                         : Writer

```
Yep.
Of course, some authors aren't careful about their metadata:
```
$ exiftool  fingerprint.pptx 
ExifTool Version Number         : 12.40
File Name                       : fingerprint.pptx
Directory                       : .
File Size                       : 6.4 MiB
File Modification Date/Time     : 2022:05:29 00:29:42-04:00
File Access Date/Time           : 2022:05:29 00:29:37-04:00
File Inode Change Date/Time     : 2022:05:29 00:29:42-04:00
File Permissions                : -rw-rw-r--
File Type                       : PPTX
File Type Extension             : pptx
MIME Type                       : application/vnd.openxmlformats-officedocument.presentationml.presentation
Zip Required Version            : 20
Zip Bit Flag                    : 0x0006
Zip Compression                 : Deflated
Zip Modify Date                 : 1980:01:01 00:00:00
Zip CRC                         : 0xcd2d44bf
Zip Compressed Size             : 755
Zip Uncompressed Size           : 10883
Zip File Name                   : [Content_Types].xml
Preview Image                   : (Binary data 14864 bytes, use -b option to extract)
[B]Title                           : Slide 1
Creator                         : Some real name
Last Modified By                : Some other real name
[/B]Revision Number                 : 68
...

```
"Slide 1" isn't very useful.  The first slide is a huge red font with "Fingerprints" ... so I'm not likely to mistake the document title.  I always rename project files in specific ways for clarity.  Usually beginning with the project number. This is for my deliverables on a project.  Any data from others get a different file name usually based on the author's name/company.  It take extra work to start, but later it makes finding stuff really easy.

---

