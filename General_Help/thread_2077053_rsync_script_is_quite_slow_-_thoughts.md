---
title: "rsync script is quite slow - thoughts?"
date: 2012-10-27
forum: General Help
---

### Post by p.s. on 2012-10-27
I've been using rsync to back up my home folder, my music, my movies, and my crontab to an external hard drive.

I made a similar little script with the intention of adding any new music I've put on my computer to an ipod (running rockbox).

The script currently looks like this:

rsync -avrz --delete /home/paul/Music/A /media/BOX
rsync -avrz --delete /home/paul/Music/B /media/BOX

It works, but when building the incremental file list it takes a really long time running through the appx. twenty-five gigs of files. In fact, it takes almost as long as it takes for me to just copy the same set of files from the hard drive to the ipod. Any way I can increase the speed here? I'm not seeing anything promising in the man pages.

---

### Post by The Cog on 2012-10-27
Try adding option ```
--modify-window=5
```. 
I've seen this suggested before. I believe that NTFS only stores timestamps with 2-second accuracy, so that files might appear to rsync to be modified at different times, which will then force a full read and bytewise compare which is time consuming.

---

### Post by p.s. on 2012-10-27
The Ipod's drive is formatted as FAT but it's definitely running faster. (Took about three minutes instead of half an hour.)

It's showing some "invalid argument" errors for files which are somesong.flac.ehf4 or anothersong.mp3.ey7r aren't transferring. I guess the .ehf4 is some sort of appellation from rsync?

---

### Post by p.s. on 2012-10-27
Figured out the failure to transfer. Scanned over the ones that didn't transfer and they all have wacky punctuation in their titles.

So, yeah, should be good to go. Thanks so much for the suggestion.

---

