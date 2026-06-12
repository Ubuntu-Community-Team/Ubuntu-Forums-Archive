---
title: "Easy (for child) VOIP software compatible with Windows too"
date: 2020-02-10
forum: General Help
---

### Post by makem2 on 2020-02-10
I am attempting to help my 7 yr old g/son Scratch programing online.

We both have Teamviewer installed and can manage both computers but need voice feedback as his typing chat is to slow.

I installed Teamviewer because it has a video conferencing facility but neither work. His audio icon is muted and I cannot communicate with his audio or vidio! Both have a greyed out panel below when I select them.

I am unfamiliar with Windows firewall settings but I know Xubuntu ufw is inactive when testing. If we can control each others machine I would expect Windows firewall is correctly set.

So, I am looking for a VOIP program, preferably free, which he can manage. Assuming if he can then I can too!

I use Discord but I think that would be to complex for him at the moment. I am an administrator on his Windows 10 machine so can remotely install.

I have searched for a suitable program but would appreciate assistance to save testing only to find it's not suitable,

---

### Post by TheFu on 2020-02-10
Would any browser-based solution work?  [https://talky.io/](https://talky.io/)  Just needs javascript and webRTC enabled.

If you want more control, I've deployed nextcloud with the "talk" extension. That provides video conferencing, chat, and voice.  Nextcloud is a little more than most home-only users might want, but it has lots of plugins, and let's me control how has access, how secure any connection will be, etc.

VoIP is a hassle.  Do you want to run a PBX?  I did that for about a decade before deciding to pay a provider $5/month and be done with it.  My phone system with 6 handsets connects to an ATA, which makes the SIP connection to the provider.  I use my phones just like any other phone - call grandma, friends, but point-to-point connects are a pain.  WebRTC is 100x easier.

---

### Post by makem2 on 2020-02-10
Well, thanks for taking the time to consider a reply, however, I avoid using any so-called clouds. I prefer to keep to my own machines.

What you are suggesting seems ott to me for a seven year old, I am not sure I understand it all.

---

### Post by TheFu on 2020-02-10
> **makem2 said:**
> Well, thanks for taking the time to consider a reply, however, I avoid using any so-called clouds. I prefer to keep to my own machines.

What you are suggesting seems ott to me for a seven year old, I am not sure I understand it all.

Nextcloud is installed on YOUR server.  There are other webrtc options.

For your 7 yr old, he would just need to open a browser to a specific URL and click OK.

---

### Post by makem2 on 2020-02-10
Is [https://talky.io/](https://talky.io/)  Just needs javascript and webRTC enabled. What you mean by the web page he would open?

Do I have to install javascript, really? I thought it was for windows.

Is there nothing ubuntu based that is also usable on windows?

I have just had winblows reboot my machine over a 2 hour period when I could not use it and now windows is corrupt but luckily grub is not!

---

### Post by TheFu on 2020-02-10
Did you even try talky.io?  It is cross platform, as is the nextcloud option provided.  30 seconds and you'd know the answers.  I've used both talky.io and the nextcloud-talk addon from Linux, Windows, and Android browsers.

---

### Post by makem2 on 2020-02-10
No, I didn't, I waited for an alternative or confirmation ideally from someone who has assisted in the past.

I will give a try thank you both - after I fix windows 10 white screen of death!

Ive been looking at upgrading my laptop for a more recent model and maybe this is the push I needed to get an  XPS 9300 as soon as they are available. Smaller and ideal for travel.

---

### Post by makem2 on 2020-02-11
I tried talky.io by entering the childs name and sending him the link ([https://talky.io/childs]("https://taky.io/childs") name).

On the other machine which in this case is alongside mine, I entered the url and 'went there'.

Nothing after talky page opens so I send a chat message which is not received my end. Except 'Game lost keep here to keep playing'

I try to send a chat message from my end but cannot type in the area becaos 'connection attempting to reconnect' play lander whilst waiting'.

More that 30 seconds have elapsed!

What am I missing, doing wrong?

---

### Post by TheFu on 2020-02-11
The URL you posted doesn't match the URL I posted.  Need to visit the correct place.  No spaces or non-ASCII characters or punctuation.  

After you enter a random room, then a screen that shows the microphone and camera settings should be seen.  WebRTC must be enabled in the browser, so if you don't see the camera/microphone selection page, check that webrtc is enabled inside your browser.

---

### Post by makem2 on 2020-02-11
> **TheFu said:**
> The URL you posted doesn't match the URL I posted.  Need to visit the correct place.  No spaces or non-ASCII characters or punctuation.  

After you enter a random room, then a screen that shows the microphone and camera settings should be seen.  WebRTC must be enabled in the browser, so if you don't see the camera/microphone selection page, check that webrtc is enabled inside your browser.

[https://talky.io/arle]("https://talky.io/harley")

That it the page I goto. The link is edited so it will not get all the world accessing it. However, after entering a name to chat it does show:

A video window which states 'No video selected'
Speaker - default - and it does work

Camera - Allow camera access

Microphone - Allow microphone access

Join a call (Button)

If I go exactly through the same procedure on the other machine I get the same result except one time on the remote machineGout a purple box with up/down/left/right key suggestions!

I can say 'Hi' in chat on the remote but not on the linux machinewhere I get a grey box with send as I type option

webRTC is enabled on bothe machines.

Here is what is a working link to 'my room', please leave a message![URL="https://talky.io/this%20is%20my%20linux%20room"]

[/URL][https://talky.io/linux](https://talky.io/linux)[ ]("https://talky.io/this%20is%20my%20linux%20room")

---

### Post by TheFu on 2020-02-11
There is a game provided while you wait for the other people to join.
I just tested it here - Firefox on Linux and a tablet running android. Worked fine, first time.

[https://about.talky.io/help/connection](https://about.talky.io/help/connection)

---

### Post by makem2 on 2020-02-11
> **TheFu said:**
> There is a game provided while you wait for the other people to join.
I just tested it here - Firefox on Linux and a tablet running android. Worked fine, first time.

[https://about.talky.io/help/connection](https://about.talky.io/help/connection)

Yes, I read that previously and firewalls are off on both machines

The windows version says it is connecting to a room (presumable 'linux' which is part of the url), flashes off and leaves me with a purple box and I suppose I can play the game.

My linux machine just says, "Lost connection. Reattempting to join...", with the same url. It does not even attempt to try it seems.

Is itpossible to test a connection with my linux machine somewhere?

```

makem@ssdTOSH:~$ sudo ufw status
[sudo] password for makem: 
Status: inactive
makem@ssdTOSH:~$

```

---

### Post by TheFu on 2020-02-11
Well, I guess webrtc doesn't work on your systems.  Sorry.

Perhaps someone else can help wth point-to-point SIP.  SIP is much harder, IME.

---

### Post by makem2 on 2020-02-11
Thanks for trying anyway.

It looks like we may have to buy him a cheap PAYG phone for whatsapp use. At least we will be able to talk.

---

### Post by TheFu on 2020-02-11
> **makem2 said:**
> Thanks for trying anyway.

It looks like we may have to buy him a cheap PAYG phone for whatsapp use. At least we will be able to talk.

Don't need a data, just wifi. A cheap tablet also works without the extra junk a cell phone brings.  I've used both with talky.io.  My PAYGO phone doesn't have a data plan.  Any house with a 7-yr old probably needs a pi-hole filtering internet access too. A simple how-to for pi-hole: [https://www.youtube.com/watch?v=rp8mi1oAvAg](https://www.youtube.com/watch?v=rp8mi1oAvAg) from the guys at Twit.

I don't think a 7 yr old can legally have a facebook account, can they?  Whatsapp is facebook.

---

