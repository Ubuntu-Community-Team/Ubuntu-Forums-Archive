---
title: "OMG! youtube in Firefox1602 is a train wreck!!"
date: 2013-02-22
forum: General Help
---

### Post by adambond on 2013-02-22
WTF!? 
I dont know whats happened, but Youtube is just a complete train wreck for me. I run Firefox 16.0.2
It takes FOREVER for a page to load. The Video will load pretty much right away, but all the other items, like comments, or clickable links under the video, or recommended vids on the right take FOREVER to load, and sometimes never load. 
Sometimes, if I want to write a comment on a vid, I have to actually refresh the page several times and wait several minutes or so. By then, not even worth it. 

But the worst part, sometimes when im cruisin youtube, I click a video and the video page comes up for a couple seconds, and then its hijacked by some [www.RXdrugs.com]("http://www.RXdrugs.com") website or something. 

I left youtube up today when I left for work. Had a video paused. Got home 8hrs later and that page was now on some guys talk radio blog page with a bunch of morons talking about lerbron james or something. 

On top of all that, the browsing in general is just slow. Infact, if I boot over to Windows XP, it actually browses a tad faster than my ubuntu firefox. 

I dont surf ANY porn in firefox. 

What the hell have I done, and how do I undo it? I dont know if youtube is giving everyone else issues also? 
Im familiar with how to clean up this with Windows. But know nothing about Linux.

---

### Post by dino99 on 2013-02-22
youtube is worst place i know; mostly due to people posting things without knowing the right way. An other cause is some links having too much connections at once, so the very slow streaming.
But you still can have problem on your side too indeed; thats where logs can help  :p

---

### Post by fdrake on 2013-02-22
> **adambond said:**
> 
Sometimes, if I want to write a comment on a vid, I have to actually refresh the page several times and wait several minutes or so. By then, not even worth it. 

On top of all that, the browsing in general is just slow. Infact, if I boot over to Windows XP, it actually browses a tad faster than my ubuntu firefox. 

try emptying your hystory temp files and chached files.
"Clear the Cache": edit>preferences> Advanced > Network > Offline Storage (Cache): "Clear Now" 
"clear history cookies": >edit>preferences>privacy> clera hist/ remov cookies

> 
I dont surf ANY porn in firefox. 

who said anything? Are you blaming porn? :D


> 
What the hell have I done, and how do I undo it? I dont know if youtube is giving everyone else issues also? 
Im familiar with how to clean up this with Windows. But know nothing about Linux.
mine is fine.

---

### Post by adambond on 2013-02-22
> **dino99 said:**
> youtube is worst place i know; mostly due to people posting things without knowing the right way. An other cause is some links having too much connections at once, so the very slow streaming.
But you still can have problem on your side too indeed; thats where logs can help  :p

[http://www.youtube.com/watch?v=m_mDTLphIVY](http://www.youtube.com/watch?v=m_mDTLphIVY)

---

### Post by fdrake on 2013-02-22
> **adambond said:**
> [http://www.youtube.com/watch?v=m_mDTLphIVY](http://www.youtube.com/watch?v=m_mDTLphIVY)

what dino means check the system logs (/var/log/syslog) for clues. I don't think this is the case . Is this proble related only to youtube or other apps are running slow.

no need to use offensive words. ppl are trying to help you here.

run firefox and a you tube video and then  in the terminal type:
```
 top
```

what is the  %CPU %MEM of firefox?

---

### Post by adambond on 2013-02-22
[IMG]http://i36.photobucket.com/albums/e44/327amc/Screenshot-1_zpscf4ffa4d.png[/IMG]

---

### Post by adambond on 2013-02-22
Well, i guess it isnt just youtube. Photobucket, youtube, facebook (sometimes), and many other sites just bog this thing down. It never used to be this way. Its gotten progressively worse. I used to be able to run with 7 windows open no problem. Now im lucky to be able to run 4. And if 2 of those are youtube, 1 of them will most definately fail to fully load at some point. 
Ive even had the audio for an ad (swiffer duster or something) suddenly come blaring through my speakers, and there was only one window open, and it was my email, where there are NO ads on that site. WTF?  Kinda like a 'phantom ad'. lol

---

### Post by fdrake on 2013-02-22
good thing you uploaded a screen shoot. The problem seems the plugin container (part of firefox too). give me a min. can you also check for me in firefox > edit> preference>applications > search for "flash"
what results you have.
give me also a screen shoot of this:
tools>adds-on>plugins

also in the adds-on page click extension> do you have a lot of them ?(more than 3 disable some of the and see )

---

### Post by adambond on 2013-02-22
Will do. Thanks. brb

---

### Post by adambond on 2013-02-22
[IMG]http://i36.photobucket.com/albums/e44/327amc/Screenshot-2_zps7ad9bcd0.png[/IMG]

[IMG]http://i36.photobucket.com/albums/e44/327amc/Screenshot-3_zps73df5e42.png[/IMG]

[IMG]http://i36.photobucket.com/albums/e44/327amc/Screenshot-4_zps645a26e9.png[/IMG]

---

### Post by fdrake on 2013-02-22
will disabling easy dial and youtube downloader make any significant difference? also did you cancel the temps file I posted previously?

---

### Post by adambond on 2013-02-22
I did clear the cache. I have done this before and it does help slightly, but doesnt last long. 

I have disabled a couple addons (the youtube downloader also) and there appears to be a slight improvement. I will run for a day or two and see if it holds up. 

The 'plugin container' has dropped to 3rd on the list now. 

Thanks for the help thus far. I will report back.

---

### Post by fdrake on 2013-02-22
for a temp solution use this . hopefully someone wiil come up with a better idea.

you are welcome.

---

