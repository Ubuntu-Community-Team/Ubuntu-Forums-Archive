---
title: "[SOLVED] Help With BackUps"
date: 2007-05-13
forum: General Help
---

### Post by MrFSL on 2007-05-13
Hello All!

I would like to back up my music folder. It is roughly 30 GB and I would like to back it up to a series of DVD-Rs.

Does anyone know of an easy way to do this? I actually have been wondering about this for awhile. Is there a shell script or a program that helps you back up to DVD-R / CD-R, automatically splitting the filesystem in order to fit on the media?

Any help would be appreciated.

MrFSL

---

### Post by indytim on 2007-05-13
As long as your Music folder is on one partition, my recommendation is:

[Partimage]("http://www.partimage.org/Partimage-manual_Usage")

There is an option to specify the backup image size so you could size it to a DVD (~4G).  Partimage will break the outputs to the size specified.

As with anything else in Linux, there are other options out there.

Good Luck,

IndyTim

---

### Post by MrFSL on 2007-05-13
Thank you for the reply.

Yes I have used PartImage in the past to make whole disk images, but as you know this is very limiting. I just want to burn the data off to disk... get prompted to insert a new disk when the previous one is full.

Anyone else?

Thanks
MrFSL

---

### Post by MrFSL on 2007-06-11
Bump...

Still having this issue... wondering if anyone has additional insight.

---

### Post by carcioni on 2007-06-11
Here's a few suggestions. I can't say I have tried any of them in quite a while, but Mondo was pretty good as i recall. Have a look at these and see if there is anything useful. They all seem to handle DVD based archives, Some are more enterprise focussed but they may suit your needs.

Cheers


[www.mondorescue.org](www.mondorescue.org)
[www.bacula.org](www.bacula.org)
[www.amanda.org/](www.amanda.org/)

---

### Post by tagra123 on 2007-06-11
A fairly easy way is to create a tar.gz file -- you can even do this from nautilus. Once the big tar file is made you can split the file into 1gb or 2gb chunks using split.

SPLIT APART (FOR 1GB files)
split -b 1000m "MyMusic.tar.gz" MyMusizSplit-


TO JOIN THEM BACK TOGETHER
cat  MyMusicSplit-ab >> MyMusicSplit-aa
cat  MyMusicSplit-ac >> MyMusicSplit-aa
cat  MyMusicSplit-ad >>  MyMusicSplit-aa

mv MyMusicSplit-aa MyMusic.tar.gz

Then you can untar them.

Not perfect, but works well for large backups.

---

### Post by MrFSL on 2007-06-12
Thank you for the replies.

Bacula and Amanda, I have used in the past (briefly) and are more designed toward large network backup solutions.

Mondo I had never heard of before so I tried it out.
There are alot of options in Mondo but it simply isn't geared to what I am trying to accomplish. For those of you that don't know, Mondo allows you to do backups of your whole system or selected directories to CD-R, DVD-R, Tape, or NFS. Mondo can create self booting removable media that allows you to rescue a broken system. 

It is just way more then I need and DIFFICULT if I simply need to restore just one file or one directory.

All I am looking for is a simple method to backup a directory to multiple DVD/CD-R. I don't really care (and actually prefer) that these backups not be compressed. I don't need a handy little GUI to restore the files - I keep my file system well organized so it is already easy to dig through my backup disks to locate files to restore.

@tagra123
Your method is helpful and thank you for posting. But your method is problematic for 3 reasons.
1) I worry about the integrity of my backups when I am splitting a 30GB tar file into 7 chunks.
2) I cannot easily restore a single file without reassembling the archive.
3) It would require a great amount of disk space (and time) to reassemble the archives and then extract all the data

