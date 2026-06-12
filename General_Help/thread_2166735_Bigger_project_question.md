---
title: "Bigger project question"
date: 2013-08-10
forum: General Help
---

### Post by ghost25 on 2013-08-10
Hey all, been a while since I've been on here, since before the hack in fact. In the time since the hack happened however, I've been working on a "little" project at home.

I've got a few computers (fortunately, the wife doesn't really care as long as they're not in pieces on the floor). With the exception of one box running Windows XP Pro (hey, gotta have something running actual Windows in case something drastically wrong pops up!) all of them are running some version of Ubuntu. I've got a couple laptops, some wireless devices (phones, tablet, the like), and a couple towers. One of my towers is acting as my media server. The other Linux tower is a SFF "breadbox" setup that I'm hoping to plug into my TV and home theater system so that I can use it as a bit of a music center. Here's the thing though, is I want to keep all media on one box and remotely access that box from all the rest.

I know hooking up the computer to the TV itself won't be that difficult, but what I'm more worried about is that since I want to use a smaller hard drive to cut down on power consumption (hey, I've already got one monster running, don't want to be overloading circuits and the power bill!) so all I really need is better RAM, GPU and CPU. I've got plenty of small drives I can use that are <1GB, although I'm willing to go as big as a 5GB drive. The other reason I need a smaller drive is because most if not all of my equipment is older, and I can't really use or afford to upgrade to SATA, so IDE it has to stay.

I need to find the smallest possible version of Ubuntu (personally, I'm willing to experiment with stuff but my wife isn't too comfortable with anything beyond Ubuntu... and she used to use Windows!) that has a minimum amount of crap to worry about. I can remove programs that I know I won't be needing, such as GIMP and Klondike, and I can find some good media players that would play nicely with networked media (movies and music, some photos).

What's the smallest version of Ubuntu available that's LTS that would allow this to happen? BTW I'm comfortable with using SSH to remotely switch things up, but it needs to have a good GUI so she can use it via either WiFi or wireless keyboard/mouse. Thanks for any help, and I may end up posting more questions as I get this setup going.

---

### Post by Boab1993 on 2013-08-10
Depending on wether you want functionality or flash graphics your choice  would either be xfce based OS like xubuntu or ubuntu studio, or  lubuntu.

All xfce systems provide a very smooth and flashy  interface, at the cost of some disk space and memory usage, as it stands  xubuntu is a minimum of 512MB and 5GB disk space required, other  varients are similar to this size.

Lubuntu is still very nice and  friendly but isnt 'as' good looking as xubuntu, but only requires 256MB  of memory and 1GB(?) disk space.

The latest LTS of both i think are 12.04, but i could be wrong.

Another OS i dont know much about, but im pretty sure from a TV stand point is pretty good, is mythbuntu, i would check it out.

Hope this helps

---

### Post by ghost25 on 2013-08-10
Thanks Boab, those look like something I'll have to look at screenshots and reviews for.

Additionally, I started thinking it over and I'm debating on something, maybe you or someone else can give me some insight. Since I'm trying to do this project on the cheap (baby on the way come Dec), I kind of wanted to use existing hardware that I have, and I thought about using my SFF PC for this. Low profile, low power consumption, and I already have a compatible video card for it; on the other hand, it *has* been a long time since I've bought any computer stuff beyond a replacement laptop and/or smartphones and a tablet. I was looking at Newegg, but since I'm one who likes using older hardware it seems more and more that I'm out of luck if I want to have something that DOESN'T have HDMI or SATA. 

Do I still want to just use my SFF since I already have it and can easily modify it if needed (gotta love expired warranties!) or should I save some money [ha!] and buy an inexpensive rig? The reason I want the older hardware is so that if anything does break, I can just replace it with parts I already have.

Thoughts? Opinions?

EDIT: Okay so I did a little bit more research, and remembered hearing something many years ago called Puppy Linux. Now, I haven't played with this yet, but it seems like this would be an ideal setup. Small (about 100MB), can run off removable media, and can save progress... sounds like it could be a winner. Any thoughts or comments on a C&C Ubuntu vs Puppy?

---

### Post by whatthefunk on 2013-08-10
Im a little unsure of what you want to do.  You want to make a small pc that will store data that can be accessed by all the other pcs?  If thats all you want to do, you might not even need a GUI.  Ubuntu server only requires 1 GB of diskspace.  If this box is going to be hooked up directly to the tv, then youll probably want some kind of GUI though.  Crunchbang is great on low resource systems.

One thing Im confused about though is that if you have all your media on this box, youll have to have a large hard drive to store it all on.  So you really arent limited on space, right?

---

### Post by ghost25 on 2013-08-11
I may have mis-typed... Basically, I have a home network set up with a large hard drive on one computer (this one will be getting upgraded when I get the money) that holds all my media. This PC also runs my cloud printer, so it kinda has to be on constantly. Fortunately, this one doesn't have much in terms of power requirements, in fact if I really wanted to I could probably modify my PSU to minimize the amount of wires coming out. The horsepower would primarily be to pull music off the server and play it locally.  I have a smaller computer, pretty good in terms of horsepower, an iDeq5000 IIRC, that I want to have as the unit set up to play networked music, as well as Pandora internet radio and the rare YouTube video. I do however need a GUI, as my wife isn't comfortable with CLI.

