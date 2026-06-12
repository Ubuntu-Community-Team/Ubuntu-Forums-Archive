---
title: "program to deal with yi and other wifi cameras"
date: 2024-03-16
forum: General Help
---

### Post by jgw on 2024-03-16
I am trying to find a linux based program that can handle multiple wi wifi based cameras.  I recently bought 2 1080 wi home cameras and to hook them up is pretty simple and, I suspect that connection is pretty much the same for other cameras as well.  The problem is that windows programs seem to be restricted to specific cameras.  I have no real experience with this stuff.  I had a camera setup which worked ok for about 15 years, each camera wired into base, then went dead.  So, then, I went out and bought a couple of wi cameras.  Wi does not deal with linux, its microsoft or nothing.  That being said I also suspect that wi fi is wi fi and there are a number of linux programs that all seem to deal with wi fi.  My ignorance about all of this is serious.  I have no idea, for instance, what "IP camera" means.  I have been reading and that seems to be the standard. 

What I would appreciate is anybody's thoughts on which of the linux/ubuntu programs that can handle multiple brands of wi fi cameras.  That would allow me to use virtually any wi fi based camera (hopefully)

Thank you!

---

### Post by TheFu on 2024-03-16
Perhaps if you posted the exact models for each camera, someone could help search for the information you need? ** "camera" is pretty generic.**  Is it a PnS, a DSLR, mirrorless, doorbell, security, webcam, game-cam, what?  More details will likely get better answers.

wifi is like the ethernet cable.  Similarly, there is a *protocol* that has to be supported on both sides to work.  With cameras that only support MS-Windows, it is extremely likely the camera maker didn't make the protocol public, so we have to use their program.  That can bring added features, but it also makes the camera less open.

For example, I have a camera that doesn't have any desktop OS software at all. It only works with an Android app AND only if it can get to the internet.  No internet, no access.  Seems companies want to gather information about how we use their products and don't give us the choice to volunteer the information. They choose to take it.

Hopefully, the vendor you picked is nicer and not stealing your data.

IP cameras are usually more expensive, but they should use standard protocols that lots of different platforms support, including Linux.  Look for the specific protocol for each of your cameras, then look for native Linux software that supports the correct version of the protocol.  I wish you luck.

In the end, with my camera, it was just easier to pull the internal storage when I wanted to get video/images off it.  I hope you aren't stuck like I am.

---

### Post by jgw on 2024-03-16
Thank you for the response.
I have two:
YI 1080p home camera ai
wifi: 802.11bgn
model YYS.2016

I also have a couple of other cameras, one of which is imou camera and another I have to find but they too rely on wifi.

the YI camera is pretty simple.  You download their program, I have it on my phone.  To set it up you put the camera and phone together and the camera reads one of them boxes with strange and that's it You also have to tell the program the yifi password.  Its a little more than I said but that is pretty much it.  

I have, basically, two wi-fi's one covers my entire house, etc. and the other is there because some things require a password.  Both are connected to the same internet connection.  

The YI program does not have linux which means I can't connect to my TV which is helpful for us.  I currently have a wire connected computer camera that works fine (cheese) and we can see when we want to but it just shows the front room.  I guess I could run a bunch of wire around but I am trying not to do that. 

My problem is that I bought the YI cameras as they were not expensive and I neglected to see if they would work with linux - they do not!

