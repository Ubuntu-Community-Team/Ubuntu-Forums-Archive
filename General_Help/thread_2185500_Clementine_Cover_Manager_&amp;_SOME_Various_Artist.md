---
title: "Clementine Cover Manager &amp; SOME Various Artist Albums Have Multiple Entries"
date: 2013-11-02
forum: General Help
---

### Post by jamesisin on 2013-11-02
As I scroll through the covers in Clementine's Cover Manager, I notice that for some (but not all) mutli-artist albums there is an entry for each artist; while for other multi-artist albums it only lists that cover/album once.

Normally, for an album with a single artist the entry will look something like this "Bob Dylan - Blood on the Tracks".  For those cases where only a single entry exists for a multi-artist album (and this is my preference) the entry just looks like this "- Putumayo Presents: African Groove".  However, for some multi-artist albums I see several covers represented in the Cover Manager with each entry looking like a single-artist album (making me think Clementine thinks each one is a separate album).

I looked at several files from different examples in EasyTag and didn't see anything which might explain this behaviour.

Does anyone have any experience in this or any suggestions?


Thanks.

---

### Post by jamesisin on 2013-11-03
Anybody else using Clementine?

[http://jamesisin.com/a_high-tech_blech/index.php/2013/04/oh-my-darling-musica/](http://jamesisin.com/a_high-tech_blech/index.php/2013/04/oh-my-darling-musica/)

---

### Post by speartip on 2013-11-03
Hi i'm using Clementine, & "think" I know what the problem may be.
It's the way the Album has been tagged. Try using Exfalso. You can batch edit by highlighting all the tracks at once.
Make sure the artist & album are all the same. For eg. if you have a compilation album with various artists, call the artist "various" on every track, & make sure the album title is the same on every track, but add the performer tag for the real artist.
Also add the Tag "compilation" & set it's value to "1" on all the tracks.
After updating your library, your compilation tracks should all be together under 1 album cover.

---

### Post by jamesisin on 2013-11-04
You bring up some interesting ideas.

I used the tag editor within Clementine to seek differences and still found none worth reporting.

I re-tagged one album to see if EasyTag would nudge it into compliance.  Nada.

I opened ExFalso but couldn't find a way to have it display the current tags.  (I want to see exactly what the difference is before I make any changes.)  Do you know how to do that?

---

### Post by speartip on 2013-11-05
Hi, I used exfalso to change a Various Artists compilation album. There where 25 Album Covers in the cover manager. Once I made the Album title & Artist consistent across the 25 tracks, & did a library rescan, all the tracks then appeared under 1 cover in cover manager. If the Artists are all different they will each have there own cover.
 To use exfalso, open & navigate to the album folder in the top left hand column, highlight the album & all the songs appear in the bottom left column. Highlight all the songs, & see if the artist & album is consistent across all songs. If not that is your problem, and you can change them.

---

### Post by jamesisin on 2013-11-05
I have several highly similar albums where some are "split" and some are singular.  Both kinds have differing artists listed in the Artist tag (as would be expected for a various-artist type album).  To reinterate: I have many albums where each track lists a different artist and yet that album is displayed only once in the Cover Manager using the format mentioned in the OP ( - Album Title).

I'm trying to determine if those correctly displaying albums include your previously mentioned Compilation tag (this is not a tag EasyTag uses/knows).

I tried highlighting tracks within a folder (bottom-left pane and top-left pane respectively) in ExFalso.  I did not see anything populated in the right-hand pane.  I will try again tonight to see if I can sort it out.

Thanks for your input.

---

### Post by speartip on 2013-11-05
I think adding the compilation Tag will do the trick. In exfalso highlight all the tracks in an album, then click the add button to add a Tag.
You will have to type "compilation" manually (it is not a pre-existing tag) & add "1" to the value. Save & then do a library rescan in Clementine.
I have just tried this & it works.

---

### Post by jamesisin on 2013-11-06
After some testing it would appear that once I have edited tags using EasyTag, Ex Falso is no longer able to identify the files as taggable: it can see no tags and the Add button is grayed.  Ex Falso cannot see many of the taggable files which I need to manipulate.  Well, it can see the files.  It just can manipulate the tags.

---

### Post by jamesisin on 2013-11-06
I looked at several known-good compilations and they have neither the *compilation* nor the *albumartist* tag present.  I added compilation to a handful of compilation albums.  I'll report back later as to success or failure.

---

### Post by jamesisin on 2013-11-08
Ok.  Adding compilation = 1 (and doing a full library rescan) did consolidate the listings for that album in the Cover Manager.  Nonetheless I find myself strangely dissatisfied.

I want to understand why I have many albums without the compilation tag (and without an albumartist tag) which display a single entry in the Cover Manager.  Clearly those tags are not necessarily required but rather they can simulate the other condition well enough to satisfy the Cover Manager.

Maybe I'll submit a Clementine bug.

---

### Post by speartip on 2013-11-09
I don't think this is a Clementine issue. From what I've read tagging tracks isn't that straight forward. I even think i've seen somewhere that it can even depend on how & on what the original tracks were tagged.
All I know is that using exfalso always seems to give me the desired results, & Clementine seems to be the best player for correctly reading those tags (in linux anyway).
At least you've found a workaround:)

---

### Post by jamesisin on 2013-11-11
Ah, so more like a standards/compliance issue?  I wonder where I might put this in front of the correct folks then.  It would be good to put in a bug report to them so the specs can be improved (if that's what's at issue).

---