I would script out a solution but am not sure how to do it. I would want to keep the file structure intact but somehow automatically split it into the appropriate sizes.... :(

Not feeling good about this. Any more suggestions?

---

### Post by tagra123 on 2007-06-12
Just for the secord I have split and recombined 10 to 12 GB files with no problems.

dar and KDAR look like they may do what you are looking for.

[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)

partimage in my opinion is by far one of the most reliable. The most reliable is to create and exact clone using dd, but this requires extra disk space which most of us simply do not have.

---

### Post by MrFSL on 2007-06-12
Well DAR is the best solution I have seen so far.

It allows me to slice the archives into Disk sized chunks and restore individual files. 

What I am really looking for is a way to backup my Music and Picture folders to disks without putting then into an archive. Just parse the folder/file structure and splitting them into DVD sized folders.

I do appreciate the help and replies though. Please if anyone knows another, more suitable method, I would appreciate it.

---

### Post by jwh400 on 2007-06-12
I haven't used it but BackUpPC may be what you're looking for since it allows access to individual files. This program is in your repositories and the following description is from the repository. 

[I]BackupPC is disk based and not tape based. This particularity allows
features not found in any other backup solution:
 * Clever pooling scheme minimizes disk storage and disk I/O.
   Identical files across multiple backups of the same or different PC are
   stored only once (using hard links), resulting in substantial savings
   in disk storage and disk writes.
 * Optional compression provides additional reductions in storage.
   CPU impact of compression is low since only new files (those not already
   in the pool) need to be compressed.
 * A powerful http/cgi user interface allows administrators to view log files,
   configuration, current status and allows users to initiate and cancel
   backups and browse and restore files from backups very quickly.
 * No client-side software is needed. On WinXX the smb protocol is used.
   On linux or unix clients, rsync or tar (over ssh/rsh/nfs) can be used
 * Flexible restore options. Single files can be downloaded from any backup
   directly from the CGI interface. Zip or Tar archives for selected files
   or directories can also be downloaded from the CGI interface.
 * BackupPC supports mobile environments where laptops are only intermittently
   connected to the network and have dynamic IP addresses (DHCP).
 * Flexible configuration parameters allow multiple backups to be performed
   in parallel.
 * and more to discover in the manual...[/I]

---

### Post by MrFSL on 2007-06-13
Its a good thought but BackUpPC is a server/client system for backing up computers to a server.

:( :( :(

I can't believe the wonderful support I'm getting. Please keep the good ideas coming.

I'm trying to script out a solution using common unix commands (du, sed, cp) but having a hard time getting it right.

If I could get a good answer to this problem it surely would be amazing!

---

### Post by tagra123 on 2007-06-13
The only other thing I can think of would be to write a bash script that would check files sizes and count to the desired size to create a copy list, then the script could copy the lists one by one.  To be extra fancy you could then call mkisofs to directly copy the files to CD.



```


#!/bin/sh


TARGETPATH=$1


for FILENAME  in `ls -dXr $TARGETPATH/*`;do

  let "FILESIZE=$(stat -c%s "$FILENAME")"
  echo $filesize
  
 done
```

The above should print the file sizes. Instead of printing you could add a couple of variables to track and reset the count and create a list this way or copy to a tmp folder and then burn the cd from there.

---

### Post by MrFSL on 2007-06-16
Well thanks again for all the help.

I started writing my script out and now have a functional solution. It ain't pretty but if someone wanted to polish it up they could. I might make it a nautilus script and perhaps add a perl/tk or xenity frontend. I still feel like I am "re-inventing the wheel" on this one. What I am after seems so basic that I felt sure there was already a solution out there. ... ... Well perhaps not. Hope this helps someone else out. It was a neat scripting challenge. Luckily mkisofs supports graph-points or else I would have had a real problem keeping my folder structure. **EDIT** - Please note that the following is NOT a functional script. It needs to be edited to suit your needs.

```
#!/usr/bin/perl
#Version:1

#--CLEAR SCREEN
system ('clear');

#--PRINT SCRIPT & AUTHOR INFORMATION
print "\n==========================================
  Backup.pl - backup your folder to DVD.
  Script by MrFSL ( UbuntuForums.org )
==========================================";

#--OPEN A FILE TO PRINT FILE / FOLDER STRUCTURE, PATH LIST / GRAFT POINTS
open (TEMP, "> /home/fsl/Desktop/temp.txt");

#--OPEN THE TRAGET DIRECTORY
$folder = "/home/share/Pictures";
print "\nTarget Directory = $folder";

#--RECURSE THE DIRECTORY CREATING TEMP.TXT
&parse ($folder);
sub parse {
        my $dir = shift;
        opendir (DIR, $dir);
        my @contents = map "$dir/$_", sort grep !/^\.\.?$/, readdir DIR;
        foreach $item (@contents) {
                #--IF NOT A LINK AND NOT A DIRECTORY WRITE TO TEMP
                if (!-l $item && !-d $item) {
                        print TEMP "$dir/=$item\n";
                }
                #--IF NOT A LINK AND IS A DIRECTORY RECURSE        
                next unless (!-l $item && -d $item);
                &parse ($item);
        }
}

#--CLOSE AND REOPEN TEMP TO PARSE
close TEMP;
open (TEMP, "/home/fsl/Desktop/temp.txt");

#--PARSE TEMP FOR FILESIZES
$total = 0;
$num = 1;
open (TEMPP, "> /home/fsl/Desktop/temp$num.txt");
while ( <TEMP> ) {
        chomp;
        #--REGULAR EXPRESSION WITH THE FOLLOWING PARSING
        #--$1 = "PATH"
        #--$2 = "/=/"
        #--$3 = "PATH AND FILENAME" ($2 CUTS OF THE LEADING / SO WE PUT IT BACK)
        s/(.*)(\/=\/)(.*)/\/$3/;
        #--FIND THE FILE SIZE AND ADD IT TO $total
        $temp = $total + (-s "$_");
        if ($temp <= 700000000){
                print TEMPP "$1/=$_\n";
                $total = $temp;
        } else {
                $total = 0;
                $total += (-s "$_");
                $num ++;
                close TEMPP;
                open (TEMPP, "> /home/fsl/Desktop/temp$num.txt");
                print TEMPP "$1/=$_\n";
        }
}
close TEMP;
close TEMPP;

#--SOME USEFUL INFO
print "\n\nBackup Will Require $num CD-R's\n";
print "\nHit Return To Continue...\n";
$pause = <STDIN>;

#--BURN
$temp = 0;
until ($temp == $num) {
        $temp ++;
        system ('clear');
        print "\nPlease insert Blank Disk \#$temp";
        print "\nWait for the disk to load then press";
        print "\nENTER to continue.";
        $pause = <STDIN>;
        #--MAKE ISOs
        #system ("mkisofs -J -R -D -iso-level 3 -graft-points -path-list /home/fsl/Desktop/temp$temp.txt -o /home/fsl/Desktop/temp$temp.iso");
        #--BURN TO DISK
        #system ("mkisofs -J -R -D -iso-level 3 -graft-points -path-list /home/fsl/Desktop/temp$temp.txt | cdrecord -vv -");
        print "\n\nBackUp - $folder - Disk \#$temp Complete!";
        print "\nPress ENTER to continue.";
        $pause = <STDIN>;
}

#--COMPLETE!
print "\n\nBurn Process Complete!\nPress ENTER to exit.\n";
$pause = <STDIN>;

```

---

### Post by dgrafix on 2007-06-21
I too am having a nightmare trying to find a multi DVD spaning backup simply to backup a few dirs and just installed backupPC.

I dont get how to start the program. Theres nothing in the menus and typing backuppc from terminal says nothing either.
If i "locate backuppc" it finds nothing, but under synaptic properties for pcbackup there are several installed files.

Any ideas?

I just want something with a simple gui that you tick some directories to back up and click go. (it then burns the disks using a multi part compressed archive)

---

### Post by namityadav on 2007-06-22
/etc/init.d/backuppc start

But if you aren't aware of this, then that means that you haven't configured the backuppc for it to work correctly anyway. I installed backuppc (Along with external tools that it needs like some perl plugins etc - you'll find them all in synaptics), followed the instructions on the backuppc website, and I had the backups running in no time (Backing up both linux and windows laptops). I must say, this tool is very easy and very powerful.

---

