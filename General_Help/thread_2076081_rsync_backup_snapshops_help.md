---
title: "rsync backup snapshops help"
date: 2012-10-25
forum: General Help
---

### Post by jdratcliffe1987 on 2012-10-25
at the moment i have a lubuntu machine running rsync to grab and copy the users workstations desktops and documents 6 times a working day i was wondering would they be a way to merge these once a into one combined snapshot ie mon 8 10 12 2 4 6 would then on tue @ 2am merge into a mon backup? below is a exaple of one of my backup scripts.

START=`date +%d-%b-%Y_%H-%M`
PROFILE="Full House workstations"
echo Backup of $PROFILE began: $START
echo " "


###### PEPMAC001 ######
echo PEPMAC001
rsync -avh BH08@10.195.128.57:/Users/BH08 /media/fullhouse/current/fullhouse/PEPMAC001 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

###### PEPMAC002 ######
echo PEPMAC002
rsync -avh editorial@10.195.128.51:/Users/editorial /media/fullhouse/current/fullhouse/PEPMAC002 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

###### PEPMAC003 ######
echo PEPMAC003
rsync -avh editorial@10.195.128.61:/Users/editorial /media/fullhouse/current/fullhouse/PEPMAC003 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5


###### PEPMAC004 ######
echo PEPMAC004
rsync -avh burda15@10.195.128.59:/Users/burda15 /media/fullhouse/current/fullhouse/PEPMAC004 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

###### PEPMAC005 ######
echo PEPMAC005
rsync -avh fullhouse@10.195.128.54:/Users/fullhouse /media/fullhouse/current/fullhouse/PEPMAC005 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

###### PEPMAC006 ######
echo PEPMAC006
rsync -avh editorial@10.195.128.58:/Users/editorial /media/fullhouse/current/fullhouse/PEPMAC006 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

###### PEPMAC007 ######
echo PEPMAC007
rsync -avh fullhouse14@10.195.128.62:/Users/fullhouse14 /media/fullhouse/current/fullhouse/PEPMAC007 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

##### PEPMAC008 ######
echo PEPMAC008
rsync -avh burda12@10.195.128.60:/Users/burda12 /media/fullhouse/current/fullhouse/PEPMAC008 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

##### PEPMAC009 ######
echo PEPMAC009
rsync -avh editorial@10.195.128.63:/Users/editorial /media/fullhouse/current/fullhouse/PEPMAC009 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5

###### PEPMAC010 ######
echo PEPMAC010
rsync -avh burda11@10.195.128.56:/Users/editorial /media/fullhouse/current/fullhouse/PEPMAC010 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5


###### PEPMAC011 ######
echo PEPMAC011
rsync -avh editorial@10.195.128.64:/Users/editorial /media/fullhouse/current/fullhouse/PEPMAC011 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5


###### PEPMAC012 ######
echo PEPMAC012
rsync -avh editorial@10.195.128.50:/Users/editorial /media/fullhouse/current/fullhouse/PEPMAC012 --delete-after --exclude-from '/home/swabs/scripts/exclusions/fullhouse.txt' --timeout=10 --ignore-errors
echo " "
sleep 5


END=`date +%d-%b-%Y_%H-%M`
echo " "
echo Backup of $PROFILE completed: $END!

# Now create a snapshot of the backup
cp -al /media/fullhouse/current/fullhouse /media/fullhouse/snapshots/fullhouse-$END
echo  " "
echo Snapshot of fullhouse completed
JOB="fullhouse"
PROFILE="Full House workstations backup"
FROM=backups@peppublishing.co.uk
TO=james@peppublishing.co.uk
SUBJECT="Backup report for $JOB"
AUTH=auth.smtp.1and1.co.uk
AUTHUSER=backups@peppublishing.co.uk
PASSWD=*******
BODY="Backup report $DATE for $JOB attached"
LOG=/home/swabs/backuplogs/workstations/fhwks.log
sendEmail -f $FROM -t $TO -u $SUBJECT -m $BODY -a $LOG -s $AUTH -xu $FROM -xp $PASSWD
sleep 5
rm -f /home/swabs/backuplogs/workstations/fhwks.log
sleep 5
# End of script

---

### Post by shreepads on 2012-10-25
Wouldn't this be possible using hour specific folders as follows:

/media/fullhouse/<hournumber>/fullhouse

Then tweak each rsync command to put the correct <hournumber> in the destination path

And get rid of the cp -al command at the end..

Maybe I haven't understood what you need!

---

