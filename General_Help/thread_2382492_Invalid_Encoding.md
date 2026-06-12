---
title: "Invalid Encoding"
date: 2018-01-14
forum: General Help
---

### Post by bookie2 on 2018-01-14
Hi guys!
I tend to use Linux and often Ubuntu Live cd's to back up files from customer computers etc...

I always choose to boot to a Swedish desktop from the live cd....

The problem I get some times is I attach a hard drive from an external enclosure and that comes up error on documents etc...we have there extra Swedish letters å, ä, ö. these often get replaced by a obviously when there are hundreds of documents...one can't change every one by hand......help....:p

Is there something I need to check on the Live Cd before attaching an external drive so that the "(invalid Encoding" doesn't take over documents with the 3 extra Swedish letters?

If I need to install something on the live cd...please say....

Now I have files that have been attributed with the replacement of the Swedish letters with either a ? or other symbols etc...can I replace the errors with the original letters through running a command?

Any help with this would make my life a lot easier....


If you need other info...please say!

bookie32

---

### Post by Holger_Gehrke on 2018-01-14
Are you talking about changed file **names** or file **contents** ? The solution to your problem depends on the answer to that question ...

Holger

---

### Post by bookie2 on 2018-01-14
Hi [COLOR=#000000]Holger_Gehrke[/COLOR]:P
Yep....Example Anders Sjöholm becomes Anders Sj?holm (invalid Encoding)

bookie32

---

### Post by The Cog on 2018-01-14
I don't think Holger_Gehrke intended to ask a logical OR question.
I think he wanted to know which of the two you are actually having trouble with.

If the problem is with filenames, then please tell which filesystem (e.g. ext4, FAT32) the external drive is formatted with.

If the problem is with file contents, then please tell what type of documents these files are.

---

### Post by bookie2 on 2018-01-15
Hi again!
Ok....thought my example was showing the problem with changed file names...that means everything...

Folders, documents, zipped files....just everything can have "?" or a couple of ",," to replace the Swedish letters a name can have "?", ",," or even a name can have H&#8224;kan instead of Håkan...
The file system on the external drives at the moment is ext4...

Is there anything else you need to know?

bookie32

---

### Post by Holger_Gehrke on 2018-01-15
ext4 uses Unicode for file names, so Swedish characters should not be a problem. I think the problem is the encoding at the source - on the hd of the customer's machine. I would check the next time you do a backup what file system is used with what encoding and whether the file names already look wrong when seen from the live system. Let's say you mount it as ntfs with utf-8 encoding and it actually is something else like for example iso-latin-1, then that would explain the wrong characters. You would have to unmount and mount again with different options (or remount ...).

As for correcting the wrong names: use ```

find . -iname '*[[COLOR=#ff0000]list of the wrong characters here[/COLOR]]*'

```
then do a ```

rename 'y/[COLOR=#ff0000]list of wrong characters[/COLOR]/[COLOR=#00ff00]list of right characters[/COLOR]/' *
```
in all the directories where 'find' found names with the wrong characters. Replace the coloured parts of the commands as needed.
(rename has an option '-n' which will make it only show what it would do;use it until you're sure that the replacement will do what you want.)

Holger

---

### Post by bookie2 on 2018-01-15
Thank you so much for your help!

I am at a loss to why the files are coming up with symbols now when they didn't before....I have a installed version of Ubuntu on a USB and that is automatically mounting the drives as I add them in the external enclosure ....the drives are all ext4....so they would be automatically added as ext4 drives.

Most of the files come from Windows drives and I use linux to back them up....so at one stage or another I have transfered them to ext4....

I am a little busy with work related stuff at the moment but will test your info as soon as I have a mo....


If I have more questions I will add them:D

bookie32

---

### Post by SeijiSensei on 2018-01-15
You could zip the files on the Windows machine then copy the zip archive to Linux.

If this problem persists, look into the iconv command which converts between character encodings.  The Windows machine is probably using "Windows-1252" rather than UTF-8.  Take a problematic file from the backup and run

```
iconv -f=WINDOWS-1252 -t=UTF-8 filename
```

and see if the errors disappear.  You can get a list of valid codes with the command "iconv -l".  Take a look at "[man iconv]("https://linux.die.net/man/1/iconv")" for more details.  

You can determine the encoding of many files with the "[file]("https://linux.die.net/man/1/file")" command.
```

file -i world-bank-codebook.txt
world-bank-codebook.txt: text/plain; charset=us-ascii

```

---

### Post by The Cog on 2018-01-15
I think choosing a swedish desktop will simply choose your keyboard layout and date format. I'm pretty sure it won't change the way names are displayed. Also, ext4 uses utf8 for filenames so there should be no confusion once the filename is written to ext4. So I suspect that the problem is in how the file is transferred from windows in the first place. I would be surprised if reading NTFS filenames gave problems, because NTFS uses UTF16. 

I can imagine a problem when reading files from FAT because FAT uses 8-bit characterset, often 1252. It may be that choosing a swedish desktop changes the default characterset that Linux uses for FAT partitions. The only way I can think of to verify this is to use the mount command to see how a drive has been mounted after connecting it. And repeat the test with different desktop choices. I don't know how you might actually specify the characterset to use when mounting a FAT drive other than changing your desktop or using command-line arguments to the mount command.

For file contents, the filesystem is not relevant - the filesystem will store what it's given. For plain text files you could use iconv as SeijiSensei suggests. For more complex documents you will have to deal with problems like compression and other internal representations etc. If you are just backing these documents up with the intention of restoring them to where they were backed up from then I guess it's not worth worrying about how they appear on Linux.

P.S.
If I'm wrong about anything, I am very happy to be corrected.

---

