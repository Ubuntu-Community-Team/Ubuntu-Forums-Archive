---
title: "Questions about second monitor"
date: 2006-12-26
forum: General Help
---

### Post by jimbob on 2006-12-26
I have just succeeded (by some miracle of fate) to generate an xorg.conf file that will run dual monitors on my system.

I have an Nvidia AGP card and an older Nvidia PCI card installed to do the job.

Everything works as expected except I am unable to bring up a second instance of Firefox on the other monitor.  It complains that FF is already running.  Why should this be so when it will start as many instances as I want on the first monitor?

Also, I am unable to create any icons on the second monitor - they pop up on the first monitor.  I guess this is to be expected since I guess it is really the same desktop except that it will let me duplicate anything I want on the upper and/or lower quick launch panels.

My question is is there any way to create a completely independent second desktop?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jimbob on 2007-01-02
** Bump **  ?

---

### Post by bodhi.zazen on 2007-01-02
What are you using now ? Twinview?

You will need to write an xorg.conf

Back up your current

See here for starters: [http://www.ubuntuforums.org/showthread.php?&t=240150](http://www.ubuntuforums.org/showthread.php?&t=240150)

---

### Post by earobinson on 2007-01-02
post your xorg file!

---

### Post by jimbob on 2007-01-03
I guess what I am using is what you would call twinview although my xorg file is home grown.

All I did was to generate a file using dpkg-reconfigure -phigh xserver-xorg with both nvidia cards and both monitors connected.

I then inserted my mouse section from my original xorg file and also specified the screen resolutions for each monitor.  

This works fine except for the two questions I asked in my original post.

Here is the xorg file:

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by bodhi.zazen on 2007-01-03
I think you are runing two separate monitors and not twinview.

Twinview is "one big monitor"

See these two links:

[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

As well as the link in my original post ....

---

