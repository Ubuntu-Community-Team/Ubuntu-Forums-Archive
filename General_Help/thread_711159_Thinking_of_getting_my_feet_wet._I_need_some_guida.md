---
title: "Thinking of getting my feet wet. I need some guidance."
date: 2008-02-29
forum: General Help
---

### Post by Tirade75 on 2008-02-29
Hi, I'm Tirade and I'm a windows user... "Hi Tirade!"

First I apologize if this isnt the right forum. Hopefully I dont get off to a bad start ):P

I've been glancing over at Linux pool for a while now and I see a lot of kids swimming and having fun but honestly I can't swim. I'm considering putting my toes in the water but I need a little guidance to (and some floaties) to push me towards the edge of the pool.

Ok, a recent drive crash started a spiral that ended up with me building a new server dedicated to file sharing/media serving. You can see the project [HERE]("http://s275.photobucket.com/albums/jj305/Tirade75/Media%20Server/")(Ignore the date stamp!). I'm proud of it but as you can see while its heavy on storage its light on power.

I started out by grabbing Server 2008 and I believe Im having a lot of issues that are beta driver related. I was going to just wipe and go to Vista 64 when I a co-worker sneakily planted the idea of Ubuntu in my head. It was a passing comment that was almost whispered instead of spoken but that seed has turned into a vine thats wrapped around my brain.

Anyway, this "media server" currently does 3 things (and I dont see this changing).

1. File Serving: I have roughly 3TB of FLAC files and 2TB of Mpeg2 rips direct from DVD. I have 4 other desktops and a laptop in the house. One of the desktops is a HTPC that needs seamless access to the movies/music. The other PC's need access as well but just for general file storing (my wifes pics/videos, my sons school work, etc).

2. Tversity: I use Tversity to transcode my movies on the fly to a format compatible with my HR-20 direcTV boxes. The boxes are basically limited media extenders and need a uPNP server running in order to connect.

3. h.264 transcoding: I use AutoMKV (essentially meGUI) to transcode my mpeg2 rips to h.264/AAC. The machine isnt beefy so it takes a few hours to transcode each movie. It requires things like ffdshow, x264, etc etc.


Thats it. Once the h.264 transcoding is done in a few months I dont even plan to keep a monitor hooked to the machine. All my data is stored on a hardware RAID6 using LBA-64bit so I need to be able to read that array.

So, on a scale from 1-10 my linux knowledge is about a .5 and thats only because Ive taken an SGI Irix course or 2 a LONG time ago.

So on to my questions...

Unbuntu seems to be the easiest way to make the transition. My hardware isn't tricky so I assume there is good support for it (I'll give a list of hardware at the end) and the GUI seems windowsesque.

I assume its fairly straight forward to set up file shares in Ubuntu and that even a novice could figure it out without too much pain? Will doing so affect my existing array if I install Ubuntu on a separate boot drive that isnt part of the array? Are the shares easily seen in windows with a path so that I can map or access the shares w/o a hitch?

I'm pretty sure Tversity does not run on Linux and that people havent had much luck getting to work in  a virtual windows setup either. I can probably run Tversity on another machine and have it transcode off the media server and then stream to the TV boxes. It adds another hop in the path but if thats how I have to go then so be it. Does anyone have any experience with this? Is there Linux software out there that does the same thing?

Now for the h.264 transcoding. I know this is being done on linux, but trust me Im REALLY nervous just thinking about installing Ubuntu, trying to learn new software as well is scary. Is there a way to run the transcoders Im used to in a virtual windows environment until Im ready to start wading into the deep end?

Last but not least... what version of Ubuntu is right for me? I wasnt even able to download it last night because I wasnt sure if I wanted Desktop or Server, 32 or 64, 6.0 or 7.0, etc etc. Any help here would be greatly appreciated.

Hardware:
Nvidia nForce 630a/7025 chipset mobo
AMD 64 X2 4200
2GB DDR2
80GB Sata boot drive
Intel Pro/1000 PCI-e Gigabit NIC
Areca 1280 PCI-e RAID controller

---

### Post by PreviousN on 2008-02-29
Whoa buddy!

Those things are certainly possible, but diving into that kinda setup is likely to cause some headaches. 

