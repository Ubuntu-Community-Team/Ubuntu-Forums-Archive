---
title: "Error : &quot;Could not initialise Xv output&quot; on Parole video player"
date: 2015-01-26
forum: General Help
---

### Post by elvis6 on 2015-01-26
Using Xubuntu and Parole Player, and whenever I set a video to "repeat", or add multiple videos to a playlist, I get the error message "could not initialise Xv output"

Is there a missing plug-in I can install from the Ubuntu Software Center, that will solve this ?

---

### Post by elvis6 on 2015-02-15
Still in need of a resolution to this

---

### Post by SeijiSensei on 2015-02-15
Try installing smplayer from the repositories and see if you get the same result.

---

### Post by elvis6 on 2015-02-16
> **SeijiSensei said:**
> Try installing smplayer from the repositories and see if you get the same result.

Okay, I am trying out SMPlayer as you suggested, but having a couple problems, if anyone can help with these.

1) When I add a Playlist, and then set it to Repeat, it only repeats the first file over and over, even though it shows the other files in the Playlist. But, of course, what I want, is for it to run through the whole Playlist and repeat them all.

2) I can't seem to manually advance to specific locations in a video file. In other words, when I click to a "forward location" in the video progress, it won't go there, as it does in every other media program I've used, but rather it actually goes back a few seconds.

---

### Post by SeijiSensei on 2015-02-17
Does that mean smplayer works with the xv driver?  You can control the driver in use by going to Options > Preferences > General and clicking the Video tab.

1) I've never used the repeat function so I can't help with that.

2) Clicking to various locations in the progress bar takes me to the correct location, both forward and back.  Is the content on your local hard drive or streaming from a network location?  

For smplayer support, visit [http://forum.smplayer.info/](http://forum.smplayer.info/).

---

### Post by elvis6 on 2015-02-23
> **SeijiSensei said:**
> Does that mean smplayer works with the xv driver?  You can control the driver in use by going to Options > Preferences > General and clicking the Video tab.

When I go to the tab you mentioned, it shows that xv is the current driver, with a long list of other options.
Is there another recommended driver, that you suggest switching to, to see if it resolves this ?

> **SeijiSensei said:**
> Clicking to various locations in the progress bar takes me to the  correct location, both forward and back.  Is the content on your local  hard drive or streaming from a network location?

The content is from the local hard drive.

---

