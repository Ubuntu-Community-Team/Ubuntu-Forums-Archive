---
title: "file roller won't extract &quot;gz&quot; file"
date: 2016-12-03
forum: General Help
---

### Post by krgingerich01 on 2016-12-03
Cannot get file roller to extract a ".gz" file. Found a closed thread in this forum, from 2009, but it doesn't really offer much remedy, other than "try something else".
I am running Ubuntu 16.04 LTS (Dell 64bit i3 w/ssd & 20gb RAM)

---

### Post by mcduck on 2016-12-03
Does it give any error? Have you tried unzipping it from command line? Any errors there? Maybe try checking that it really is a gzip file with the "file" command?

---

### Post by krgingerich01 on 2016-12-03
There is no error msg. it just hangs-up on the progress bar, and does nothing. I have used the command line, with this command: gunzip retropie-4.1-rpi2_rpi3.img.gz  and again,
it begins the extraction and hangs there.
(This is a image file that I would flash on an sd-card, for the "Retro Pi" distro, on a raspberry pi 3.)

---

### Post by howefield on 2016-12-03
How long does it "hang" for ?

In my experience these image files do take quite a bit longer than you would expect to extract.

---

### Post by mcduck on 2016-12-03
If it just hangs without any error message, I would suspect the file you have is corrupted. The website for RetroPie has md5 checksum for the file, might be worth checking that (you can just run "md5sum *filename* in a terminal) to make sure nothing went wrong while downloading it.

---

### Post by krgingerich01 on 2016-12-03
Yes, I also thought this may be the case. I downloaded it twice, but I did not check the checksum. Thank's for the advice!

---

### Post by krgingerich01 on 2016-12-03
I waited for over 30min, and gave up. Do you think it would take longer than that? (with 20 GB of ram and an i3 ?)

---

### Post by mcduck on 2016-12-03
30 min sounds way too long, I bet even the Raspberry Pi 3 itself would uncompress that package in less time...

---

### Post by howefield on 2016-12-03
> **krgingerich01 said:**
> I waited for over 30min, and gave up. Do you think it would take longer than that? (with 20 GB of ram and an i3 ?)

No, nothing like that.

Just long enough to wonder if something was up.

The suggestion to checksum the download is a good one.

---

### Post by krgingerich01 on 2016-12-03
Yes, checksum is bad. 
Thank you for the help, you guys!

---

