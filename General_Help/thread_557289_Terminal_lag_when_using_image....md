---
title: "Terminal lag when using image..."
date: 2007-09-22
forum: General Help
---

### Post by daicoden on 2007-09-22
Hi!

I recently tried to set up compiz on an AMD/ATI machine.  Absolutely miserable experience which availed an unusable desktop.  The only thing I wanted was to rotate my monitor 90 degrees clockwise.  But I have long since given up that dream.

After that I had to remove everything.  I used the package manager and I believe I succeeded.

I have used Ubuntu for a few years and have never had a problem using a background image.  I'm afraid I might have installed something/ removed something that might be critical for display.  The only symptoms i can find are in the terminal.  

When I first boot up gdm and open a terminal:
   The image the background is set to takes about a second to load.  While the image is loading I can see no text either.  If I switch between desktops or terminals the image takes just as long to reload again.  Even resizing the terminal causes major delay.

If I then go in and switch the image to a different one:
  Terminal works fine

Restart gdm:
   Same symptoms with new image...

Switch image back to original one...
   Works fine.

Close all terminals and reopen...
    Symptoms are back and now random, switching to a new image fixes the current terminal but all new ones made are now lagy.

Why is this happening?  It's like whatever the image is on boot it puts into some file that takes a long time to read, but this has never happened to me before?

Any ideas of what to look for, or a package that has compiz, emerald, or glx that might be necessary?

Thanks!

---

### Post by daicoden on 2007-09-22
I suppose I should not have made the subject terminal image problems...

Again, I'm worried that I might have removed some packages I shouldn't have because the symptoms were not present before.  Any ideas of what to run to check if things are ok with my system would be appreciated!

Thanks!

---