If you still want to do it, you know the risks (being very very frustrated). 

I'd recommend you just take a glance at ubuntu first. You may even try wubi first if you already have xp or vista installed:
[http://wubi-installer.org/](http://wubi-installer.org/)

Now, onto the more complicated parts. Well, what processor do you have in your computer? You didn't mention. That would let me tell you 32 or 64. 

I'd recommend going with the desktop version if its anything above 1ghz. The server install is essentially without a desktop/x server and text only. It's bound to be a huge headache if this is your first jump in the linux pond. 

If you still want the server edition, good fufffing luck ;-). 

Onto your questions:
1. Yes, you can set up shares. You can even password protect them a lot easier than you can using windows server. Samba is usually the best bet, especially if there are other windows computers around. 
2. Tversity...never heard of it. I'd recommend googling it. Try "tversity linux" in google. Alternatively, google has a dedicated linux search. [www.google.com/linux](www.google.com/linux)
3. I'm certain this is possible. It's a pain in the a though. I once tried it but couldn't get it figured out. This is because the H264 is a closed standard and there's legal issues involved in getting it to work easily. What you really have to do is get ffmpeg (the encoder) from source and compile it. There's guides out there but they are likely to drive you nuts. 

Why don't you reply with your response to my suggestions/tips and we'll go from there.

---

### Post by Tirade75 on 2008-02-29
> **PreviousN said:**
> 
Now, onto the more complicated parts. Well, what processor do you have in your computer? You didn't mention. That would let me tell you 32 or 64. 

Sorry, I updated the OP, but its an Athlon 64 X2 4200.

> I'd recommend going with the desktop version if its anything above 1ghz. The server install is essentially without a desktop/x server and text only. It's bound to be a huge headache if this is your first jump in the linux pond. 

If you still want the server edition, good fufffing luck ;-).

Youve convinced me that desktop is the way to go. Had I known server was all command line, it wouldnt even has been a question haha. So version 7 or 6 and 32 or 64?

 
Onto your questions:
1. *Yes, you can set up shares. You can even password protect them a lot easier than you can using windows server. Samba is usually the best bet, especially if there are other windows computers around.* -** Excellent. Can I avoid having password though? Vista for example is a pain if there isnt a passworded account on the machine for the share.**

2. *Tversity...never heard of it. I'd recommend googling it. Try "tversity linux" in google. Alternatively, google has a dedicated linux search. [www.google.com/linux](www.google.com/linux)* - **I did some googling and didnt have much luck but I didnt dig into it deep enough. I think the easy answer here is to just run Tversity off of another machine thats running Windows until I get comfortable.**

3. *I'm certain this is possible. It's a pain in the a though. I once tried it but couldn't get it figured out. This is because the H264 is a closed standard and there's legal issues involved in getting it to work easily. What you really have to do is get ffmpeg (the encoder) from source and compile it. There's guides out there but they are likely to drive you nuts. * - [B]Ive been doing a little reading and apparently there is no Avisynth support for linux and thats a huge problem. Considering that my transcoding is a short term project, I may just keep doing it on my main PC for now.
[/B]
Thanks for the quick reply so far.

---

### Post by PreviousN on 2008-02-29
I'd go with 64 bit edition. There is about a 30% performance plus for encoding video/audio from what i've read. 

1. Yes...kind of. If you add a user to samba configuration that is the same name and password as your user(s).  You can also enable guest account. I personally, however, prefer password access. 

I've got my linux server serving stuff to xbmc, so its pretty easy and compatable. 

2. Sorry to hear that. 
3. Also sorry to hear it. I dont' do too much encoding, mainly I rip dvds when I buy them so I can stream them to my xbox. The xbox isn't fast enough for H264 so I don't bother anyways. 


Ok, so go over to ubuntu.com and download the 64bit desktop 7.10 edition. I recommend 7.10 just for good times. It's what I use and its more current (even if 6.x is still supported).

Then, install! After your done, reply and someone will likely help you out (if not me - but don't count on it..). I usually kinda help people while I'm seeking help :-) and my question was answered. 

here's a link for samba: 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Tirade75 on 2008-02-29
Thanks for the help. I feel a little better after do some reading.

---

