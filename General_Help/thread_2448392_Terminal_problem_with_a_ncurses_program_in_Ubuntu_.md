---
title: "Terminal problem with a ncurses program in Ubuntu 20.04 OK in Ubuntu 18.04"
date: 2020-08-07
forum: General Help
---

### Post by adrian-h on 2020-08-07
This may be a bit hard to explain, but I use the terminal screen and scripting to monitor udp video streams and provide information about the stream.  This is to do with radio Amateur TV via a satellite.
Anyway one package, written by another person works well under Ubuntu18.04 but is not displaying in Ubuntu20.04.
This package uses ncurses to help it compile, so In both 18 and 20 I installed with sudo apt install libncurses5-dev all OK the program compiles.  When it comes to running the program it will not display in terminal, unless I start with a reduced window, then expand the window then I can reduce the window again where it is OK untill the package restarts.  If I start with a full terminal window I can never see the display even after reducing it's size and then going full size.

I have tried to show this with a few pictures as below.
The first shows the small terminal window on the left displaying a title but no data.
The second shows this window after being made full size by clicking maximize, then the data appears.
The third picture is the terminal window after clicking minimize to bring back to original.

If anyone can assist in finding out why this is happening and why the data in the terminal screen is not showing in the first place.  It may be I am missing something I have previously installed in 18. It may be a bug in a new version of gnome-terminal it could be anything but I would not know what to do/where to start.

Cheers

Adrian

---

### Post by TheFu on 2020-08-07
Maybe just work around the issue by wrapping the program start in a script that resizes the window as needed, twice?
```
#!/bin/bash

NAME="firefox"

#launch the program
$NAME   &

# Find the window using the Title Bar name, place in upper left corner and resize to 800x600
xdotool search --onlyvisible --desktop 0 --name $NAME  windowmove 0 0 windowsize --sync 800 600 windowactivate
sleep 0.5s
xdotool search --onlyvisible --desktop 0 --name $NAME  windowmove 0 0 windowsize --sync 600 800 windowactivate

```
Obviously, change firefox to the real program name. Tweaking the windowsize is expected. Some editors may wrap the lines, so be aware of that.

---

### Post by adrian-h on 2020-08-07
Hello TheFu

I will try that, it may take me a little time to understand what you are suggesting in the script above, but I put that down to an age thing!

Here is the script I am running in terminal, it does a few other things as well such as start a small window to quit all processes, the package that is not running correctly is started by the line:-

~/longmynd-status-curses/status &

The script constantly monitors for input on port 6789, in which case it will kill the status process and others and start afresh

I had tried adding a few lines of resize after but typically get a resize time out error.

```
#!/bin/bash
# Auto entry Freq & SR
resize -s 35 50 # resize the screen to take up less space
cd ~/longmynd
gnome-terminal --geometry 31x6+1000+0 -- ./quit & # Start routine to kill all
clear
# Routine to read Quicktune
echo "Listening port 6789"

netcat -ul 6789 | while read line
do

killall -q longmynd fake_read totem    # standard killall rem out what is not used in the next few lines
killall -q lmdisplay-v1        # Brians C prog
killall -q status         # Davids C prog
echo &#8220;$line&#8221;
freq=$( awk -F "," '{print $2}' <<< $line | awk -F "=" '{print $2}' )
sr=$( awk -F "," '{print $5}' <<< $line | awk -F "=" '{print $2}' )
lnb_offset=$( awk -F "," '{print $3}' <<< $line | awk -F "=" '{print $2}' )
#echo &#8220;$freq&#8221;        # Remove #'s to see frequencies from quicktune
#echo &#8220;$sr&#8221;
#echo &#8220;$lnb_offset&#8221;
# set frequency and symbolrate
freq2=$((freq - lnb_offset))
echo &#8220;Rx $freq with a symbolrate of $sr&#8221;
# Start Rx process
./longmynd -i 192.168.1.194 20000 $freq2 $sr & # Start LongMynd stream to pc port 20000

#  Options to be set.  Remove the leading # to activate 
# ----------------------------------------
#./fake_read &                      # The normal scrolling status display
# ----------------------------------------
#cat longmynd_main_status > /dev/null &   # This gives no status whatever
# ----------------------------------------
# This is for  Brians lmstatus-v1
#setterm -cursor off               # turn the curser off if wanted
#fifofile=longmynd_main_status
#if ! test -p $fifofile 
#then
#mkfifo $fifofile
#chmod 666 $fifofile
#fi
#./lmdisplay-v1 & 
# ----------------------------------------
# This is to use Davids status
~/longmynd-status-curses/status &
#resize -s 50 180
#resize -s 35 50
# ----------------------------------------
# Display option. Remove the leading # to activate, add # to 'rem' out if using as OBS media input
totem udp://0.0.0.0:20000/QO-100 &      # This gives a local display, could also use vlc
done
```


