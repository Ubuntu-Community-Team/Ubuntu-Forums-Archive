---
title: "bash script works perfect in Gentoo, but not in Ubuntu"
date: 2014-12-10
forum: General Help
---

### Post by ronnie5 on 2014-12-10
So here is the deal, I am an avid supporter of Gentoo, but one of my customers is running ubuntu lts 14.04. He needed a script that made backing up his data to an external HDD, and to a private offsite server, that would automate everything, from mounting the drive, to backing up the data, unmounting the drive, then also turning on the remote server and doing the process all over again. so now I have a script that works perfect in Gentoo, which is nice, but when ever I run it in ubuntu i get a ton of errors. I also wrote a gui for it using gtkdialog. Is there a reason that simple bash scripting would be different in ubuntu? attached is the script, so you can take a look at it, as it has me stumped. 


Here is the main script
```

##################################################################################
###########################Backup.sh V1.5#########################################
##################################################################################
########################Written by: Ronald Brown##################################
##################################################################################
#######################Released Under GPLv2 licence###############################
##################################################################################
##########################Software Requirements:##################################
###########################1. SSH(Don't worry, you should have it)################
############################2. wol(Wake On Lan)###################################
#############################3. RSYNC(File transfer app of choice)################
##############################4. NOTIFY_SEND(App for messages)####################
###############################5.sync (app for sync for HDD)######################
################################6.gtkdialog#######################################
##################################################################################
#                                                                                #
##################################################################################
#             Things To Fix/ADD                     #
#      1. Check for better way to verify network connections, due to router ping #
#      2. Verify this works for the clients needs.                 #
#      3. Find a way to choose a specific days backup to download, so you dont   #
#             have to download all backups every time.                           #
#      4. Make it less idiot proof, but keep simple functionallity               #
#      5. Finish coding remote backup, so local and remote backups match         #
#             as far as file paths go.                          #
#      6. Add Reminder function, so the script will remind you to save data      #
#          before script starts, and to remind you that backup is coming      #
#          1 to 2 days in advanced                                            #
##################################################################################
#                                         #
##################################################################################
#                        CHANGELOG V1.5                                          #
#     1. Added Diff comparason for drive location                         #
#     2. Changed where settings, and temporary files used by script are used     #
#     3. Added install function, to create settings folder, and copy default     #
#            settings to folder, and to create tmp dir.                          #
##################################################################################
#                                         #
##################################################################################
#                        CHANGELOG V1.4                                          #
#     1. Remove All Script, and keep just functions, and settings                #                                         #
#     2. Designed GUI with gtkdialog, for backup.                  #
##################################################################################
#                                         #
##################################################################################
#                        CHANGELOG V1.3                                          #
#     1. Added Functions for mounting/unmounting Local backup drive with         #
#          tests to make sure it was mounted/unmounted.                       #
#     2. Added Terminal Messages, so if you miss the pop up, there is another    #
#             Message.                                  #
#     3. Modified Variable placement, so local and remote backup paths match     #
#     4. added option to only download most current backup from offsite server   #
#             vs to download the whole tree. You can still download the whole    #
#          backup tree.                             #
#     5. Added GTKDialog, so script will pause so backup can be checked          #
#     6. added options for local backup retrieval.                               #
#     7. Log File is displayed in terminal in realtime, as script is running     #
##################################################################################
#                                         #
##################################################################################
#                        CHANGELOG V1.2                                          #
#     1. Set up auto mounting/unmounting of external drive                       #
#     2. Integrated chrisjbackup script for loacl backup                         #
##################################################################################
#                                         #
##################################################################################
#                        CHANGELOG V1.1                                          #
#     1. Added Functions, cleaned up code                                        #
##################################################################################
#                                         #
##################################################################################
#                        CHANGELOG V1.0                                          #
#     1. Initial script. Not much funtionallity, and really messy                #
#            repetitive code.                                                    #
##################################################################################


#!/bin/bash

if [ "$1" == "--gui" ]; then
    GUI=1
    SOPTS=$2
else
    SOPTS=$1
fi

if [ "$SOPTS" == "--no-offsite-backup" -o "$SOPTS" == "-N" ]; then
                REMOTE_BACKUP="false"
        else
                REMOTE_BACKUP="true"
fi

HOSTNAME=`hostname`
NOW=`date +"%Y-%m-%d.%H-%M-%S"`
TMP_LOCATION="./.tmp"
source ./settings.cfg

########################DONT CHANGE AFTER THIS LINE###############################

if [ "$TEST" == "true" ]; then
    DEVPATH=/dev/sdc3
    PREFIX=/mnt/usb
    OFFSITE_PREFIX=/home
    FOLDER_TO_BACKUP="/home/ronnie/John_computer_work/"
    RSYNCUPOPTS="--archive --compress --one-file-system --hard-links --human-readable --inplace --numeric-ids --delete --quiet"
    RSYNC_SERVER=localhost 
    RSYNC_PATH=ronnie-backup
    SSH_USER=root
    CURRDIR=/backup/rsync/$HOSTNAME/_home_$USRNAME.current 
    NEWCURRDIR=/backup/rsync/$HOSTNAME/_home_$USRNAME.$NOW
    INCOMPDIR=/backup/rsync/$HOSTNAME/_home_$USRNAME.incomplete/
else
    RSYNCUPOPTS="$RSYNCUPOPTS --exclude-from=$EXCLUDES"
 
fi

LCURRDIR=$PREFIX$CURRDIR 
LNEWCURRDIR=$PREFIX$NEWCURRDIR 
LINCOMPDIR=$PREFIX$INCOMPDIR
LALLDOWNLOAD="$PREFIX/backup/rsync/$HOSTNAME/"

OCURRDIR=$OFFSITE_PREFIX$CURRDIR 
ONEWCURRDIR=$OFFSITE_PREFIX$NEWCURRDIR 
OINCOMPDIR=$OFFSITE_PREFIX$INCOMPDIR

########################FUNCTIONS#################################################
function INSTALL {
    echo "Not Finished"
    exit
}

function MOUNT {
        if [ "$TEST" == "true" ]; then
            NOTIFY_SEND "Backup" "About to attempt Mounting of $PREFIX in test mode, will not wait."
        else        
            NOTIFY_SEND "Backup" "About to attempt Mounting of $PREFIX, Please turn on external drive at $DEVPATH.\n\n\nPlease wait $LOCAL_WAIT_TIME sec for drive to initialize."        
            sleep $LOCAL_WAIT_TIME
        fi        
        echo "Mounting Backup Drive at $PREFIX" >> "$LOGPATH/log-$NOW.log"
        NOTIFY_SEND "Backup" "Mounting Backup Drive at $PREFIX"
        if grep -qs "$DEVPATH $PREFIX" /proc/mounts; then
            echo "Backup Drive already Mounted" >> "$LOGPATH/log-$NOW.log"
            NOTIFY_SEND "Backup" "$DEVPATH is already mounted at $PREFIX"
        else
            if grep -qs "$PREFIX" /proc/mounts; then
                  echo "It's mounted. unmounting $PREFIX" >> "$LOGPATH/log-$NOW.log"
                NOTIFY_SEND "Backup" "A partition is mounted at $PREFIX.\n\nUnmounting it to mount backup drive"
                echo "$PREFIX already mounted, forcing unmount, to mount external hdd" >> "$LOGPATH/log-$NOW.log" >> "$LOGPATH/log-$NOW.log"
                UMOUNT
                MOUNT
            else
                  echo "Nothing is mounted to $PREFIX" >> "$LOGPATH/log-$NOW.log"
                if [ "$DIFFCOMPARE" == "true" ]; then
                    ls /dev | grep sd >> $TMP_LOCATION/ls1.txt
                    [ -z $GTKDIALOG ] && GTKDIALOG=gtkdialog
    
                        MAIN_DIALOG='
                            <window>
                                <vbox>
                                    <vbox border-width="30">
                                        <text>
                                        <label>Please Plug in External Backup Drive</label>
                                            </text>
                                    </vbox>
                                    <hbox>    
                                    <button ok></button>
                                    </hbox>
                                </vbox>
                            </window>'
            
                        export MAIN_DIALOG
                        $GTKDIALOG --program=MAIN_DIALOG >> /dev/null
                    NOTIFY_SEND "Backup" "Sleeping for 10 sec while waiting for drive to init"                    
                    sleep 10                  
                    ls /dev | grep sd >> $TMP_LOCATION/ls2.txt
                    if [ "$TEST" == "true" ]; then
                        DEVPATH="/dev/"`diff $TMP_LOCATION/ls1.txt $TMP_LOCATION/ls2.txt | grep 3 |awk  -F " " '/>/ {print $2}'`                    
                    else
                        DEVPATH="/dev/"`diff $TMP_LOCATION/ls1.txt $TMP_LOCATION/ls2.txt | grep 1 | awk  -F " " '/>/ {print $2}'`
                    fi
                fi                        
                mount $DEVPATH $PREFIX >> /dev/null
                  if [ $? -eq 0 ]; then
                       echo "Mount success!" >> "$LOGPATH/log-$NOW.log"
                    NOTIFY_SEND "Backup" "External Drive mounted successfully"
                  else
                       echo "Something went wrong with the mount command...Please check that HDD is connected, and turned on...Exiting" >> "$LOGPATH/log-$NOW.log"
                    NOTIFY_SEND "Backup" "Mount Failed\n\nPlease check that HDD is connected, and turned on and try again\n\nExiting, backup failed"
                    exit
                  fi
            fi
        fi
}

function UMOUNT {
        echo "Unmounting Drive at $PREFIX" >> "$LOGPATH/log-$NOW.log"
        NOTIFY_SEND "Backup" "Unmounting Backup Drive $PREFIX"
        umount $PREFIX >> /dev/null
        if grep -qs "$PREFIX" /proc/mounts; then
              echo "It's still mounted.forcing unmounting of $PREFIX" >> "$LOGPATH/log-$NOW.log"
            NOTIFY_SEND "Backup" "Unmount failed\n\nForcing unmount"
            umount -l $PREFIX
            fi
        if [ "$DIFFCOMPARE" == "true" ]; then
            rm $TMP_LOCATION/ls1.txt
            rm $TMP_LOCATION/ls2.txt
        fi
        echo "Unmount Complete" >> "$LOGPATH/log-$NOW.log"
}

function LOCAL_BACKUP {
            
        MOUNT            
        PROGRESSBAR 10        
        LINKDEST=`readlink -f $LCURRDIR`
        LINKDEST=${LINKDEST%/} #remove traling "/"
        mkdir -p $LINCOMPDIR >> /dev/null
        sync >> /dev/null
        PROGRESSBAR 20        
        echo "Still Running...... Please wait" >> "$LOGPATH/log-$NOW.log"
        rsync $RSYNCUPOPTS --link-dest=$LINKDEST $FOLDER_TO_BACKUP $LINCOMPDIR >> /dev/null
        PROGRESSBAR 75        
        sync >> /dev/null
        echo "Still Running...... But getting closer" >> "$LOGPATH/log-$NOW.log"
        PROGRESSBAR 90        
        echo "Moving $LINCOMPDIR to $LNEWCURRDIR" >> "$LOGPATH/log-$NOW.log"        
        mv $LINCOMPDIR $LNEWCURRDIR >> /dev/null
        echo "Starting Final Sync Command....... Almost Done" >> "$LOGPATH/log-$NOW.log"        
        sync >> /dev/null
        echo "Creating symbolic link(shortcut) for latest backup This keeps backup size way down" >> "$LOGPATH/log-$NOW.log"
        ln -sfn $LNEWCURRDIR $LCURRDIR >> /dev/null
        if [ "$GUI" != "1" ]; then
            [ -z $GTKDIALOG ] && GTKDIALOG=gtkdialog
    
            MAIN_DIALOG='
                    <window>
                        <vbox>
                            <vbox border-width="30">
                                <text>
                                    <label>The Local Backup Has completed. Please Hit OK to Unmount Drive, and continue with the script</label>
                                    </text>
                            </vbox>
                            <hbox>    
                                <button ok></button>
                            </hbox>
                        </vbox>
                    </window>'
        
            export MAIN_DIALOG
            $GTKDIALOG --program=MAIN_DIALOG >> /dev/null
        fi
        UMOUNT
        PROGRESSBAR 100        
        echo "Local Backup complete" >> "$LOGPATH/log-$NOW.log"                
        NOTIFY_SEND "Backup" "Local Backup Complete"
        echo "Local Backup Complete" >> "$LOGPATH/log-$NOW.log"
}

function RETRIEVE_LOCAL_BACKUP {
                MOUNT
        PROGRESSBAR 10
        NOTIFY_SEND "Backup" "Downloading Data"
                if [ "$SOPTS" == "--retrieve-all-local-backup" -o "$SOPTS" == "-RL" ]; then
            echo 'RETRIEVE BACKUP ALL LOCAL Started' >> "$LOGPATH/log-$NOW.log"        
            PROGRESSBAR 25
            rsync $RSYNCDOWNOPTS $LALLDOWNLOAD $DOWNLOAD_PATH >> /dev/null
            PROGRESSBAR 75            
            echo 'RETRIEVE BACKUP ALL LOCAL Finished' >> "$LOGPATH/log-$NOW.log"                
            NOTIFY_SEND "Backup" "ALL Data Downloaded From Local Backup to:$DOWNLOAD_PATH"        
        else
            if [ "$SOPTS" == "--retrieve-current-local-backup" -o "$SOPTS" == "-RZ" ]; then
                echo 'RETRIEVE BACKUP CURRENT LOCAL Started' >> "$LOGPATH/log-$NOW.log"
                PROGRESSBAR 25                
                rsync $RSYNCDOWNOPTS $LCURRDIR $DOWNLOAD_PATH >> /dev/null
                PROGRESSBAR 75                
                echo 'RETRIEVE BACKUP CURRENT LOCAL Finished' >> "$LOGPATH/log-$NOW.log"
                NOTIFY_SEND "Backup" "Most Current Backup Data Downloaded to:$DOWNLOAD_PATH"
            fi
        fi        
        UMOUNT                
        PROGRESSBAR 100        
        
}

function OFFSITE_BACKUP {
        NOTIFY_SEND "Backup" "Starting RSYNC/Offsite Backup."
                REMOTE_BOOT
        PROGRESSBAR 10
                PING
        PROGRESSBAR 20                
        NOTIFY_SEND "Backup" "Starting RSYNC Backup"
                echo 'OFFSITE BACKUP STARTED' >> "$LOGPATH/log-$NOW.log"
                LINKDEST=`ssh -l $SSH_USER $RSYNC_SERVER readlink -f $CURRDIR`
        LINKDEST=${LINKDEST%/} #remove traling "/"
        ssh -l $SSH_USER $RSYNC_SERVER mkdir -p $OINCOMPDIR >> /dev/null
        ssh -l $SSH_USER $RSYNC_SERVER sync >> /dev/null
        echo "Still Running......This may take a while... Please wait" >> "$LOGPATH/log-$NOW.log"
        PROGRESSBAR 30        
        rsync $RSYNCUPOPTS  --link-dest=$LINKDEST $FOLDER_TO_BACKUP $RSYNC_SERVER:$OINCOMPDIR >> /dev/null
        PROGRESSBAR 75        
        ssh -l $SSH_USER $RSYNC_SERVER sync >> /dev/null
        echo "Still Running...... But getting closer" >> "$LOGPATH/log-$NOW.log"
        echo "Moving $OINCOMPDIR to $ONEWCURRDIR"    >> "$LOGPATH/log-$NOW.log"    
        ssh -l $SSH_USER $RSYNC_SERVER mv $OINCOMPDIR $ONEWCURRDIR >> /dev/null
        echo "Starting Final Sync Command....... Almost Done" >> "$LOGPATH/log-$NOW.log"        
        ssh -l $SSH_USER $RSYNC_SERVER sync >> /dev/null
        PROGRESSBAR 25
        echo "Creating symbolic link(shortcut) for latest backup This keeps backup size way down" >> "$LOGPATH/log-$NOW.log"
        ssh -l $SSH_USER $RSYNC_SERVER ln -sfn $ONEWCURRDIR $OCURRDIR >> /dev/null
        REMOTE_SHUTDOWN
        PROGRESSBAR 100                
        NOTIFY_SEND "Backup" "RSYNC Backup Complete"
        echo "Offsite Rsync backup complete" >> "$LOGPATH/log-$NOW.log"
        if [ REMOTE_ALWAYS_ON == 0 ]; then
            NOTIFY_SEND "Backup" "RSYNC Server shut down\n\nAll files backed up.\n\nBackup Complete"
            echo "RSYNC Server shut down" >> "$LOGPATH/log-$NOW.log"
        else
            NOTIFY_SEND "Backup" "RSYNC Server still running\n\nAll files backed up.\n\nBackup Complete"
            echo "RSYNC Server still running" >> "$LOGPATH/log-$NOW.log"
        fi
}        

function RETRIEVE_OFFSITE_BACKUP {
                REMOTE_BOOT
        PROGRESSBAR 10                
        PING
        PROGRESSBAR 20
                NOTIFY_SEND "Backup" "Downloading Data"
        if [ "$SOPTS" == "--retrieve-all-offsite-backup" -o "$SOPTS" == "-RA" ]; then
            echo 'RETRIEVE BACKUP CURRENT OFFSITE Started' >> "$LOGPATH/log-$NOW.log"            
            PROGRESSBAR 25            
            rsync $RSYNCDOWNOPTS $RSYNC_SERVER::$RSYNC_PATH $DOWNLOAD_PATH >> "$LOGPATH/log-$NOW.log"
            PROGRESSBAR 75            
            echo 'RETRIEVE BACKUP ALL OFFSITE Finished' >> "$LOGPATH/log-$NOW.log"
        else
            if [ "$SOPTS" == "--retrieve-current-offsite-backup" -o "$SOPTS" == "-RC" ]; then
            echo 'RETRIEVE BACKUP CURRENT OFFSITE Started' >> "$LOGPATH/log-$NOW.log"
            PROGRESSBAR 25            
            rsync $RSYNCDOWNOPTS $RSYNC_SERVER:$CURRDIR $DOWNLOAD_PATH >> "$LOGPATH/log-$NOW.log"                            
            PROGRESSBAR 75
            echo 'RETRIEVE BACKUP CURRENT OFFSITE Finished' >> "$LOGPATH/log-$NOW.log"                    
            fi
                    
        fi        
        REMOTE_SHUTDOWN
        PROGRESSBAR 100        
                NOTIFY_SEND "Backup" "Server Shutdown.\n\nData Downloaded to:$DOWNLOAD_PATH"
}

function REMOTE_BOOT {
        if [ REMOTE_ALWAYS_ON == "0" -o "$SOPTS" == "-B" -o "$SOPTS" == "--boot-server-only" ]; then
            echo 'Server Bootup' >> "$LOGPATH/log-$NOW.log"
            NOTIFY_SEND "Backup" "Booting remote RSYNC server $RSYNC_SERVER\n\nPlease allow $REMOTE_WAIT_TIME seconds for remote computer to boot"
            wol -p $REMOTE_PORT -h $RSYNC_SERVER $REMOTE_MAC_ADDRESS >> /dev/null
            sleep $REMOTE_WAIT_TIME
        else
            echo 'Server Bootup Disabled' >> "$LOGPATH/log-$NOW.log"
            NOTIFY_SEND "Backup" "Server Boot Up Disabled\n\nServer should always be on"
        fi
}

function REMOTE_SHUTDOWN {
        if [ REMOTE_ALWAYS_ON == 0 -o "$SOPTS" == "-S" -o "$SOPTS" == "--shutdown-server-only" ]; then
            echo 'Server Shutdown' >> "$LOGPATH/log-$NOW.log"
            NOTIFY_SEND "Backup" "Shutting down server"
            ssh $RSYNC_SERVER -l $SSH_USER halt
        else
            echo 'Server Shutdown Disabled' >> "$LOGPATH/log-$NOW.log"
            NOTIFY_SEND "Backup" "Server Shutdown Disabled"
        fi
}

function PING {
        NOTIFY_SEND "Backup" "Establishing Connection" 
    PING_TEST=0
    PING_TEST_COUNTER=0
    while [  $PING_TEST -lt 1 ]; do
               if [ $PING_TEST_COUNTER -lt 11 ]; then
                        ping -c1 $RSYNC_SERVER >> /dev/null && PING_TEST=1 && NOTIFY_SEND "Backup" "Connection Established"
                        ((PING_TEST_COUNTER+=1))
               else
                        NOTIFY_SEND "Backup" "Connection failed. \n\n Could Not Connect to $RSYNC_HOST\n\n RSYNC Transfer did not complete"
                        echo 'Connection Test Failed' >> "$LOGPATH/log-$NOW.log"
            exit
               fi
         done
     echo 'Connection Test Passed' >> "$LOGPATH/log-$NOW.log"
}

function HELP {
            echo ================Help=======================
                echo USAGE
                echo "  backup.sh -NR(A,C,L,Z)Hh?OBSMU"
                echo flags---use only 1 at a time
        echo ===========================================                
        echo --only-offsite-backup, -O
                echo     Only do offsite backup
                echo --no-offsite-backup, -N
                echo     Do not do RSYNC Backup
                echo --retrieve-all-offsite-backup, -RA
                echo     Download Whole offsite backup tree
        echo --retrieve-current-offsite-backup, -RC
        echo     Only download most current offsite backup
                echo --retrieve-all-local-backup, -RL
                echo     Download Whole offsite backup tree
        echo --retrieve-current-local-backup, -RZ
        echo     Only download most current backup        
        echo --boot-server-only, -B
        echo     Boot offsite server
        echo --shutdown-server-only, -S
                echo     Shutdown remote server
        echo --remote-ssh-client, -Z
        echo     open ssh client for $SSH_USER at $RSYNC_SERVER.
        echo --mount, -M
        echo     Mount Local backup drive
        echo --umount, -U
        echo     Install Script - If installed does nothing
        echo --install, -I
        echo     Unmount Local backup drive
        echo --help, -h, -H, -?
                echo     Display this help page
                echo No Flag will automatically run your backup
                echo ===========================================
                exit
}

function SSH {
        ssh -l $SSH_USER $RSYNC_SERVER
        exit
}

function NOTIFY_SEND {

        if [ "$GUI" != "1" ]; then
            notify-send "$1" "$2"
        fi
}

function PROGRESSBAR {

        echo 0 > $TMP_LOCATION/pb.txt        
        if [ "$GUI" == "1" ]; then
            echo $1 > $TMP_LOCATION/pb.txt
        fi
}

function TEST {
    I=0
    #I=$(cat $TMP_LOCATION/pb.txt)
    while [ $I -lt "100" ]; do
        ((I+=10))
        PROGRESSBAR $I
        
    done
#sleep 10
#echo 0 >$TMP_LOCATION/pb.txt    
}
##########################Script#########################################


if [ "$SOPTS" == "--install" -o "$SOPTS" == "-I" ]; then
    INSTALL
    exit
fi

if [ "$SOPTS" == "-T" ]; then
    TEST
    exit
fi
if [ "$SOPTS" == "--remote-ssh-client" -o "$SOPTS" == "-Z" ]; then
    SSH
    exit
fi
if [ "$SOPTS" == "--help" -o "$SOPTS" == "-h" -o "$SOPTS" == "-H" -o "$SOPTS" == "-?" ]; then
        HELP
fi
touch "$LOGPATH/log-$NOW.log"
if [ "$GUI" != "1" ]; then
    tail -f "$LOGPATH/log-$NOW.log" &
fi
ln -sfn "log-$NOW.log" "$LOGPATH/log-current.log" >> /dev/null
if [ "$TEST" == "true" ]; then
    echo "Running in Test/Debug Mode. Please change TEST variable to TEST=0 if you are not debugging" >> "$LOGPATH/log-$NOW.log"
    NOTIFY_SEND "Backup" "Script Running in Test/Debug Mode"
fi
if [ "$SOPTS" == "--umount" -o "$SOPTS" == "-U" ]; then
        UMOUNT
        exit
fi
if [ "$SOPTS" == "--mount" -o "$SOPTS" == "-M" ]; then
        MOUNT
        exit
fi
if [ "$SOPTS" == "--boot-server-only" -o "$SOPTS" == "-B" ]; then
    REMOTE_BOOT
    PING
    exit
fi
if [ "$SOPTS" == "--shutdown-server-only" -o "$SOPTS" == "-S" ]; then
    REMOTE_SHUTDOWN
    exit
fi
if [ "$SOPTS" == "--retrieve-all-local-backup" -o "$SOPTS" == "-RL" ]; then
    RETRIEVE_LOCAL_BACKUP -RL
    exit
fi
if [ "$SOPTS" == "--retrieve-current-local-backup" -o "$SOPTS" == "-RZ" ]; then
    RETRIEVE_LOCAL_BACKUP -RZ
    exit
fi
    
if [ "$SOPTS" == "--retrieve-all-offsite-backup" -o "$SOPTS" == "-RA" ]; then
    RETRIEVE_OFFSITE_BACKUP -RA
    exit
fi
if [ "$SOPTS" == "--retrieve-current-offsite-backup" -o "$SOPTS" == "-RC" ]; then
    RETRIEVE_OFFSITE_BACKUP -RC
    exit
fi
NOTIFY_SEND "Backup" "Backup Has Started\n\n Do NOT Shut Down Computer"
if [ "$SOPTS" == "--only-offsite-backup" -o "$SOPTS" == "-O" ]; then
    OFFSITE_BACKUP
    exit
else
    LOCAL_BACKUP
fi
if [ "$REMOTE_BACKUP" == "false" ]; then
    NOTIFY_SEND "Backup" "External HDD backup complete. RSYNC/Offsite Backup disabled.\n\n Backup Script Finished"
    echo "External HDD backup complete. RSYNC/Offsite Backup disabled. Backup Script Finished" >> "$LOGPATH/log-$NOW.log"
    exit
else
    OFFSITE_BACKUP
fi

```

