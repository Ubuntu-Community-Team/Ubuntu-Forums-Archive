---
title: "How does one get steam game running in x screen 1"
date: 2012-12-16
forum: General Help
---

### Post by milesnorth on 2012-12-16
Trine 2 runs fine on display 0.  How does one get it to run on the  projector which is display 1?  I'm not a script writer but the following  code starts Trine 2 on display 0.
```
#!/bin/sh
# Run Trine 2 game on display :0.1.

# put the mouse to display 1.
`xwit $ARGS -root -warp 520 1080`

cd "/home/theatre/.steam/steam/SteamApps/common/trine 2"

export DISPLAY=:0.1
sh ./bin/trine2_bin_starter.sh

# put the mouse back.
`xwit $ARGS -root -warp 520 540`
```I'm running the separate x screen option under nvidia x server settings in Kubuntu 12.04. Not quite sure what I'm doing, hints greatly needed.  Thanks

---

### Post by BicyclerBoy on 2012-12-17
Looks a little familiar..

I would place the "export DISPLAY=:0.1" at the top (first non commented line)

You have to set ARGS to something..
ARGS="-display :0.1"

The 2nd fn call of "xwit" is not going to do anything for you unless you *change*
ARGS="-display :0.0"
so don't bother with variable substitution, just use
`xwit -display :0.0 -root -warp 520 540`

Not sure what "trine2_bin_starter.sh" is going to do?
It may ignore the DISPLAY env variable.
I have the HumbleBundle non-steam Trine, but not installed on the right PC..

---

### Post by milesnorth on 2012-12-18
Cleaned up the script using your suggestions.  
```
#!/bin/sh
# Run Trine 2 game on display :0.1.
export DISPLAY=:0.1

# put the mouse to display 1.
`xwit -display :0.1 -root -warp 520 1080`

# move to required pwd and start steam coded script to start trine 2.
cd "/home/theatre/.steam/steam/SteamApps/common/trine 2"
sh ./bin/trine2_bin_starter.sh

# put the mouse back to display 0.
`xwit -display :0.0 -root -warp 520 540`
```It still starts trine on display 0, so you're right about ignoring the DISPLAY env variable.  
The steam script at ./bin/trine2_bin_starter.sh follows:
```
#!/bin/sh

### Start the actual Trine 2 game application
### This should normally get run by the Trine 2 launcher, but you can
### run this directly too, should you want to skip the launcher.
### (Notice, that the working directory needs to be the parent directory)

if [ -f ./bin/trine2_linux_32bit ]; then
    :
else
    echo "\nYou are attempting to run the trine2_bin_starter.sh directly."
    echo "You should probably run the trine2.sh located at the parent directory instead."
    echo "If you wish to run this script directly, you'll have to have"
    echo "the parent directory as the working directory.\n"
    exit 1
fi

### Notice, by default, we set the library path to use the specific provided
### library versions (since they are tested to work)
### Generally, you should be able to use any compatible versions of these
### libraries as well, provided that you have them installed on your system.
### Any library versions other than the provided ones are totally untested
### with the game though.
if [ -n "$LD_LIBRARY_PATH" ]; then
    # Note, this may end up adding the library path to the env even
    # though it may have already been previously added by trine2.sh.
    # Having a duplicate of this should not break anything though.
        export LD_LIBRARY_PATH="./lib/lib32:$LD_LIBRARY_PATH"
else
        export LD_LIBRARY_PATH=./lib/lib32
fi

### Query the display size
### This logic is placed here and passed as a parameter so that users
### experiencing issues with dual monitor setups, etc. may change the logic
### if it is necessary.
### Notice, there are also the ForceFullscreenWidth and ForceFullscreenHeight
### values in the .frozenbyte/Trine2/options.txt which are something
### you may want to normally change, instead of changing this.
FB_FULLSCREEN_WIDTH=`xwininfo -root | grep -F "Width" | cut -d : -f 2 | cut -d " " -f 2`
FB_FULLSCREEN_HEIGHT=`xwininfo -root | grep -F "Height" | cut -d : -f 2 | cut -d " " -f 2`


### Start the actual game
### This starts the game without any stdin/out, thus, if you need to debug
### those, you'll want to run this without the "nohup" and the redirection
### stuff following following the binary.

nohup ./bin/trine2_linux_32bit "-RenderingModule:DetectedFullscreenWidth=$FB_FULLSCREEN_WIDTH" "-RenderingModule:DetectedFullscreenHeight=$FB_FULLSCREEN_HEIGHT" >/dev/null &


```Not quite sure how or if the nohup command can start trine in display 1.  But the goal for my boys is to get games running on the 14 ft diagonal screen they built for the Mythtv home theatre.  Thanks for any more insights.

