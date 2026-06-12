---
title: "trying to get gstreamer plugins"
date: 2008-06-12
forum: General Help
---

### Post by ceclauson on 2008-06-12
I'm trying to get the gstreamer plugins that my computer is telling me that I need in order to view this media file.  Let me start from the beginning.

The file is a file with a *.vro extension that, when double clicked, the OS tries to load in Totem Movie Player.  A dialog box appears that says that I don't have the codec to read the format, and asks me if I would like to get the codec.

A list of these appear with check boxes, with stars to indicate the popularity (I get three, gstreamer Extra, gstreamer ffmpeg, and gstreamer fluendo).  If I try to click the check box, I get a new dialog box that asks me to confirm the installation of restricted software.  I click "confirm".  It then tells me that a list of applications is not available, and asks me to press the "refresh" button to reload the list (it tells me that I need a working internet connection -- I have one).  So I press the reload button, a new dialog box appears, a bar moves quickly across the screen, and now I'm looking at the same list of plugins with checkboxes. If I try to check any of the boxes, the cycle repeats.

I don't think that the plugins actually installed, because the file still won't play, and when I try to play it, I again get the same list of plugins.  When I close the list, I get a message box that says "The playback of this movie requires a MPEG-2 System Stream demuxer plugin which is not installed."

I've gone through the installation of plugins before and they've gone smoothly, but not this one.  What's going on here?

---

### Post by mick222 on 2008-06-12
Open synaptic package mananger  in System-administration click on settings and make sure  all the boxes except for source code are ticked then install ubuntu restricted extras

---

### Post by ceclauson on 2008-06-19
I'm not sure how to do what you described, but I was able to fix the problem by enabling (more) repositories.  I forgot that they come deselected by default upon installation.

Thanks,
Cooper

---

### Post by Pjotr123 on 2008-06-19
Make sure you've got all codecs:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

This will ensure 100 % multimedia support.  :-)

---

