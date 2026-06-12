---
title: "Internet radio and xmms"
date: 2005-05-03
forum: General Help
---

### Post by christooss on 2005-05-03
Hello

I am curently listening internet radio in xmms. But....

I got name of radio where author and name of the song should be.

What should I do.

P.S. I have this problems only with those ones which are NOT ogg format.

---

### Post by kvidell on 2005-05-04
For actual XMMS:
Right click on title of main window -> Options -> Preferences

in Audio I/O select "MPEG Layer 1/2/3 Player 1.2.10 [libmpg123.so]"
Click "Configure"
Select "Streaming" tab and near the bottom in "SHOUTcast/ICEcast:" enable the first option, "Enable SHOUT/Icecast title streaming"

for Beep-Media-Player:
Right Click title -> Preferences
Select "Plugins" group on the left.
Select "MPEG Audio Plugin", click Preferences.

Go to Streaming tab, enable same option as in the XMMS instructions.

Hope that does ya :)
- Kel

---

### Post by christooss on 2005-05-12
Thanks it really helped. This was the only thing that didn't worked. and now I am very very very happy. I think beacause I managed to get rid of all the problems. 

I am happy beacause now I can change my mother. From Win to Ubuntu.

I am happy beacause I reached 5 Cups of Ubuntu status  \\:D//

And I am happy beacause you guys here at ubuntuforums are great. You help alott of newbies to experience pure ubuntu. I was newbie searching for help and now I am shearing help to others. Maybe not here there are a lot of gurus here that are smarter than me. But in Slovenia there are many guys and girls who need help.

---

### Post by DutchLau on 2005-05-12
How did you get XMMS to stream without Streamtuner?


I can only get XMMS working with the Streamtuner and it doesn't contain my favorite radio station [http://www.slamfm.nl/stream/slamfm.pls](http://www.slamfm.nl/stream/slamfm.pls)  When I copy and paste this into the XMMS "open location" it gives me an error. What can I do to make it work with this .pls extention?

Thanks already,

DutchLau

---

### Post by christooss on 2005-05-12
I think you should get this radio in this form