Here is the gui script

```

##################################################################################
###########################backup_gui.sh V1.1#####################################
##################################################################################
########################Written by: Ronald Brown##################################
##################################################################################
#######################Released Under GPLv2 licence###############################
##################################################################################
##########################Software Requirements:##################################
###########################1.gtkdialog############################################
############################2.backup.sh v1.5######################################
##################################################################################
#                                                                                #
##################################################################################
#             Things To Fix/ADD                     #
#               1. Progress bar loop still running when window X button Pressed. #
#        2. Backup Browser                         #
##################################################################################
#                                         #
##################################################################################
#                Version 1.1                         #
#        1. Added Diff Comparison Option for Drive Mounting               #
#        2. Changed where settings and temp files are stored         #
##################################################################################
#                                         #
##################################################################################
#                Version 1.0                         #
#        1. Initial Release                                               #
##################################################################################

#!/bin/bash 

GTKDIALOG=gtkdialog 


###############################Variables to Export#################################

export BACKUP_FUNC="./backup.sh --gui"
export TMP_LOCATION="./.tmp"
export SETTINGSDIR="."

###################################################################################


###############################Clear Progress Bar##################################

echo "0" > $TMP_LOCATION/pb.txt

###################################################################################


###############################GTKDIALOG XML Code##################################

export MAIN_DIALOG=' 
 
<window title="Backup_GUI V1.0" resizable="true"> 
    <vbox>
        <notebook labels="Backup/Restore|Mount/Unmount|Offsite Server|Settings|Log|About "> 
                <vbox>                 
                    <frame Backup>
                        <vbox>                
                            <vbox space-fill="false"> 
                                      <radiobutton>
                                        <label>Local Backup Only</label>
                                    <default>true</default>
                                    <variable>LBO</variable>
                                      </radiobutton>
                                      <radiobutton>
                                        <label>Offsite Backup Only</label>
                                    <variable>OBO</variable>
                                      </radiobutton>
                                      <radiobutton>
                                        <label>Local And Offsite Backup</label>
                                    <variable>LOB</variable>
                                      </radiobutton> 
                            </vbox>
                            <hbox>
                                <button>
                                    <label>BACKUP</label>
                                    <action>echo 0 > $TMP_LOCATION/pb.txt; case "true" in $LBO) $BACKUP_FUNC -N ;; $OBO) $BACKUP_FUNC -O ;; $LOB) $BACKUP_FUNC ;; esac;</action>
                                </button>
                            </hbox>
                        </vbox>                
                    </frame>
                    <hseparator width-request="440" visible="false"></hseparator>
                    <frame Restore>                
                        <vbox>
                            <vbox space-fill="false"> 
                                      <radiobutton>
                                        <label>Current Local Backup Only</label>
                                    <default>true</default>
                                    <variable>RCLBO</variable>
                                      </radiobutton>
                                      <radiobutton>
                                        <label>Current Offsite Backup Only</label>
                                    <variable>RCOBO</variable>
                                      </radiobutton>
                                      <radiobutton>
                                        <label>All Local Backups</label>
                                    <variable>RALB</variable>
                                      </radiobutton>                           
                                <radiobutton>
                                        <label>All Offsite Backups</label>
                                    <variable>RAOB</variable>
                                      </radiobutton> 
                            </vbox>
                            <hbox>
                                <button>
                                    <label>RESTORE</label>
                                    <action>echo 0 > $TMP_LOCATION/pb.txt; case "true" in $RCLBO) $BACKUP_FUNC -RZ ;; $RCOBO) $BACKUP_FUNC -RC ;; $RALB) $BACKUP_FUNC -RL ;; $RAOB) $BACKUP_FUNC -RA ;; esac;</action>
                                </button> 
                             </hbox>
                        </vbox>
                    </frame>
                </vbox> 
            
            <vbox> 
                <hbox space-fill="false" space-expand="true"> 
                    <button> 
                        <label>Mount Backup Drive</label>
                        <action>$BACKUP_FUNC -M</action>
                    </button>
                    <button> 
                        <label>Unmount Backup Drive</label>
                        <action>$BACKUP_FUNC -U</action>
                    </button> 
                </hbox> 
                <hbox>
                    <hseparator></hseparator>     
                </hbox>
    
            </vbox> 
            
            <vbox> 

 
                <hbox>
                    <button> 
                        <label>Boot Offsite Server</label>
                        <action>$BACKUP_FUNC -B</action>
                    </button>
                    <button> 
                        <label>Shutdown Offsite Server</label>
                        <action>$BACKUP_FUNC -S</action>
                    </button> 
                    <button> 
                        <label>Open SSH Terminal on Offsite Server</label>
                        <action>$BACKUP_FUNC -Z</action>
                    </button>
                </hbox>                    

    
            </vbox>            
            

                        
            <vbox>
                <notebook labels="General|Local|Offsite|Automatic Backup|Advanced| ">
                    <vbox>
                        <hbox>
                            <text>
                                <label>Username:</label>
                            </text>
                            <entry tooltip-text="User To Back Up">
                                <default>'"$(cat settings.cfg |grep USRNAME= |awk  -F "=" '/USRNAME/ {print $2}')"'</default>
                                <variable>USRNAME_TB</variable>
                            </entry>
                        </hbox>
                
                        <hbox>
                            <text>
                                <label>Excludes Path:</label>
                            </text>
                            <entry  tooltip-text="Path to Excludes txt file">
                                <default>'"$(cat settings.cfg |grep EXCLUDES= |awk  -F "=" '/EXCLUDES/ {print $2}')"'</default>
                                <variable>EXCLUDES_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                                <label>CURRDIR:</label>
                            </text>
                            <entry tooltip-text="Path to Current Backup Directory">
                                <default>'"$(cat settings.cfg |grep CURRDIR= |awk  -F "=" '/CURRDIR/ {print $2}'| head -n 1)"'</default>
                                <variable>CURRDIR_TB</variable>
                            </entry>
                        </hbox>
        
                        <hbox>
                            <text>
                            <label>NEWCURRDIR:</label>
                            </text>
                            <entry tooltip-text="Path to Save New Backup">
                                <default>'"$(cat settings.cfg |grep NEWCURRDIR= |awk  -F "=" '/NEWCURRDIR/ {print $2}')"'</default>
                                <variable>NEWCURRDIR_TB</variable>
                            </entry>
                        </hbox>    

                        <hbox>
                            <text>
                                <label>INCOMPDIR:</label>
                            </text>
                            <entry tooltip-text="Path to Save Incomplete Backup">
                                <default>'"$(cat settings.cfg |grep INCOMPDIR= |awk  -F "=" '/INCOMPDIR/ {print $2}')"'</default>
                                <variable>INCOMPDIR_TB</variable>
                            </entry>
                        </hbox>

                        <hbox>
                            <text>
                                <label>Folder To Back Up:</label>
                            </text>
                            <entry tooltip-text="Path to What You Are Backing Up">
                                <default>'"$(cat settings.cfg |grep FOLDER_TO_BACKUP= |awk  -F "=" '/FOLDER_TO_BACKUP/ {print $2}')"'</default>
                                <variable>FOLDER_TO_BACKUP_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                                <label>Download Path:</label>
                            </text>
                            <entry tooltip-text="Where to Restore Backup To">
                                <default>'"$(cat settings.cfg |grep DOWNLOAD_PATH= |awk  -F "=" '/DOWNLOAD_PATH/ {print $2}')"'</default>
                                <variable>DOWNLOAD_PATH_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                                <label>Log Path:</label>
                            </text>
                            <entry tooltip-text="Where to Save Log Files">                    
                                <default>'"$(cat settings.cfg |grep LOGPATH= |awk  -F "=" '/LOGPATH/ {print $2}')"'</default>
                                <variable>LOGPATH_TB</variable>
                            </entry>
                        </hbox>                        
                        <hbox>
                            <text>
                                <label>Temp Directory:</label>
                            </text>
                            <entry tooltip-text="Where to Save Temporary files">                    
                                <default>'"$(cat settings.cfg |grep TMP_LOCATION= |awk  -F "=" '/TMP_LOCATION/ {print $2}')"'</default>
                                <variable>TMP_LOCATION_TB</variable>
                            </entry>
                        </hbox>
                        
                        <hbox>
                            <text>
                                <label>REMOTE BACKUP:</label>
                            </text>
                            <checkbox tooltip-text="Enable/Disable Remote Backup When Running Backup.sh from Command Line, Or When Running As An Automatic Task">
                                <label>'"$(echo \"\")"'</label>                                
                                <default>'"$(cat settings.cfg |grep REMOTE_BACKUP= |awk  -F "=" '/REMOTE_BACKUP/ {print $2}')"'</default>
                                <variable>REMOTE_BACKUP_CB</variable>
                            </checkbox>
                        </hbox>
        
                    </vbox>
                    <vbox>
                        <hbox>
                            <text>
                                <label>Device Path:</label>
                            </text>
                            <entry tooltip-text="Path to device we are Mounting">
                                <default>'"$(cat settings.cfg |grep DEVPATH= |awk  -F "=" '/DEVPATH/ {print $2}')"'</default>
                                <variable>DEVPATH_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                                <label>PREFIX:</label>
                            </text>
                            <entry tooltip-text="Path to Where We Mounted Device">
                                <default>'"$(cat settings.cfg |grep PREFIX= |awk  -F "=" '/PREFIX/ {print $2}')"'</default>
                                <variable>PREFIX_TB</variable>
                            </entry>
                        </hbox>
        
                        <hbox>
                            <text>
                                <label>Local Wait Time:</label>
                            </text>
                            <entry tooltip-text="How Long In Seconds to Wait Before Mounting Drive">
                                <default>'"$(cat settings.cfg |grep LOCAL_WAIT_TIME= |awk  -F "=" '/LOCAL_WAIT_TIME/ {print $2}')"'</default>
                                <variable>LOCAL_WAIT_TIME_TB</variable>
                            </entry>
                        </hbox>
                        
                        <hbox>
                            <text>
                                <label>Use Diff Comparason</label>
                            </text>
                            <checkbox tooltip-text="Use Diff Compare instead of Device Path to find device we are mounting">
                                <label>'"$(echo \"\")"'</label>                                
                                <default>'"$(cat settings.cfg |grep DIFFCOMPARE= |awk  -F "=" '/DIFFCOMPARE/ {print $2}')"'</default>
                                <variable>DIFFCOMPARE_CB</variable>
                                  </checkbox>
                        </hbox>
                    </vbox>
    
    
                    <vbox>
        
                        <hbox>
                            <text>
                            <label>RSYNC SERVER:</label>
                            </text>
                            <entry tooltip-text="RSYNC Server DNS/IP Address">
                                <default>'"$(cat settings.cfg |grep RSYNC_SERVER= |awk  -F "=" '/RSYNC_SERVER/ {print $2}')"'</default>
                                <variable>RSYNC_SERVER_TB</variable>
                            </entry>
                        </hbox>
            
                        <hbox>
                            <text>
                                <label>RSYNC Path:</label>
                            </text>
                            <entry tooltip-text="RSYNC Server Path Path eg. John-Backup">
                                <default>'"$(cat settings.cfg |grep RSYNC_PATH= |awk  -F "=" '/RSYNC_PATH/ {print $2}')"'</default>
                                <variable>RSYNC_PATH_TB</variable>
                            </entry>
                        </hbox>

                        <hbox>
                            <text>
                                <label>SSH USER:</label>
                            </text>
                            <entry tooltip-text="User on Remote Computer to Login With">
                                <default>'"$(cat settings.cfg |grep SSH_USER= |awk  -F "=" '/SSH_USER/ {print $2}')"'</default>
                                <variable>SSH_USER_TB</variable>
                            </entry>
                        </hbox>
            
                        <hbox>
                            <text>
                                <label>Remote Port:</label>
                            </text>
                            <entry tooltip-text="Port Forwarded Port for Wake On LAN on Remote Computer/Router">
                                <default>'"$(cat settings.cfg |grep REMOTE_PORT= |awk  -F "=" '/REMOTE_PORT/ {print $2}')"'</default>
                                <variable>REMOTE_PORT_TB</variable>
                            </entry>
                        </hbox>
            
                        <hbox>
                            <text>
                                <label>Remote MAC Address:</label>
                            </text>
                            <entry tooltip-text="Remote Server MAC Address. Needed For Wake on LAN">
                                <default>'"$(cat settings.cfg |grep REMOTE_MAC_ADDRESS= |awk  -F "=" '/REMOTE_MAC_ADDRESS/ {print $2}')"'</default>
                                <variable>REMOTE_MAC_ADDRESS_TB</variable>
                            </entry>
                        </hbox>
            
                        <hbox>
                            <text>
                                <label>Remote Wait Time:</label>
                            </text>
                            <entry tooltip-text="How Long to Wait In Seconds Before Establishing Connection With Remote Server">
                                <default>'"$(cat settings.cfg |grep REMOTE_WAIT_TIME= |awk  -F "=" '/REMOTE_WAIT_TIME/ {print $2}')"'</default>
                                <variable>REMOTE_WAIT_TIME_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                                <label>Offsite Prefix:</label>
                            </text>
                            <entry tooltip-text="Folder on Offsite Server to Save Data">
                                <default>'"$(cat settings.cfg |grep OFFSITE_PREFIX= |awk  -F "=" '/OFFSITE_PREFIX/ {print $2}')"'</default>
                                <variable>OFFSITE_PREFIX_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                                <label>Remote Always On:</label>
                            </text>
                            <checkbox tooltip-text="Disable/Enable Booting/Shutting Down Remote Backup Server">
                                <label>'"$(echo \"\")"'</label>                                
                                <default>'"$(cat settings.cfg |grep REMOTE_ALWAYS_ON= |awk  -F "=" '/REMOTE_ALWAYS_ON/ {print $2}')"'</default>
                                <variable>REMOTE_ALWAYS_ON_CB</variable>
                             </checkbox>
                        </hbox>

                    </vbox>

                    <vbox>
                        <hbox>
                            <frame Automatic Backup Option>
                                <vbox space-fill="false"  width-request="500">                                 
                                    <radiobutton>
                                            <label>Disabled</label>
                                        <default>'"$(if [ ! -f "/etc/cron.hourly/backup.sh" ] && [ ! -f "/etc/cron.daily/backup.sh" ] && [ ! -f "/etc/cron.weekly/backup.sh" ] && [ ! -f "/etc/cron.monthly/backup.sh" ] ; then echo true; else echo false;fi)"'</default>
                                        <variable>AB_DISABLED</variable>
                                          </radiobutton>
                                         <radiobutton>
                                        <default>'"$(if [ ! -f "/etc/cron.hourly/backup.sh" ]; then echo false; else echo true;fi)"'</default>                                        
                                        <label>Hourly</label>
                                        <variable>AB_HOURLY</variable>
                                          </radiobutton>
                                         <radiobutton>
                                            <label>Daily</label>
                                        <default>'"$(if [ ! -f "/etc/cron.daily/backup.sh" ]; then echo false; else echo true;fi)"'</default>
                                        <variable>AB_Daily</variable>
                                          </radiobutton>
                                         <radiobutton>
                                            <label>Weekly</label>
                                        <default>'"$(if [ ! -f "/etc/cron.weekly/backup.sh" ]; then echo false; else echo true;fi)"'</default>
                                        <variable>AB_WEEKLY</variable>
                                          </radiobutton>
                                         <radiobutton>
                                            <label>Monthly</label>
                                        <default>'"$(if [ ! -f "/etc/cron.monthly/backup.sh" ]; then echo false; else echo true;fi)"'</default>
                                        <variable>AB_MONTHLY</variable>
                                          </radiobutton>
                                </vbox>                
                            </frame>
                        </hbox>
                </vbox>

                    <vbox>
                        <hbox>
                            <text>
                                <label>Rsync Upload Options:</label>
                            </text>
                            <entry tooltip-text="RSYNC Backup Options">
                                <default>'"$(cat settings.cfg |grep RSYNCUPOPTS= |awk  -F "=" '/RSYNCUPOPTS/ {print $2}')"'</default>
                                <variable>RSYNCUPOPTS_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                            <label>Rsync Download Options:</label>
                            </text>
                            <entry  tooltip-text="RSYNC Restore Options">
                                <default>'"$(cat settings.cfg |grep RSYNCDOWNOPTS= |awk  -F "=" '/RSYNCDOWNOPTS/ {print $2}')"'</default>
                                <variable>RSYNCDOWNOPTS_TB</variable>
                            </entry>
                        </hbox>
                        <hbox>
                            <text>
                                <label>Test/Debug Mode:</label>
                            </text>
                            <checkbox tooltip-text="Leave Disabled for Normal Opperation">
                                <label>'"$(echo \"\")"'</label>                                
                                <default>'"$(cat settings.cfg |grep TEST= |awk  -F "=" '/TEST/ {print $2}')"'</default>
                                <variable>TEST_CB</variable>
                                  </checkbox>
                        </hbox>
    
                    </vbox>
                
                </notebook>
                <hseparator width-request="240"></hseparator>
                <hbox>
                    
                    <button>
                        <label>Save Settings</label>
                        <action>rm $SETTINGSDIR/settings.cfg</action>        
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "###########################Backup/Backup_gui Settings#############################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "########################Written by: Ronald Brown##################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#######################Released Under GPLv2 licence###############################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##########################Software Requirements:##################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "###########################1.Bash#################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#                                                                                #" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#             Things To Fix/ADD                     #" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#        1. Nothing                                                       #" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "##################################################################################" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#user to back up" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "USRNAME=$USRNAME_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Files To Exclude" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "EXCLUDES=\"$EXCLUDES_TB\"" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#RSYNC UPLOAD/Backup Options" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "RSYNCUPOPTS=\"$RSYNCUPOPTS_TB\"" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#RSYNC Download Options" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "RSYNCDOWNOPTS=\"$RSYNCDOWNOPTS_TB\"" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Path to current backup" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "CURRDIR=$CURRDIR_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Path for new backup" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "NEWCURRDIR=$NEWCURRDIR_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Path for incomplete backups on hdd/server" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "INCOMPDIR=$INCOMPDIR_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#What you are backing up" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "FOLDER_TO_BACKUP=\"$FOLDER_TO_BACKUP_TB\"" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Path to folder to save log files to" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "LOGPATH=\"$LOGPATH_TB\"" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Set to true for test mode(Used For Debugging) Mainly changes variables to other preset options." >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "TEST=$TEST_CB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#uncomment if you want to force disable offsite backups from default" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "REMOTE_BACKUP=$REMOTE_BACKUP_CB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Allow remote shutdown false(Allow booting/shutting down remote host)  or true(Disable booting/shutting down remote host)" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "REMOTE_ALWAYS_ON=$REMOTE_ALWAYS_ON_CB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Server IP or DNS Address" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "RSYNC_SERVER=$RSYNC_SERVER_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#RSYNC PATH" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "RSYNC_PATH=$RSYNC_PATH_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#SSH user remote computer" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "SSH_USER=$SSH_USER_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "# Port Forwarded port for Wake on lan Magic Packet" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "REMOTE_PORT=$REMOTE_PORT_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#MAC address of the network interface you are trying to wake" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "REMOTE_MAC_ADDRESS=$REMOTE_MAC_ADDRESS_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Time in seconds to wait for remote computer to wake up, before running network test" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "REMOTE_WAIT_TIME=$REMOTE_WAIT_TIME_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Where to download backed up files to." >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "DOWNLOAD_PATH=\"$DOWNLOAD_PATH_TB\"" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "OFFSITE_PREFIX=$OFFSITE_PREFIX_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Partition to mount" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "DEVPATH=$DEVPATH_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Path to mount to" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "PREFIX=$PREFIX_TB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Time to wait in seconds before mounting external hdd" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "LOCAL_WAIT_TIME=$LOCAL_WAIT_TIME_TB" >> "$SETTINGSDIR/settings.cfg"    </action>
                        <action>echo "" >> ./settings.cfg</action>
                        <action>echo "#Temp Directory" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "TMP_LOCATION=\"$TMP_LOCATION_TB\"" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "#Set to true to use DIFF Comparison to find drive." >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>echo "DIFFCOMPARE=$DIFFCOMPARE_CB" >> "$SETTINGSDIR/settings.cfg"</action>
                        <action>case "true" in $AB_DISABLED) if [ -f "/etc/cron.hourly/backup.sh" ]; then rm /etc/cron.hourly/backup.sh; fi; if [ -f "/etc/cron.daily/backup.sh" ]; then rm /etc/cron.daily/backup.sh; fi; if [ -f "/etc/cron.weekly/backup.sh" ]; then rm /etc/cron.weekly/backup.sh; fi; if [ -f "/etc/cron.monthly/backup.sh" ]; then rm /etc/cron.monthly/backup.sh; fi; ;; $AB_HOURLY) if [ -f "/etc/cron.hourly/backup.sh" ]; then rm /etc/cron.hourly/backup.sh; fi; if [ -f "/etc/cron.daily/backup.sh" ]; then rm /etc/cron.daily/backup.sh; fi; if [ -f "/etc/cron.weekly/backup.sh" ]; then rm /etc/cron.weekly/backup.sh; fi; if [ -f "/etc/cron.monthly/backup.sh" ]; then rm /etc/cron.monthly/backup.sh; fi; ln -s $(pwd)/backup.sh /etc/cron.hourly/backup.sh; ;; $AB_DAILY) if [ -f "/etc/cron.hourly/backup.sh" ]; then rm /etc/cron.hourly/backup.sh; fi; if [ -f "/etc/cron.daily/backup.sh" ]; then rm /etc/cron.daily/backup.sh; fi; if [ -f "/etc/cron.weekly/backup.sh" ]; then rm /etc/cron.weekly/backup.sh; fi; if [ -f "/etc/cron.monthly/backup.sh" ]; then rm /etc/cron.monthly/backup.sh; fi; ln -s $(pwd)/backup.sh /etc/cron.daily/backup.sh; ;; $AB_WEEKLY) if [ -f "/etc/cron.hourly/backup.sh" ]; then rm /etc/cron.hourly/backup.sh; fi; if [ -f "/etc/cron.daily/backup.sh" ]; then rm /etc/cron.daily/backup.sh; fi; if [ -f "/etc/cron.weekly/backup.sh" ]; then rm /etc/cron.weekly/backup.sh; fi; if [ -f "/etc/cron.monthly/backup.sh" ]; then rm /etc/cron.monthly/backup.sh; fi; ln -s $(pwd)/backup.sh /etc/cron.weekly/backup.sh; ;; $AB_MONTHLY) if [ -f "/etc/cron.hourly/backup.sh" ]; then rm /etc/cron.hourly/backup.sh; fi; if [ -f "/etc/cron.daily/backup.sh" ]; then rm /etc/cron.daily/backup.sh; fi; if [ -f "/etc/cron.weekly/backup.sh" ]; then rm /etc/cron.weekly/backup.sh; fi; if [ -f "/etc/cron.monthly/backup.sh" ]; then rm /etc/cron.monthly/backup.sh; fi; ln -s $(pwd)/backup.sh /etc/cron.monthly/backup.sh; ;; esac;</action>
                    </button>
                </hbox>

            </vbox>            

            <vbox> 
                <frame Log File:>
                    <edit editable="false">
                        <variable>LOG</variable>                        
                        <width>350</width><height>170</height>
                        <input file>./backup-logs/log-current.log</input>
                    </edit>                         
                    <hbox>
                        <button>
                            <label>Refresh</label>
                            <action type="refresh">LOG</action>
                        </button>
                    </hbox>                   
                </frame>

            </vbox>
            <vbox>
                <text>                
                    <label>backup_gui.sh/backup.sh (C) Ronald Brown 2014</label>
                </text>
            </vbox>

        </notebook> 
            <hseparator width-request="240"></hseparator> 
            <progressbar>                
                <variable>PROGRESS_BAR</variable>
                <input>while [ "$M" != "101" ]; do M=`cat $TMP_LOCATION/pb.txt`; if [ "$M" != "101" ]; then echo $M; fi; if [ "$M" == "100" ]; then M=0; fi; sleep .125; done;</input>
            </progressbar>
            <hseparator width-request="240"></hseparator> 
            <hbox>
                <button>
                    <label>Exit</label>
                    <action>`echo 101 > $TMP_LOCATION/pb.txt`</action>
                    <action type="exit">1</action>
                </button>
             </hbox>
    
    </vbox>
</window> 
' 
###################################################################################


##################################Script###########################################

case $1 in 
    -d | --dump) echo "$MAIN_DIALOG" ;; 
    *) $GTKDIALOG --program=MAIN_DIALOG --center
        unset BACKUP_FUNC
        unset TMP_LOCATION
        
        ;; 

esac

###################################################################################

```

