---
title: "Zoom Communications Services"
date: 2020-03-29
forum: General Help
---

### Post by Skaperen on 2020-03-29
has anyone [here]("https://ubuntuforums.org") tried [Zoom]("https://zoom.us") on Ubuntu, yet?  does it work for you?  which browser(s) or client(s) work?

---

### Post by timgood on 2020-03-30
Yes, it works fine for me using Chrome and the standalone Zoom .deb which you can download from Zoom. Very easy to use and the quality is OK!

---

### Post by SeijiSensei on 2020-03-30
I'm using the standalone client for Linux as well. As I recall, I had to install a couple of other packages manually.

After downloadin the .deb, I ran

```

$ sudo dpkg -i zoom_amd64.deb 
[sudo] password for xxx: 
Selecting previously unselected package zoom.
(Reading database ... 250645 files and directories currently installed.)
Preparing to unpack zoom_amd64.deb ...
Unpacking zoom (3.5.374815.0324) ...
dpkg: dependency problems prevent configuration of zoom:
 zoom depends on libgl1-mesa-glx; however:
  Package libgl1-mesa-glx is not installed.
 zoom depends on libxcb-xtest0; however:
  Package libxcb-xtest0 is not installed.
 zoom depends on ibus; however:
  Package ibus is not installed.

```
After running 
```
sudo apt intall ibus libgl1-mesa-glx libxcb-xtest0
```
the client runs flawlessly.

I'm using Kubuntu.  Those packages might be included in other flavors of Ubuntu.

---

### Post by Skaperen on 2020-03-30
is this something PPA would be good for?

---

### Post by SeijiSensei on 2020-03-30
I don't think that's possible. The Zoom client is a proprietary binary. I doubt the source code is publicly available.

