---
title: "print screen resolution"
date: 2017-08-26
forum: General Help
---

### Post by seekertom on 2017-08-26
Ive asked this question on www, and believe it or not, there has been no answer. While many 'hot stuffs' have responded, none had an answer. 
"Where does print screen (ps) get the data it places on the clipboard?"

In the olden days, there was video memory (vm), either dedicated or shared, sometimes part of main memory, sometimes part of a separate video board. From my understanding, what you see on the monitor is stored temporarily in vid mem. Back then, ps just captured what was in ram at those vm locations. But what about now? Is the image still finding a home in vid mem?

Now, if the screen image is a jpeg file, say from a 10 mega pixel camera, is the whole file, full resolution, loaded into vm? and if I do a ps, will the clipboard be handed the full resolution file?

Heres the crux of my dilemma... If my crappy monitor is vga only, that 10 mp image will look like crap on the screen. Knowing that the pc wants to know what monitor I'm using, will it adjust the contents of vm to match the monitor resolution, or will vm contents still be full res and still hold the full 10 mp file, even tho it displays poorly? in the end, will a ps put onto the clipboard the dummed-down image as I see it on the crappy monitor, or will ps deliver the full 10 mp file-image to the clipboard?

In the end, if I have a hi-res picture that is displayed on my crappy monitor, and looks crappy there, and if I do a ps and send it to you who uses a super hi-res monitor, will that image from me look hi-res like my original 10 mp picture, or will it look crappy on your monitor, as on my crappy monitor?

Lots to consider, but can you answer my question? "Where does print screen (ps) get the data it places on the clipboard?"

thanks, seekertom ):P

Additional tests and experiments show this: I have an external monitor connected to my laptop. I do three prtscrns of the same subject: one, only lt screen enabled, two, both lt and ext mon enabled, and three, only ext mon enabled. When I examine properties of all three screen shot files, I find all are same size. I think this might indicate that what gets screen printed is the contents of video memory as available for display on the primary display, which contents are independent of the characteristics of the external monitor.
jes sayin'...

---

### Post by gordintoronto on 2017-08-27
I can't answer your specific question, but I can assure you that the resolution of print screen will be the resolution of your monitor. (I've pasted many print-screens into GIMP.)

Here's some trivia for you: the different flavors of Ubuntu have different print screen programs! I use Xubuntu; a Kubuntu user might give you a different answer.

---

### Post by seekertom on 2017-08-31
Thanks for the comeback. Have to wonder, if what you say is true, and I don 't doubt it, what about the situation where you have a high res external monitor connected to a low res laptop? I'm thinking info shown on both screens?.... if so, which screen gets the results of prtscrn?
st

---

### Post by gordintoronto on 2017-08-31
I'm not sure, but it would make sense that the screen which has the focus would be saved.

---