If you do a internet search for: linux yi home camera 
You get interesting stuff such as:
[https://www.home-assistant.io/integrations/yi/](https://www.home-assistant.io/integrations/yi/)
[https://forum.yitechnology.com/t/how-do-i-view-my-cameras-on-linux/10301](https://forum.yitechnology.com/t/how-do-i-view-my-cameras-on-linux/10301)

---

### Post by TheFu on 2024-03-16
> **jgw said:**
>  
My problem is that I bought the YI cameras as they were not expensive and I neglected to see if they would work with linux - they do not!


I have a cheap Chinese 1080 wifi videocam.  Got it to find the type of critters in the attic. Turned out that was just a 1-time visitor, looking around.  Mostly, it was squirrels.  As I said, it only works with their android app and only if internet is up.  I tried to find another method to access it. Was completely unsuccessful.

My location is pretty safe, so having video cams looking outside isn't needed. I don't want any where humans are, except under very specific needs. All the data is sent to China, which is something I don't want.  That's what I get for going cheap.

Hopefully, someone with similar wifi videocams to you will see this and post what they do.

Found this: [https://www2.yitechnology.com/support/answer/id/3/tid/0/qid/12/oid/_](https://www2.yitechnology.com/support/answer/id/3/tid/0/qid/12/oid/_) which is pretty clear that you have to use their web-portal or android app to get anything, unless you pull the SD card out.
> Option 1: Save the video clip or image needed to your smart phone using the YI APP, and then export the files from your smart phone to the computer.
Option 2: All the files are stored in the microSD card in the camera. Extract the microSD card from the camera and insert it into your computer to export the files.
Option 3: Detach the camera from the holder and connect it to the computer using the micro-USB data cable (the charging cable provided with the camera is not a USB data cable so it cannot be used for data transportation).

It appear that some people have created alternate firmware to get an RTSP feed directly from the camera. There's some risk of bricking the camera, so use at your own risk. [https://github.com/roleoroleo/yi-hack-Allwinner-v2#is-my-cam-supported](https://github.com/roleoroleo/yi-hack-Allwinner-v2#is-my-cam-supported)  **Verify the firmware is actually for your version of the camera!**  I didn't and it isn't listed with the "YYS.2016" model.  There are other projects for other cameras.

I need to see if my cheapo cam has alternate firmware. I'd rather not use Android for security stuff. I don't trust android at all.

---

### Post by jgw on 2024-03-16
Thanks for the reply!

You are, exactly, where I am.  I had been thinking that if all it needs is a wifi connection everything would be fine and dandy.  Apparently, what one needs is a camera that will simply connect by way of wifi.  This is what is called a pc camera (I think, so far).  I think somebody told me that these are pricey.  I just went to ebay and they start at 8.00 and go up from there.  Basically, they are not pricey unless you have the bucks to spend, which I don't (my wife calls me 'cheap' which is true).  All I want to do is to put a camera on my front door (to see who is there) and my front room (for now).  I can do this with the YI cameras I do have but I am not a happy camper and will probably get a couple of pc cameras eventually as, in theory, those will work with any wifi.  

Oh, YI is a Chinese company too and, I am sure, they are going to waste a lot of time seeing who is at my door or in my front room.  This company is also anxious to allow me to use their part of the cloud (not interested).  I have a little of that and its all I need and its mine.  Its strange.  There are A LOT of people celling parts of the cloud today and its very very strange to me. 

My wife and daughter are off to Europe next month and she can then also see home with her phone.

Here is ebay: [https://www.ebay.com](https://www.ebay.com)

then search for: pc camera wifi

---

### Post by TheFu on 2024-03-16
pc camera usually doesn't mean what you think.  I would search for "IP camera" and be 100% certain to look for compatible Linux software like ZoneMinder in their marketing materials, unless you plan to try and load after-market firmware (possibly bricking the camera).

For years in the early 2000s, I connected a standard $20 USB webcam to a local computer here and pointed it at my front yard.  Then I wrote a small script to snap a photo every 30 seconds.  From anywhere in the world, I could view those images with any browser.  It was interesting, but not exactly useful, since my home office can see the street and form the upstairs hallway, I can see who's at the front door.

When I first got the Chinese wifi-camera, I placed it in a front window facing the street.  Every vehicle that passed cause a motion alert.  We don't have many visitors to the front door, so that really wasn't too useful.  Deliveries can be placed behind a bush there, so only a few neighbors see it after the truck leaves.  

Anyway, we all live in different places and have different security needs.

My home has woods behind it, so all the most interesting stuff happens out back.  Lots of critters to see from coyotes, deer, owls, chipmunks, squirrels, hawks, cardinals, bluejays, sparrows, opossums, and far too many raccoons.  I've heard some foxes, but never saw any.  The first time any deer showed up was a bit of a shock. There really isn't any food back there for them. There are more critters back there, but I don't see the snakes and turtles through cameras. They move too slow to see. ;)  **The rabbits are just so cute!**  Too bad they prefer to eat my grass and never touch the weeds.

---

### Post by jgw on 2024-03-17
I live in Port Angeles, WA  I live 5 blocks from the straights of juan de fuca (canada) and on the other side there is the Olympic National Park and mountains (about 1.5 miles the park starts).  

I went to ebay again (they normally sell stuff for the right price) and this time the low price for cameras was 5.00 (small little things) to Wireless Security IR Camera System Outdoor Home 5G Wifi Night Vision Cam 1080P for about 7.50   (pre-paid shipping)

I am not sure what I am looking at but, for that kind of money I think I will order one just to see how it works.  

One of my worst habits is that if I see something cheap I tend to buy it just to see what it does.  Its a bad habit but I really don't spend much on it and I don't do alcohol, etc. really don't need much so why not?  The bad part is that I seem to have a LOT of little things laying around.  After a while I no longer what they are for.  Its kinda embarrassing.  

Just tried to order it and its sold out.  I will continue until I find one that looks good and is available.

Later!

---

### Post by synergy-now on 2024-03-19
Windows version works in Wine from [https://www.kamihome.com/firmware/](https://www.kamihome.com/firmware/) don't download from Yi site it will not work

---

### Post by MAFoElffen on 2024-03-20
Here are 8 (1 is paid/ rest are free): [https://www.makeuseof.com/tag/awesome-diy-security-camera-clients-linux/](https://www.makeuseof.com/tag/awesome-diy-security-camera-clients-linux/)

Here is another list, though some are for Windows and OSX: [https://medevel.com/19-free-os-ip-camera-software/](https://medevel.com/19-free-os-ip-camera-software/)

---

### Post by jgw on 2024-03-20
I have, pretty much, given up on yi/kami.  Its the strangest and worst company I have ever dealt with.  I now have no less than 3 passwords and only one may work (or none and I have to setup yet another one)  I have setup one camera for my wife to take on a trip so she can check the house wiles traveling.  When she gets back I will sell off the two cameras and move on.  When I ask a question I think I get an ignorant robot so I go back and demand a human and I get a human that is, if possible, more confused than I!  Its simply bizarre.  Sometimes a password will only work on kami and, then, the same password will only work on yi - its always a crapshoot.  I have yi cameras but to set one up I was sent to kami.  It just goes on and on and on.

I would not suggest this outfit to an enemy!  

I really do think their cameras are pretty good though.  I also suspect that if I was running Windows or, the program that runs windows in Ubuntu, it would be easier but I left Windows a long time ago and am not interested in going back.

Oh, one other thing.  You also, for instance, cannot hook up two phones to the same camera.  Took me a while to find that information.  They have a pile of places on the net and one really can't tell what is what.  Then they want to hook you into "the cloud"  too.  I already have a place there if I want am not interested but they just keep trying which is a waste of everybody's time.

---

### Post by HermanAB on 2024-03-22
In my experience, cheap streaming cams all use  free software and therefore run RTP/RTSP streams.  You should therefore be able to discover the IP address and port with tcpdump and view the video with ffplay, gsplay, mplayer, videolan etc.

Maybe see this: 
[https://www.aeronetworks.ca/2022/01/linux-security-cameras.html?m=1](https://www.aeronetworks.ca/2022/01/linux-security-cameras.html?m=1)

---

### Post by jgw on 2024-03-22
Thank you for the reply!

I'll give it a try and see what happens.............

---

