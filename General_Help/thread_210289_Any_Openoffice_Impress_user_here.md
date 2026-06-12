---
title: "Any Openoffice Impress user here?"
date: 2006-07-06
forum: General Help
---

### Post by boom2k1 on 2006-07-06
While OpenOffice 2.0 Impress seems to be a nice alternative for Microsoft Powerpoint, the thing that bothers me is the very slow transition between slides when using the slideshow mode. I am not that sure if it is a graphic card thing, because in Windows Powerpoint slide transitions are quite smooth.

Does anyone here experience the same problem?
Why is it like that and are there any ways to get around this problem?
Thanks

---

### Post by deadgobby on 2006-07-06
[QUOTE=boom2k1]While OpenOffice 2.0 Impress seems to be a nice alternative for Microsoft Powerpoint, the thing that bothers me is the very slow transition between slides when using the slideshow mode. I am not that sure if it is a graphic card thing, because in Windows Powerpoint slide transitions are quite smooth.

Does anyone here experience the same problem?
Why is it like that and are there any ways to get around this problem?
Thanks[/QUOTE]
 How much Ram do you have. I have 512 and runs with no problem. When I just have 256. It kind was slug slow.
Gobby

---

### Post by T700 on 2006-07-06
I've noticed the same thing on slower machines, but I don't use transitions much, so it's never been much of an issue to me.  I've seen the problem brought up on other groups and there was never any real solution offered.

Sorry, wish I could be of more help.

Paul

---

### Post by boom2k1 on 2006-07-07
I am using 756 mb of Ram.

It doesn't appear to be a Ram problem.

---

### Post by canadianwriterman on 2006-07-07
I use Impress all the time for teaching. I've noticed the slow transition on some slide sets, too. I have 1 Gig of RAM, so that's not the problem. I think they are on slides that were originally PowerPoint set that I opened in Impress and used as a template. They also are heavy on inserted graphics and scans. But, to be honest, I haven't tried building a set from scratch in Impress.

---

### Post by ayllu on 2006-11-02
Hi... I use oo impress and seem to work fine... but i cannot animate a tex beacuse wen y put personalize animate text I don not got the animation of the text just the animantion of the objet and y get the text after it. I tried to reinstall oo impress but dosnt work... anyone now how i can solve my problem.

---

### Post by fragos on 2006-11-03
I haven't noticed a lag in performance with Impress.  That my relate to my presentation style.  I don't use transition effects or object linking.  I rarely have more than six bullets and minimize the word count.

---

### Post by gladen on 2006-11-05
> **boom2k1 said:**
> While OpenOffice 2.0 Impress seems to be a nice alternative for Microsoft Powerpoint, the thing that bothers me is the very slow transition between slides when using the slideshow mode. I am not that sure if it is a graphic card thing, because in Windows Powerpoint slide transitions are quite smooth.

Does anyone here experience the same problem?
Why is it like that and are there any ways to get around this problem?
Thanks

I don't usually use slide transitions per se, so I cannot speak to this.  But, I have found that some of the animations are VERY slow if they are on Power Point slides/presentations that I've imported into Impress.  If I remove the animations and then re-do them (usually not too much work) then they are nice and fast in impress.

---

### Post by impman89 on 2006-11-09
I'm having the same problem - very laggy transitions, even on presentations built from scratch in OOo. I'm running xgl/beryl so that could be the issue - i'll try it without xgl later and report and differences.

---

### Post by impman89 on 2006-11-09
nope, same without xgl running. Anyone have any ideas why its so laggy?

---

### Post by hardyn on 2006-11-09
Ill throw one out...

what is the Idle CPU usage of your machine?

