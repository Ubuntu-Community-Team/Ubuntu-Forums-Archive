---
title: "Can't get a video to play"
date: 2006-08-26
forum: General Help
---

### Post by JimS on 2006-08-26
...
I can't get this video to play.

[http://www.nationx.dk/coats/](http://www.nationx.dk/coats/)

It works in Windoz Firefox, but not in Breazy or Dapper.

Thanks in advance.
...

---

### Post by scxtt on 2006-08-26
```
<object 
       classid="CLSID:22d6f312-b0f6-11d0-94ab-0080c74c7e95"
       codebase="http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab#Version=6,4,7,1112"
       id="wmp" 
       type="application/x-oleobject" 
       width="480" 
       height="414" 
       standby="Loading Microsoft Windows Media Player components...">
       <param NAME="Filename" VALUE="coats.wmv">
       <param NAME="Volume" VALUE="0">
	          <embed TYPE="video/x-ms-asf-plugin"
	            PLUGINSPAGE="http://www.microsoft.com/Windows/Downloads/Contents/Products/MediaPlayer/" 
         SRC="coats.wmv"
	            name="wmp" 
	            SHOWCONTROLS="1" 
	            SHOWDISPLAY="0" 
	            SHOWSTATUSBAR="1" 
	            autosize="1" 
	            autostart="1" 
	            width="480" 
	            height="414" 
	            displaybackcolor="black">
	          </embed>
     </object>
```you need to install windows codecs and something like mplayer-mozilla to play it via your browser ...

---

### Post by JimS on 2006-08-26
...
I have been able to play other wmv files,
so I think I have the necessary codecs.
My Firefox in Breasy is v1.0.8.
Maybe the latest Firefox would play it.
I see mplayer ext. are available for v. newer than mine.
I will try to get the seperate wmv file from its Danish website.
My Danish is very weak.  Jeg forstå meget lidt dansk.
I'm sure I can play it as a file in Breasy.
Also I'll work on Dapper in my notebook pc.
This week I spilled a bit of coffee on my notebook
and a few drops ran into a speaker.
No harm done, but after 40 years on a computer keyboard,
this is my first accident with food or drink.
I must be getting old!! 
I would like some explaination of the code you gave me.
I see mention of activex, so maybe that is an issue.
Seems no one in Linux land has yet to write a Linux
version of activex.  Maybe I wrong here.
Anyway thanks for your reply.
Have a good weekend.
...

---

### Post by reclusivemonkey on 2006-08-28
> **JimS said:**
> ...
I can't get this video to play.

[http://www.nationx.dk/coats/](http://www.nationx.dk/coats/)

It works in Windoz Firefox, but not in Breazy or Dapper.

Thanks in advance.
...

Works fine for me in Dapper Firefox with MPlayer plugin.

---

### Post by JimS on 2006-08-28
...
I loaded the Mozilla Mplayer plugin and it works on my Epiphany web browser.

Thanks
...

---

