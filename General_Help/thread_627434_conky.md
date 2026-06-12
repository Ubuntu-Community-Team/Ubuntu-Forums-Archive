---
title: "conky"
date: 2007-11-30
forum: General Help
---

### Post by billgoldberg on 2007-11-30
I didn't find any good explanation on how to (after installing from repo's in ubuntu 7.10) make conky appear on the top right side of the screen instead bottow left side.

Can anyone help me?

---

### Post by alphane on 2007-11-30
If you'd spent 5 mins on a search, you'd have your answer already.

[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

That thread is loaded with info.  Check out the screenshots, find one that has the positioning where you would like, and copy it.

I'm at work, and as such have no access to my conkyrc file to help you with specific commands.

If you edit your ~/.conkyrc file and fish out the following values (or something very similar)

x_offset 0
y_offset 0
position top_right

a combination of these will give you the result you require.

---

### Post by billgoldberg on 2007-11-30
Thanks, I did a search, but there was too much info on that page and didn't have the time to read through the whole thing.

---

### Post by CanonKen on 2007-12-01
This is mine and its set at bottom right
> # Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 70

To get it to be on top right edit the .conkyrc file 
Remove the # before the position you want, put a # before the unwanted options

---

### Post by RedSquirrel on 2007-12-01
The documentation on the conky website is helpful...

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