[http://84.16.227.19:3026](http://84.16.227.19:3026)

IP + port

I am not familiar with dutch(it is dutch isn't it) so if you send email to page manager. You should also try to check in winamp. This pls preferences. Maybe there is a url with port included

---

### Post by DutchLau on 2005-05-12
Thanks christooss for your speedy reply,

The thing is I CAN get this radio station to work with the .pls link, but only with Realplayer (which I don't like very much). You didn't install any extra programs to stream other than the standard XMMS and Streamtuner?  :neutral:  

I'm going to go mess around with the settings, see if I can get it up and running,

Thanks,

DutchLau

---

### Post by christooss on 2005-05-12
Try to use link i gave you. Add it to the xmms. Its a station from stream tuner

---

### Post by christooss on 2005-05-12
The problem is beacause streamtuner does not suport desse kind of links. you HAVE to have a link like mine :)

I tried to add your station to streamtuner but it didnt worked

---

### Post by DutchLau on 2005-05-12
I'm installing XMMS again, I reinstalled Ubuntu this afternoon after a Kernel panic. I made a custom Kernel that messed up my system  :grin:  God I'm a noob

I'm going to email the webmaster for the IP adress and the Port, but I don't see why I can't do something in XMMS that I CAN do in RealPlayer. Doesn't everyone agree with everyone that XMMS is the best music player out there?

DutchLau

---

### Post by DutchLau on 2005-05-12
@ christooss,

The answer to your original question is simple. Many radio stations don't send out the Artist/Filename in the streams that are mp3/wma etc. With OGG I believe they do. Correct me if I'm wrong, but often Artist and Filenames are just not sent out with the stream  :grin: 

Does that answer your original question?

---

### Post by christooss on 2005-05-12
I found this

[http://www.desktoplinux.com/news/NS9784616314.html](http://www.desktoplinux.com/news/NS9784616314.html)

but I am unable to find how to change this in FF

I solved that problem with editing preferences in xmms like I was told

---

### Post by christooss on 2005-05-12
And a second later I found

[http://forums.fedoraforum.org/showthread.php?t=51224](http://forums.fedoraforum.org/showthread.php?t=51224)

---

### Post by christooss on 2005-05-12
[QUOTE=DutchLau]@ christooss,

The answer to your original question is simple. Many radio stations don't send out the Artist/Filename in the streams that are mp3/wma etc. With OGG I believe they do. Correct me if I'm wrong, but often Artist and Filenames are just not sent out with the stream  :grin: 

Does that answer your original question?[/QUOTE]
 Artist and filenamse are almost always sent to machine. Its the problem that machine doesn't recognize that. But.. the problem is solved.

Did you tried that last link

---

### Post by DutchLau on 2005-05-12
I'm trying it now  :razz: 

XMMS is sweet, I'm installing nice skins for it right now  :grin:

---

### Post by DutchLau on 2005-05-12
>  First, open your Mozilla browser. In the Edit menu of the Mozilla browser, select Preferences. In the Navigator section in the left pane, select Helper Applications. 

Where in the world is the "helper applications?" I don't see it! I see "General" "Privacy" "Web Features" "Downloads" and "Advanced" no "helper applications. What did you do?

---

### Post by DutchLau on 2005-05-12
Are you using Mozilla or Firefox??

---

### Post by christooss on 2005-05-12
check the other link if you are using Firefox

---

### Post by christooss on 2005-05-12
There is something vrong with your radio.

I changed mimetypes

And all radios work when I clck on them in Firefox. But your radio keps putingout this output

> [playlist]
File1=http://stream01.slamfm.trueserver.nl:8000/idt
Title1=SLAM!FM - powered by TrueServer
Length1=-1
File1=http://stream01.slamfm.trueserver.nl:80/idt
Title1=SLAM!FM - powered by TrueServer
Length1=-1
File1=http://stream01.slamfm.trueserver.nl:8080/idt
Title1=SLAM!FM - powered by TrueServer
Length1=-1
File2=http://stream02.slamfm.trueserver.nl:8000/idt
Title2=SLAM!FM - powered by TrueServer
Length2=-1
File2=http://stream02.slamfm.trueserver.nl:80/idt
Title2=SLAM!FM - powered by TrueServer
Length2=-1
File2=http://stream02.slamfm.trueserver.nl:8080/idt
Title2=SLAM!FM - powered by TrueServer
Length2=-1
File3=http://stream03.slamfm.trueserver.nl:8000/idt
Title3=SLAM!FM - powered by TrueServer
Length3=-1
File3=http://stream03.slamfm.trueserver.nl:80/idt
Title3=SLAM!FM - powered by TrueServer
Length3=-1
File3=http://stream03.slamfm.trueserver.nl:8080/idt
Title3=SLAM!FM - powered by TrueServer
Length3=-1
NumberOfEntries=9
Version=2

Here are i think urls plus ports :)

Use
this one
copypaste in xmms works like charm    ](*,) 
I had it right in front of my eyes  :mad: 
[http://stream01.slamfm.trueserver.nl:8000/idt](http://stream01.slamfm.trueserver.nl:8000/idt)

---

### Post by DutchLau on 2005-05-12
Hhaha Thanks cristooss!

This works like a charm, I weaseled my way out of using XMMS to play the files by using RealPlayer, but now I can make this as a launcher and get XMMS to play it  :grin: 

Thanks! (I added a point to your reputation)  :-P 

DutchLau

P.S. Good radio station eh? Where are you from?

---

### Post by christooss on 2005-05-12
[QUOTE=DutchLau]
Thanks! (I added a point to your reputation)  :-P [/QUOTE]

Thanks  \\:D/

[QUOTE=DutchLau]
P.S. Good radio station eh? Where are you from?[/QUOTE]

I am from slovenia

European Union like you  :grin:

---

### Post by DutchLau on 2005-05-12
True, I might be Dutch, but I live in Brazil right now (been living here for the past 3 years). In the summer I am moving back. I'm infecting everyone here with Ubuntu mania  :grin:  I must have passed Ubuntu along to about 12 people right now including an IT administrator who admins all of the computers in a local American school. In the future (when the enterprise edition of Ubuntu comes out) he is planning on putting Ubuntu on all of the computer  :-P  

What do you think about that?

---

### Post by christooss on 2005-05-12
There will be NO enterprise edition of Ubuntu.

So he will have to migrate to Ubuntu without support [-X] There is this forum and why he wouldn't migrate to ubuntu. He have to lurn ubuntu. And with breezy or maybe sooner he will be ready

---

### Post by DutchLau on 2005-05-12
Serious?

I thought there would be one in October  :-|  I was sure of it.. Are you sure?

---

### Post by christooss on 2005-05-12
[QUOTE=ubuntu.com]Ubuntu will always be free of charge, and there is no extra fee for the "enterprise edition", we make our very best work available to everyone on the same Free terms.[/QUOTE]

This tells you all

---

### Post by christooss on 2005-05-12
I was mistaken SORRY

[http://www.ubuntulinux.org/ubuntu/releases/document_view](http://www.ubuntulinux.org/ubuntu/releases/document_view)

[http://www.ubuntuforums.org/showthread.php?t=28648&highlight=enterprise+edition](http://www.ubuntuforums.org/showthread.php?t=28648&highlight=enterprise+edition)

---

### Post by DutchLau on 2005-05-12
See, so there IS going to be an enterprise edition  :grin: 

You just contradicted yourself  ;-)

---

### Post by christooss on 2005-05-12
I sad i have made a mistake

But if you read the whole thread (the second link) nobody knows what enterprise edition is all about. we'll see won't we? :?

---

### Post by christooss on 2005-05-12
Maybe its all about proffesional support. but...

I stilll think that normal users like me and you will not suffer lack of support.

---

### Post by DutchLau on 2005-05-12
Oops, sorry, I pressed "Reply" before I had time to see your correction post. 

True about the enterprise edition. They aren't sure even if they will make it  :grin: 

Christooss, it's been fun forum spamming with you, but I'm off. I'm going to play some America's Army, if you know that game  :-P 

Very good, I reccommend it: [www.americasarmy.com](www.americasarmy.com)

Have fun and have a good night,

DutchLau

---

### Post by kvidell on 2005-05-14
[QUOTE=DutchLau]@ christooss,

The answer to your original question is simple. Many radio stations don't send out the Artist/Filename in the streams that are mp3/wma etc. With OGG I believe they do. Correct me if I'm wrong, but often Artist and Filenames are just not sent out with the stream  :grin: 

Does that answer your original question?[/QUOTE]
 No, they pretty much always do, whether it be MP3 or Ogg. It's just sending a meta-data tag over in the encapsulation headers of the packets I believe.
If they don't send it then they're doing something wrong on the server end... I've personally never seen a station that didn't send artist/title information that was readable by any standard mp3 streaming technology... and it is all very standardized.

Ogg streaming is a little bit different but I think even in that it sends the information just fine.
- Kev

---

### Post by christooss on 2005-05-14
[QUOTE=kvidell]I've personally never seen a station that didn't send artist/title information that was readable by any standard mp3 streaming technology... and it is all very standardized.
[/QUOTE]

Try slamfm.nl station. I don't get author and name of the song :mad:

---

