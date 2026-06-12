---
title: "[SOLVED] Blue screen during video playback"
date: 2005-06-08
forum: General Help
---

### Post by Cygnus on 2005-06-08
Hi,

I just installed Kubuntu 5.04 and most things seem to work fine. Kaffeine has crashed a few times though.

Anyway here is my problem:

When I try to watch a video I only get a blue screen but I do hear the sound. This seem not to be an uncommon problem, I have seen others report the same thing. And it do not seem to be dependant on which videoplayer I use. I have tried both Kaffeine, Xine and GXine and they show exactly the same behaviour. The strange thing is that if I start the videofile in one of the players, and then start the video in another player without closing the first one it works fine in the second one. ( Note that I do not have any problem with the codecs, they are properly installed, I have installed it the same way on other systems without problems). 

I am not not sure but it seems like when the players try to play to the default vide output it fails, but when I start another player then this video output is occupied and it selects another one which works.

So it seems like I can watch videos fine, but very irritating that I have to open two players each time to get the correct output in the second one.

Anyone experienced the same ? Or know what the problem might be ?

---

### Post by paulvandenberg on 2005-06-08
I got the same thing. You need to specify the video driver for the Xine based player (Kaffeine, Gxine, Xine, etc.). You might need to activate the 'Master of the Known Universe' setting to be able to see the proper video setting. I found that the xshm video driver worked for me. I can't give more precise directions right now as I'm at work and my Linux box is at home.

---

### Post by Cygnus on 2005-06-09
Thank you, that worked perfectly fine. :smile: I browsed around the xine settings yesterday but did not notice you could set the 'Master of the known universe' setting. Xshm worked fine for me aswell. 

Wonder what's the problem with auto though. I suppose there are more people that will have problems with this.

---

### Post by Pixilarion on 2006-08-20
I still have this problem in Dapper. Switching the settings to xshm did solve the problem for me in Kubuntu. Don't know how to solve it under Ubuntu... Still, it works for me now, but I think it is something that should be solved in a next release...

---

### Post by wieman01 on 2007-07-27
Problem persists in Feisty... Selecting "xshm" as video driver (xine parameter) resolves the problem.

---

### Post by saurabh kakkar on 2007-12-21
[SIZE="3"]^^ how can i select "xshm" as video driver on ubuntu 7.04 where is the option located  plz let me know as i m a noob[/SIZE]

---

### Post by Cygnus on 2007-12-21
I have Swedish setup so trying to translate for Kaffeine:

Make sure you use the xine engine: Settings -> Player engine -> Kaffeine-Xine

Then: Settings -> Xine engine parameters -> Video -> driver -> xshm

---

### Post by saurabh kakkar on 2007-12-21
> **Cygnus said:**
> I have Swedish setup so trying to translate for Kaffeine:

Make sure you use the xine engine: Settings -> Player engine -> Kaffeine-Xine

Then: Settings -> Xine engine parameters -> Video -> driver -> xshm

Not getting man where is xine engine located there is no Setting option in my ubunut 7.04

---

### Post by beachreader on 2007-12-30
very cool!! thank you been having this problem since November 2007////thanks again.

---

### Post by Boom.dk on 2008-02-08
I registered just to add a little note about VLC. I had the blue screen problem here, but overcame it by going to Preferences -> Video -> Output Modules (or whatever it is called, my OS is in Danish), and choosing another output module ("Advanced settings" has to be enabled for this option to show).

Now, I'm actually using openSuSE, but I figured that it might work in Ubuntu, too.

---

### Post by wieman01 on 2008-02-09
> **Boom.dk said:**
> I registered just to add a little note about VLC. I had the blue screen problem here, but overcame it by going to Preferences -> Video -> Output Modules (or whatever it is called, my OS is in Danish), and choosing another output module ("Advanced settings" has to be enabled for this option to show).

Now, I'm actually using openSuSE, but I figured that it might work in Ubuntu, too.
I think it does. I remember that's what I did when facing blue-screen issues with VLC.

---

### Post by irisheoin on 2008-03-04
Thank you!..had this problem for ages!...switched to opensuse, but liked ubuntu better, cept for not been able to watch videos!...now its all good!..ubuntu does everything i need! :D

---

