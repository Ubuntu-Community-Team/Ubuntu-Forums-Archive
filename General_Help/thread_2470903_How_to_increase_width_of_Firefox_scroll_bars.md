---
title: "How to increase width of Firefox scroll bars"
date: 2022-01-15
forum: General Help
---

### Post by Ralph L on 2022-01-15
I updated to firefox 96.0 on xubuntu 18.04 (the latest update). The scroll bars are now so narrow that I can barely use them. I have googled this, but can't find anything that I can understand.  Anybody know how I can increase the width of the scrollbars?????

---

### Post by &amp;KyT$0P# on 2022-01-15
Most of them can be by going to [FONT=Courier New]about:config[/FONT] and set [FONT=Courier New]widget.non-native-theme.scrollbar.size.override[/FONT] to the width in pixels you'd like.

---

### Post by Ralph L on 2022-01-16
Thank you Halogen2. That worked very well. 
I also did some further customization of the firefox scroll bar with the following settings:```
widget.non-native-theme.scrollbar.size.override to 16
widget.non-native-theme.gtk.scrollbar.thumb-size to .95
widget.non-native-theme.gtk.scrollbar.round-thumb to false
widget.non-native-theme.gtk.scrollbar.allow-buttons from false to true
```
The first widget setting above set the trough width; the second set the fraction of the trough width filled by the slider (thumb); the third squared the ends of the slider (thumb); the fourth enabled the stepper arrows at the ends of the trough.

To change the scrollbar slider (thumb) to light blue and trough to gray I edited, in the firefox profile folder, the file /chrome/userContent.css. My userContent.css file now contains:```
html
{
	scrollbar-color: rgb(102, 178, 255) lightgray;
}
```
The first color (using RGB notation) sets the slider (thumb) color. The second color parameter sets the trough color. The system accepts common colors such as red, green, etc. A lighter color can be attained by using lightred, lightgreen, etc. RGB notation can also be used. I obtained the RGB values from the website [https://www.bing.com/search?form=MOZLBR&pc=MOZI&q=rgb+color+wheel](https://www.bing.com/search?form=MOZLBR&pc=MOZI&q=rgb+color+wheel). I went to the second chart entitled RGB color codes and hovered over the color I wanted and read the values to get that color.

Incidentally for anyone who wants to change sizie and color of thunderbird scrollbars, see "How to change color of ALL Thunderbird scrollbars"

---