---

### Post by BicyclerBoy on 2012-12-18
The export DISPLAY env var is visible in the trine launcher script..
Would have to determine other trine cmd line opts..

This needs changing so you get size of display 1 & not 0:
xwininfo -root
xwininfo -root -display :0.1
but I doubt this is going to fix the original problem..

Should make no difference but could try:
export DISPLAY=":0.1"

Sad that multiple displays are mentioned in the launcher script & yet there is nothing to get off primary.

What's in the file: ?
.frozenbyte/Trine2/options.txt

---

### Post by milesnorth on 2012-12-19
> **BicyclerBoy said:**
> 
Sad that multiple displays are mentioned in the launcher script & yet there is nothing to get off primary.

Thanks for your tweaks.  Gave them a try in my script and the trine2_bin_starter.sh file.  Also started the steam client on display 1 and fired up trine.  Looked for launch options for trine in the steam client. Looked in the options.txt file for trine.  Nothing gives me any indication of how to start trine or steam games on display 1.  I might have to just live with my ignorance for awhile and see what comes along.  Hope Steam can work on this frustration factor for HTPC systems.

---

### Post by BicyclerBoy on 2012-12-20
The problem is with "trine".
Well behaved apps recognise the DISPLAY variable..

Maybe the problem is that "separate X screens" has become a fringe use case.
The unity desktop project seems to think so.

AFAICT nVidia video cards set the primary screen based on VGA>DVI>HDMI.

Some display drivers allow you to change the primary display.
xrandr --output VGA-0 --primary
rrandr could be better with nVidia driver

The order of the displays/devices in xorg.conf seems to effect the primary desktop.

My HTPC posts on TV screen (VGA) & has primary desktop on small DVI because of the xorg.conf sequence..

---

### Post by milesnorth on 2012-12-22
> **BicyclerBoy said:**
> 
Some display drivers allow you to change the primary display.
xrandr --output VGA-0 --primary
rrandr could be better with nVidia driver
xrander from display 0 lists DVI-I-3
xrander from display 1 lists DVI-I-2

from display 0 I tried the following commands:
```
$ $ xrandr -q
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
.....
$ xrandr --output DVI-I-2 --primary
warning: output DVI-I-2 not found; ignoring
```System Settings>Display and Monitor> shows only the DVI-I-3 output and not the DVI-I-2 projector output.

Does nvidia not allow kde  to see both the DVI-I-3 and DVI-I-2 outputs concurrently?
Does nvidia not allow primary display swapping?
Does KDE not allow this behaviour?
How does steam interpret all this dual monitor madness?  
I'm a bit out of my understanding here.

Would a utility like Disper help manage dual monitors better?

I noticed that display management in KDE is considered a problem: [http://www.progdan.cz/2012/09/display-management-in-kde/](http://www.progdan.cz/2012/09/display-management-in-kde/)
 
Haven't looked at rrandr.

---

### Post by BicyclerBoy on 2012-12-22
The gnome display tool has never worked with proprietary drivers.
This situation might have changed with the latest nVidia driver.

YMMV xrandr has never worked very well with nVidia, works good with intel driver.
There was a comment in nvidia forums or phoronix that latest driver works with xrandr.

xrandr should be showing all attached screens (:0.0 & :0.1)

The Unity desktop & separate X screens did not work the last time I tried.
The unity works with twinview which is sub-optimal for HTPC..
Kwin is prob the same..

I think the really problem is X server & the support for multi-displays on same desktop. (Xorg xinerama which is not usable).

I would use
sudo nvidia-xconfig or nvidia-settings to create/save setup to /etc/X11/xorg.conf file.
Then we fiddle the order of the device sections..

My /etc/X11/xorg.conf lists device 1 & screen 1 first & this makes it primary.

xrandr --output LVDS1 --primary
- works okay here on intel..
But with nVidia separate X screens xrandr is hopeless.
For e.g. from display :0.0..
xrandr -display :0.1 --prop 
- returns info but with no display label

---

