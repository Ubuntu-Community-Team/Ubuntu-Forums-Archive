---
title: "Backup How-to.  Uncertainty about command &quot;read cd&quot;"
date: 2008-04-13
forum: General Help
---

### Post by billdotson on 2008-04-13
I have written a bash script that concatenates the files off of 7 DVDs into a single compressed image, decompresses that image, and then restores a partition.

Here is what I did:

#! /bin/sh

# concatenate split XP image files from DVDs; waits for user input before continuing
umount /dev/sda1
# Disc 1
cat /media/cdrom0/Windows_XP_full.bz2-aa* >> /media/XP_backup/Windows_XP.bz2
echo -n "Please insert the next DVD"
read cd
echo "Continuing..."
# Disc 2
cat /media/cdrom0/Windows_XP_full.bz2-aa* >> /media/XP_backup/Windows_XP.bz2
echo -n "Please insert the next DVD"
read cd
echo "Continuing..."
# Disc 3
cat /media/cdrom0/Windows_XP_full.bz2-aa* >> /media/XP_backup/Windows_XP.bz2
echo -n "Please insert the next DVD"
read cd
echo "Continuing..."
# Disc 4
cat /media/cdrom0/Windows_XP_full.bz2-aa* >> /media/XP_backup/Windows_XP.bz2
echo -n "Please insert the next DVD"
read cd
echo "Continuing..."
# Disc 5
cat /media/cdrom0/Windows_XP_full.bz2-aa* >> /media/XP_backup/Windows_XP.bz2
echo -n "Please insert the next DVD"
read cd
echo "Continuing..."
# Disc 6
cat /media/cdrom0/Windows_XP_full.bz2-aa* >> /media/XP_backup/Windows_XP.bz2
echo -n "Please insert the next DVD"
read cd
echo "Continuing..."
# Unmount /dev/sda1 (with your setup, that is Windows XP partition.)
# Disc 7
# Decompress and restore Windows XP backup image
cat /media/cdrom0/Windows_XP_full.bz2-aa* >> /media/XP_backup/Windows_XP.bz2
echo -n "Task complete, commencing restore operation."
bzip2 -dc /media/Windows_backup/Windows_full.bz2 | ntfsclone -r -O /dev/sda1 -
echo "Let forth a triumphant sound; Restore operation has been completed!"


The first thing that is done is to unmount the partition that the image will be overwriting.  If you do not do this, you will almost certainly, if not always end up with some very serious problems.  This same idea applies for using the dd program as well.

The * with the cat is due to all the files on these DVDs are the same file, only split up into 14 parts.  So I have Windows_XP_full.bz2-aaa through Windows_XP_full.bz2-aan.  
This part (I am pretty sure) prints the string to the terminal, then read waits for a disc to be in the drive and for the user to press return (enter).  Then echo prints the other string to the terminal and continues concatenating the files: 
"echo -n "Please insert the next DVD"
read cd
echo "Continuing..."

"bzip2 -dc /media/Windows_backup/Windows_full.bz2 | ntfsclone -r -O /dev/sda1 -"
That line decompresses the file Windows_full.bz2, and then that file is passed through a pipe as it is being decompressed and is passed onto ntfsclone (part of ntfsprogs) which rewrites that specified partition over with the image.  The "-" at the end is to specify standard input.  

I am not so sure what the command "read cd" does.  I know that if I only use read, I get an "arg 27" error, so what then does the "cd" do?

Other than that, this is a great way for anyone seeking to keep a backup of their Windows installation as is.  Personally, I installed Windows, installed all the updates and core applications that I would absolutely always need, along with a few games and then made the backup image.  I used bzip2 to compress the image, and the "split" command in bash to split the archive into 13 1.8GB pieces, and 1 1.5GB piece (the last piece).  The way I compressed and split the image all in one step was "bzip2 -c /media/Windows_backup/Windows_XP_full | split -b 1850m - /media/Windows_FAT32/Windows_img_full/Windows_XP_backup.bz2-a"

Then I burned 2 pieces at a time onto 7 single layer DVDs.  This way you can try out all the software you want and not be concerned about constantly checking for virii and spyware.  That is of course, unless you get spyware or virii that affects your computer hardware, other partitions, or even other hard drives.  Although, if Ubuntu is on your external hard drive that is very easily unplugged.  

Even if you do not feel comfortable when thinking that your computer could possibly acquire virii or spyware, then you can still scan for it (obviously).  Another reason this is a useful way to backup Windows is that Windows has a half-life and after a few months of installation gets slower and slower and slower.  It will often (in my experiences) begin to have errors, be exceedingly slow, and need a fresh installation.  If anyone has ever done a fresh Windows installation, including getting all of the drivers necessary for your system and reinstalling all your applications, you know how long that takes.  By restoring from an image with all of your core applications and drivers installed it takes (for my 25GB compressed image) about 1-2 hours to "reinstall".  That is much better than a real reinstallation.  

Of course, you must remember to make constant backups of your files.  I made a shutdown script for both Ubuntu and Windows XP (using the bash shell for Ubuntu and the DOS terminal for XP) that backs up all my files upon shutdown of the system. program configuration files and save games into a separate backup partition.  If the programs you have (all of mine I can do this with) can be reinstalled and set back to the way you had them by replacing configuration files and what not, then you could even add some lines at the bottom of the restore script to put all of your files back into place after the image is restored.  For my purposes this method of backing up my XP partition and my files works well and I have had no problems with this method so far.  

If you have any questions about it I will be glad to try to answer them.

---

### Post by JerryK on 2008-04-13
read cd takes input from the keyboard and stores it in the variable cd.  In this case, it is a throw-away, since your script is simply waiting for some input from the user before continuing on to the next DVD.

If you needed to get something meaningful from the user, you could access it by referencing the variable cd later in the script.  I have not done much with bash, but in an older sh, you could do echo $cd to display the contents of the variable cd.

---

