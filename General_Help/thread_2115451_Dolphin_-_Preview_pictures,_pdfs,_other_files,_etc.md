---
title: "Dolphin - Preview pictures, pdfs, other files, etc?"
date: 2013-02-12
forum: General Help
---

### Post by Roasted on 2013-02-12
Hello friends! I recently began using Kubuntu 12.04 + KDE 4.10 pretty heavily. I'm getting used to it and loving it. The only thing is, Dolphin is not showing previews of my files. I still see an array of blank thumbnails when I'm really looking at a series of JPGs or PNGs, etc.

I went into the preview settings and adjusted everything I could, but it didn't make a difference as I suspected.

Also, a solid bonus would be obtaining the ability to preview videos as well. 

Any insight?

---

### Post by rotave on 2013-02-13
to preview videos in dolphin install "kffmpegthumbnailer" then go into dolphins settings and select video files. 
can't help with the other issue on pics etc not showing. however you might try going to view > preview in dolphin to see if that make a difference

---

### Post by SeijiSensei on 2013-02-13
Dolphin has always generated preview thumbnails if I press the Preview button.  It does take it a while to generate them all if you are looking at a directory with a lot of images.  Still you should start to see the images appear at the top of the listing and spread downward through the list.

All the generated thumbnails are placed in $HOME/.thumbnails.  Most of mine are in the "normal" subdirectory of .thumbnails.  What do you see in that directory?

---

### Post by Roasted on 2013-02-13
> **rotave said:**
> to preview videos in dolphin install "kffmpegthumbnailer" then go into dolphins settings and select video files. 
can't help with the other issue on pics etc not showing. however you might try going to view > preview in dolphin to see if that make a difference

I'll check that out - thanks!

> **SeijiSensei said:**
> Dolphin has always generated preview thumbnails if I press the Preview button.  It does take it a while to generate them all if you are looking at a directory with a lot of images.  Still you should start to see the images appear at the top of the listing and spread downward through the list.

All the generated thumbnails are placed in $HOME/.thumbnails.  Most of mine are in the "normal" subdirectory of .thumbnails.  What do you see in that directory?

You know, I didn't even realize this. I was indeed using "Preview", but the thing is I clicked it when I was in the top level of my home directory. I assume it stuck when I went layers deeper. So when I went from ~ to Pictures, the Preview became unset and I had to re-click it to enable previews again. Is there a way to get this to stick indefinitely for all directories recursively?

---

### Post by oldos2er on 2013-02-13
> **Roasted said:**
> Is there a way to get this to stick indefinitely for all directories recursively?

Open 'Configure Dolphin', General, Behavior, tick the box 'Use common properties for all folders'.

---

### Post by Roasted on 2013-02-13
Nice! All three of you nailed it. Appreciate the help fellas! Videos are previewing nicely, all pictures are coming up as visible thumbnails as I had hoped for, etc.

Semi off topic: I think it's official. I just might be hooked on KDE. Of course, I had to customize KDE to look like Unity since that layout is my happy place, but dang... this is one crazy nice desktop environment.

---