and here is the settings file, with some private data changed of coarse.

```

##################################################################################
###########################Backup/Backup_gui Settings#############################
##################################################################################
########################Written by: Ronald Brown##################################
##################################################################################
#######################Released Under GPLv2 licence###############################
##################################################################################
##########################Software Requirements:##################################
###########################1.Bash#################################################
##################################################################################
##################################################################################
#                                                                                #
##################################################################################
#             Things To Fix/ADD                     #
#        1. Nothing                                                       #
##################################################################################

#user to back up
USRNAME=bobbarker
#Files To Exclude
EXCLUDES="/home/$USRNAME/rsync/excludes.txt"
#RSYNC UPLOAD/Backup Options
RSYNCUPOPTS="--archive --compress --one-file-system --hard-links --human-readable --inplace --numeric-ids --delete --quiet --delete-excluded"
#RSYNC Download Options
RSYNCDOWNOPTS="--archive --compress --update --hard-links"
#Path to current backup
CURRDIR=/backup/rsync/$HOSTNAME/_home_$USRNAME.current
#Path for new backup
NEWCURRDIR=/backup/rsync/$HOSTNAME/_home_$USRNAME.$NOW
#Path for incomplete backups on hdd/server
INCOMPDIR=/backup/rsync/$HOSTNAME/_home_$USRNAME.incomplete/
#What you are backing up
FOLDER_TO_BACKUP="/home/$USRNAME/"
#Path to folder to save log files to
LOGPATH="./backup-logs"
#Set to true for test mode(Used For Debugging) Mainly changes variables to other preset options.
TEST=true

#uncomment if you want to force disable offsite backups from default
REMOTE_BACKUP=false
#Allow remote shutdown false(Allow booting/shutting down remote host)  or true(Disable booting/shutting down remote host)
REMOTE_ALWAYS_ON=true
#Server IP or DNS Address
RSYNC_SERVER=localhost
#RSYNC PATH
RSYNC_PATH=ronnie-backup
#SSH user remote computer
SSH_USER=root
# Port Forwarded port for Wake on lan Magic Packet
REMOTE_PORT=1111
#MAC address of the network interface you are trying to wake
REMOTE_MAC_ADDRESS=00:10:0f:fe:05:10
#Time in seconds to wait for remote computer to wake up, before running network test
REMOTE_WAIT_TIME=120
#Where to download backed up files to.
DOWNLOAD_PATH="/home/ronnie/backup_test"
OFFSITE_PREFIX=/home

#Partition to mount
DEVPATH=/dev/sde1

#Path to mount to
PREFIX=/media/ef8bb6f4-5c46-480d-b2b3-4bb0da844e31
#Time to wait in seconds before mounting external hdd
LOCAL_WAIT_TIME=45

#Temp Directory
TMP_LOCATION="./.tmp"

DIFFCOMPARE=true

```


