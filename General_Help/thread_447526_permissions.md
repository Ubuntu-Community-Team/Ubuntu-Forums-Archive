---
title: "permissions?"
date: 2007-05-18
forum: General Help
---

### Post by blazini on 2007-05-18
I'm totally new to linux and I'm trying to get a bunch of things working. Right now I have a problem with Mplayer. I get an error for video output device when trying to open a video file. The faq on the site says

"Q:	

I've just installed MPlayer. When I want to open a video file it causes a fatal error:

Error opening/initializing the selected video_out (-vo) device.

How can I solve my problem?
A:	

Just change your video output device. Issue the following command to get a list of available video output drivers:

mplayer -vo help

After you've chosen the correct video output driver, add it to your configuration file. Add

vo = selected_vo

to ~/.mplayer/config and/or

vo_driver = selected_vo

to ~/.mplayer/gui.conf "

I really can't figure out what to do, I tried a bunch of different commands in the terminal.  "mplayer -vo help" gives me a list of video output drivers but if I enter it the way it suggests I get command not found. How am I supposed to enter this?

---

### Post by zvacet on 2007-05-18
**preferences>video>x11**

If this not work for you select other one.

---

### Post by fanatik on 2007-05-18
Hi and welcome!

You just need to edit the file called  ```
~/.mplayer/config
```
so use whichever editor suits you, nano from a command line is friendly:

```
$ nano ~/.mplayer/config
```

then add in the line:

```
vo = selected_vo
```

hit Control+X to save and exit.

repeat for the other file.

Hope that's clear, if not, post back. :)

James.

---

### Post by blazini on 2007-05-18
Thanks for the replies. I get command not found using $ nano ~/.mplayer/config. I'm not sure about the instructions the Mplayer Faq gave, I don't think that file exists. I did find /etc/mplayer/mplayer.conf, which I'm assuming is the file, I can access it via the GUI and it has the text specifying the video output driver. I can't change the file in GUI because it needs root access. Trying any commands on it in Terminal come up as "permission dinied" even when accessing as root. I want to use Mplayer cuz a few other programs I am trying to get to work rely on it, plus I here it's the better media player.

---

### Post by taurus on 2007-05-18
```
gedit ~/.mplayer/gui.conf
```
Then, replace whatever driver for "vo_driver" (usually the second line) with "xv."

```
vo_driver = "xv"
```
Save it and restart MPlayer.

---

### Post by blazini on 2007-05-18
Hey, thanks alot, that worked. Maybe one day I'll be able to figure this stuff out for myself. What's weird is that the file that I mentioned before listed "XV" as the current driver. When I popped in that first command it showed up as "XMGA", switched it to "xv" and all is well. Now I just gotta get 32bit Firefox running on my freshly built 64bit machine. I'll make a new post for that tho.

---

