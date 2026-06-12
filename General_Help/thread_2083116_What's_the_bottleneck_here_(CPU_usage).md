---
title: "What's the bottleneck here (CPU usage)"
date: 2012-11-11
forum: General Help
---

### Post by Rocket J Squirrel on 2012-11-11
I've resurrected an old computer and installed 12.04 on it, in hopes of using it to watch streaming videos with it. 

[LIST]
[*]Celeron cpu running at 2.6GHz, 
[*]1MB of RAM, [Edit: 1GB of RAM]
[*]82865G integrated graphics controller,
[*]the display is my HD TV and Ubuntu is driving it at 1920x1080 through the VGA port (I'm using a VGA > HDMI adaptor)
[/LIST]

It's choking on streaming videos, such as YouTube and national news shows. 

Even with the video in small-screen mode, htop reports the CPU running at 100%. In full screen mode, forget it -- too stuttery to watch.

I tried FireFox and Chrome and get the same results. 

With the video paused I see 15% cpu usage. Memory usage is 450MB out of the available 1GB, so I don't think it's disk swapping causing the problem.

Do I need a faster motherboard to watch full-screen videos?

---

### Post by idoitprone on 2012-11-11
> **Rocket J Squirrel said:**
> I've resurrected an old computer and installed 12.04 on it, in hopes of using it to watch streaming videos with it. 

[LIST]
[*]Celeron cpu running at 2.6GHz,
[*]1MB of RAM,
[*]82865G integrated graphics controller,
[*]the display is my HD TV and Ubuntu is driving it at 1920x1080 through the VGA port (I'm using a VGA > HDMI adaptor)
[/LIST]

It's choking on streaming videos, such as YouTube and national news shows. 

Even with the video in small-screen mode, htop reports the CPU running at 100%. In full screen mode, forget it -- too stuttery to watch.

I tried FireFox and Chrome and get the same results. 

With the video paused I see 15% cpu usage. Memory usage is 450MB out of the available 1GB, so I don't think it's disk swapping causing the problem.

Do I need a faster motherboard to watch full-screen videos?

No, you need a faster processor to run full-screen videos.
You cpu is the bottleneck. Flash is cpu hungry if you do not have a proper video card to offload the work. Since your integrated card is not worth mentioning, your cpu have to do all the work

---

### Post by pqwoerituytrueiwoq on 2012-11-11
if you did not make a typo in your ram info it would be the cpu
this may help you [http://ubuntuforums.org/showthread.php?t=2078303](http://ubuntuforums.org/showthread.php?t=2078303) it will allw you to play flash videos outside of flash and get hardware acceleration

---

### Post by mayagrafix on 2012-11-11
My guess is the driver for the Intel 82865G integrated graphics controller. The stock drivers included in 12.10 are pretty good right out of the box, but may need some tweaking for ur particular graphics controller since it is 7 or 8 years old. It would be nice if you could temporarily install a AGP video card and see if that solves the problem.

Also, you list 1 meg of RAM in the specs, but later you mention 1 gig. The later is good enough, the former is obviously not enough.

Instead of a newer mobo (which entails new CPU and RAM) try a SSD (solid state drive).

Good luck!:KS

---

### Post by Rocket J Squirrel on 2012-11-11
Oops -- 1GB of RAM.

---

### Post by Rocket J Squirrel on 2012-11-11
> **mayagrafix said:**
> My guess is the driver for the Intel 82865G integrated graphics controller. The stock drivers included in 12.10 are pretty good right out of the box, but may need some tweaking for ur particular graphics controller since it is 7 or 8 years old.

Er.... 

> **mayagrafix said:**
> It would be nice if you could temporarily install a AGP video card and see if that solves the problem.

The mobo only has PCI slots. 

> **mayagrafix said:**
> Also, you list 1 meg of RAM in the specs, but later you mention 1 gig. The later is good enough, the former is obviously not enough.

Yeah, sorry -- 1GB is the correct answer. Thanks, KS. 

pqwoerituytrueiwoq's suggestion -- using a script to open the Flash video in another player, sounds a bit tweaky for the Missus to use. 

I think I'd rather just hand this box over to someone in the office to use as a generic workstation, and concentrate on building one that can do a better job. Can someone point me to minmum specs needed for Flash videos and maybe a mobo with hdmi?

---

### Post by TenPlus1 on 2012-11-11
Hold on, I have a Compaq m2000 laptop with Intel 82852 graphics (older than yours) and a 1.5ghz Celeron processor (half the speed or yours) and 1gb memory...  From that I can play youtube videos smoothly and in full screen if need be...

What version of Ubuntu do you have installed, have you tried Lubuntu 12.10 ? and check out Google Chrome as your browser since it uses PepperFlash 11.3+ instead of the old 11.2 flash plugin most linux users are stuck with through the software centre...

[https://www.google.com/intl/en_uk/chrome/browser/](https://www.google.com/intl/en_uk/chrome/browser/)

---

### Post by Rocket J Squirrel on 2012-11-11
Thanks, TenPlus1

> **TenPlus1 said:**
> Hold on, I have a Compaq m2000 laptop with Intel 82852 graphics (older than yours) and a 1.5ghz Celeron processor (half the speed or yours) and 1gb memory...  From that I can play youtube videos smoothly and in full screen if need be...

I wish it were so here!

> **TenPlus1 said:**
> What version of Ubuntu do you have installed, have you tried Lubuntu 12.10 ? and check out Google Chrome as your browser since it uses PepperFlash 11.3+ instead of the old 11.2 flash plugin most linux users are stuck with through the software centre...

Well, as I mentioned in my OP, I'm running 12.04, and have tried this with both FireFox and Chrome. 

Lubuntu -- what will that buy me?

Anyone got a suggestion for an hdmi mobo & cpu and the other specs I need to gut this thing and rebuild it?

---

### Post by pqwoerituytrueiwoq on 2012-11-11
I will suggest using dvi to hdmi and analog audio, it is much less headache to get working, in my exp HDMI audio is nothing but trouble

[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.1100870](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.1100870) - cpu+mobo
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231394](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231394) - ram
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812117641](http://www.newegg.com/Product/Product.aspx?Item=N82E16812117641) - hdmi to dvi cable
[http://www.newegg.com/Product/Product.aspx?Item=N82E16882850012](http://www.newegg.com/Product/Product.aspx?Item=N82E16882850012) - 3.5mm analog audio cable
just use the 1st hdmi plug on the tv and the audio plug next to the vga plug

if you are using ubuntu (unity) try xubuntu (xfce) or lubuntu (lxde)

btw with that script you just make a luncher in the panel to click after pausing the video (if you-tube change the quality setting), have it run *video smplayer '-fullscreen -close-at-end'*  for example

---

### Post by Rocket J Squirrel on 2012-11-11
Thank you, pqwoerituytrueiwoq

I appreciate that you took the time to point me to some hardware. I have a follow-up question, if you don't mind. 

I popped into my wife's office to see how it handles the videos. Hers is the fastest machine we have: it has a Pentium dual-core E5500 processor running at 2.8GHz and is running Windows 7. [Edit: video is reported to be an Intel G45/G43 Express chipset.]

With a generic YouTube music video, the cpu was loafing at 35% usage, even in full-screen. But when I took a look at one of the American football sports feeds that I like to watch it was pegging at 100% most of the time. So her machine isn't powerful enough for those feeds. 

I know that comparing things like this under different operating systems may not be possible, but do you think that the mobo you suggest (which uses a Pentium G630 Sandy Bridge 2.7GHz LGA 1155 65W Dual-Core Desktop Processor and Intel HD Graphics BX80623G630) would do much better?

---

### Post by pqwoerituytrueiwoq on 2012-11-11
[http://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G630+%40+2.70GHz](http://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G630+%40+2.70GHz)

[http://www.cpubenchmark.net/cpu.php?cpu=Pentium%20Dual-Core%20E5500%20@%202.80GHz](http://www.cpubenchmark.net/cpu.php?cpu=Pentium%20Dual-Core%20E5500%20@%202.80GHz)

it would be about 30% faster
i only consider this benchmark for comparing if they have the same number of threads

flash is the devil incarnated
i will try to run a 1080p youtube and a 720p you tube at the same time in flash on my laptop using dual monitors, if it can do that that chip can do you should have no issue with that cpu i linked

---

### Post by mardybear on 2012-11-12
Hi Rocket J Squirrel...

Try disabling all necessary desktop eyecandy that isn't required.

When playing Flash video, do you have a process running called 'plugin-container'? To check, run 'top' via terminal, sort by CPU usage by pressing 'P' (capital P).

mardybear

---

### Post by pqwoerituytrueiwoq on 2012-11-12
I was able to play 2 1080p flash videos on youtube at the same time in fullscreen with my 2.3GHz Pentium laptop, so the 2.7Ghz desktop Pentium should have no problem with a single 1080p flash video
i can't try 3 as the Intel GPU only supports 2 monitors

---

### Post by Rocket J Squirrel on 2012-11-12
> **mardybear said:**
> Hi Rocket J Squirrel...

Try disabling all necessary desktop eyecandy that isn't required.

Standard Unity desktop with pretty photo of flower on it. Don't see what else I could disable?

> **mardybear said:**
> When playing Flash video, do you have a process running called 'plugin-container'? To check, run 'top' via terminal, sort by CPU usage by pressing 'P' (capital P).

Nope, no "plugin-container in the top 80 processes running. This running the Chrome browser. I'll try with FF, one moment, please. Oh yes, there is it. What do this tell us?

_pqwoerituytrueiwoq_: thanks for running the test. Before I get the new hardware, though, I reckon I'll give that idea on page 1 of this thread a shot: handing the playback of Flash videos over to another player, although installing and setting that thing up looks like Advanced Prgramming. I'll try to hack my way through it.

---

### Post by pqwoerituytrueiwoq on 2012-11-12
> **Rocket J Squirrel said:**
> 
_pqwoerituytrueiwoq_: thanks for running the test. Before I get the new hardware, though, I reckon I'll give that idea on page 1 of this thread a shot: handing the playback of Flash videos over to another player, although installing and setting that thing up looks like Advanced Prgramming. I'll try to hack my way through it.
i dont know what socket is on your current board, but if it is a 1155 socket, you may not new a mobo and ram

the attached file has a installer for you to run in the terminal, it will add a launcher under multimedia

---

### Post by Rocket J Squirrel on 2012-11-12
> **pqwoerituytrueiwoq said:**
> i dont know what socket is on your current board, but if it is a 1155 socket, you may not new a mobo and ram

Thank you. The CPU does not appear to be socketed. 

> **pqwoerituytrueiwoq said:**
> the attached file has a installer for you to run in the terminal, it will add a launcher under multimedia

That's very kind of you to do this. Alas, I cannot see any sign of an attachment. This might be what my wife calls "Male Pattern Blindness"?

---

### Post by pqwoerituytrueiwoq on 2012-11-12
> **Rocket J Squirrel said:**
> That's very kind of you to do this. Alas, I cannot see any sign of an attachment. This might be what my wife calls "Male Pattern Blindness"?
bottom of 1st post above signature

---

### Post by Rocket J Squirrel on 2012-11-12
Please forgive me. I've looked at all your posts on this thread. The first is #3 and I don't see an attachment above your sig, though I do see a link to the how-to thread. Is the attachment p-mailable?

---

### Post by pqwoerituytrueiwoq on 2012-11-12
it is the [1st post in the thread](http://ubuntuforums.org/showpost.php?p=12327256&postcount=1)

---

### Post by Rocket J Squirrel on 2012-11-12
Oh -- the first post in *that* thread. I thought you meant this thread. My bad.

Thank you.

---

### Post by Rocket J Squirrel on 2012-11-12
Say - and BTW - do we know whether Lubuntu will noticeably improve Flash videos on a computer like this one? (See OP for system description, including excellent typo.

---

### Post by BertN45 on 2012-11-13
> **Rocket J Squirrel said:**
> Say - and BTW - do we know whether Lubuntu will noticeably improve Flash videos on a computer like this one? (See OP for system description, including excellent typo.
The cpu usage is caused by Flash and the stream decoding, the operating system will make no difference. I also have an integrated intel video controller and a Pentium IV 3.2 GHz multi threaded and also that one gets loads of more then 90% on some HD 720p video from youTube. On some other movies it runs at 50% cpu load. I think it depends on how well the compression/decompression can handle the complexity of the frames. It stutters a little bit, but it runs on the limit of my internet bandwidth of 1.8 mbps/s. In my case internet is the real bottleneck.
If you do not want to spend money, you could set the you tube quality to auto, in my case it would run at 480p.

I also read somewhere that the intel drivers are overhauled in co-op between intel and canonical, maybe the problem will be solved in a couple of months. I have some 5-6 years old video cards lying around and could try one of those somewhere this week. One is 128mb Geforce 6200 and that is a standard PCI card.

---

### Post by Rocket J Squirrel on 2012-11-13
Thank you, BertN45.

Good point about lowering the quality of the YouTube stream to reduce stuttering when watching their videos. But my actual goal here is watching live sports feeds and the service that provides them doesn't give a way to do that, so I gotta make the computer faster. 

Regarding video card, your comment brings up a point. The video on this mobo is integrated, there is no card. However there are two empty PCI slots. 

Does anyone think there is joy to be gained by plugging in a card? 

(And if yes, then followup questions: what cards would be a good choice, and will Ubuntu find the card and utilize it?)

_And to pqwoerituytrueiwoq_: I'll tinker around with the hand-the-Flash-to-another-player tip today.

---

### Post by BertN45 on 2012-11-13
I am not very familiar with video cards. The PCI card I mentioned GeForce 6200 has a performance worst then my integrated Intel video according to the following benchmark results: [http://www.videocardbenchmark.net](http://www.videocardbenchmark.net)
I think that card is one of the few still available using standard PCI.

---

### Post by mardybear on 2012-11-13
Hi again Rocket J Squirrel.

Unity is not a lightweight desktop environment. It utilizes system resources that could otherwise be used to run higher definition video. Lubuntu would be a good alternative. You can simply install/boot to another desktop environment without reinstalling your entire OS. I use Openbox myself...about as lightweight as it gets as it is simply a window manager, not a full blown desktop environment.

If you are going to try a dedicated graphic card, do NOT use an nvidia product...lots of problems with linux systems. In many cases, the onboard video will work pretty good as it's designed for your hardware...your mileage may vary...trial and error.

To disable plugin-container while running Firefox enter 'about:config' as a URL on your Firefox browser, use the search below to find dom.ipc.plugins.enabled, double click on it to change true to false, might have to restart Firefox. This will disable plugin-container (not Flash), which will help your system run leaner and should improve your video frame rate.

Also disable any unnecessary services to help your system run lean. I use Ubuntu 10.04 so can't comment specifically on Unity and Ubuntu 12.XX. Examples that you might not use, blue tooth, printer and scanner, etc.

mardybear

---

### Post by Rocket J Squirrel on 2012-11-13
Thank you Mardybear,

With plugin-container disabled, FF still takes up 100% of cpu even running at 240p resolution. This with a generic music video on YouTube. With the video pauses, cpu usage drops to 24% or so. Other than FF, Terminal running htop is the only other application running. 

FF: 18% cpu
htop: 4%
/usr/bin/X 2%

other stuff below that.

---

### Post by mardybear on 2012-11-13
Hi Rocket J Squirrel...

Too bad - that's pretty heavy resource use. As long as your frame rates are okay but running at 240 pixels is poor.

Have you tried disabling Flash hardware acceleration. Pause a Flash video, right click on the video and select settings, uncheck enable hardware acceleration. Any better?

If not, post the results of 'sudo lshw' from terminal...curious about your video chip.

mardybear

Edit: Nevermind sudo lshw, forgot you already mentioned your graphics chip...it seems to be a problem with Ubuntu. See if you find anything useful here, otherwise try a different video card:
[http://www.google.com/search?q=82865G+integrated+graphics+controller&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=seamonkey-a](http://www.google.com/search?q=82865G+integrated+graphics+controller&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=seamonkey-a)

---

### Post by Resistent on 2012-11-13
Try LUBUNTU ! 
I think your hardware is good enough. You will be suprised! 

The Windows Vista on my Laptop was horrible slow.. then I deactivated the "Windows Search" service and Windows worked faster. But I wanted to get rid of Windows, It was a pain for long time (Win 95, 98, XP, Vista in my life)

My Laptop looks like:
- 1 GB RAM
- Intel Celeron M430 1.73 Mhz
- Intel 943GML (Calistoga)+ICH7+M

So I decided to try Ubuntu and installed it with the Wubi Installer. In the installer window I took the standard "desktop environment" which was called "Ubuntu".
Horrible, it was horrible, again I could not do anything, Ubuntu also loaded very slow
like Windows. 

Then I installed the packages for the Lubuntu "desktop environment". After that, I could login with the "Lubuntu" Look and Feel. Very great! Fast and I can watch youtube videos without problems. LibreOffice? No problem. I am very glad that my Laptop is usable. For what you need the different special effects for dissapearing windows etc.. Isn't that also the reason why the quality of movies is so bad? The too much beautiful explosions and whatever, and the reason the newest movies are boring. The meaning actor dissappears. 
In Lubuntu, no need for special effects, I want to surf the web, the important content is INSIDE the web browser, and not around it.

Only Lubuntu will be installed on my machines from now on. Nothing else.

---

### Post by Rocket J Squirrel on 2012-11-13
mardybear: Interesting. I paused the flash video, right clicked on it, a menu popped up -- briefly, then FF crashed. Re-launched, tried again, and FF crashed again.

[Edit: In chrome I can enable/disable hardware acceleration w/o a crash. It has no visible influence on quality.* In 240p your generic music video on YouTube clocks in at 88% cpu, unlike FF which ran at 100%.

This is pretty poor performance, I reckon.]

*[EDIT EDIT: which ain't great.]

---

### Post by mardybear on 2012-11-13
Hey Rocket J Squirrel.

Yeah that's pretty poor performance...i can watch 240 Flash videos okay on my celeron 700MHz system :)

When i googled your video hardware and added Ubuntu, it seemed many Ubuntu users have had performance issues/given up on that graphic chip. As mentioned, you could try a different graphic card....or use Chrome if the performance is acceptable.

Few last things i would try before giving up:

I assume you've tried clearing all of your Firefox cache?

Try unchecking/checking Firefox, preferences, advanced, general tab 'use hardware acceleration when available'.

Try closing Firefox and renaming the following (if they exist on your system, make sure your file manager is set to show hidden files). Restart Firefox.
/home/your_home_directory/.adobe
/home/your_home_directory/.macromedia

Any improvements?

mardybear

---

### Post by Moose on 2012-11-13
1 MB or RAM? LMAO i wanna see Skyrim running on that!

---

### Post by Rocket J Squirrel on 2012-11-13
mardybear: Hardware acceleration off, .adobe and .macromedia renamed, same lousy performance.

---

### Post by Rocket J Squirrel on 2012-11-13
Say there pqwoerituytrueiwoq - I sent you a PM about setting up the flashVideo thingy - did you get it?

---

### Post by Rocket J Squirrel on 2012-11-13
Update: I installed LXDE and ran the test again. Here, the cpu was running 80% - 100% @ 320p. It was almost watchable, but full-screen, no way. 

I'm waiting for some clarification on how to install flashVideo before I give up on this mobo and upgrade.

---

### Post by Resistent on 2012-11-14
Other ideas:

Try other Flash Players (not from Adobe), there are some alternatives.

Try Google Chromium instead of Google Chrome. 

Make an update of everything with..
1.) sudo apt-get update
2.) sudo apt-get upgrade

---

### Post by Rocket J Squirrel on 2012-11-14
Hi Resistent,

Good suggestions, thank you. I am getting almost watchable 320p video running Chromium in LXDE. But still not good on full screen and quite lousy when watching the live sports feeds I'm interested in. These latter don't have any way to select quality, unlike YouTube; they are what they are.

Regarding using another flash player -- since the feeds are streaming into the browser, how would one replace the one in the browser with another flash player?

---

### Post by pqwoerituytrueiwoq on 2012-11-14
google chrome does not use adobe flash it uses google's pepper flash
some times it is better, and sometimes it it worse

---

### Post by Stonecold1995 on 2012-11-15
If you're fine with not using Flash, you may be able to use YouTube's experimental HTML5 support.  Otherwise you could try VLC Media Player, I think it has support for streaming video (I use to occasionally watch YouTube on VLC).  If streaming is still too slow, try downloading the video with youtube-dl (it's in the repositories) and watch it offline with a lightweight video player.

And I think the bottleneck here is the CPU.  1 GB of RAM is fine, and unless you're running memory-intensive programs at the same time it shouldn't be causing any problems.

---

### Post by TenPlus1 on 2012-11-15
I tend to run UMPlayer and use the built in YouTube player to watch my videos so that it doesnt use flash but instead the native codecs of mplayer which play videos a lot smoother...  It will let you search YouTube and even select the resolution to play and record with...

[https://launchpad.net/~webupd8team/+archive/umplayer](https://launchpad.net/~webupd8team/+archive/umplayer)

---

