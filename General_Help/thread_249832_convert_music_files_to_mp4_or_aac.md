---
title: "convert music files to mp4 or aac"
date: 2006-09-03
forum: General Help
---

### Post by seshomaru samma on 2006-09-03
hi
i have a vodafone sharp 703shf mobile phone that would not play mp3 or ogg music files. I read somewhere that it would play mp4 and aac files. How can I convert my mp3 to mp4 or aac format?

---

### Post by ato on 2006-09-03
You can try nautilus-script-audio-convert.
sudo apt-get install nautilus-script-audio-convert

It works for me

---

### Post by seshomaru samma on 2006-09-03
Thanks ,
What do I do after I download the script?

---

### Post by &#12465;&#12452;&#12488; on 2006-09-03
Right-click on a file and choose to convert it.

---

### Post by seshomaru samma on 2006-09-03
mmmm
I don't have a 'convert' option when I right-click on a file....

---

### Post by arkangel on 2006-09-03
the script is installed in /usr/share/nautilus-scripts/ConvertAudioFile,

make a link to this file in your ~/gnome2/nautilus-scripts, type in a terminal  :

#cd  ~/.gnome2/nautilus-scripts
#ln -s /usr/share/nautilus-scripts/ConvertAudioFile .


then  you will have it in the right click menu

---

### Post by seshomaru samma on 2006-09-03
I suspected that , but didn't know how to do it...
thanks
Now when I try to convert a file it says I miss a codec 'lame'
:confused:

---

### Post by PriceChild on 2006-09-03
Have you installed the restricted formats from [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) ?

There is a special section towards the end about mp4s and aac.

---

### Post by seshomaru samma on 2006-09-04
thanks
i installed all possible codecs but it didn't work.
then installed 'lame' and now i can convert the files , except I can only convert them into WAV and not AAC......

---

### Post by arkangel on 2006-09-06
i dont remember   well but i think i use automatix to install that codec 

[www.getautomatix.com](www.getautomatix.com)

---

### Post by puppy on 2006-09-07
I hope you get it working - just to note that if you do convert the files they will lose some quality because of the conversion process itself... if they're already high quality mp3s (192kbps plus) that shouldn't be a problem but if they're lower than that you might find it introduces clipping etc into the music - I'm an audio snob myself so I record everything at 320kbps VBR anyways...  :mrgreen:

---

