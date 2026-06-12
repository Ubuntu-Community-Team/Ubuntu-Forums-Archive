---
title: "Video files no longer work!"
date: 2007-06-07
forum: General Help
---

### Post by darkmage77 on 2007-06-07
While trying to get all my video files to work, I have somehow caused all the video players I have to stop working. Movie Player closes an instant after the GUI pops up, as does Democracy after I choose a file from my collection; I get an error from Mplayer about "video out device not supported"; and VLC is not playing all my files correctly (mpegs are choppy and movs look like the old blacked out cable channels). 

I've installed most of the libs for all these players, including the w32 codecs and libdvdcss2. I've looked through all the logs and I don't see anything posting at the times these players act up.

---

### Post by eggdeng on 2007-06-07
What graphics card / drivers are you using?

---

### Post by darkmage77 on 2007-06-12
I have an ATI X1650 and I'm using fglrx 8.36.5.

---

### Post by jimbob on 2007-06-12
I think you can fix the Mplayer vo problem by right clicking on the player window, selecting the video tab and selecting X11 from the list of video out devices.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by eggdeng on 2007-06-13
You could try changing fglrx back to ati in your xorg.conf just to see if it's a problem with the driver.

---

