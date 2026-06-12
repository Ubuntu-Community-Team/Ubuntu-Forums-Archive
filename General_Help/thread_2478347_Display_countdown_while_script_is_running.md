---
title: "Display countdown while script is running"
date: 2022-08-23
forum: General Help
---

### Post by raleigh3 on 2022-08-23
I would like to modify this to display a progress bar or something similar while it is running. 

Preferably showing how much time has elapsed.

```
#!/bin/bash
#
#  Sound alarm after specifying time and message 
# Must input time delay AND message in double quotes !!
#
#       
# ** sleep can also accept intergers ex. sleep 7.63
# Made alias for it type al and time
# 2> /dev/null suppresses messages for amixer AND (c)vlc
#
soundfile="/usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3"
#originalVolume=$(amixer -D pulse get Master | grep -m 1 -o -E [[:digit:]]+%)
clear
amixer -D pulse sset Master 100% > /dev/null 2>&1
if [ -f "$soundfile" ];
then
     echo "Soundfile is present."
else
      
  echo "File $soundfile does NOT exist."
  echo
  echo "Program will now exit."
  exit
fi

[ -z "$2" ] && {
echo 
echo -e "   Error!! No time value given and/or message specified !!"
echo
echo -e "   Alarm Program 2018"
echo
echo -e "   alarm.sh [time value in seconds] Message in double Quotes"; 
echo -e "   alarm 5m   = 5 minute alarm"
echo -e "   alarm 5h   = 5 hour alarm"
echo -e "   alarm 5d   = 5 day alarm"
echo -e "   alarm 1.5m = 1 minute 30 seconds alarm"
echo 
echo -e "   alarm.sh 1m "\"Tea is ready."\""  

echo 
exit 1; }

echo  -e "\033[32;5mTIMER COUNTING DOWN to $1 \033[0m"
sleep $1
{
    for ((volume = 35; volume <= 85; volume += 2)); do
        amixer -D pulse sset Master ${volume}% > /dev/null
        sleep .5
    done
} &

cvlc --play-and-exit "$soundfile" > /dev/null 2>&1
#set back to original volume
amixer -D pulse sset Master %85
echo $2

gxmessage -fg blue -font  'sans 20' -timeout 2 ' TIME IS UP !!'
```

I found something that may help.

```
#!/bin/bash
GREEN='\033[0;32m'
RED='\033[0;31m'
YELLOW='\033[0;33m'
RESET='\033[0m'
hour=0
min=0
sec=11
tput civis
echo -ne "${GREEN}"
        while [ $hour -ge 0 ]; do
                 while [ $min -ge 0 ]; do
                         while [ $sec -ge 0 ]; do
                                 if [ "$hour" -eq "0" ] && [ "$min" -eq "0" ]; then
                                         echo -ne "${YELLOW}"
                                 fi
                                 if [ "$hour" -eq "0" ] && [ "$min" -eq "0" ] && [ "$sec" -le "10" ]; then
                                         echo -ne "${RED}"
                                 fi
                                 echo -ne "$(printf "%02d" $hour):$(printf "%02d" $min):$(printf "%02d" $sec)\033[0K\r"
                                 let "sec=sec-1"
                                 sleep 1
                         done
                         sec=59
                         let "min=min-1"
                 done
                 min=59
                 let "hour=hour-1"
         done
echo -e "${RESET}"
tput cnorm

```

---

### Post by HermanAB on 2022-08-25
There are special tools for prettyfying scripts. For example Zenity: [https://www.aeronetworks.ca/2015/09/?m=1](https://www.aeronetworks.ca/2015/09/?m=1)
See also https://man.archlinux.org/man/zenity.1.en

---

### Post by raleigh3 on 2022-08-25
Thanks for your help.

This is what I ended up with.

```
#!/bin/bash
# Much help from https://ubuntu-mate.community
# tkn, pavlos_kairus, and charles-nix
#
#  Timer that counts down and displays a message
#
soundfile="/usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3"

#clear
#amixer -D pulse sset Master 50% > /dev/null 2>&1
if [ -f "$soundfile" ];
then
     echo "Soundfile is present."
else
  echo -e "File $soundfile does NOT exist.\n\nProgram will now exit.\n"
  exit
fi
sleep 2
#clear

# Below, I cleaned it up a bit by using a  "here document"

[ -z "$2" ] && {
echo 
echo -e "   Error!! No time value given and/or message specified !!"
echo
echo -e "   Alarm Program 2022"
echo
echo -e "   alarm.sh [time value in seconds] Message in double Quotes"; 
echo -e "   alarm 5m   = 5 minute alarm"
echo -e "   alarm 5h   = 5 hour alarm"
echo -e "   alarm 5d   = 5 day alarm"
echo -e "   alarm 1.5m = 1 minute 30 seconds alarm"
echo 
echo -e "   alarm.sh 1m "\"Tea is ready."\""  

echo 
exit 1; }

# alternative way to do colors
Reset=$( tput sgr0    ) ; Bl=$( tput blink   ) ; Gr=$( tput setaf 2 )

echo  -e "${Gr}${Bl}TIMER COUNTING DOWN to $1${Reset}"


# countdown display
# below is the part you are interested in
# it replaces your "sleep" command


#this converts days,hours,months to seconds
case "$1" in
*d ) fact=86400 ;;
*h ) fact=3600  ;;
*m ) fact=60    ;;
*  ) fact=1     ;;
esac
(( period = ${1/[a-z]/} * fact ))


#this calculates the endtime based on 'now'
start=$( date +"%s" ) ; (( finish = start + period ))


# this is the counter,  based around charles-nix's counter format idea 
while (( period >= 0 ))
do
       echo -ne "$(date -u --date @${period} +%H:%M:%S)\t\t\r";
       (( period = finish - $( date +%s ) )) 2>/dev/null
done	    	 


# Fade-in process:
#you used curly brackets but you probably wanted  parenthesis
(
    for ((volume = 35; volume <= 40; volume += 2)); do
        amixer -D pulse sset Master ${volume}% > /dev/null
        sleep .5
    done
) &

cvlc --play-and-exit "$soundfile" &> /dev/null
clear
echo $2 > /home/andy/Downloads/test.txt
gxmessage -geometry 1100x100 -fg red -font 'sans 30' -timeout 3 -file /home/andy/Downloads/test.txt
rm /home/andy/Downloads/test.txt
```

---

