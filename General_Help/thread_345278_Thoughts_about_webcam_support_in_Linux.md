---
title: "Thoughts about webcam support in Linux"
date: 2007-01-24
forum: General Help
---

### Post by javierfh on 2007-01-24
Hello,

I have been wondering few days about something and would like to know if anyone can clarify that for me. It is about webcam and drivers.

I guess that for motherboards, processors, video cards and some other basic components there are several options, but still in orders of tens, whereas for network card or wireless cards and some other small components the possibilities to choose are in bigger orders and not to mention webcams where you can get from so many manufacturers.

So my point is, that I believe drivers for the motherboards, processors or video cards are easier to find for Linux, but then when we move to the realm of wireless cards you see the problems in the forums: lots of them. And that, if I understood right, was the origin/motivation of the Ndiswrapper. To be able to install the windows drivers to your Linux system. Is that correct?

So would it make sense to make similar thing for webcams? They all come normally with some software for windows. And they normally work easily under windows, but when you try with Linux, that’s another story.
See in this feature specification for feisty: 
[https://launchpad.net/~webcam-support](https://launchpad.net/~webcam-support)

In fact it is a pity that there could be more applications working, but they depend on the webcam and its support it is limited.
[https://blueprints.launchpad.net/ubuntu/+spec/webcam-gestures](https://blueprints.launchpad.net/ubuntu/+spec/webcam-gestures)


Well I just wanted to contribute the only way I can so far, by giving some idea. It might not make sense or maybe it does. Hope someone can comment on that, if I am totally wrong or makes some sense.

Thanks for reading,

Javi

---

### Post by PetePete on 2007-01-24
i agree. 
maybe webcam support is so poor 'cos all the proper coding geeks dont like seeing themselfs on webcam :-D 

........
..
.
ps only j/k. i'm sure you're all beutiful!

---

### Post by javierfh on 2007-01-24
:D you might have some reason there, but dont think thats the answer.

I still would like to know, if what i wrote makes any sense or if there are other reasons that make the webcam case different than the wireless. In my oppinion complexity of wlan cards seems much bigger than the webcam support.

What you think?

Javi

---

### Post by Robor on 2007-01-24
I sooooooo wish we had good webcam support in Linux.  Not only that but good program support for Webcams as well.  Under Linux neither Gaim, YahooIM, or Skype have video support.  :(  

The main reason I still use Windows on my desktop at home is voice/video chat with my wife who is overseas.  That and gaming are the only 2 things that keep me from being 100% Linux but I'd be happy just dual booting to game and using Linux (Ubuntu) for everything else.

---

### Post by mahiyar on 2007-01-24
Webcam, wireless, scanner support are the weak spots in Linux. I wish something more could be done.

---

### Post by nalmeth on 2007-01-24
You could suggest the same about printers I suppose.. It seems for a lot of printers, even when part functionality is there, there are other problems, like formatting.

Its just about supporting companies that support us. 

My Logitech webcam works great BTW

---

### Post by mahiyar on 2007-01-24
nalmeth can i know which model is that ? Or ar all logitech webcam supported? (planning to get one)

---

### Post by nalmeth on 2007-01-24
Sorry, I don't have the model name. It doesn't even say on the cam itself, and I don't have the packaging.

All I had to do was follow instructions here:
[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

I'm not sure if all logitech's are supported or not.. Perhaps some of the hardware compatibility guides would be of use, theres one at the UDSF. 

There's also a pretty active hardware incompatibility guide, which would be probably just as useful.

---

### Post by javierfh on 2007-01-25
Hi,

thanks for the replies, but still havent heard anything about my proposal. Does it make any sense.

In my case, the webcam sort of works, i can see myself, i can use it to take snapshots and i can see it in camorama, but then when using amsn thats another story. The camera kind of freezes, well in fact nothing happens..the whole application freezes for about 40 secs and nothing happens.

And well, im not the only one and this is basically because of the weak webcam support, as some of the previous poster mentioned. In fact i have read so many times that people keeps double booting just to use skype with video. It might be that if the webcam support would be better, some other applications could benefit from it.

Well just wanted to contribute at least with ideas,since i cant jump into code, wouldnt know how to start :D

Javi

---

### Post by gusjones on 2007-01-25
Out of interest which apps are you running with your Webcam?

---

### Post by javierfh on 2007-01-25
Hi,

basically none at the moment.. amsn doesnt work (i can get video, but cant send), similar thing happens for me with Kopete and well there is no skype support for video. But well, probably if support would be better, some other applications would appear, read that one for example [https://blueprints.launchpad.net/ubu...ebcam-gestures](https://blueprints.launchpad.net/ubu...ebcam-gestures) not sure how good would that be, but well at least its interesting from technology point of view. 
And well there are applications for surveilance or broadcasting, dont know.. never went into too much detail because the webcam doesnt work..ok to be fair it seems to work with camorama and some other application , but then when you try to interact with other users..big no no.

Javi

---

### Post by gusjones on 2007-01-25
I've recently got myself a webcam, I'll try out these apps and see what I come across.

It may be you have some driver related problems.

---

### Post by nalmeth on 2007-01-25
Have you tried OpenWengo? Linux/Mac/Windows support, though my Dad had a lot of trouble getting it working in Windows. 

All those apps work OK for me, how fast of a system do you have?

---

### Post by javierfh on 2007-01-25
Hi,

i havent tried openwengo basically because everyone else has either msn or yahoo messenger...or then skype.

And about my system...shouldnt be problem. I have pentium iv dual core, with 2Gb ram and very fast internet connection.. so im sure it might be some problem with my webcam or some driver problem.

I just wish that would be just more straight forward, to use webcam, as it is with windows. And thats why i was wondering if it wouldnt be possible to reuse the windows drivers.

Javi

---

### Post by loell on 2007-01-26
bear in mind, that it is the webcam manufacturers responsibility to make it comaptible with linux , not the other way around, to be safe on webcam compatibility

refer to this [growing webcam list]("http://mxhaard.free.fr/spca5xx.html")

---

### Post by javierfh on 2007-01-26
Hello,

and thanks a lot for that link...starts to look very promissing.

From there i can see my camera it is supported,it is aiptek mini pen cam.
But then i understand that i need to download the new driver from the download section.
The driver i guess is the following gspcav1-20070110.tar.gz and i have downloaded it, but then i dont have any clue what to do with it.
Any idea? or any idea how to find the installation guidelines?
All help is more than welcome...i have the feeling im getting closer :)

Javi

---

### Post by nalmeth on 2007-01-26
Unpack it, and I should think there will be a README with some instructions. 

Maybe you could install it directly with EasyCam, as the program searches for a driver anyway. 

Wiki page again, play around with EasyCam if the driver has no instructions.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

