---
title: "Sound Device Problem"
date: 2007-03-01
forum: General Help
---

### Post by Apoorv on 2007-03-01
Suddenly I'm facing this new problem. The log out sound has ceased to play. And I can't make Skype calls too. It tells me that I have some kinda problem with my sound device. Tried the default sound card from the preferences menu, but can't do that. It changes back to the old one immediately. Any idea?

---

### Post by Apoorv on 2007-03-01
And the rest of the sounds are working fine. I can play music, and the Log in sound is perfect.

---

### Post by Apoorv on 2007-03-01
Why is it that whenever I post something, it gets pushed back, and it never gets answered?

---

### Post by ovopax on 2007-03-01
I'll tell you why.
Because when they know the answer to your problem they tell you to RTFM or use Google noob.
And when they don't know the answer they sit back and avoiod your posts, because they don't know how to help.
That is my general impression of the Linux community. I hope it's better here in the Ubuntu forums, you seem like decent fellows.

---

### Post by Apoorv on 2007-03-01
I obviously have searched the world before posting this here. I don't like the fact that I'm dependent on anybody else, so I like to solve my problems on my own. I have tried everything possible before posting this over here...

---

### Post by NewOldTimer on 2007-03-01
hey guys, sorry you've been having trouble getting any help, there are a few of us that would love to respond but if we're not knowledgeable  enough to offer any real help then we usually pass and wait for those who know to help.

I'm new here and at linux in general but if you like maybe we can work on your sound problem together. I have no knowledge with skype though.

what do you mean by it changes back to the other one? another sound device or what? 
I'll help all I can until others join in if thats fine with you.

---

### Post by Apoorv on 2007-03-02
[http://ubuntuforums.org/showthread.php?t=373309](http://ubuntuforums.org/showthread.php?t=373309)
[http://ubuntuforums.org/showthread.php?t=366662](http://ubuntuforums.org/showthread.php?t=366662)

My problem here is a mixture of both the above problems. I tried changing my sound card with the method suggested by Shampyon, and I even tried Iceni's method. But no luck here.

There are two sound devices (by default) in System>>Preferences>>Sound>>Sounds Tab>>Default Sound Card.

There is a drop down menu listing two cards - 
HDA ATI SB
SAA 7134.

I can change the sound card now by using Shampyon's method -

[http://ubuntuforums.org/showthread.php?t=366662](http://ubuntuforums.org/showthread.php?t=366662)

But it doesn't make any difference. The log out sound problem and Skype problem still persists. This is strange because this change was sudden and earlier there wasn't any such problem.

---

### Post by seshomaru samma on 2007-03-02
did you install any programmes or updates before this sudden change in sound?

---

### Post by Apoorv on 2007-03-02
I was thinking on the same lines, but I don't seem to remember...

Most probably it started when I installed gstreamer plugins, and downloaded amaroK.

---

### Post by NewOldTimer on 2007-03-02
Apoorv, heres what I can offer

Right click volume icon..open volume control... make sure nothing is disabled..
click on file{same window}...click change devise.. .make selection"alsa mixer"
click preferences{same window}..check all boxes, this will place them all as choices on vol control window, again make sure nothing is disabled          close windows

right click volume icon again...select preferences...check that device is alsa mixer...click master...close

go to...Systems...preferences...sound...devices
test all as auto detect...test all under alsa
click sound tab..make sure sound card is right one

once you are sure all options are using the same device...restart and let's see what you get

as I said previously I'm a n00b so take the above with a grain of salt.

another observation...I use an external sound card with my laptop, and when its not connected I lose the opening and log-out sounds too, only those sounds everything else works fine...maybe related?

---

### Post by Apoorv on 2007-03-02
Everything you listed over here - I've tried it myself already.
I'll tell you what happened today. I was tinkering with the volume control. Suddenly, Skype was working fine. I talked to my friend for about 5 minutes, when the call stopped in between, and I got the stupid "problem with sound device" error again. It wasn't event triggered, beacuse I was just sitting back and talking, my hands weren't on the keyboard or mouse. It was just spotaneous.


Another thing which may help you in figuring out my problem....
I have a TV Tuner card, which doesn't work under Ubuntu (drivers aren't available). But the sound fro it comes in Line in. If I turn up the Line in volume, then all the sounds become rough and sorta 'blasty'. If I turn it to full, the sound just goes away. That's why I keep the Line in on mute or zero volume.

---

### Post by NewOldTimer on 2007-03-02
Like I said I'm a n00b but maybe you could go into bios and disable tv card since you say its not supported anyways or maybe just take the card out and see if its been causing some sort of conflict with your system....just a thought...:confused:

---

### Post by Apoorv on 2007-03-03
But I use it to watch TV on Windows.... Even if it is being caused due to the card, I can't take it out! I can't sacrifice my card for this minor problem! There must be a workaround.

---

### Post by NewOldTimer on 2007-03-03
sorry didn't know you were dual booting...
any sound problems in windows side? skype work there also?

Edit - maybe theres a way to edit out{disable} your SAA  7134 tv card from ubuntu?

---

