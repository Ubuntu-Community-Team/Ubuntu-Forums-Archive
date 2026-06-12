---
title: "Can you identify this code?"
date: 2021-12-20
forum: General Help
---

### Post by Gnusboy on 2021-12-20
Hello, y'all

I just noticed this code on my system and I have never seem anything like it. It was in a folder for a person I know, but we have never exchanged files etc. that I can recall. It comes out at 2.4 MB or 24,000 words. 
I found it in 2 locations on my drive.
This seems like a big file to hang around.
I formated part of this file to make it easier to read, but it's all shown as single spacing.I've sent a message to him to see if he know anything.
This is only an excerpt, changed from the original format 
CAn you help me solve this mystery?
Thanks
```
<link rel="preload" href="John%20Moses_files/FwhMvxUglB3N0CwFNU=bqXU0ydMoPnDnn8frHe59l1EzViLot8uuq4r-FkEEKr.js" as="script" crossorigin="anonymous" nonce=""><script src="John%20Moses_files/FwhMvxUglB3N0CwFNUbqXU0ydMoPnDnn8frHe59l1EzViLot8uuq4r-FkEEKr.js" data-bootloader-hash="iONOQ6e" async="1" crossorigin="anonymous" data-p=":160,17,424,21,9,29,11,26,164,93,18,204,375,425,151,263,43,27,34,122,15,68,285,67,61,2,246,174,155,7" data-c="1" onload='_btldr["iONOQ6e"]=1' onerror='_btldr["iONOQ6e"]=1' nonce=""></script>
<link rel="preload" href="John%20Moses_files/R4Eyw_0AN2M.js" as="script" crossorigin="anonymous" nonce=""><script src="John%20Moses_files/R4Eyw_0AN2M.js" data-bootloader-hash="tly5h9U" async="1" crossorigin="anonymous" data-p=":4" data-c="1" onload='_btldr["tly5h9U"]=1' onerror='_btldr["tly5h9U"]=1' nonce=""></script>
<link rel="preload" href="John%20Moses_files/K6wQz6OHHdSTptNDhK-sLRQ8E3xq0JPrez-lj_iObUjDk8ee1L_vliIPwmL1L.js" as="script" crossorigin="anonymous" nonce=""><script src="John%20Moses_files/K6wQz6OHHdSTptNDhK-sLRQ8E3xq0JPrez-lj_iObUjDk8ee1L_vliIPwmL1L.js" data-bootloader-hash="uYcjqHO" async="1" crossorigin="anonymous" data-p=":84,32,80,78,73,99,79,358,82,53,91,289,76,39,92,278,41,185,77,35" data-c="1" onload='_btldr["uYcjqHO"]=1' onerror='_btldr["uYcjqHO"]=1' nonce=""></script>
<link rel="preload" href="John%20Moses_files/cTRrmVYOCH9.js" as="script" crossorigin="anonymous" nonce=""><script src="John%20Moses_files/cTRrmVYOCH9.js" data-bootloader-hash="JkDB/SJ" async="1" crossorigin="anonymous" data-p=":186" data-c="1" onload='_btldr["JkDB\/SJ"]=1' onerror='_btldr["JkDB\/SJ"]=1' nonce=""></script>
<link rel="preload" href="John%20Moses_files/XJXwTcg3R7t.js" as="script" crossorigin="anonymous" nonce=""><script src="John%20Moses_files/XJXwTcg3R7t.js" data-bootloader-hash="gV7Q1bA" async="1" crossorigin="anonymous" data-p=":211" data-c="1" onload='_btldr["gV7Q1bA"]=1' onerror='_btldr["gV7Q1bA"]=1' nonce=""></script>
<link rel="preload" href="John%20Moses_files/7Dh7aM-FO14.js" as="script" crossorigin="anonymous" nonce=""><script src="John%20Moses_files/7Dh7aM-FO14.js" data-bootloader-hash="c5l9CVU" async="1" crossorigin="anonymous" data-p=":137" data-c="1" onload='_btldr["c5l9CVU"]=1' onerror='_btldr["c5l9CVU"]=1' nonce=""></script>
<link rel="preload" href="John%20Moses_files/BWpQmQ9vyo5.js" as="script" crossorigin="anonymous" nonce=""><script src="John%20Moses_files/BWpQmQ9vyo5.js" data-bootloader-hash="oK9Il4y" async="1" crossorigin="anonymous" data-p=":14" data-c="1" onload='_btldr["oK9Il4y"]=1' onerror='_btldr["oK9Il4y"]=1' nonce=""></script>
<!--EF-->
```
This is the format of the file as I found it.
 


This might not be the best place to ask this question,

---

### Post by TheFu on 2021-12-20
Looks like cached javascript.  Do you allow javascript on your system?

---

