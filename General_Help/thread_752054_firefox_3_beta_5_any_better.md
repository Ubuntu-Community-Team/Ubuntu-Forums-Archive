---
title: "firefox 3 beta 5 any better?"
date: 2008-04-11
forum: General Help
---

### Post by svaens on 2008-04-11
I'm hoping Firefox 3 is going to be twice as fast and stable as firefox 2 on linux. 
I probably shouldn't be holding my breath. 
However, firefox 2 is hopelessly slow. 
To futher prove what a bad job they did on building this for linux, is that I can 
1. create a virtual machine (vmware for linux), running windows xp (on my ubuntu gutsy),  
2. store the vm-file on my external NTFS USB drive, 
3. run firefox on this virtual windows, 

and it runs faster on the vmware than the linux version of firefox does running on ubuntu. 

How is this possible? Even with a second level between it and the hardware (the virtual machine, and a second operating system), running from a pretty slow USB drive, and it is still running faster than my linux firefox 2. 

Is that saying how great a job vmware did with their virtualization product vmware server, 
or is an indication of how bad firefox 2 is on linux. 

My question would be, 

a) has anyone installed firefox 3 beta 5 on linux yet?
and if they have, 
b) have the experienced much of a performance improvement over version 2?

I am crossing my finger with hope.

anyone tell me some good news?

---

### Post by Weichpudding on 2008-04-11
I have tried Firefox 3 since beta 4 without installing it, got the binaries from here: [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html).

If you have used FF2 for a long time then you will notice that FF3 ist significantly faster. According to the changelogs the HTML rendering engine as well as the Javascript engine and I can confirm that this is true. I am coding my own website and noticed severe lags when using certain scripts with FF2, they now run smoothly in FF3. As for the start up time I cannot tell that there is an improvement but it might be different for you or on other platforms. With FF3 passing acid2 test web developers have another reason to look forward to FF3.

So stop crossing your fingers, Firefox 3 will be amazingly fast. :)

Greetz, WP

---

### Post by w0ng on 2008-04-11
I've definitely noticed FF3 to be much faster than FF2.

Can you explain exactly what you mean by FF2 being slow? 
The two main fixes for Firefox speeds are disabling ipv6 and fixing your network.http.* settings in Firefox's about:config

---

### Post by svaens on 2008-04-11
Q firefox 2 slow. What do I mean? 

A I was not so much talking about rendering or download/fetch speed, as generally usability as a GUI. 

For example, having over 10 tabs open, various web pages, navigating from one to the other takes lots of time. To click on one tag can take a whole second or two for the tab to switch. 

