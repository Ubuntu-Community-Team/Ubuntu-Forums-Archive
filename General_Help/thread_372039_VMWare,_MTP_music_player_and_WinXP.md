---
title: "VMWare, MTP music player and WinXP"
date: 2007-02-27
forum: General Help
---

### Post by disembodied on 2007-02-27
Alright, so this may belong in another forum, but I couldn't figure out which one so I posted it here:

I am running ubuntu 6.10 and have tried way too many methods to get my Creative MP3 player (Zen Vision: M) to sync only to have them all fail.

So anyway, I also was missing MediaMonkey on windows (I dual boot, but I missed having such an awesome media player in linux, which is what I keep my PC in most of the time). So I installed VMWare Server, winXP pro and MediaMonkey. Music plays fine and all that, but it won't recognize my MP3 player (which is an MTP device by the way). 

Now I know that the guest OS under VMWare isn't supposed to (or more accurately won't) work with any hardware that linux doesn't work with, but I didn't know if the player would be different. Ubuntu recognizes it as a camera, but thats it, so I was wondering if there was a way to get it to work under VMWare.

Thanks

---

### Post by disembodied on 2007-02-27
This may be too early to bump, but my stuff always seems to get dropped pages back and never gets looked at.

Thanks!

---

### Post by kodoku on 2007-02-27
I personally use Virtualbox, but I'm guessing VMWare works similarly.  The virtual machine runs ON TOP of ubuntu, not alongside.  So if a device doesn't work properly in ubuntu, it probably won't work in the virtual machine.

---

### Post by zanglang on 2007-02-28
By default Edgy doesn't have support for the new MTP players so you'll have to built some software from scratch. Check here:
[http://ubuntuforums.org/showthread.php?t=316246](http://ubuntuforums.org/showthread.php?t=316246)

Also have you tried using Amarok? Give it a whirl sometimes, you might like it. ;)

---

### Post by disembodied on 2007-02-28
Thanks for the info everybody... 
kodoku ~ I understand how it works, my thing was - ubuntu recognizes A DEVICE, just not the RIGHT device (it sees it as a camera), so I didn't know if that means it may work.

zanglang ~ I understand it is hypothetically possible to get ubuntu to work with an MTP device, but EVERY SINGLE method I have tried (gnomad2, MTPsync, MTPdude, amarok) has failed (obviously I know you install libmtp first and what not, I have followed specific instructions for all these).

If I were to install libmtp, and it were to recognize my device (in console, this has worked before) would that allow the program in my virtual machine to recognize it? Since technically ubuntu sees it and treats it correctly (just no program will).

Thanks

---

### Post by zanglang on 2007-02-28
Quick Q, for ubuntu when you compiled and installed libmtp did it come with some binaries like mtp_connect, mtp_detect and so on? (It's been a while and I can't quite remember if it does or not.) To check if MTP is working on your system, plug in the device and run mtp_detect. It should spew out the correct name of your device and other detailed info on it.

---

### Post by disembodied on 2007-03-01
> **zanglang said:**
> Quick Q, for ubuntu when you compiled and installed libmtp did it come with some binaries like mtp_connect, mtp_detect and so on? (It's been a while and I can't quite remember if it does or not.) To check if MTP is working on your system, plug in the device and run mtp_detect. It should spew out the correct name of your device and other detailed info on it.
Yeah this is exactly what I did (thats why I knew it was an amarok/gnomad2 problem and not libmtp) .

mtp_detect did detect my device just fine, but the program wouldn't... but thats not an issue anymore, I actually (as of yesterday) got gnomad2 to recognize my device and am able to transfer music... there are other problems (like playlists not working) but its at least better.

Also, I tried, after getting all that to work, to connect my device and have Media Monkey recognize it in virtual windoze and that still didn't work, so im assuming music players in general (or at least MTP players) won't work in a virtual environment.

If anyone comes along with a way to make the players work in the virtual world that'd be awesome, since I haven't found a transfer program for linux that does everything I want (thats my mission now) and Media Monkey does do everything anyone would ever need (and more).

Final side note, Media Monkey 3 is supposed to be released in the next few months and it uses SQLite instead of microsoft based databases and what not, and although the MM team themselves haven't said they will release a linux version along with it, the fact that MM won't be microsoft dependent anymore increases the chance of a linux version by making it easier to do! This is good news.

---

### Post by zanglang on 2007-03-01
I see... could be a bug with those applications you've tried, or some unnoticed mistake while compiling. Oh well, Feisty is just 1 month away, you might have better luck later on if you wait.

(You could also, like a lot of OSS developers who want to scratch a particular itch, contribute to the community by helping us make that perfect transfer app, but that's up to you. ;))

What's MediaMonkey written on? If it's C++ and uses a lot of Windows API calls changes of it getting port are kind of slim... (I'm still disappointed I had to switch from my foobar2000 media player :/)

---

### Post by disembodied on 2007-03-02
> **zanglang said:**
> I see... could be a bug with those applications you've tried, or some unnoticed mistake while compiling. Oh well, Feisty is just 1 month away, you might have better luck later on if you wait.

(You could also, like a lot of OSS developers who want to scratch a particular itch, contribute to the community by helping us make that perfect transfer app, but that's up to you. ;))

What's MediaMonkey written on? If it's C++ and uses a lot of Windows API calls changes of it getting port are kind of slim... (I'm still disappointed I had to switch from my foobar2000 media player :/)

I would certainly contribute if I had better programming knowledge - I can do some stuff a little bit, and I can edit other people's code alright... but I can't write a program outright... maybe sooner or later.

As for your question about MM, its not written in C++ but I can't remember what specifically it is written in, but a lot of the discussion over at the MediaMonkey forums is that version 3.0 (not released yet, still in beta) will be easy to port to linux/mac as opposed to the 2.x versions which were near impossible. I know one reason for this is the move from microsoft databases to SQLite for the database and also they mentioned a complete trashing of any MS APIs... the goal was to make MM 3.0 as independent as possible, which bodes well I would think.

On a slightly related note - I was using gnomad2 to transfer music to my creative player and noticed later that it doesn't maintain any sort of folder structure for my files... is there a way to get gnomad2 to do this or is there another program that does maintain folder structures?

---

### Post by toasterofirony on 2007-03-03
ASAIK Gnomad2 doesn't do recursive folder creation at all. I'm in much the same bind and trying everything that I can think of. It's even got to the stage where I'm installing kubuntu-desktop to try and encourage Amarok to recognise it.

*sigh*

Maybe I should have followed the crowd and bought an iPod?

---

### Post by andybleaden on 2007-07-30
I have a creative zen with mtp firmware that while I was on windoze I faithfully installed as an upgrade!Could only get it to work with gnomad 2 for a while which was a great help but not so user friendly as it could be for the reasons mentioned elsewhere. 

I have finally with help from a friend upgraded to feisty and with it the amarok with mtp support which finally works AT LAST!

This makes it much easy to transfer files and folders. Have not tried yet to create playlists so will update this when I get that sorted.

---

