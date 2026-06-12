---
title: "a strange condition on X - is there a full display magnifier?"
date: 2019-10-14
forum: General Help
---

### Post by Skaperen on 2019-10-14
this happened just once, and i don't what feature this might be and how it got enabled.  i later rebooted again and this strange condition did not come back.  just before dinner i rebooted to do an upgrade, but i didn't have enough time.  i logged in 4 users, one of which is the digital clock display user.  dinner was earlier than usual, tonight.  as usual, i left the computer running on the clock display.  after dinner, i noticed the right side of the clock was cut off at the edge and there was no xfce panel being display. when i got back to the computer and turned the mouse back on, i was planning to first see what was up with the panel being gone or covered by the clock window.  instead, as i moved the mouse around the contents on the screen also moved slowly in the opposite direction.  it was still working with a 1920x1080 buffer as far as a few programs could see.  the monitor was getting a subset of the 1920x1080.  it looked at least 90%.  fonts did look larger.  i could find out the buffer size (1920x1080) but i could not find a tool that would reveal what X thought the display size is (the video it was sending out to the monitor).  i switched user among the 4 users i had logged in.  this only affected 2 of the users.  the other 2 were normal.  their screens did not move around.

is this some kind of magnify feature that i don't know about?  it could be nice to use if i had control over it, especially if i can go back to normal when done.  i'm wondering how i might have engaged that.  i find nothing suggestive in the keyboard shortcuts or list of installed packages. if this was a magnifier is was doing only about a 10% increase.  the difference, unlike xmag, is that it was magnifying the whole screen.  googling for this finds such a feature for all popular systems, with it being built-in on Mac OS X.  what is not clear is whether these are window (like xmag) magnifiers or full screen magnifiers (like what i effectively had).  i tried scanning /usr but grepping for "magn" has no useful results and "mag" has too many to read (5943) because of so many names with word like "image".

i am particularly curious how i could have accidentally enabled in for 2 users.

---