The package that does not work is Davids program that works with ncurses.

I wish I was better at scripting, but I basically have to learn each command and work on poke and hope.

For a link to the background information if it helps  [https://forum.batc.org.uk/viewtopic.php?f=101&t=6594](https://forum.batc.org.uk/viewtopic.php?f=101&t=6594) 

I will look to see if I can incorporate as a temp measure what you have suggested.

Many thanks

Adrian

---

### Post by TheFu on 2020-08-07
**xdotool** looks for the title in the window, so if that doesn't match the program it isn't important. The title just needs to be unique and a partial match.
The xdotool method is just like you grabbed the corner with a mouse and resized it.  But, there is a bug that once a window is maximized, then no more **xdotool windowsize** methods work.  If the only work-around is to maximize first, then you'll need to use **xdotool mousemove  click** commands instead.  Those are harder, since mouse inputs require x, y coordinates, not just through these events at active window xyz.

There are lots of ways to get mouse events and clicks.
**cnee --record --mouse | awk  '/7,4,0,0,1/ { system("xdotool getmouselocation") }'**
is one. It only prints the data when a mouse button is clicked.  You may be able to create a workable script using only cnee with many caveats. The exact location and size of the window on the desktop needs to be the same every run. Hassles.

---

### Post by adrian-h on 2020-08-07
As an aside, I had noticed that if the terminal screen size if maximised initially then resize will not work so I have set a profile to always start with a reduced window.

To make the messages appear on the screen I only have to widen the terminal screen by one column and it appears, it was just faster when trying to view things to click the top right maximize then minimize when trying to grab the windows with the mouse.

I have been trying to implement your idea but admit it is not finding name, so think I am loosing the plot and struggling.

Would you have any ideas on finding out what the problem is rather than trying a work around is there any logs I should be checking so I can report this better?

Adrian

---

### Post by TheFu on 2020-08-07
> **adrian-h said:**
>  
Would you have any ideas on finding out what the problem is rather than trying a work around is there any logs I should be checking so I can report this better?

[https://invisible-island.net/ncurses/ncurses.faq.html#handle_resize](https://invisible-island.net/ncurses/ncurses.faq.html#handle_resize)  seems related. Perhaps the programmer isn't handling resize events the way ncurses wants? Perhaps just not in the program startup code since it seems to handle it fine after any resize.

Whoever wrote the ncurses code had a terminal size in mind, probably to hold information you may not use/see. Use that size or something larger. I've never written any ncurses code, but use wicd-curses on my laptop when traveling to manage network connections. Most of my GUI programming was writing C++ with X11 clients. Sorry.    In X11, the minimal required window size is controlled by the layout manager and all the widgets that have to fit on the canvas being displayed.  I'd assume ncurses has a similar requirement, but don't know this for certain.

---

### Post by adrian-h on 2020-08-07
I will have a read of that link thank you.

It is probably worth a note that in ubuntu 18.04 one the resize has been done, this is before it starts any other processes there is no need to resize to get the data to show, this is only in Ubuntu 20.04.

I have noted different versions 
3.28.2 Using VTE version 0.52.2 +GNUTLS -PCRE2 for 18.04 and 
3.36.2 Using VTE version 0.60.3 +BIDI +GNUTLS +ICU +SYSTEMD for 20.04

So looks like a lot has changed.  The web page for terminal shows a method of debugging so I will see if I can get anything I could understand and possibly report on.

Adrian

---

### Post by TheFu on 2020-08-07
I'd guess wayland or X11 would matter more than most of those.

---

### Post by adrian-h on 2020-08-07
Well I can not even follow the debugging method on the web site for gnome-terminal.    This has got rather quickly passed my understanding of all things Linux.  I am thankful of your time and effort 'TheFu' but I would not like to get you frustrated with my constant questions, when in truth I just do not know enough to properly fault find.

I will go back to my 18.04 PC and continue running the scripts and programs on there, I will see check after applying each new update to the Ubuntu20 machine if things get fixed at some point.


Thanks again for your assistance.

Adrian

---

### Post by TheFu on 2020-08-07
Sometimes we have to wait until the developers move to a new release before we can. Forcing seldom works.  I have some software that won't support 20.04 until next year sometime, so I'm waiting and will probably wait a few months AFTER the new version is released so I'm not an alpha tester of the code.

---