They have a GitHub repository, [https://github.com/zoom](https://github.com/zoom), but I don't see the client source, and there's nothing there for Linux per se.

---

### Post by Skaperen on 2020-03-30
i'm just thinking that their binary .deb could be put in a private repository so it can be upgraded by them when needed.

also, since it is binary and proprietary, i'm thinking out how to run it in isolation.  a VM is overkill.  but a container might do (lxc is probably sufficient).  i don't want to let it see my system (users, files, /etc).  i think i can be safe enough running Xorg outside of the container and run everything else inside (with essential net access that i can tcpdump if i need to).

---

### Post by EuclideanCoffee on 2020-03-30
Easier way, Skaperen would be simply to use reprepro.

[https://wiki.debian.org/DebianRepository/Setup#reprepro](https://wiki.debian.org/DebianRepository/Setup#reprepro)

---

### Post by DuckHook on 2020-03-30
From a security perspective: [https://protonmail.com/blog/zoom-privacy-issues/](https://protonmail.com/blog/zoom-privacy-issues/)

In our understandable rush to offset social distancing with virtual bonding, these concerns sometimes get overlooked.

---

### Post by Tadaen_Sylvermane on 2020-03-30
My wife and I used it sunday for a religious service. Worked great even on our 11mbit connection. Actually had 2 connections, 1 being at my parents place across the yard. We had 70+ participants without trouble. We will be doing this twice a week for the foreseeable future. The .deb even at 14.04 worked just fine on Xenial.

Just wanted to add that we weren't able to use the test audio option. It worked anyway off of Hdmi on the living room tv. The option was greyed out.

*EDIT* mean to say bionic, not xenial. I'm assuming it works fine there as well.

---

### Post by grahammechanical on 2020-03-30
My Christian community has just started using Zoom for their meetings. I installed the Zoom client for Ubuntu. Yes it is for 14.04 but it works fine on Ubuntu 18.04. I have one gripe with Zoom (apart from the privacy concerns, that is). 

The application does not come with a help document. I could not find any information on how to indicate that I wished to participate in the conference. And there is a lot of audience participation in our Christian meetings. I have now found out how to do it but at the time I did not fancy clicking everything in sight during the actual meeting.

Regards

---

### Post by Irihapeti on 2020-03-30
I prefer to use jitsi, but it only works on Chrome/Chromium-based browsers. I know it works on Slimjet, but I don't know about Vivaldi.

I've been involved with Toastmasters meetings on zoom, which I guess I'll need to still be involved with, but I might rule it out for individual conversations.

---

### Post by QIII on 2020-03-30
I use Zoom regularly several times a day to attend video meetings remotely since I work from home  --  which is out in the boondocks.

I use Ubifi and a directional Yagi antenna to hit an AT&T cell tower and I get about 32 - 34 Mbps, which is pretty good for a rural connection.  Works just fine.

---

### Post by DuckHook on 2020-03-31
> **Irihapeti said:**
> &#8230;I've been involved with Toastmasters meetings on zoom, which I guess I'll need to still be involved with, but I might rule it out for individual conversations.
Work and organizations will dictate the apps that we must use. Unfortunately, there's no getting around that.

But on a personal level, we thankfully have choices. I use Signal (in snap form): FOSS, secure, distributed, point-to-point, encrypted. Apps for Android, Apple/iOS and Windows.

Major drawback is: it only connects one-on-one. No group video chat AFAIK, which for some is a deal breaker.

There's also Jami which *does* permit group video chat. Same benefits: FOSS, secure, distributed, point-to-point, TLS encrypted. Also in snap store and has Android, Windows, Apple/iOS apps.

---

### Post by Skaperen on 2020-03-31
can i get source in snap?

---

### Post by Skaperen on 2020-03-31
> **grahammechanical said:**
> My Christian community has just started using Zoom for their meetings. I installed the Zoom client for Ubuntu. Yes it is for 14.04 but it works fine on Ubuntu 18.04. I have one gripe with Zoom (apart from the privacy concerns, that is). 

The application does not come with a help document. I could not find any information on how to indicate that I wished to participate in the conference. And there is a lot of audience participation in our Christian meetings. I have now found out how to do it but at the time I did not fancy clicking everything in sight during the actual meeting.

Regards
very few things break in future Linux or other distros.  a program i wrote in a very old Slackware and last compiled in a more recent Slackware works fine in Xubuntu 18.04.  it won't compile due to some gcc changes.  i'm rewriting it in Python rather than fixing the C version.  but for now, the binary works on x86_64.

---

### Post by SeijiSensei on 2020-04-01
When you install the Zoom client with dpkg, it will complain about three missing dependencies. You need to install them manually and then it works as advertised.  See my post [above](https://ubuntuforums.org/showthread.php?t=2439567&p=13942730&viewfull=1#post13942730).

---

### Post by carl4926 on 2020-04-01
> **Irihapeti said:**
> I prefer to use jitsi, but it only works on Chrome/Chromium-based browsers. I know it works on Slimjet, but I don't know about Vivaldi.

I've been involved with Toastmasters meetings on zoom, which I guess I'll need to still be involved with, but I might rule it out for individual conversations.

Does it have a limit on number of participants? I couldn't just see anything about that

---

### Post by geoffrey-p on 2020-04-01
I didn't want to install the .DEB package outside of the repository. So, I installed the snap package instead.

One minor issue I encountered is that the camera was disabled in the "limited environment" of snap. So, I had to enter a command to map the laptop camera:

> snap connect zoom-client:camera core:camera

---

### Post by ajgreeny on 2020-04-01
> **SeijiSensei said:**
> When you install the Zoom client with dpkg, it will complain about three missing dependencies. You need to install them manually and then it works as advertised.  See my post [above](https://ubuntuforums.org/showthread.php?t=2439567&p=13942730&viewfull=1#post13942730).
Much easier to use ***sudo apt install*** rather than ***sudo dpkg install*** as apt will sort out and install all the dependencies automatically and does not need the manual installation of those dependencies.

---

### Post by ajgreeny on 2020-04-01
> **carl4926 said:**
> Does it have a limit on number of participants? I couldn't just see anything about that

Group chats of up to 100 are possible.

---

### Post by SeijiSensei on 2020-04-01
> **ajgreeny said:**
> Much easier to use ***sudo apt install*** rather than ***sudo dpkg install*** as apt will sort out and install all the dependencies automatically and does not need the manual installation of those dependencies.
I always thought apt was used to retrieve software from the repositories, while dpkg was used to install stand-alone programs (rather like the difference between yum and rpm on RedHat systems). 

So, yes, running "sudo dpkg /path/to/zoom_amd64.deb" brought in the needed dependencies.  It ended with this error:
```
N: Download is performed unsandboxed as root as file '/tmp/mozilla_phl0/zoom_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
```
but Zoom itself works as advertised.

Thanks for the tip!

---

### Post by DuckHook on 2020-04-02
> **SeijiSensei said:**
> …It ended with this error:
```
N: Download is performed unsandboxed as root as file '/tmp/mozilla_phl0/zoom_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
```…
To get rid of the error, you need to:```
sudo chown -R _apt:root /tmp/mozilla_phl0 && sudo chmod -R 755 /tmp/mozilla_phl0
```Because _apt has no rights to traverse the directory, the apt process falls back to root. The process still completes, but for tidyness's sake, it's nice to eliminate the error.

---

### Post by carl4926 on 2020-04-03
> **ajgreeny said:**
> Group chats of up to 100 are possible.

Thanks for that

---

### Post by ajgreeny on 2020-04-03
> **SeijiSensei said:**
> I always thought apt was used to retrieve software from the repositories, while dpkg was used to install stand-alone programs (rather like the difference between yum and rpm on RedHat systems). 

Thanks for the tip!
You are partly correct about that.
Local .deb packages can, however, be installed with ***apt*** but not ***apt-get***; that's a big advantage of the move to apt from apt-get in my opinion.

---

### Post by Skaperen on 2020-04-03
> **geoffrey-p said:**
> I didn't want to install the .DEB package outside of the repository. So, I installed the snap package instead.

One minor issue I encountered is that the camera was disabled in the "limited environment" of snap. So, I had to enter a command to map the laptop camera:

snap uses an "environment"?  i thought it was just a different way to organize where files were installed.  is it a container?

---

### Post by Skaperen on 2020-04-06
if someone were to set up a web site that allowed people to have group communications (simple meetings) without running a proprietary application or just in a web browser, what do you think they might be using on the user/client side a/o as the communication protocol?

---

### Post by DuckHook on 2020-04-06
> **Skaperen said:**
> if someone were to set up a web site that allowed people to have group communications (simple meetings) without running a proprietary application or just in a web browser, what do you think they might be using on the user/client side a/o as the communication protocol?

[https://xmpp.org/](https://xmpp.org/)

---

### Post by Skaperen on 2020-04-06
is that doable in just a web browser on each end?

---

### Post by DuckHook on 2020-04-06
Not being a dev of any kind, I have no idea. All I know is that a number of apps are based on it: aTAlk, Movim, Conversations, Quicksy, Xabber Jabber, and those two granddaddies of them all, MAXS and Jabber. Jitsi also supports it and it has a nice browser-only implementation, so I'm guessing that what you are asking would not be a problem. Further details will need to come from someone who actually knows something about it.

---

### Post by Skaperen on 2020-04-06
now i'm thinking of building a script that launches server instances in a cloud that does this kind of thing without the need to download any extension or software and can work in any web browser.  while i have seen websites that can play videos under those restrictions (YouTube being the first mention), i have never seen one that can *take* your video and audio at the same time.  i don't know if that can be done on all the major web browsers.  the idea is, if you want to run your own group video, just get a cloud account and run the script.  i would like for all that it runs to be FOSS.  schools might be interested.

---

### Post by dragonfly41 on 2020-04-07
Alternatives to Zoom  .. Red5  open source ??

[https://www.red5pro.com/blog/](https://www.red5pro.com/blog/)

[https://www.red5pro.com/blog/9-essential-features-for-alternatives-to-zoom-for-distance-learning/](https://www.red5pro.com/blog/9-essential-features-for-alternatives-to-zoom-for-distance-learning/)

---

### Post by DuckHook on 2020-04-07
Not sure if the whole thing is open source or just some components. For unrestricted FOSS video-chat/conferencing, consider [Jitsi]("https://jitsi.org/") or [Jami]("https://jami.net/"). Jami in particular is a GNU project. They don't come any more FOSS than that. Jitsi is privately owned but its entire app is FOSS. Don't know how long that will last. For now, it is freely available to all. I use both. Good solid products.

I expect a lot of opportunistic app developers to be angling for adoption of their app. Security conscious types need to be especially on the lookout now.

---

### Post by Skaperen on 2020-04-07
are these programs designed for peer to peer (client to client) or many to many via a server?  is the XMPP protocol made to work over HTTP or HTTPS or just TCP or TLS?  IOW, is it easy to work through an HTTP proxy?

---

### Post by Skaperen on 2020-04-08
Jami looks interesting.  but i don't want to be using SIP or anything resembling a PSTN.  i want to have video and audio done purely in an IP context.  being able to support things that expect SIP and/or PSTN should be entirely optional.  to do things that need to connect to a central server, a domain based host name or IP address (and maybe transport protocol a/o port number) should be enough to find where to connect.

if there is a daemon program i can launch on a server and clients that can connect to it, it sounds like a go.  some means to manage user access would be appropriate even if it means editing files (as long as i don't need to kill any existing setups to engage the changes).

---

### Post by DeadlyOats on 2020-07-27
Hello.

I have a Dell Latitude E6520.  I have Kubuntu 18.04 LTS installed, both Firefox and Chrome.  I just ordered a [webcam]("https://www.overstock.com/Electronics/Webcam-with-Microphone-1080P-HD-Web-Camera-Vitade-672-USB-Desktop-Web-Cam-Facecam-Video-Cam-for-Streaming-Gaming-Conferencing/31769405/product.html?elementId=orderConfProductInfo&pos=15&tid=0&utm_source=Braze&utm_source=Braze&ehid=759920DB51F9EA85E0531006140AF932&ehid=759920DB51F9EA85E0531006140AF932&token=297487-29748714687552820200727190714-20200727-1-e4eecd&token=297487-29748714687552820200727190714-20200727-1-e4eecd&utm_medium=email&utm_medium=email&utm_campaign=297487&utm_campaign=297487&cid=297487&cid=297487&sentTime=1595901134984&sentTime=1595901134988&send_id=4376644f-802a-47d1-a7bc-7060cbebf53f&send_id=4376644f-802a-47d1-a7bc-7060cbebf53f&ahid=0cc2abfbf3b24a1254899be640313601&ahid=0cc2abfbf3b24a1254899be640313601&dispatch_id=49ce6747f33befebc6a6b9e5bc013d5d&dispatch_id=49ce6747f33befebc6a6b9e5bc013d5d&%243p=e_ab&%24original_url=https%3A%2F%2Fwww.overstock.com%2FElectronics%2FWebcam-with-Microphone-1080P-HD-Web-Camera-Vitade-672-USB-Desktop-Web-Cam-Facecam-Video-Cam-for-Streaming-Gaming-Conferencing%2F31769405%2Fproduct.html%3FelementId%3DorderConfProductInfo%26pos%3D15%26tid%3D0%26utm_source%3DBraze%26ehid%3D759920DB51F9EA85E0531006140AF932%26token%3D297487-29748714687552820200727190714-20200727-1-e4eecd%26utm_medium%3Demail%26utm_campaign%3D297487%26cid%3D297487%26sentTime%3D1595901134984%26send_id%3D4376644f-802a-47d1-a7bc-7060cbebf53f%26ahid%3D0cc2abfbf3b24a1254899be640313601%26dispatch_id%3D49ce6747f33befebc6a6b9e5bc013d5d%26utm_source%3DBraze%26ehid%3D759920DB51F9EA85E0531006140AF932%26token%3D297487-29748714687552820200727190714-20200727-1-e4eecd%26utm_medium%3Demail%26utm_campaign%3D297487%26cid%3D297487%26sentTime%3D1595901134988%26send_id%3D4376644f-802a-47d1-a7bc-7060cbebf53f%26ahid%3D0cc2abfbf3b24a1254899be640313601%26dispatch_id%3D49ce6747f33befebc6a6b9e5bc013d5d&_branch_match_id=754534419898938830") which I have to wait for it to be shipped.

I need to install Zoom for a coming meeting.

I am a complete incompetent End User.  I was reading your posts, but they seemed really technical.  Where specifically did you get the zoom client for Kubuntu, and what specific commands were used to install it?  I saw a few different methods explained, but being command-line illiterate, I didn't understand which one worked the best.

Is Kubuntu 18.04 LTS O.K. for Zoom or should I upgrade to 20.04 instead?

This thread is a few months old, is there a Zoom client in the Ubuntu/Kubuntu software repositories, or do I have to get it from outside, still?

---

### Post by kansasnoob on 2020-07-27
> **DeadlyOats said:**
> Hello.

I have a Dell Latitude E6520.  I have Kubuntu 18.04 LTS installed, both Firefox and Chrome.  I just ordered a [webcam]("https://www.overstock.com/Electronics/Webcam-with-Microphone-1080P-HD-Web-Camera-Vitade-672-USB-Desktop-Web-Cam-Facecam-Video-Cam-for-Streaming-Gaming-Conferencing/31769405/product.html?elementId=orderConfProductInfo&pos=15&tid=0&utm_source=Braze&utm_source=Braze&ehid=759920DB51F9EA85E0531006140AF932&ehid=759920DB51F9EA85E0531006140AF932&token=297487-29748714687552820200727190714-20200727-1-e4eecd&token=297487-29748714687552820200727190714-20200727-1-e4eecd&utm_medium=email&utm_medium=email&utm_campaign=297487&utm_campaign=297487&cid=297487&cid=297487&sentTime=1595901134984&sentTime=1595901134988&send_id=4376644f-802a-47d1-a7bc-7060cbebf53f&send_id=4376644f-802a-47d1-a7bc-7060cbebf53f&ahid=0cc2abfbf3b24a1254899be640313601&ahid=0cc2abfbf3b24a1254899be640313601&dispatch_id=49ce6747f33befebc6a6b9e5bc013d5d&dispatch_id=49ce6747f33befebc6a6b9e5bc013d5d&%243p=e_ab&%24original_url=https%3A%2F%2Fwww.overstock.com%2FElectronics%2FWebcam-with-Microphone-1080P-HD-Web-Camera-Vitade-672-USB-Desktop-Web-Cam-Facecam-Video-Cam-for-Streaming-Gaming-Conferencing%2F31769405%2Fproduct.html%3FelementId%3DorderConfProductInfo%26pos%3D15%26tid%3D0%26utm_source%3DBraze%26ehid%3D759920DB51F9EA85E0531006140AF932%26token%3D297487-29748714687552820200727190714-20200727-1-e4eecd%26utm_medium%3Demail%26utm_campaign%3D297487%26cid%3D297487%26sentTime%3D1595901134984%26send_id%3D4376644f-802a-47d1-a7bc-7060cbebf53f%26ahid%3D0cc2abfbf3b24a1254899be640313601%26dispatch_id%3D49ce6747f33befebc6a6b9e5bc013d5d%26utm_source%3DBraze%26ehid%3D759920DB51F9EA85E0531006140AF932%26token%3D297487-29748714687552820200727190714-20200727-1-e4eecd%26utm_medium%3Demail%26utm_campaign%3D297487%26cid%3D297487%26sentTime%3D1595901134988%26send_id%3D4376644f-802a-47d1-a7bc-7060cbebf53f%26ahid%3D0cc2abfbf3b24a1254899be640313601%26dispatch_id%3D49ce6747f33befebc6a6b9e5bc013d5d&_branch_match_id=754534419898938830") which I have to wait for it to be shipped.

I need to install Zoom for a coming meeting.

I am a complete incompetent End User.  I was reading your posts, but they seemed really technical.  Where specifically did you get the zoom client for Kubuntu, and what specific commands were used to install it?  I saw a few different methods explained, but being command-line illiterate, I didn't understand which one worked the best.

Is Kubuntu 18.04 LTS O.K. for Zoom or should I upgrade to 20.04 instead?

This thread is a few months old, is there a Zoom client in the Ubuntu/Kubuntu software repositories, or do I have to get it from outside, still?

Should work fine. I'd never used it before this COVID "shut down" and I installed it very easily from:

[https://zoom.us/download](https://zoom.us/download)

Just select Ubuntu 14.04+. I installed that version on Ubuntu 18.04 and it worked just fine (I think I used gdebi). If you're using any desktop environment with "tree view" it should show up in the "Internet" category.

I started by testing my webcam with Cheese and opened sound settings > Input where I could visually view whether or not my voice was creating a response.

I've used it to "see" a few doctors without issue. It's the platform they use so i just roll with the flow.

I'll hopefully have time to test it in 20.04 later this week when the first point release drops.

---

### Post by DeadlyOats on 2020-07-28
> **kansasnoob said:**
> Should work fine. I'd never used it before this COVID "shut down" and I installed it very easily from:

[https://zoom.us/download](https://zoom.us/download)

Just select Ubuntu 14.04+. I installed that version on Ubuntu 18.04 and it worked just fine (I think I used gdebi). If you're using any desktop environment with "tree view" it should show up in the "Internet" category.

I started by testing my webcam with Cheese and opened sound settings > Input where I could visually view whether or not my voice was creating a response.

I've used it to "see" a few doctors without issue. It's the platform they use so i just roll with the flow.

I'll hopefully have time to test it in 20.04 later this week when the first point release drops.

It turned out to be easier than I thought.  I used Chrome.  I did what you said, and while it was downloading, an arrow pointed to the zoom download and said, "Click to install."

I clicked it.  A warning came up that it might be harmful, I accepted it anyway, then clicked on it again.  It installed, but then asked for dependencies.  I clicked OK, and put in my password to authorize the dependencies to install.

Now all I have to do is get the microphone working...  And when my web cam comes in the shipment, I'll get that set up, too.  Oh, wait!  I forget, the web cam has a built in mic....  Maybe I'll set that one up.

Thanks!

---

### Post by mIk3_08 on 2020-07-28
Yes! it work fine for me using chrome web browser. No need to install the zoom apps.

---

### Post by Skaperen on 2020-07-29
the reason i do not want to use either the Zoom app (the 64-bit executable for Linux) or Chrome is the lack of source code available to the public so they will fear being discovered if they put sneaky code in there.

so i will limit myself to Firefox (or other OSS browsers) and apps that come in source code form.

---

### Post by Skaperen on 2020-07-29
Google Meet seems to work in Firefox visiting their page.  but i didn't have anyone else to communicate with so i don't know how far it can go or how well it works.

---

### Post by DeadlyOats on 2020-07-31
> **Skaperen said:**
> the reason i do not want to use either the Zoom app (the 64-bit executable for Linux) or Chrome is the lack of source code available to the public so they will fear being discovered if they put sneaky code in there.

so i will limit myself to Firefox (or other OSS browsers) and apps that come in source code form.

I totally get that.  In fact, many apps made in China is full of spyware designed to run all of the traffic through their servers, so that they can sift through it.  As soon as I'm done with my online meeting, I'm gonna totally reinstall Kubuntu without Zoom.

---

