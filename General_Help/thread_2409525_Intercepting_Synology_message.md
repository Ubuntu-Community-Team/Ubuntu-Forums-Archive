---
title: "Intercepting Synology message"
date: 2019-01-03
forum: General Help
---

### Post by GettingNowhere on 2019-01-03
Ubuntu 18.04
Mate Indicator Applet 1.20.0

Hi all.
I am writing a script to attempt to send files one by one to a Synology server 15 miles away.
The Synology Cloudstation app sits in the Indicator app and outputs a message onto the screen for a couple of seconds as shown below.

[IMG]https://www.dropbox.com/s/imb15e05glnicvy/cs.png?dl=1[/IMG]

Is there a way to intercept this message with a bash script to get it to send the next file.

I'm not asking for a fully blown script, as I already have one.
At the moment it just asks what the transfer rate is today (anything from 40K bits/sec to 200 k bits, depending on the weather - nothing can be done about that as the town does not have fast broadband). checks the file size and attempts to guess when it will complete before sending the next one.

Hit and miss at the best of times.
The file transfer is done at night when I am asleep, so I thought if there was an stdout, or whatever it's called that the script could monitor, I could make it much more reliable, and stay in bed.

Thanks.

---

### Post by dragonfly41 on 2019-01-03
I can think of one possible tool for this type of action.

There is a tool in Software Centre named **actiona** (you can find it in Synaptic search).

It runs automation actions (extension .ascr) on what is seen in the desktop.
In your example I would look for the icon with i and blue background.
Use the action "Find Image", then when it is found run another action which can be "Command" or "Detached Command".
You will have to run this in a loop. 

there is a command **actexec myscript.ascr** which removes the need for Gui.

---

### Post by GettingNowhere on 2019-01-03
Thanks for the reply.

It worked great!  until.....

It appears that the image shown in post 1 is not as reliable as it would seem.

When a relatively short file went through, Cloudstation didn't give the message.  Damn!

I thought we were on to a winner there.

(Also, both CPU's run at over 75% when waiting, possibly for hours, waiting for the image).

---

### Post by dragonfly41 on 2019-01-03
If searching for an image is not reliable you can search for other targets .. such as a window condition .. or even a block of black in the message. Sorry .. I read again .. and if Cloudstation does not even give a response then you have a problem.  Can you concatenate mp4 files to give a longer target period?

---

### Post by CatKiller on 2019-01-03
Trying to do image recognition seems like an incredibly convoluted way to do that.

The message needs to be sent to display the notification in the first place.

The transfer of the file is likely logged.

Both of those seem like much more sensible places to start.

---

### Post by dragonfly41 on 2019-01-03
Actually recognition works very well on a range of desktop automation tasks.
It can be useful in tutorials where you walk a user through a series of actions.
For the record here is another example ... [http://sikulix.com/](http://sikulix.com/)

However. if the location of the incoming message is known isn't there some"listen" or "watch" command looking for changes?

[COLOR=#b22222]**[edit]**[/COLOR]

Found reference to inotify here ...

[https://askubuntu.com/questions/819265/bash-script-to-monitor-file-change-and-execute-command](https://askubuntu.com/questions/819265/bash-script-to-monitor-file-change-and-execute-command)

---

### Post by GettingNowhere on 2019-01-03
I have to agree with CatKiller in that there is a log that can be displayed using the Cloudstation app, but I have no idea where it is kept.
By checking the last line every now and then for the file name, being transferred, it would solve the problem.

---

### Post by dragonfly41 on 2019-01-03
Can you use inotify to look through range of directories watching for incoming messages?

Or possibly a capture filter in wireshark looking at incoming messages.

---

### Post by GettingNowhere on 2019-01-03
I found the history log, but it's an sqlite file.
/home/me/.CloudStation/data/db/history.db
It certainly has the files and "action"s.  I'm guessing 17 is added, and 18 is deleted.

The date time number next to file 16.mkv (1546529564) stands for 2019-01-03 15:32:44 apparently (doesn't resolve in a spreadsheet).


So if I install inotify and check this sqlite file for an update that should do it?

No I won't. I've just looked at the modification date, and it was last month.
history.sqlite-wal (a binary file) looks good as it was modified at exactly the time of the last successful upload.

Actually, do I need Inotify, or could I just use zenity and the "(date)" function to test it?

history.sqlite:
[IMG]https://www.dropbox.com/s/r367347jun1t83k/4.png?dl=1[/IMG]

---

### Post by dragonfly41 on 2019-01-03
Well the earlier thread about usage of inotify indicates that you can try that with history.sqlite and history.sqlite-wal as the watched files.

I have an sqlite browser under Accessories .. DB Browser for SQLite .. which might help.

---

### Post by GettingNowhere on 2019-01-03
I went the "stat" way.

It works a treat.

Thanks.

```
#!/bin/bash
##
[COLOR=#0000ff]**histfile="/home/me/.CloudStation/data/db/history.sqlite-wal"**[/COLOR]
## Choose directories
cd ~/Downloads
d1="$(zenity  --file-selection --title="Bulk Move    Choose starting directory"  --directory)"
cd ~/CloudStation
d2="$(zenity  --file-selection --title="Bulk Move    Choose destination directory"  --directory)"
##
## This delays the start of the transfer, if there is already a file being processed.
start="$(zenity --entry --title="Bulk Move" --text="Start in how many minutes:")"
   if [ "$start" = "" ]; then
      startmin=1
        else 
        startmin=`echo "$start *60" | bc`
   fi
sleep $startmin
##
## Start the transfer, one file at a time
find "$d1" -maxdepth 1 -type f | sort -n | while IFS= read file; do
    ## Set the flag back to 0 for each file
    flag=0;
    ## The flag will be 0 until the file is moved
       while [ $flag -eq 0 ]; do
       ## Move the current file to $d2 and increment the counter, 
       ## using the file size to guess the time it will take
       mv -v "$file" "$d2" && flag=1;
       starttime=" Started "$(date +%H:%M)  
          if [ -z "$(ls -A "$d1")" ]; then
          zenity --info --text "Move Completed"
            else
              [COLOR=#0000ff][B]date=$(stat -c %y "$histfile")
              date2=$(stat -c %y "$histfile")
              while [ "$date2" = "$date" ]; do sleep 30; date2=$(stat -c %y "$histfile")[/B][/COLOR]
done | zenity --progress --text "${file##*/}   $starttime" --pulsate --auto-close --auto-kill &
# get zenity process id
PID_ZENITY=${!}
# get firstly created child process id, which is running all tasks
PID_CHILD=$(pgrep -o -P $$)
# loop to check that progress dialog has not been cancelled
while [ "$PID_ZENITY" != "" ]
do
  # get PID of all running tasks
  PID_TASKS=$(pgrep -d ' ' -P ${PID_CHILD})
  # check if zenity PID is still there (dialog box still open)
  PID_ZENITY=$(ps h -o pid --pid ${PID_ZENITY} | xargs)
  # sleep for 2 second
  sleep 2
done
# if some running tasks are still there, kill them
[ "${PID_TASKS}" != "" ] && kill -9 ${PID_TASKS}
fi
done
done

```

---