### Post by Skaperen on 2019-10-15
i found the feature in xfce ... [COLOR=#800080][FONT=arial narrow]**alt+mouse scroll**[/FONT][/COLOR] zooms the whole screen in and out ... nice

---

### Post by Holger_Gehrke on 2019-10-15
Yeah, it's a new(-ish) feature in XFCE 4.11 (or so), so it's been there for the last three or four years. Found out about it a few days *after* getting my first pair of reading glasses a few months ago.

If you want the old behaviour (alt+scrollwheel on titlebar of a window changes it's transparency) back, you can set the property 'zoom_desktop' in the channel xfwm4 of xfconf to false either using xfce4-settings-editor or with
```

xfconf-query -c xfwm4 -p /general/zoom_desktop --set false

```
Might even be possible to write a script to toggle between the two states and assign it to a key ...

Holger

---

### Post by Skaperen on 2019-10-15
i don't think i need the old feature.  i may, some day, look for the zoom source code to see if i can change it to not move the view when the mouse moves within the area being viewed.

---

### Post by Skaperen on 2019-10-16
if i can change the way mouse movement works ... not move viewed portion until the point hits the edge, than drag the view as the mouse tries to move the pointer past the edge ... then it could be useful, in some cases, to run X with a buffer even larger than the video display, with the viewed area the same size as the video display.

---

### Post by Holger_Gehrke on 2019-10-17
That's already possible with xrandr with the --fb and --panning options. Example
```

xrandr --output HDMI-0 --fb 3840x2160 --panning 3840x2160

```
gives me a moving "window" of 1920x1080 (display resolution) into a desktop of 3840x2160. There's several more optional parameters to '--panning' to control the panning behaviour.

Holger

---

### Post by Skaperen on 2019-10-17
does xrandr do this to only one instance of X?  i usually run several userids, each on their own X server, switched around with [COLOR=#0000cd][FONT=courier new]_**os.execvp('dm-tool',['dm-tool','switch-to-user',sys.argv[1]])**_[/FONT][/COLOR] (Python), via lightdm.

---

### Post by Skaperen on 2019-10-17
is that command correct?  i see "3840x2160" in it twice and "1920x1080" not at all.

---

### Post by Holger_Gehrke on 2019-10-18
re. #7:
AFAIK it should only affect the display it's connecting to, either set through the option '-d'  or '--display' or taken from '$DISPLAY'.

re. #8:
I probably phrased that badly. '--fb' defines the size of the framebuffer, '--panning' defines the area to move around in and they can be different. The sizes of the moving "window" is the resolution the display is set to, which on my machines is currently 1920x1080. If I changed resolution it wouldn't affect either the buffer or the panning area, so I could just as easily have a movable 1024x768 'window' in that buffer by using '--mode 1024x768'.

Holger

PS: while playing around with this I got into several situation where I couldn't come up with the right parameters to undo my changes. No need to panic if that happens, 'xfce4-display-settings' (either from the command-line or from 'Menu'->'Settings'->'Display Settings' will restore everything to it's normal state.

---

### Post by Skaperen on 2019-10-18
so, what does "--panning 3840x2160" do?

i going to set this up on one userid intend to watch 4K videos online.

---

### Post by Holger_Gehrke on 2019-10-18
It defines the area reachable by panning. There's a lot more parameters you can give after '--panning', reading the manual page for xrandr will tell you more.

And I'm not so sure about watching 4k video on a panning display ... the risk of not seeing something you want (or need) to see seems rather big. And I don't know if hardware acceleration of decoding will work with that ... 

The manual gives a nice example that might be of use in this experiment:
```

Have one small 1280x800 LVDS screen showing a small version of a huge 3200x2000 desktop, and have a big VGA screen display the surrounding of the mouse at normal size.
              xrandr --fb 3200x2000 --output LVDS --scale 2.5x2.5 --output VGA --pos 0x0 --panning 3200x2000+0+0/3200x2000+0+0/64/64/64/64

```

Holger

---

### Post by Skaperen on 2019-10-18
of course i will also watch the video in 2K (probably first).  watching in 4K will be to see certain detail.  what i will do is have a separate userid and X server set by xrandr.  then, right after watching the whole thing in 2K (HD), note the time and save the URL, switch to the other userid, fetch the URL, start the video in 4K (UHD), skip ahead to the noted time, and move the view to the interesting areas.  i'll probably use the shortcut keys a lot to replay that part of the video a few times.

---

### Post by Skaperen on 2019-10-19
various error messages i got
```

warning: output HDMI-0 not found; ignoring
warning: output LVDS not found; ignoring
warning: output VGA not found; ignoring

```

---

### Post by Holger_Gehrke on 2019-10-19
You obviously need to substitute the outputs you've actually got for the ones used in examples. To find out what your outputs are called run xrandr without any options or parameters. This shows an overview of the currently configured screen and all outputs including their possible and current configurations.

Holger

---

### Post by Skaperen on 2019-10-20
i don't know any video output names on this laptop.

---

### Post by Holger_Gehrke on 2019-10-20
> **Skaperen said:**
> i don't know any video output names on this laptop.

As I wrote in #14:
> To find out what your outputs are called run xrandr without any options or parameters.
example:
```

$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
**eDP** connected (normal left inverted right x axis y axis)
   1366x768      59.97 +
   1280x720      59.97  
   1152x768      59.95  
   1024x768      59.95  
   800x600       59.96  
   848x480       59.94  
   720x480       59.94  
   640x480       59.94  
**HDMI-0** connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08 
```
The parts I marked in bold are the names of the outputs on my system.

Holger

---

### Post by Skaperen on 2019-10-20
what is that a list of?  the sizes i can use?

---

### Post by Skaperen on 2019-10-20
the first few lines of my output are:```
lt2a/forums /home/forums 16> xrandr|head
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1920x1080     60.02*+  60.01    59.97    59.96    59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
lt2a/forums /home/forums 17>
```what does that one very first line mean?  that i can use any buffer size up to that limit?

i am very unfamiliar with the Linux/X GUI system and how it works.  where do these output names coming from?  i don't see anything in /dev that names them.  media and network device drivers seem to like to bypass the usual major/minor device codes.

---

### Post by Skaperen on 2019-10-20
i got it to work this time.  now i need to figure out how to get whatever needs to (maybe Xfce), to use the big buffer.

---

### Post by Skaperen on 2019-10-20
firefox took most of the 3840x2160 when i clicked maximize,  i went to youtube and started up a 4K video.  then i clicked full screen and it did take the full 3840x2160.  that was awesome being about to view any of 8294400 pixels, 2073600 at a time.  and since the limit appears to be 8192x8192, i can probably do 8K (7680x4320, 33134400 pixels).  8K would push my 4 cores to the max.  4K was using 133%.  lots of 4K laptops are on the market these days.  i expect to get one in a year or two.  i can't even see individual pixels in HD now.  UHD might not really be any better.  i wonder if people will buy it and if they do, will 8K really be a popular thing?  the only reason i'd want more resolution is to get finer text positioning for terminals, not to double the rows and columns. right now i typically have terminals at 172x44.  a few more rows might be nice, but 88 would be unreadable.

---

