---
title: "DVD insertion issue"
date: 2005-10-30
forum: General Help
---

### Post by dtfinch on 2005-10-30
When I insert a DVD into a system running kubuntu breezy (freshly installed  yesterday), it takes it upon itself to launch 6 instances of Kaffeine and one instance of Konqueror to play it.

---

### Post by odrop on 2005-10-31
Yeah, I have about the same problem with DVD's as you do.  Except I only get one kaffiene and 1 konqueror. I also get another pop up dialog box asking what action I wish to take.  Kinda annoying.  Maybe someone out there has a solution as I haven't figured out one yet, but I'm hoping to sometime.

---

### Post by dtfinch on 2005-10-31
After getting DVD playback to work, it settled down to launching only one Kaffeine, and one Konqueror. Previously, it was like the first try to start Kaffeine didn't work right, so it decided to try several more times, leaving me with a half a dozen Kaffeine instances, all unable to actually play the DVD.

---

### Post by gingermark on 2005-10-31
This is due to the new ivman program. Apparently you can configure it by editing xml files, and future versions will have a gui so you can change the options a tad easier.

---

### Post by odrop on 2005-11-01
Well, thanks to gingermarks post, I figured out to stop making kaffeine try to play dvds I insert.  The file that needs editing is:

/etc/ivman/IvmConfigActions.xml

Near the bottum you'll find:
```

<!-- kaffeine for videos -->
   <ivm:Match name="hal.volume.disc.type" value="dvd_rom">
       <ivm:Option name="execdvd" value="pumount $hal.block.device$ &amp;&amp; /usr/bin/kaffeine dvd://1" />
   </ivm:Match>

```

Change that to:

```

<!-- kaffeine for videos -->
   <!-- <ivm:Match name="hal.volume.disc.type" value="dvd_rom">
       <ivm:Option name="execdvd" value="pumount $hal.block.device$ &amp;&amp; /usr/bin/kaffeine dvd://1" />
   </ivm:Match> -->

```

And it will at least stop kaffeine starting up.  I might go and disable most of this.  It isn't working 100% for me anyway.

---

