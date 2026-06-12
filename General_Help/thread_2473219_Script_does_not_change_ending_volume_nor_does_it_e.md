---
title: "Script does not change ending volume nor does it exit the terminal"
date: 2022-03-28
forum: General Help
---

### Post by raleigh3 on 2022-03-28
This script mostly works ok.

But this script does not reset the volume to 30% nor does it exit the terminal.

What am I doing wrong?

```
soundfile="/usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3"
#originalVolume=$(amixer -D pulse get Master | grep -m 1 -o -E [[:digit:]]+%)
clear
amixer -D pulse sset Master 50% > /dev/null 2>&1
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
echo -e "   alarm.sh 1m "\"Take bread out of oven."\""  

echo 
exit 1; }
echo  -e "\033[32;5mTIMER COUNTING DOWN to $1 \033[0m"
sleep $1
{
    for ((volume = 35; volume <= 65; volume += 2)); do
        amixer -D pulse sset Master ${volume}% > /dev/null
        sleep .5
    done
} &

cvlc --play-and-exit "$soundfile" > /dev/null 2>&1
echo $2
#set back to original volume
amixer -D pulse sset Master %30

gxmessage -fg blue -font  'sans 20' -timeout 2 ' TIME IS UP !!'
exit


```

---

### Post by Holger_Gehrke on 2022-03-28
It should be '30%' not '%30' for the volume.

The exit problem is a bit more difficult. An 'exit' command exits the shell executing the script. The terminal is a separate thing from the shell (it's a program offering text only input and output channels for programs in a graphical environment). If you start a terminal without any further options it will run a shell. If you now start a script in this shell it will execute the script in a separate second shell. The end of the script ends this child process. So either start the script in a terminal of it's own ('gnome-terminal -- name-of-your-script parameters-for-your-script') that way the script ending will close that terminal or create a .desktop file for your script with the option to run it in a terminal ('Terminal=true') then run it from the GUI and it will open a terminal and show any output there and close it at the end. You could also run your script directly in the shell running in the terminal by using the 'source' command. That way there would be no child process for the script and an exit command would end the shell which would close the terminal.

Holger

---

