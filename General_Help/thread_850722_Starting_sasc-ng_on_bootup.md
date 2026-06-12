---
title: "Starting sasc-ng on bootup"
date: 2008-07-05
forum: General Help
---

### Post by djh82uk on 2008-07-05
Hiya guys

Im struggling to get sasc-ng to start on bootup, I have followed the instructions here:

[https://opensvn.csie.org/traccgi/sascng/wiki/SascInitScripts](https://opensvn.csie.org/traccgi/sascng/wiki/SascInitScripts)

But it just won;t work, it comes up saying unexpected "(" in runsasc it does not like any "(" which all the functions use.

I can start it manually by typing the following, based on that is there any other way to start it automatically?

cd /usr/local/src/sasc-ng/trunk/
Sudo insmod dvbloopback.ko
sudo ./sasc-ng -j 0:1

Thanks

DJH

---

### Post by dcstar on 2008-07-05
> **djh82uk said:**
> Hiya guys

Im struggling to get sasc-ng to start on bootup, I have followed the instructions here:

[https://opensvn.csie.org/traccgi/sascng/wiki/SascInitScripts](https://opensvn.csie.org/traccgi/sascng/wiki/SascInitScripts)

But it just won;t work, it comes up saying unexpected "(" in runsasc it does not like any "(" which all the functions use.

I can start it manually by typing the following, based on that is there any other way to start it automatically?

cd /usr/local/src/sasc-ng/trunk/
Sudo insmod dvbloopback.ko
sudo ./sasc-ng -j 0:1

Thanks

DJH

**Exactly** what happens when you type:

```
sudo /etc/init.d/sascd restart
```

---

### Post by djh82uk on 2008-07-06
hiya

it gives:

/usr/local/bin/runsasc: 28: Syntax error: "(" unexpected


djh

---

### Post by djh82uk on 2008-07-08
anyone able to help?

DJH

---

### Post by covert on 2008-09-17
The startup script is written for a old shell.

Try this one.

```
#! /bin/bash
#
# sasc-ng and driver management script by opacus
# thanks to xjosh for MapCards routine
# Updated 03-10-08  - version 17.0
#

# IMPORTANT: Copy dvbloopback.ko (or link it) to  /lib/modules/2.6.XX/misc
#            after that run "depmod -a" so the modprobe works without being in the current directory.
#            Two distribution packages must be priorly installed: "screen" and "dvbsnoop"
#
# Depending on your configuration, the script could load, reload or kill sasc-ng, mythtv, vdr and all the associate drivers.
# Link this script as part of your startup default level. Procedure may vary as per your distro.
#

# These are the available commands on the console (please test the script manually before linking it to startup):
# sascd start >> Normal boot start. Starts sasc-ng and optionally mythtv or vdr. Assumes all driver modules preloaded
# sascd restart >> Restarts sasc-ng and optionally mythtv or vdr. Assumes all driver modules preloaded
# sascd stop >> Stops sasc-ng and optionally mythtv or vdr. Unloads all driver modules
# sascd reload >> Restarts sasc-ng and optionally mythtv or vdr. Unloads and reloads all driver modules.
# sascd reload-drivers >> Unloads and reload all driver modules.

## ************* Configuration Section *************** ##
 
ENABLED=1                                     # Change to 1 to enable sasc-ng's script. Change to 0 to disable it.

SCREEN="no"                                 # Change to "yes" to enable starting sasc-ng, myth or vdr thru "screen" command.
                                           # With screen you could get dynamic output using command:
                                           # "screen -r sasc-ng-scr" for sasc-ng or "screen -r addl-scr" for myth or vdr
                                           # Screen is recommended mostly for debugging only.
                                           # You MUST add a daemon option to sasc-ng, vdr and mythtv if SCREEN="no"
                                           # otherwise remove the daemon option if SCREEN="yes"

NAME="sascd"                               # name of this script.
LOOPDRIVER=" dvbloopback"                  # name of dvbloopback module
SASCLIB="LD_LIBRARY_PATH=/usr/src/sasc-ng/sc/PLUGINS/lib/ "
SASCDIR="/usr/src/sasc-ng/"           # sasc-ng directory
SASCPRG="sasc-ng"                          # name of sasc-ng program to be started by this  script.
KILLPRGS=" tvtime xawtv vdr mythbackend "  # programs to be killed when sascd exits

# Add here the startup Options passed to SASC-NG.  Adjust according to your devices.
# DO NOT USE ANY JOIN PARAMETER. This is appended automatically.

# SASCOPTION=" --daemon --sid-allpid --cam-dir=/video/plugins -o --log /var/log/sasc-ng/sasc-ng.log"                   # example for nexus
SASCOPTION=" --daemon --sid-allpid --cam-dir /etc/camfiles --cam-budget -o --log /var/log/sasc-ng.log"         # example for genpix + budget card + nexus

# Add here the of name of mythtv or vdr which may be loaded automatically after sasc-ng:

# ADDLPRG="xxxxxxxx"                       # Use xxxxxxxx  if no additional program is to be started
ADDLPRG="mythtv-backend"                      # additional program will be started  (choose mythbackend or vdr, but not both)
ADDLDIR="/etc/init.d/"                  # additional program directory
ADDREAL="/usr/bin/mythbackend"

# Add here the startup Options passed to ADDLPRG:

ADDLOPTIONS=" "                            # If no options, leave at least an empty string.
# ADDLOPTIONS=" -d -Premote -Pprefermenu -Pyaepg -D 1 -v /video " # additional options for vdr
ADDLOPTIONS=" start" # additional options for mythtv.
 

# Add here your dvb card or remote control drivers which may be loaded and unloaded with this script (in addition of  LOOPDRIVER).
# CAUTION: The order of drivers is critical. Drivers with dependants must be at the end of the list
# THE WRONG ORDER OF DRIVERS MAY CRASH YOUR SYSTEM

# Do you have a genpix usb adapter (yes/no) ?
GPADAPTER="no"
GPDRIVERS="dvb_usb_gp8psk"                                                # This is the driver to be loaded.
GPDRIVERSKILL=" dvb-usb-gp8psk dvb-usb dvb-pll dvb-core "                 # These are the v4l modules to be unloaded

# Do you have a Twinhan 1020a budget card (yes/no) ?
BUDGET="no"
BUDGETDRIVERS1="bttv"                                                     # This is the driver1 to be loaded
BUDGETDRIVERS1OPTION="i2c_hw=1 card=0x71"                                 # This driver1 needs special options
BUDGETDRIVERS2="dvb_bt8xx"                                                # This is the driver2 to be loaded
BUDGETDRIVERSKILL=" dvb_bt8xx tuner dst bt878 bttv ir_common compat_ioctl32 \
                    btcx_risc tveeprom videodev v4l2_common v4l1_compat \         
                    video_buf dvb_core "                                  # These are the v4l modules to be unloaded

# Do you have a digistar 103g budget card (yes/no) ?
DIGIBUDGET="no"
DIGIBUDGETDRIVERS="cx88_dvb"                                              # This is the driver1 to be loaded
DIGIBUDGETDRIVERSKILL=" cx88_dvb cx24123 cx88_vp3054_i2c videobuf_dvb cx8800 cx8802 cx88xx videodev v4l1_compat ir_common compat_ioctl32 v4l2_common videobuf_dma_sg videobuf_core btcx_risc tveeprom"                                                 # These are the v4l modules to be unloaded

# Do you have a Nexus-S card (yes/no) ?
NEXUS="no"
NEXUSDRIVERS="dvb_ttpci"                                                  # This is the driver to be loaded.
NEXUSDRIVERSKILL=" ves1x93 dvb_ttpci stv0299 video_buf saa7146 \
    v4l2_common v4l1_compat ttpci_eeprom saa7146_vv videodev dvb_core  "  # These are the v4l modules to be unloaded
# NEXUSDRIVERSKILL=" dvb_ttpci lnbp21 l64781 saa7146_vv video_buf saa7146 ves1820 tda8083 sp8870 stv0297 ves1x93 ttpci_eeprom stv0299 dvb_core "  # These are the kernel modules to be unloaded

# Number of times runsasc will attempt to restart SASC-NG
MAXTRIES=3

# Do you want sascd to monitor sasc-ng continuously (yes/no)?
MONITOR="no"                                                         # <<<< say "yes" only if sascd is started MANUALLY from the console.
# When monitor is "yes", how often sascd will check the status of sasc-ng (in seconds) ?
INTERVAL=20

# Set STARTFLAG to 1 if you want the drivers NOT to be unloaded and reloaded on command "sascd start" or "sascd restart"
# In this case, the script expects the drivers to be priorly loaded on boot-up by udev of by other module loading routines.
# When STARTFLAG=0 all driver modules are unloaded and force reloaded on: "sascd start" and "sascd restart" commands.
# On command "sascd reload" drivers get unloaded and reloaded regardless of STARTFLAG settings.
STARTFLAG=1

# Input your preferred virtual card map order here. If needed add more adapters as dvb[2], dvb[3]...
# This is the virtual adapter order known to mythtv database, regardless of real adapter order.
# As an example if you have two adapters: dvb[0] will always be known to Mythtv as virtual adapter 2, dvb[1] as 3, etc..
# The real adapter order could change but the virtual order stays the same. .
# Initially write any card name here and run the script. After you'll see the correct names printed out, please insert them.
# dvb[0]="ST STV0299 DVB-S"                   # this is a nexus-s card
# dvb[1]="Conexant CX24123/CX24109"           # this is a digistar budget card
# dvb[2]="DST DVB-S"                          # this is a twinhan budget card
# dvb[3]="Genpix 8psk-to-USB2 DVB-S"          # this is genpix-usb adapter

## ******************* End Configuration Section ***************** ##



#Global variables (do not change)
FILENAME=""
RUNFLAG=0
MODULE=""
MODULEOPTION=""
LOOPCOUNT=0
JOINPARM=""
DVBSIZE=0

# Calculate the real-virtual join parameters
MapCards() {
     JOINPARM=""
     JOINPARM=`echo -n "$JOINPARM -j 306:3 -j 307:4"`
      return 1
}

# Test modules for existence
TestModule() {
     grep -qse $MODULE [-_]core /proc/modules
}

# Insert generic modules
LoadModule() {
     local LOOP=0
 
     while (true); do
           if ! TestModule; then
                   if [ $STARTFLAG -eq 0 ]; then
                         if [ $((LOOP+=1)) -le  $MAXTRIES ]; then
                                insmod /usr/src/sasc-ng/dvbloopback.ko num_adapters=2 >> /var/log/sascd.log
                                sleep 2
                                if TestModule; then
                                      return 1
                                fi
                         else
                                echo "ERROR: Module $MODULE failed insertion after $MAXTRIES tries. Exiting..." | tee -a /var/log/sascd.log
                                exit 1
                         fi
                   else
                         echo "WARNING: Module $MODULE supposed to be loaded before running $NAME. Ignoring adapter..."  | tee -a /var/log/sascd.log
                         return 0
                   fi
           else
                   return 1
           fi
     done
}

# Load all DVBLoopback driver modules needed for your hardware:
LoadDrivers() {
     if [ $STARTFLAG -eq 0 ]; then
          echo -e " `date` Loading all drivers" | tee -a /var/log/sascd.log
     fi
     if (test $BUDGET = "yes"); then
          MODULE=$BUDGETDRIVERS1; MODULEOPTION=$BUDGETDRIVERS1OPTION; LoadModule
          MODULE=$BUDGETDRIVERS2; MODULEOPTION=""; LoadModule
     fi     
     if (test $DIGIBUDGET = "yes"); then
          MODULE=$DIGIBUDGETDRIVERS; MODULEOPTION=""; LoadModule
     fi     
     if (test $NEXUS = "yes"); then
           MODULE=$NEXUSDRIVERS; MODULEOPTION=""; LoadModule
     fi
     if (test $GPADAPTER = "yes"); then
           MODULE=$GPDRIVERS; MODULEOPTION=""; LoadModule
     fi
     sleep 1
     MapCards     # Mapping is done after adapter driver insertion, but before dvbloopback
     sleep 1
     STARTFLAG=0
     MODULE=$LOOPDRIVER;  MODULEOPTION=" num_adapters=$DVBSIZE"; LoadModule 
     return 1 
}

# Unload all DVBLoopback driver modules loaded in LoadDrivers 
UnloadDrivers() {
     if [ $STARTFLAG -eq 0 ]; then
           echo -e " `date` Unloading all drivers"  | tee -a /var/log/sascd.log
           screen -wipe > /dev/null  2>&1
           killall  -q $SASCPRG $KILLPRGS > /dev/null 2>&1
           sleep 1
           rmmod -f $LOOPDRIVER > /dev/null 2>&1
           sleep 1
           if (test $GPADAPTER = "yes"); then
                  rmmod -f $GPDRIVERSKILL > /dev/null 2>&1
             sleep 1
           fi
           if (test $NEXUS = "yes"); then
                  rmmod -f $NEXUSDRIVERSKILL > /dev/null 2>&1
             sleep 1
                  rmmod -f $NEXUSDRIVERSKILL > /dev/null 2>&1
             sleep 1
           fi
           if (test $BUDGET = "yes"); then
                  rmmod -f $BUDGETDRIVERSKILL > /dev/null 2>&1
             sleep 1
           fi   
           if (test $DIGIBUDGET = "yes"); then
                  rmmod -f $DIGIBUDGETDRIVERSKILL > /dev/null 2>&1
             sleep 1
           fi   
     fi
     return 1 
}

# Retry and exit after MAXTRIES
ReloadDrivers() {
      if [ $((LOOPCOUNT+=1)) -le  $MAXTRIES ]; then
           echo " `date` $NAME trying $LOOPCOUNT time(s). Max retries $MAXTRIES" | tee -a /var/log/sascd.log
            UnloadDrivers
            sleep 5
            LoadDrivers
            sleep 5
     else
            echo "ERROR: Something is wrong! $SASCPRG could not be started. Exiting...." | tee -a /var/log/sascd.log
            UnloadDrivers
            sleep 5
#           killall $NAME   
            exit 1
     fi
     return 1
}

# Grep thru ps results and eliminate zombie processes.
CheckStatus() {
     RUNFLAG=0
     if (ps -A ax | grep -v "ps ax" | grep -v grep | grep $FILENAME | grep -v "<defunct>") > /dev/null 2>&1; then
           RUNFLAG=1
     fi
     return 1
}

# Print file status
EchoF() {
    local YESNO=""

    if [ $RUNFLAG -eq 0 ]; then
            YESNO="NOT"
    fi
    if  !(test $MONITOR = "yes"); then   
           echo " `date` <<<<<< $FILENAME is $YESNO running >>>>>" | tee -a /var/log/sascd.log
    fi
    return 1
}

# Retry loop 
RunLoop() {
     local RUNFLAGs=0
     local RUNFLAGa=0
     local LOOP=0

     while (true); do
           sleep 1
           if (test -f $SASCDIR$SASCPRG); then           # check sasc-ng existence
                   FILENAME=$SASCPRG; CheckStatus
                   if  [ $RUNFLAG -eq 1 ]; then
                         RUNFLAGs=1
                        EchoF
                   fi
 

#                  if (test -e $ADDLDIR$ADDLPRG); then    # check addl-prg existence
#                           FILENAME=$ADDLPRG; CheckStatus
#                           if  [ $RUNFLAG -eq 1 ]; then
#                                 RUNFLAGa=1
#                                 if [ $RUNFLAGs -eq 1 ]; then
#                                       EchoF
#                                 fi
#                           fi
#                   else
#                           RUNFLAGa=1
#                   fi

                   if (pidof mythbackend); then
                      FILENAME=$ADDLPRG;
                      echo "pid found"
                      RUNFLAGa=1
                      if [ $RUNFLAGs -eq 1 ]; then
                                       EchoF
                       fi

                   else
                      RUNFLAGa=1
                      echo "no pid found"
                   fi

                   echo "RUNFLAGs>> $RUNFLAGs RUNLGAGa>> $RUNFLAGa"
                   if [ $RUNFLAGs -eq 0 ] || [ $RUNFLAGa -eq 0 ]; then
                           ReloadDrivers
                           sleep 5
                          echo "Starting $SASCLIB $SASCDIR$SASCPRG $SASCOPTION $JOINPARM "  | tee -a /var/log/sascd.log

                          if  (test $SCREEN = "yes"); then
                              # start sasc-ng with screen. Daemon option must not be set
                               eval "screen -D -m -S sasc-ng-scr $SASCLIB $SASCDIR$SASCPRG $SASCOPTION $JOINPARM &"
                          else
                              # start sasc-ng without screen. Daemon option must be set
                              eval "$SASCLIB $SASCDIR$SASCPRG $SASCOPTION $JOINPARM"
                          fi

                          if (test -f $ADDLDIR$ADDLPRG) ; then
                                 sleep 1
                                 cd $ADDLDIR
                                 echo "Starting $ADDLDIR$ADDLPRG $ADDLOPTIONS " | tee -a /var/log/sascd.log
                                 sleep 5
                                 if  (test $SCREEN = "yes"); then
                                      # start myth or vdr with screen. Daemon option must not be set
                                      eval "screen -D -m -S addl-scr $ADDLDIR$ADDLPRG $ADDLOPTIONS &"
                                 else
                                      # start myth or vdr without screen. Daemon option must be set
                                      eval "$ADDLDIR$ADDLPRG $ADDLOPTIONS"    # start myth or vdr.
                                 fi
                          else
                             echo "not starting program ($ADDLDIR$ADDLPRG)"
                          fi
                   fi
           else
                  echo "ERROR: file $SASCPRG not found. Exiting..." | tee -a /var/log/sascd.log
                  exit 1;
           fi 
           if  (test $MONITOR = "yes"); then
#                 echo -e "monitoring in progress... checking status again in $INTERVAL sec  \n"
                  sleep $INTERVAL
           else
                  if [ $RUNFLAGs -eq 1 ] && [ $RUNFLAGa -eq 1 ]; then
                           exit 0;
                  fi
           fi
     done
}

# Main script
test "$ENABLED" != "0" || exit 0

if (test $ADDLPRG = "mythbackend"); then
     export MYTHCONFDIR=/var/lib/mythtv
fi

case "$1" in
     start)
          RunLoop
          ;;
     stop)
          STARTFLAG=0
          UnloadDrivers
          ;;
     restart)
          killall  -q $SASCPRG $ADDLPRG $KILLPRG > /dev/null 2>&1
          sleep 5
          RunLoop
          ;;
     reload)
          STARTFLAG=0
          killall  -q $SASCPRG $ADDLPRG $KILLPRG >> /dev/null 2>&1
          sleep 5
          RunLoop
          ;;
     reload-drivers)
          STARTFLAG=0
          killall  -q $SASCPRG $ADDLPRG $KILLPRG > /dev/null 2>&1
          sleep 5
          UnloadDrivers
          sleep 5
          LoadDrivers
          ;;
     *)
          echo "Use: $N {start|stop|restart|reload|reload-drivers}" >&2
          ;;
esac
# killall $NAME
exit 0 
```

---