Any help would be appreciated. Thank you.

PS, I know there are some better ways to do some of this stuff, this script is kind of dirty, but should work. as said it is a work in progress, but I cant seem to figure out why it works perfect in gentoo, and gets random syntax errors in Ubuntu. Last time I checked bash is bash on any distribution, so unless there are some ubuntu specific changes to bash that I am unaware of, this should work for my client.

---

### Post by Lars Noodén on 2014-12-10
You might move "#!/bin/bash" up to the first line, I get different behaviour in my test script if it is not on the first line.

---

### Post by ronnie5 on 2014-12-10
I will give that a try, I will post back later, as I dont currently have time to test on ubuntu at the moment, Will have to install in a virtual machine and then install gtkdialog, as there isnt a package for it in the ubuntu repositorys.

---

### Post by nerdtron on 2014-12-10
Or try to run the script in Ubuntu using "bash /path/to/scriptname"
This is to define that this script should run in "bash". In other systems, the "/bin/sh" shell is pointed to "/bin/bash" so they're basically the same. But in ubuntu, /bin/sh points to /bin/dash.

There could be some syntax problems if you run the script intended for bash to run on the dash shell.

---

### Post by ronnie5 on 2014-12-10
> **nerdtron said:**
> Or try to run the script in Ubuntu using "bash /path/to/scriptname"
This is to define that this script should run in "bash". In other systems, the "/bin/sh" shell is pointed to "/bin/bash" so they're basically the same. But in ubuntu, /bin/sh points to /bin/dash.

There could be some syntax problems if you run the script intended for bash to run on the dash shell.

Now, this I did not know. I am going to be really mad, if this is what the problem is, as I have been stairing at this script for 2 weeks, and trying to find out why it wont work on my customers computer. I still have some more features to write into it, but didnt want to continue until I could figure out why it wasnt working in ubuntu.

---

