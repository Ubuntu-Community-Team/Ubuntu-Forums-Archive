---
title: "Burn DVD From video_ts.bup, .ifo, .vob"
date: 2007-12-17
forum: General Help
---

### Post by xluryan on 2007-12-17
I have the following files in my directory, and would like to know how to burn them to DVD. Help?

video_ts.bup
video_ts.ifo
video_ts.vob
vts_01_0.bup
vts_01_0.ifo
vts_01_0.vob
vts_01_1.vob
vts_01_2.vob
vts_01_3.vob
vts_01_4.vob
vts_02_0.bup
vts_02_0.ifo
vts_02_0.vob
vts_02_1.vob
vts_03_0.bup
vts_03_0.ifo
vts_03_1.vob
vts_04_0.bup
vts_04_0.ifo
vts_04_1.vob
vts_04_2.vob

---

### Post by ~LoKe on 2007-12-17
Hm...try this:
> mkisofs -dvd-video -o dvd.iso foldername/

So, if the folder containing those files is "Movie", it would look like this:
> mkisofs -dvd-video -o dvd.iso Movie/

That *should* do it.  Then you just simply have to burn the iso (CD image).

---

### Post by sonofusion82 on 2007-12-17
if you use k3b, you can just create a dvd video project and add the files into the project and burn away!

---

### Post by xluryan on 2007-12-17
Loke, I tried what you said and got this:

```

$ mkisofs -dvd-video -o dvd.iso tmp/
Setting input-charset to 'UTF-8' from locale.
mkisofs: Could not find correct 'VIDEO_TS' directory.
mkisofs: Unable to make a DVD-Video image.

```

Any ideas? I'd really like to keep this all command-line ;)

---

### Post by danwood76 on 2007-12-17
All of those files need to be in a folder called VIDEO_TS
and you need an empty directory in the base dir called AUDIO_TS aswell for completeness.

you then use the base directory as the file in the above example

---

### Post by mellowd on 2007-12-17
> **danwood76 said:**
> All of those files need to be in a folder called VIDEO_TS
and you need an empty directory in the base dir called AUDIO_TS aswell for completeness.

you then use the base directory as the file in the above example

so:

Base DIR -->> VIDEO_TS -->> DVD files here
                >> AUDIO_TS

Audio TS doesn't always have to be there. I've iso'd a vob folder without it and it worked perfectly.

Once this is done you'll have in iso file which you can then burn and stick in your DVD player

---

### Post by disturbedite on 2007-12-17
just do what sonofusion82 said.  you can just start a new dvd video project in k3b and plop those files right in the VIDEO_TS folder.

---

### Post by yabbies on 2007-12-17
```
makedvd -burn *your dvd_directory*
```

---

### Post by aonegodman on 2008-01-10
> **yabbies said:**
> ```
makedvd -burn *your dvd_directory*
```

Please continue with this advise as I got that part down, but makedvd will not -burn without including the additional info   -device /dev/????   (where to burn).

I can't identify the dvdrom device name where I placed a blank DVD-R disc.

I did  sudo fdisk -l (that's L) and it show only HD's not cdroms?  :confused:

---

### Post by danwood76 on 2008-01-11
try /dev/dvdrw

I normally create the ISO first (like post 2) and burn the ISO with the gnome burning tool.

regards,
Danny

---

### Post by aonegodman on 2008-01-11
I found the device name by opening k3d with the blank DVD in DVD drive. Mouseover the drive listed in K3d and it shows device name.

Thanks!

---

### Post by danwood76 on 2008-01-11
> **aonegodman said:**
> I found the device name by opening k3d with the blank DVD in DVD drive. Mouseover the drive listed in K3d and it shows device name.

Thanks!

Well done, glad you got it working!
Could you add the [SOLVED] tag to the thread title to help others.

regards,
Danny

---

