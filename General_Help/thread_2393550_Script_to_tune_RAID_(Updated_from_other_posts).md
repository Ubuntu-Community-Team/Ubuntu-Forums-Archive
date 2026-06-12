---
title: "Script to tune RAID (Updated from other posts)"
date: 2018-06-05
forum: General Help
---

### Post by Chino9656 on 2018-06-05
I found these threads super helpful during my first MDADM deploy.

The base script I used was from @alfonso78
[https://ubuntuforums.org/showthread.php?t=1916607](https://ubuntuforums.org/showthread.php?t=1916607)

Also worth crediting is this post from @apeganz
[https://ubuntuforums.org/showthread.php?t=1494846](https://ubuntuforums.org/showthread.php?t=1494846)

I was running into an issue where my read results were being returned in GB/s instead of MB/s.
I added a small check for that occurrence. I couldn't reply to the original threads, and I figured this script was worth preserving.
I found how to do this from this SO answer: [https://stackoverflow.com/a/35634409](https://stackoverflow.com/a/35634409)

Some important info from the original post:
> **alfonso78 said:**
> I've been learning a lot in these past weeks on tuning RAID so I decided to write a script that should find from actual tests which are the best settings for your system.Please run it without any other kind of load on the CPU and disks to have a realistic measure.

It's far from perfect. For sure it won't harm your system (any change done is lost after reboot if you don't edit manually /etc/rc.local). So feel free to test it and let me know if it brings any increase in performances!

It must run as root and it takes a few hours to finish (a suggest running it overnight).

For the sake of explanation, the script is for sure sub-optimal since it tests only 9 * 4 settings instead of 9 * 9 * 9 * 9 but the script would probably need days to find "the optimal settings" plus I notice there is a certain fluctuation in results anyway, so I think this is a good enough approximation.


```
#!/bin/bash#
# Please note this test requires 30 GB of free space
# in your RAID md device
#
# The aim of this script is to find the best settings for performance 
# of your RAID by testing each setting separately.
# This script does make some system modification, but if you don't
# make these changes permanent (e.g. write them in /etc/rc.local)
# At the next boot all the changes will be lost, 
# so fill free to play with it!
#
# developed by alfonso / Jan 2012
# updated by chino9656 / June 2018
#
# this is your mount point for the RAID
# PLEASE NOTE the script will REMOVE any file called testfile*.out in this folder!!
MNT=/storage
# this is device from which to get input
# no need to change this
INPUT=/dev/zero


# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  echo Need to be root!
  echo ABORT
  exit 1
fi


if ! [ -d $MNT/lost+found ]
then
  echo
  echo "$MNT is not a file system! Something went wrong?"
  echo ABORT
  exit 1
fi


# find out which one is your md
# note that the script only works for one md. If you have more than one 
# just uncomment the line below and type something like MDDEV=md0
MDDEV="`cat /proc/mdstat | grep md | head -1 | awk '{print $1}'`"
# MDDEV=md0


if [ -z "$MDDEV" ]
then
  echo
  echo "I can\'t find any md"
  echo ABORT
  exit 1
fi


#
# get the letter of all devices from cat /proc/mdstat
#
# this expression takes the output of /proc/mdstat
# then takes the line of our md
# then changes spaces into new lines
# then takes only lines starting with sd
# then take the 3rd character (a for sda1, etc)
# and then remove new lines to make a single string
DEVS="`cat /proc/mdstat | grep $MDDEV | tr " " "\n" | grep '^sd' | awk '{print substr($0,3,1)}' | tr -d "\n"`"
echo "These are devices found in $MDDEV: $DEVS"


function test_write()
{
# writing tests:


  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  WRTE1=`dd if=$INPUT of=$MNT/testfile1.out bs=100kB count=100000 2>&1 | grep copied`
  WRUN1=`echo $WRTE1 | awk ' { print ( $(NF) ) }'`
  WRSP1=`echo $WRTE1 | awk ' { print ( $(NF-1) ) }'`
  if [ $WRUN1 == "GB/s" ];
  then
    #echo "Result returned in GB/s; Converting to MB/s"
    WRSP1=$(echo "$WRSP1 * 1024" | bc)
  elif [ $WRUN1 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  WRTE2=`dd if=$INPUT of=$MNT/testfile2.out bs=1MB count=10000 2>&1 | grep copied`
  WRUN2=`echo $WRTE2 | awk ' { print ( $(NF) ) }'`
  WRSP2=`echo $WRTE2 | awk ' { print ( $(NF-1) ) }'`
  if [ $WRUN2 == "GB/s" ];
  then
    #echo "Result returned in GB/s; Converting to MB/s"
    WRSP2=$(echo "$WRSP2 * 1024" | bc)
  elif [ $WRUN2 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  WRTE3=`dd if=$INPUT of=$MNT/testfile3.out bs=10MB count=1000 2>&1 | grep copied`
  WRUN3=`echo $WRTE3 | awk ' { print ( $(NF) ) }'`
  WRSP3=`echo $WRTE3 | awk ' { print ( $(NF-1) ) }'`
  if [ $WRUN3 == "GB/s" ];
  then
    #echo "Result returned in GB/s; Converting to MB/s"
    WRSP3=$(echo "$WRSP3 * 1024" | bc)
  elif [ $WRUN3 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  AVG_WRITE=`echo "($WRSP1+$WRSP2+$WRSP3)*100/3" | bc`
    
  #echo " Average write is $AVG_WRITE MB/s NOTE: there should be a dot before the last 2 digits"
  echo " average write is `echo "scale=2; $AVG_WRITE / 100;" | bc` MB/s"
  
#  echo $WRTE1
#  echo $WRTE2
#  echo $WRTE3
}


function test_read()
{


# reading tests:


  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  READ1=`dd if=$MNT/testfile1.out of=/dev/null bs=100kB count=100000 2>&1 | grep copied`
  RDUN1=`echo $READ1 | awk ' { print ( $(NF) ) }'`
  RDSP1=`echo $READ1 | awk ' { print ( $(NF-1) ) }'`
  if [ $RDUN1 == "GB/s" ];
  then
    #echo "Result returned in GB/s; Converting to MB/s"
    RDSP1=$(echo "$RDSP1 * 1024" | bc)
  elif [ $RDUN1 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  READ2=`dd if=$MNT/testfile2.out of=/dev/null bs=1MB count=10000 2>&1 | grep copied`
  RDUN2=`echo $READ2 | awk ' { print ( $(NF) ) }'`
  RDSP2=`echo $READ2 | awk ' { print ( $(NF-1) ) }'`
  if [ $RDUN2 == "GB/s" ];
  then
    #echo "Result returned in GB/s; Converting to MB/s"
    RDSP2=$(echo "$RDSP2 * 1024" | bc)
  elif [ $RDUN2 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  READ3=`dd if=$MNT/testfile3.out of=/dev/null bs=10MB count=1000 2>&1 | grep copied`
  RDUN3=`echo $READ3 | awk ' { print ( $(NF) ) }'`
  RDSP3=`echo $READ3 | awk ' { print ( $(NF-1) ) }'`
  if [ $RDUN3 == "GB/s" ];
  then
    #echo "Result returned in GB/s; Converting to MB/s"
    RDSP3=$(echo "$RDSP3 * 1024" | bc)
  elif [ $RDUN3 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  AVG_READ=`echo "($RDSP1+$RDSP2+$RDSP3)*100/3" | bc`
  
  #echo " Average read is $AVG_READ MB/s NOTE: there should be a dot before the last 2 digits"
  echo " average read is `echo "scale=2; $AVG_READ / 100;" | bc` MB/s"
  
  #echo $READ1
  #echo $READ2
  #echo $READ3
}


echo 
echo CURRENT SYSTEM SETTINGS
echo your current value of /sys/block/$MDDEV/md/stripe_cache_size is `cat /sys/block/$MDDEV/md/stripe_cache_size`
echo your current value of disk readahead is `blockdev --getra /dev/sd[$DEVS]`
echo your current value of md readahead is `blockdev --getra /dev/$MDDEV`
DEVINDEX=0
NUMDEVS=${#DEVS}
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  echo your current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`
  DEVINDEX=$[$DEVINDEX+1]
done
echo


for i in 1 2 3 4
#for i in 1 
# 1 when testing /sys/block/$MDDEV/md/stripe_cache_size
# 2 when testing disk readahead
# 3 when testing md readahead
# 4 when testing /sys/block/sdX/queue/max_sectors_kb
do
  BEST_WRITE=0
  BEST_WRITE_ID=0
  WORST_WRITE=0
  WORST_WRITE_ID=0
  BEST_READ=0
  BEST_READ_ID=0
  WORST_READ=0
  WORST_READ_ID=0
  for j in 64 128 256 512 1024 2048 4096 8192 16384 32768
#  for j in 64 16384
  do
    #echo 
    #echo SYSTEM SETTINGS
    #echo your current value of /sys/block/$MDDEV/md/stripe_cache_size is `cat /sys/block/$MDDEV/md/stripe_cache_size`
    #echo your current value of disk readahead is `blockdev --getra /dev/sd[$DEVS]`
    #echo your current value of md readahead is `blockdev --getra /dev/$MDDEV`
    #DEVINDEX=0
    #NUMDEVS=${#DEVS}
    #until [ $DEVINDEX -ge $NUMDEVS ]
    #do
    #  DEVLETTER=${DEVS:$DEVINDEX:1}
    #  echo your current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`
    #  DEVINDEX=$[$DEVINDEX+1]
    #done
    #echo
    case "$i" in
    1)  echo "We are testing md stripe_cache_size"
        echo $j > /sys/block/$MDDEV/md/stripe_cache_size
        echo "step 1/4: NOW your current value of /sys/block/$MDDEV/md/stripe_cache_size is `cat /sys/block/$MDDEV/md/stripe_cache_size`"
        ;;
    2)  echo "We are testing disks readahead"
        blockdev --setra $j /dev/sd[$DEVS]
        echo "step 2/4: NOW your current value of disk readahead is `blockdev --getra /dev/sd[$DEVS]`"
        ;;
    3)  echo "We are testing md readahead"
        blockdev --setra $j /dev/$MDDEV
        echo "step 3/4 NOW your current value of md readahead is `blockdev --getra /dev/$MDDEV`"
        ;;
    4)  echo "We are testing disks max_sectors_kb"
        DEVINDEX=0
        NUMDEVS=${#DEVS}
        until [ $DEVINDEX -ge $NUMDEVS ]
        do
          DEVLETTER=${DEVS:$DEVINDEX:1}
          echo $j > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
          echo "step 4/4 NOW your current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`"
          DEVINDEX=$[$DEVINDEX+1]
        done
        ;;
    *)  echo "This text should never appear"
        echo ABORT
        exit 1
        ;;
    esac
    rm $MNT/testfile*.out 2> /dev/null
    test_write
    if [ "$BEST_WRITE" -eq "0" ]
    then
      #echo 1st test BEST_WRITE
      BEST_WRITE=$AVG_WRITE
      BEST_WRITE_ID=$j
    fi
    if [ "$WORST_WRITE" -eq "0" ]
    then
      #echo 1st test WORST_WRITE
      WORST_WRITE=$AVG_WRITE
      WORST_WRITE_ID=$j
    fi
    if [ "$AVG_WRITE" -ge "$BEST_WRITE" ]
    then
      echo "found new best write - old: `echo "scale=2; $BEST_WRITE / 100;" | bc` new: `echo "scale=2; $AVG_WRITE / 100;" | bc`"
      #echo "old: $BEST_WRITE new: $AVG_WRITE"
      BEST_WRITE=$AVG_WRITE
      BEST_WRITE_ID=$j
    fi
    if [ "$AVG_WRITE" -le "$WORST_WRITE" ]
    then
      echo "found new worst write - old: `echo "scale=2; $WORST_WRITE / 100;" | bc` new: `echo "scale=2; $AVG_WRITE / 100;" | bc`"
      #echo old: $WORST_WRITE new: $AVG_WRITE
      WORST_WRITE=$AVG_WRITE
      WORST_WRITE_ID=$j
    fi
    test_read
    if [ "$BEST_READ" -eq "0" ]
    then
      #echo 1st test BEST_READ
      BEST_READ=$AVG_READ
      BEST_READ_ID=$j
    fi
    if [ "$WORST_READ" -eq "0" ]
    then
      #echo 1st test WORST_READ
      WORST_READ=$AVG_READ
      WORST_READ_ID=$j
    fi
    if [ "$AVG_READ" -ge "$BEST_READ" ]
    then
      echo "found new best read - old: `echo "scale=2; $BEST_READ / 100;" | bc` new: `echo "scale=2; $AVG_READ / 100;" | bc`"
      #echo old: $BEST_READ new: $AVG_READ
      BEST_READ=$AVG_READ
      BEST_READ_ID=$j
    fi
    if [ "$AVG_READ" -le "$WORST_READ" ]
    then
      echo "found new worst read - old: `echo "scale=2; $WORST_READ / 100;" | bc` new: `echo "scale=2; $AVG_READ / 100;" | bc`"
      #echo old: $WORST_READ new: $AVG_READ
      WORST_READ=$AVG_READ
      WORST_READ_ID=$j
    fi
    rm $MNT/testfile1.out
    rm $MNT/testfile2.out
    rm $MNT/testfile3.out


  done
  echo BEST_WRITE is $BEST_WRITE
  echo BEST_WRITE_ID is $BEST_WRITE_ID
  echo WORST_WRITE is $WORST_WRITE
  echo WORST_WRITE_ID is $WORST_WRITE_ID
  echo BEST_READ is $BEST_READ
  echo BEST_READ_ID is $BEST_READ_ID
  echo WORST_READ is $WORST_READ
  echo WORST_READ_ID is $WORST_READ_ID
  # now we want to understand if this test affected more READ or WRITE performances
  DIFF_WRITE=$[ BEST_WRITE - WORST_WRITE ]
  DIFF_READ=$[ BEST_READ - WORST_READ ]
  if [ "$DIFF_READ" -gt "$DIFF_WRITE" ]
  then
    echo this test affected more READ than WRITE
    BEST_OVERALL_ID=$BEST_READ_ID
    WORST_OVERALL_ID=$WORST_READ_ID
  else
    echo this test affected more WRITE than READ
    BEST_OVERALL_ID=$BEST_WRITE_ID
    WORST_OVERALL_ID=$WORST_WRITE_ID
  fi
  case "$i" in
  1)  echo "$BEST_OVERALL_ID is the OPTIMAL value for md stripe_cache_size"
      BEST_1_ID=$BEST_OVERALL_ID
      echo $BEST_OVERALL_ID > /sys/block/$MDDEV/md/stripe_cache_size
      ;;
  2)  echo "$BEST_OVERALL_ID is the OPTIMAL value for disks readahead"
      BEST_2_ID=$BEST_OVERALL_ID
      blockdev --setra $BEST_OVERALL_ID /dev/sd[$DEVS]
      ;;
  3)  echo "$BEST_OVERALL_ID is the OPTIMAL value for md readahead"
      BEST_3_ID=$BEST_OVERALL_ID
      blockdev --setra $BEST_OVERALL_ID /dev/$MDDEV
      ;;
  4)  echo "$BEST_OVERALL_ID is the OPTIMAL value for max_sectors_kb"
      BEST_4_ID=$BEST_OVERALL_ID
      DEVINDEX=0
      NUMDEVS=${#DEVS}
      until [ $DEVINDEX -ge $NUMDEVS ]
      do
        DEVLETTER=${DEVS:$DEVINDEX:1}
        echo $BEST_OVERALL_ID > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
        DEVINDEX=$[$DEVINDEX+1]
      done
      ;;
  *)  echo "This text should never appear"
      echo ABORT
      exit 1
      ;;
  esac
done


echo the best for md stripe_cache_size is $BEST_1_ID
echo the best for disks readahead is $BEST_2_ID
echo the best for md readahead is $BEST_3_ID
echo the best for max_sectors_kb is $BEST_4_ID
echo
echo "Add the following lines to your /etc/rc.local"
echo 
echo "echo $BEST_1_ID > /sys/block/$MDDEV/md/stripe_cache_size"
echo "blockdev --setra $BEST_2_ID /dev/sd[$DEVS]"
echo "blockdev --setra $BEST_3_ID /dev/$MDDEV"
DEVINDEX=0
NUMDEVS=${#DEVS}
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  echo "echo $BEST_4_ID > /sys/block/sd$DEVLETTER/queue/max_sectors_kb"
  DEVINDEX=$[$DEVINDEX+1]
done


exit 0
```

---