The reason I want the small hard drive, as I said, is so that there's less power requirements for this box. Here's what I'm figuring then. I have the one Linux desktop set up as my server, with the rest of my devices connected to that via SSH. My laptop for now is not portable, dead battery. My TV does not have HDMI. I have a couple wireless keyboard/mouse kits laying around for almost-optimum control (would like to eventually set up voice control but not worrying about that for now). So, I want to take my SFF and hook it up to my TV, with minimal system performance so it's not wasting power on music, and use that to only play music from the server. Being a larger TV I need a large-display compatible, "pretty" version of Linux to run. If I could figure out how to just run this device off of an SD card I would probably do that. But, that isn't gonna happen yet, so next best thing is to run off a small HDD.

Ergo, small, low power PC with good networking speed and small hard drive pulling music from server, the music found on this device will only exist as symbolic links. Hopefully that makes it a bit more clear.

---

### Post by whatthefunk on 2013-08-11
Ahh....your music is not going to be on this machine?  You basically just want this to connect to your TV?  I run KDE on my computer and feed it to my TV.  Looks nice and runs great.

Clean
[IMG]http://i.imgur.com/HbBTNxUl.png[/IMG]

With Amarok music player
[IMG]http://i.imgur.com/W1FNZwyl.png[/IMG]

With Amarok and the menu button active
[IMG]http://i.imgur.com/2PMctxyl.png[/IMG]

Although KDE looks fantastic, it isnt necessarily great with resources.  You could do something similar to this with Lubuntu or Xubuntu.  After install, purge everything not related to multimedia.  On the desktop, get rid of the panel (useless on a TV) and add a big menu button.  Customize the menu to have your media players and file managers easy to access.  Finished.

---

### Post by ghost25 on 2013-08-11
I actually really like the look of that desktop layout. Only one problem  that I can see... how big is your total install, and does that include  anything on your rig besides multimedia? Like I said, I want to keep the  physical size of the drive down (If I have to I can run off a USB drive  but I'd rather have the slight speed boost that comes with a real  drive) to avoid excess power consumption. If that setup has been trimmed  down to only be a couple of gigs at most, that would be great.

---

### Post by whatthefunk on 2013-08-11
My install is at about 12 GB right now.  This is my main computer and has pretty much everything on it that I need.  Im guessing that I could easily cut it in half if I got rid of all the non-multimedia stuff.

Why not just connect your media server to the TV and cut out the small computer all together?

---

### Post by Boab1993 on 2013-08-11
I had a look into mythbuntu, turns out you can actually live stream a form of tv - 'mythTV' - which ill have to look into, but heres the system requirements

[http://www.mythbuntu.org/support](http://www.mythbuntu.org/support)

Also an attached screen shot of what it can look like, i believe.

---

### Post by Boab1993 on 2013-08-11
On the other thoughts you had about Puppy etc its a great little OS, especially if your stress testing or need an alternative to say a broken windows copy. 

Personally ive never used for anything else, but id have a look into what media performance it has, if it works, it works, cant complain.

But most Ubuntu alternatives, apart from say edubuntu and ubuntu studio, are very old hardware friendly, esspically the likes of xubuntu and lubuntu, They were created with this in mind. The main problem with most old systems and these OS are the lack of RAM or processor clock speed. 

If you need to upgrade this - im not very experienced in old computer components - i imagine it should cost you too much, bare in mind that the minimum for alot of ubuntu based installs is 512MB.

I also noticed in your question you mentioned how you want the system to have a network drive set-up, essentially. If you are unfamiliar with how to do this, someone on the forum will drop advice.

---

### Post by Cheesemill on 2013-08-11
I know you want to use what you already have but I'm going to suggest something different.

Get yourself a [Raspberry Pi]("http://www.raspberrypi.org/faqs") for $35 and put [OpenELEC]("http://openelec.tv/") on it. The things are tiny and the power consumption will be far less than the hardware you currently have (I actually have a couple that are powered from the USB ports in the TV they are attached to).

Even if you don't go for a Pi then Take a look at OpenELEC as your OS as a full install is only around 100MB and the UI it uses is specifically designed for using on a TV.

---

### Post by ghost25 on 2013-08-11
I'd actually looked at the Raspberry Pi before but the thing is, they seem to be all made with HDMI and to find a VGA is very rare, even more so than trying to find one that might perhaps support S-Video. My TV is a rear-projection that was I guess a "transition TV" in that it can display HD video but lacks the HDMI (how that works, I don't know). That being said, I do wish to keep all older hardware because I don't have the money to be buying new stuff or upgrading beyond similar capabilities that which I do have.

Can you tell me if OpenELEC is built with roughly the same capabilities/dependencies as Ubuntu? I figure I can transfer libraries or at least repositories from one of my other Ubuntu boxes if need be, and why not keep everything running more or less the same backbone?

---