Another example, the venerable GMail is perfect ... 
For some reason, if i scroll the GMail page (with the roller, using the scroll pane doesn't provide me such bad performance) it seems to almost freeze the whole browser... 
It goes into this processing mode, and I see the page slowly, line by line, scroll down, long after I have stopped rolling the mouse roller. Eventually  the page catches up to where it should be, and I get my firefox back. 

These are my main issues with firefox in linux. I am using Gutsy Ubuntu Desktop, quite a vanilla installation. 

By the way. While I wasn't concerned about network issues here, I am curious,
why the hell would you want to disable ipv6 ?
And I also didn't know about this other fix.... 
Do you know much about it, to give a rough explanation, or provide a link to where I can read it?

Thanks for your replies so far! It is very interesting to hear about peoples experiences!

---

### Post by cdenley on 2008-04-11
Does gmail use flash or javascript? Is your system 64-bit? The only firefox problems I have is with flash, because on 64-bit systems, it needs a plugin wrapper to use 32-bit plugins. This plugin wrapper seems a little buggy. Is it possible the switching tabs issue could be related to your graphics driver? What graphics driver are you using? Are desktop effects enabled? Is all your memory being taken by your windows virtual machine while using firefox in ubuntu?

I've had problems with other software, I think in FreeBSD, where disabling IPV6 fixes an issue or improves performance. Most ISP's and routers don't support IPV6, and if software tries to use it first, then falls back to IPV4, it could affect performance when sending web requests. It doesn't sound like it would help with your issue.

---

### Post by svaens on 2008-04-11
HI, 

I'm running 32bit Ubuntu on a 32 bit machine. when i was having the problems which inspired this post, I didn't have any flash websites open. Just trying to view my gmail. 

I normally don't use firefox within my virtual machine..... in fact, i don't use the virtual machine much because of the fact it is on a external disk (my internal drive not having enough space to spare a full sized second OS). It was just an example. 
And the machine which I am running now (at work) is no sluggard... being a Dell with some sort of centrino processor... 2 gig or ram I think... NVidia graphics card... fast... should be. Although, I don't think the driver I'm using is the greatest... (nvidia driver for linux) ..
As for whether or not the graphics driver is to blame. 
I doubt it. If i run a different app, which uses tabs ... and make lots of tabs... there is no problem. Only with firefox. 
I guess then it probably IS a rendering problem, as it is probably the rendering which slows it down. Clicking through 10 EMPTY tabs isn't so fast either, but it is a hell of a lot faster than clicking through 10 tabs with actual content in.

---

### Post by pmaconi on 2008-04-11
I don't have any problems with performance on FF2 related to the number of tabs open. Right now there are 12 open and I can move between them without any noticeable lag. I did, however, have the scrolling problem that you have. In my case the problem was the video card driver. I updated to a newer one and the problem went away.

---

### Post by svaens on 2008-04-11
hmmm..... 

Perhaps instead of asking if firefox would improve, I should have asked:

what hardware (particularly video card) would people recommend, for best suited to work with linux Ubuntu.

I thought NVidia would have made a good choice (not that I had a choice) but I have had only problems at the start, and now really only crummy performance. 
And hearing stories of people changing video card drivers fixing such problems... makes me wonder, is this just another problem to add to my list with my nvidia GeForce?

I am using the non-free nvidia drivers (downloaded and installed using Envy, which turned out the best way to get it working at all) ..... 
I had been using before that the nv driver that comes with Ubuntu, but that didn't have any better performance, and the rendering of fonts wasn't so nice. 

I should really start another thread for this though.

---

### Post by RTrev on 2008-04-11
For what it's worth, I've been using Hardy for a while now, and just got Fx b5 recently.  I was blown away by the speed improvement!  GMail is now usable, moving between tabs is instantaneous, reloading pages is much quicker, and I've encountered only minimal oddities with it.  For example, every now and then I'll close Fx and then try to restart it and it tells me it's already running.  System Monitor in fact shows it still running.  If I just kill that process, then we're back to normal.

Also, of course, they've surfaced the UI controls for third party cookies again, which is a big plus in my book.

So, Fx 3 b5 is my main browser now, and I'm very pleased with it.

Disclaimer: I don't know how it runs under anything but the 64-bit version of Ubuntu Hardy 8.04 beta.

HTH,
Bob

---

### Post by gali98 on 2008-04-11
I like it a lot.... It has some cool features and runs a little better. Supposedly they worked out a lot of the memory leaks that were in firefox 2.
Kory

---

### Post by wolfen69 on 2008-04-11
FF3 is indeed faster for me, but i cant get streaming media to play very well, if at all. this was never a problem in FF2.

---

### Post by RTrev on 2008-04-11
> **wolfen69 said:**
> FF3 is indeed faster for me, but i cant get streaming media to play very well, if at all. this was never a problem in FF2.

Possibly you're hitting the oddity I've run into.  If I use my browser to watch streaming video (Youtube for example) I then cannot play any sound with any other application.  If I use some other application (say VLC) to play sound or video, then I can't get sound from streaming video.  It requires a re-start of X before I can use the one which is currently not working at any given time.

Not sure if this is related to your problem, but streaming video works fine here in 64-bit Fx b5 *provided* I've met the conditions above.

I'm guessing I don't understand something about Pulse...

HTH,
Bob

---

### Post by Ptero-4 on 2008-04-11
There's a setting in the PulseAudio control panel to enable multiple sound sources.

---

### Post by svaens on 2008-04-11
given that firefox is still in the beta phase (albeit, late stage) i should imagine that video streaming problems will be ironed out before final release. 
@RTrev, those are certainly words of encouragement! I have been looking forward to Hardy.. but was holding out to do a bit of an 'update all' as soon as both firefox 3 and hardy are final and released. I am relatively new to Linux... I wonder, (also should be in another thread) how much should I trust an upgrade Ubuntu option? I am I recommended to do a clean install, when it is time to install Hardy?

---

### Post by RTrev on 2008-04-11
> **Ptero-4 said:**
> There's a setting in the PulseAudio control panel to enable multiple sound sources.

Newbie question.. how does one get to the the PulseAudio control panel?

Thanks!

---

### Post by RTrev on 2008-04-11
> **svaens said:**
> given that firefox is still in the beta phase (albeit, late stage) i should imagine that video streaming problems will be ironed out before final release. 
@RTrev, those are certainly words of encouragement! I have been looking forward to Hardy.. but was holding out to do a bit of an 'update all' as soon as both firefox 3 and hardy are final and released. I am relatively new to Linux... I wonder, (also should be in another thread) how much should I trust an upgrade Ubuntu option? I am I recommended to do a clean install, when it is time to install Hardy?

Just my personal opinion, but I usually wait until a couple weeks after final release.. just to see if any major problems appear.  Then I do a clean install and customize to my likings.  This let's me miss the huge download flurry which slows things to a crawl, and I just watch the forums in the meantime and see how many people start screaming.  <grin>

Bob

---

### Post by svaens on 2008-04-11
I read just then (but may have misunderstood... ) that there are some applications that won't work with PulseAudio.... 
[http://www.linux.com/feature/119926?theme=print](http://www.linux.com/feature/119926?theme=print)

But sounds interesting. 
I often have problems with some application not releasing the audio properly, (firefox mostly) and me not being able to use my rhythmbox!

> and I just watch the forums in the meantime and see how many people start screaming. <grin>

@bob, I had exactly that idea ;) hehe.

---

### Post by dondad on 2008-04-12
Firefox3 seems to work well for me in Hardy, but most all of the extensions that I use still don't work in FF3. I used the nightly extension to force some of them, but there are still problems. Tab mix plus doesn't work properly and gmail and the gmail reader will not remember my password. I like the speed, but won't be using FF3 until the extensions catch up.

---

### Post by vishzilla on 2008-04-12
Hey does Firefox 3b5 follow the application font in Gutsy? Changing the application font doesn't change the font on the Firefox UI.

---

### Post by Ptero-4 on 2008-04-12
> **RTrev said:**
> Newbie question.. how does one get to the the PulseAudio control panel?

Thanks!

I'm still on gutsy, so I don't actually know. But there are threads on it.

---