### Post by Gnusboy on 2021-12-21
Thanks FU

I never thought about it, but I haven't added it to 20.04 or earlier. Where do I look for it?

Also, why would it show up in the folder of the guy's name?

---

### Post by The Cog on 2021-12-21
It looks like html to me. See [https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types/preload](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types/preload) for what preload means. So this is meant to be run by a web browser, but I certainly wouldn't try to even view it with a web browser without knowing more about what it's doing there. It all looks suspicious to me, with obfuscated javascript file names.

---

### Post by TheFu on 2021-12-21
> **Gnusboy said:**
> Thanks FU

I never thought about it, but I haven't added it to 20.04 or earlier. Where do I look for it?

Also, why would it show up in the folder of the guy's name?

Without knowing how they got there and where these files are actually stored on the system, it could be all sorts of reasons.  Ever used "Save As" in a web browser?  One of the choices is "Complete HTML" ... that would pull CSS and javascript parts too.  The name for a directory could be anything ... or set by the end-user.  Or someone might have tried to save something inside the webpage (perhaps some media) and got the wrong thing.

It is unlikely to be anything nefarious. More likely to be left over, failed, attempt at saving something.

I typically don't allow javascript to run from most websites on my systems, but many people do.  I have a whitelist of sites where I've decided to allow javascript.

---

### Post by Gnusboy on 2021-12-22
Hey FU
I started running a checksearch for javascript and found dozens of entries. like this. The anonymous in it, makes me more curious. Does it have any importance? 

crossorigin="anonymous"><script src="John%20Moses_files/wZbsv5HDwta.js" async="
" crossorigin="anonymous"></script><link href="John%20Moses_files/7bn3sup9Jav.js" 
rel="preload" as="script" crossorigin="anonymous"><script src="John%20Moses_files/7bn3sup9Jav.js" async="" 
crossorigin="anonymous"></script><script src="data:application/x-javascript; charset=utf-

---

### Post by TheFu on 2021-12-22
[https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/crossorigin](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/crossorigin) - looks like it is just the HTML way of saying, anyone, anywhere, can include this javascript without any restrictions. It lets people use someone else's bandwidth.  I don't allow that on my webservers, and I don't use externally hosted assets, since ... security.  But kids these days think that using other people's stuff is fine and safe. They are wrong.

For these specific files, since they are on the box already and I assume there isn't a web server running, there is very little real risk. Someone saved a complete webpage and this is what we get.

---

### Post by Gnusboy on 2021-12-22
I ran searches for javascript and got dozens of hits within this 535 page file of 2,347,947 words. Dumb question: Is it possible that this is a program to harvest my data? Not to harm, but to catalog it? I think I'm going to delete it and hope it's nothing. Thanks FU. I appreciate your help with my questions. 

What is kind of curious is that some of the code - at least what I can read or understand - seems related to various sites i.e. "Facebook" and others, shows what appears to be the html page design.
But there is other code like this,
  	 	 	 	  [FONT=century gothic]```


<script>requireLazy(["Bootloader"],functi
{m.handlePayload(JSON.parse(document.getE
requireLazy(["JSScheduler","ServerJS","Sc
rverJS,ScheduledApplyEach){JSScheduler.ru
ServerJS()).handleWithCustomApplyEach(Sch
[["RelayPrefetchedStreamCache","next",[], 


```

[/FONT][FONT=century gothic][SIZE=1] 
 [/SIZE][/FONT]
[FONT=century gothic][SIZE=1]  [/SIZE][/FONT][FONT=century gothic][SIZE=1]

[/SIZE][/FONT]

---

### Post by Gnusboy on 2021-12-22
Got it. Thanks. Is it best to delete it, or move it somewhere safe? Sandbox?

---

### Post by Gnusboy on 2021-12-22
I ran searches for javascript and got dozens of hits within this 535 page file of 2,347,947 words. Dumb question: Is it possible that this is a program to harvest my data? Not to harm, but to catalog it? I think I'm going to delete it and hope it's nothing. Thanks FU. I appreciate your help with my questions. 

What is kind of curious is that some of the code - at least what I can read or understand - seems related to various sites i.e. "Facebook" and others, shows what appears to be the html page design.
But there is other code like this,
                       [FONT=century gothic]```


<script>requireLazy(["Bootloader"],functi
{m.handlePayload(JSON.parse(document.getE
requireLazy(["JSScheduler","ServerJS","Sc
rverJS,ScheduledApplyEach){JSScheduler.ru
ServerJS()).handleWithCustomApplyEach(Sch
[["RelayPrefetchedStreamCache","next",[], 


```

[/FONT][FONT=century gothic][SIZE=1] 
 [/SIZE][/FONT]
[FONT=century gothic][SIZE=1]

[/SIZE][/FONT]

---