i have a P-M based machine, and it suffers from the 686/smp kernel bug that appeared in dapper, apparently it has been fixed (no it hasn't).
Everything that demands video runs really slowly before adding "max_cstate" (this is well documented on this forum).  It sounds really overkill... but if your not looking for this problem you might not see it.

---

### Post by fragos on 2006-11-09
Could someone with the "laggy" problem quantify for the rest of us.  Is the issue before the transition starts or how long the transition takes?

---

### Post by rc_br on 2006-11-21
My problem is no sound when I use PPT
What codec or plugin  need?

---

### Post by fragos on 2006-11-21
Given that this is a Microsoft formated file, I'd use Synaptic to load package "w32codecs".  It that doesn't work we'll try something else.

---

### Post by rc_br on 2006-11-21
Thanks, but I installed the w32codecs before. 
No sound . In Powerpoint works well.

---

### Post by fragos on 2006-11-21
Installing mplayer brings a lot of miscellanious codecs.  I don't have any PPT's with sound to try so I don't know if I have the same problem.  My primary sound player is Banshee and I've installed all the gstreamer0.10 plugins that made sense to me.  I'm grasping at straws -- sorry.

---

### Post by rc_br on 2006-12-10
It is working now!
I don't know what codec, but this site save my life.
Now, the sound is on when i play PPT
[http://hamacker.wordpress.com/2006/10/11/ubuntu-tocando-todos-os-formatos-conhecidos/](http://hamacker.wordpress.com/2006/10/11/ubuntu-tocando-todos-os-formatos-conhecidos/)
Sorry is in portuguese
Thanks

---

### Post by Cippa Lippa on 2007-06-05
> **fragos said:**
> Given that this is a Microsoft formated file, I'd use Synaptic to load package "w32codecs".  It that doesn't work we'll try something else.
Hei, somebody wrote in OO forum that the problem of slow slide transitions has been solved with feisty. It has not.
Transitions are slow. Very slow compared to Powerpoint. It is an app killer.
I am running Ubuntu with KDE installed from server install (pretty trimmed down). I have 1Gb RAM, Pentium IV 2.4 GHz laptop. Video card is ATI Radeon Mobility 9000.
It seems the transitions can be pretty smooth but you have to wait several seconds before you go the next slide. If you want to flip through the presentation it is going to lag behind a lot.
It usuallly needs easily up to 5 seconds before you can safely proceed to the next slide. And we are talking about extremely simple slides with no animations, no movies....

They got to solve this problem otherwise scientists will keep on using powerpoint for their presentations.
I can't imagine going to a conference and having my presentation lagging behind...

Cippa

---

### Post by fragos on 2007-06-05
I've no performance issues with Impress and some of my slides include video.  My system is AMD 2800+, 1GB and Nvidia FX5200.  Do you have 3d rendering with your ATI or are you using the default open source video driver?  PowerPoint seems to support fewer video formats than Impress.

---

### Post by Cippa Lippa on 2007-06-06
I have the fglrx driver for my ati... I don't know if 3d is on or not... I have no video
I have though checked the memory options for openoffice. There is a menu that allows you to change the memory allocation for openoffice. Unfortunately I changed the parameters in order to give more memory to openoffice and that actually got the situation even worse, at least as far as I could see.
I think it might well be a video card problem. I just don't understand why the damn program doesn't put the whole presentation in RAM. When you switch back from full screen you see that it still has to reload from HD all the slides for the thumbnail....

I don't know. I would really love to use this program. I used it today for a presentation for my group and sometimes it was pretty embarassing to wait for the slide to switch!

Cippa

---

### Post by fragos on 2007-06-07
I'm currious what the wait time you're talking about is?  Presentation style may also be a factor.  Far too many people have slides that control rather amplify the presentation.  Slide components like images at much higher than necessary resolutions or bitmap formats can increase the size of a presentation.  Transtions can also be overdone.  It's hard to give objective help without experienceing what you're talking about.  Good presentations are an art that combine visuals, spoken word, gestures and motion.

---

### Post by Cippa Lippa on 2007-06-14
yes, I know what presentations are. I have set no specific transitions like fading or anything else. Just the very common hard switch from slide 1 to slide 2 can take up to 5 seconds. Now I have installed powerpoint via Crossover and it is still slower than winxp but pretty much better than Impress. I think it is also a question of X.

Cippa

---

### Post by cookies on 2007-06-14
Fine here. But this is Fedora core. But I have a Pentium 4 and 493MB of RAM. Have you set the speed of the transition to Fast?

---

### Post by fragos on 2007-06-14
For comparison sake I ran a graphics intensive Impress presentation by opening and pressing F5.  I then used the right arrow key to move through the presentation.  Slide changes were instantanious on my machine which is an AMD 2800+, 1GB memory, Nvidia FX5200 with 3D driver.  This is hardly a world beater for performance.  I don't doubt the slide change timing you give.  I'm curious of what we're doing differently that makes my system seem so much faster.  I'm running Ubuntu 7.04 and have seen some areas of performance improvement over 6.10.  Memory size might be a factor as might the size of your presentation.  Perhaps swapping was required?

---

### Post by Gavla on 2008-01-14
I just solved my own impress issue:
I have a sideshow where I want to use going back and forward between two slides to create a crude sort of animation. The slowness didn't bother me so much, but it got so laggy after two or three flicks back and forward that it refused to go back a slide, and the animation got locked in the second frame.

But finally I tweaked all the settings and It's working very fast and going in both directions as far as I want. 

The settings I settled for were:
MEMORY - 30 steps, 128MB, 20 objects, 20MB per object, and remove after an hour
JAVA - Do not use Java
VIEW - Open GL, optimized output, dithering, refresh during interaction and hardware acceleration all ticked.

As soon as I switched on hardware acceleration the first time, It fell into place. But then, when I did some other stuff and came back to it, it was back to being slow. Therefore, I'm not sure exactly what setting it was that eventually fixed my issue - Because shutting  down and restarting impress affected the issue. Maybe some of those settings need to have a restart in order to work properly, or perhaps it just purges some stuff from the memory,

If you're having issues, I'd recommend trying to change all the settings again, but restart the program after every change, if you didn't already do so. 
Saving the show, quitting, and restarting by double clicking on the document and going straight into the show might also help you in itself- running 'fresh' like this seems to be beneficial to performance, and might be enough to get you through your presentation.

I wish I could have worked out more decidedly what I did, 'cause from my scroogling, a lot of people seem to be having similar issues with Impress and turning back to windows.

---

### Post by Gavla on 2008-02-09
Scratch that. It makes some difference, but it didn't take much more stuff put into the slide shows to make them fall back down to their knees.

---

