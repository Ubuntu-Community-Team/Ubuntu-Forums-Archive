---
title: "Can I record video streams?"
date: 2007-01-30
forum: General Help
---

### Post by dnccnd on 2007-01-30
Hallo!

I have read some threads about video ripping but I am not quite sure about how to do this. I saw that some people suggest either mencoder or streamripper. I can see in Synaptic that both applications are installed on my system, but I don't know how to run and use them! I tried through terminal but it doesn't help.

I would like to record streams from this page:
[http://www.vicfirth.com/education/beginner_lessons/INTRODUCTION.html](http://www.vicfirth.com/education/beginner_lessons/INTRODUCTION.html)
in order to see the videos when I am not online.
The videos are opened in separete windows through javascript commands.

Any idea???

Thanks a lot!

---

### Post by schilcha on 2007-01-30
It seems that they obfuscate the actual url of the movie-files quite a bit: Here's a quick approach, that worked on my installation:
once the movie starts playing, right-click the movie and select "copy location". 
This will copy the path to the movie in the browser's cache to the clipboard.
Afterwards copy the file from the cache-directory to wherever you like.

If that does not work, you can try to track down the movies true url by inspecting the web-page's source and follow the references therein until you find the url at last. I did it for one of them, which ulitmatly is [http://www.vicfirth.com/education/beginner_lessons/01_introLQ.mov](http://www.vicfirth.com/education/beginner_lessons/01_introLQ.mov). Once you have the url, use something like wget to download the file.

Good Luck!

---

### Post by dnccnd on 2007-01-31
Thanks a lot for your help!
The first method doesn't work, I don't get anything when I right-click on the video.
I tried with the source text, but even there I couldn't find the line where the link is given. I am not an expert in HTML, but I searched for the link you gave me both in the source text of the page with the various links (the page I gave in my first message) and in the source text of the small pop-up window of the single video... and didn't find it.
Can you maybe explain me how you found the link?
Thanks!

---

### Post by dnccnd on 2007-01-31
Ok. I found out!
I opened the page info window and there Ican find the name of the file, therefore I can retrace the url.
Thanks a lot!

---

### Post by schilcha on 2007-01-31
I'll try to recall, what I did yesterday...

1) (you did that already) take a note of the address of the page displayed in the small window via the page-info window. You can skip the name of the html-file (i.e. everything from the last dash "/" to the end)
2) Have a look at the page source (just hit ctrl-u when the small window is open)
3) close to the end of the html-code is an iframe-tag (iframe src="xxx" ...). Take that xxx (everything within the double quotes) and append it to the address you noted in step 1.
4) now you have the address of the page actually displaying the move.
5) enter (copy) it to the browser's address-bar and press enter -> firefox automagically removes all those relative-path-directives ("../") and displays the more-or-less-easily readable url (no more digits-gone-wild address)
6) look at the source of thap page again (ctrl-u) and find the line containing "QT_WriteOBJECT_XHTML('01_introLQ.mov'...". This is a javascript-function that'll swoosh up the movie. The name of the movie-file is the first parameter enclosed in single quotes (in my case '01_introLQ.mov'.
7) finally remove the filename from the address in the address-bar (again everything from the last dash to the end) and substitute it with the name of the movie-file from step 6. Now you've got the complete url to the movie
8) enter the movie's url in the address-bar and watch the movie. Once you're shure it has arrived completely at you computer, you can choose "save page as" from the file-menu and save the movie locally. Alternatively you can obtain the movie by any other method, since the url is the key...

Good luck!

---

