---
title: "Need help changing resolution out of suspend because graphics look distorted after."
date: 2018-03-11
forum: General Help
---

### Post by wdcook87 on 2018-03-11
I posted in the new user forums about my pc having very distorted graphics on my old optiplex 320 with pent D 3.2, 1 gig ram and HD 6450 video card after coming out of suspend %50 of the time.  After trying a couple different drivers I was unable to resolve the root problem but after some suggestions realized that I could change the resolution after the problem occoured and change it back and it would go back to normal.  So now I'm just looking for a way to make the screen just change resolution and then revert back after suspend unless anyone has any other suggestions for lubuntu 16.04
[ATTACH=CONFIG]278905[/ATTACH][ATTACH=CONFIG]278906[/ATTACH]

---

### Post by monkeybrain20122 on 2018-03-11
I just post another reply in your old thread.Maybe this will give more info to what you want to achieve

[https://ubuntuforums.org/showthread.php?t=2386603&page=2](https://ubuntuforums.org/showthread.php?t=2386603&page=2)
> 
The workaround suggested above shouldn't be too hard to implement : you  need two ingredients 1) commands to change resolution using xrandr ,  write in a bash script, make it executable and put it somewhere in your  $HOME (say, $HOME/bin or $HOME/Scripts) , you can find those commands  online. Test if the script works by running it in the terminal (or right  click if you set in File Manager Preference to ask when click on  executable text files), then go to step 2) Write another script to call  the first script when computer awakes from suspension, put it in  /lib/systemd/system-sleep, use the template 

 	Code:
 	#!/bin/bash

set -e

if [ "$2" = "suspend" ] || [ "$2" = "hybrid-sleep" ]; then
    case "$1" in
        pre) true ;;
        post) sleep 1 && **/path/to/first/script** ;;
    esac
fi 
Now you may need something in the first script to connect to the x-server along the line of #6 in [https://ubuntuforums.org/showthread....1#post13721671]("https://ubuntuforums.org/showthread.php?t=2380045&p=13721671#post13721671").
You may need to experiment a bit.


**EDITED**: Before doing all these, maybe should try a different kernel, that may fix your problem

See the steps in post #16 of this thread [https://ubuntuforums.org/showthread....2386359&page=2]("https://ubuntuforums.org/showthread.php?t=2386359&page=2")


What is needed here is the first script, to change resolution (OP has to say to what) and in such a way that it can be invoked by the second script.

---

