---
title: "Content Management across multiple volumes"
date: 2007-12-24
forum: General Help
---

### Post by Guntherk9 on 2007-12-24
Good Morning everyone,

I'm currently running Ubuntu Server 7.10 with an attached SCSI 16Bay RAID Array.  The RAID is currently configured for RAID5 and fully populated for a file storage area of 11.25TB's.  I've partitioned the 11.25TB's into 5 - 2TB volumes and 1 - 650GB Volume and formated them all as ext3.

Everything is working fine and the setup was painless.

Here is my problem:  As I begin to fill these volumes with folders and files, Is there a content management system  or something else that I can use to keep track of which ext3 volume a certain folder or file is located on?   I found myself spending a lot of time searching these volumes for a specific folder and/or file.   

Also, I would want this content manager to be able to notify or alert of any duplicate folders existing on these 6 volumes.

Any suggestion would be much appreciated.  :confused:

With Thanks,

Gunther

---

### Post by fjgaude on 2007-12-24
I take it Nautilus File Manager doesn't do the job?

---

### Post by Guntherk9 on 2007-12-24
Hi fjgaude,

Thank you for the reply.  The Nautilus File Manager doesn't do what I want at this point.  I thought there would be something out there like a content Management system to index or track existing file/folders.

Is there a way to mount all 6 volumes as a single share point?  Or maybe a script to that can be executed across all the volumes and list and / or sort the folders by name, etc.

Thanks again for your help.

Cheers Mate :)

---

### Post by Guntherk9 on 2008-01-01
Happy New year everyone,

Over the course of the holidays, I've developed this script to get some of my issues solved.  I'm not great at script writing as you can tell from the code below. Try not too laugh to much :)

Maybe a real programmer could take a look at my code and tweak it.  It's a work in progress.  At this point the script is functional for my needs, but any help or idea's would be appreciated. I also have a  cron job to execute 'updatedb' every couple of hours.

With Many Thanks

Gunther :)

----------------------------------------------------
#! /bin/sh
clear
echo
echo "  RAID ARRAY Search & Directory Listing"
echo "  -------------------------------------"
A=x
until [ "$selection" = "$A" ]; do
echo
echo "Choose one of the following options:"
echo
echo "1 - Search for a Directory Name"
echo "2 - Find Duplicate Directory Names"
echo "3 - List All Directories"
echo "x - Exit"
echo
read selection

searchsum() {
        find /media/* -iname "$dir_name" | sort |  sort -n;
}

searchresult(){
        ls /media/* | egrep -v '~d' > results.txt;
        SUCCESS=0
        word=$dir_name
        filename=results.txt
        grep -q "$word" "$filename"
        if [ $? -eq $SUCCESS ]
        then
        echo "The Directory named, $word is found:"
        else
        echo "The Dicectory named, $word is NOT found:"
        fi
        rm results.txt;
}

duplicate() {
        ls /media/* | egrep -v '~d' > duplicate.txt;
        cat duplicate.txt | sort | uniq -c | sort -nr > 

dupoutput.txt;
        cat dupoutput.txt;
        rm duplicate.txt;
}

saveoutput() {
        if [ "$output" = "y" ]
        then
        mv dupoutput.txt /tmp/dupoutput.txt
        echo "Output File Saved  to /tmp/dupoutput.txt"
        else
        rm dupoutput.txt
        fi
}

dirlist() {
        find /media/* -maxdepth 1 -mindepth 1 -type d | sort |  sort 

n > RAID_Directory.txt;
        #ls /media/* | egrep -v '~d' > RAID_Directory.txt;
        cat RAID_Directory.txt;
}

saveresults() {
        if [ "$saveresults" = "y" ]
        then
        mv RAID_Directory.txt /tmp/RAID_Directory.txt
        echo "Output File Saved  to /tmp/RAID_Directory.txt"
        else
        rm RAID_Directory.txt
        echo "Output File deleted"
        fi
}

case "$selection" in

  "1" )
  echo
  echo -e "Please enter the Directory Name:"
  read dir_name
  echo
  searchresult
  echo
  echo "Search Summary:"
  echo "---------------"
  searchsum
  echo
  ;;

  "2" )
  echo
  echo "Duplicate Directories:"
  echo "----------------------"
  duplicate
  echo
  echo "Save Output File to Disk?  y / n "
  read output
  saveoutput
  echo
  ;;

  "3" )
  echo
  echo "RAID ARRAY Directories:"
  echo "-----------------------"
  dirlist
  echo
  echo "Save Output File to Disk?  y / n "
  read saveresults
  saveresults
  echo
  ;;

  "x" )
  echo
  echo -e "Exit"
  echo
  exit 0
  ;;
esac
done

---

### Post by RC Howe on 2008-01-01
I assume that you do not need to build a database that acts as an index of all of your files. If so, there are many utilities in the repositories such as DiskSearch and Beagle that will automatically build an index for you. I would reccomend DiskSearch from reading the Synaptic description, because it seems to be smart about multiple disks.

---

