---
title: "File browsers very slow, fades to grey"
date: 2015-01-28
forum: General Help
---

### Post by decrepit on 2015-01-28
I've just installed 14.04 alongside 12.04 in laptop and PC. The laptop is sweet but the PC has a problem.
When I installed 12 in the PC, I put /home on it's own partition, so I used the same partition for /home 14.04. 
Trouble is I called myself "Michael" in 12 and "Mike" in 14, so none of my data or settings came across.
I then selected everything in Michael and dropped it into "Mike". Must have been much too much stuff or something because nautlius just got this mess of text across it, and locked up.
Now Nautilus is very unreliable, at best it takes 20 seconds to do anything. If I click on home, the Nautilus window opens but it empty, will fade to grey and about 20 to 30 seconds later colour comes back with my files. If I then try to change from icon to list view, files dissapear, fades to grey and about 15seconds later the list view appears. When I hit the "x" button, it fades to grey and I get an "unresponding window"
It's also not holding the "list view" it always starts up in icon view.
I tried installing Thunar to see if that worked any better, but it's doing similar things.
I tried opening nautilus through a terminal to see if there was any info, but I got my cursor back as soon as nautilus opened.

Nautilus is still acting normally in 12.04, I can browse both homes without a problem.
I can also browse 14.04 from the terminal (although I'm very rusty at this).

I'm wondering if there's a solution to this, or should I just reinstall?

---

### Post by decrepit on 2015-01-28
OK some change in the situation, I found the files I'd dropped over in "Templates", started taking them out of templates and dropping them where they actually belonged. But much too slow in 14.04, so booted into 12.04 and finished the job.
Now when I booted back into 14.04 nautilus appears to be behaving normally.
Fingers crossed!

---

### Post by Impavidus on 2015-01-28
Nautilus must have been very busy doing things with the Templates folder. I don't know its exact purpose, I assume it's something I don't need. It seems that your problem is gone now.

In general, it's a bad idea to use the same home directory on two different releases of Ubuntu. The applications on 14.04 will save config files in that shared home directory, which cannot be read by the older versions of that software on 12.04. But if you call yourself Mike on one system and Michael on the other, you'll be fine.

---

### Post by decrepit on 2015-01-29
Thanks Impavidus, yes everything is still behaving itself.
I don't like inadvertently fixing things, it'd be nice to know just what was wrong, but I'm not going to try and recreate the problem so we can find out!

---

