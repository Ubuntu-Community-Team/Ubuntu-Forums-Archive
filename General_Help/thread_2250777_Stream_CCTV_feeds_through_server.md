---
title: "Stream CCTV feeds through server?"
date: 2014-10-31
forum: General Help
---

### Post by Roasted on 2014-10-31
Hello friends. I have several network based cameras on my LAN that tie in to my server through two methods. 1) via Motion by saving motion snapshots, and 2) via Samba, where the cameras themselves just record 24/7 to a specified Samba share. This allows me to view snapshots and see what took place, and if need be, reference the 24/7 feeds to get a full view of what happened.

I set up a custom HTML page, very basic, all but 6 lines to view the live stream of the feeds. This is great because it pulls the stream from Motion's built in web server. That way instead of me having 4 computers attached to the cameras, sucking their individual bandwidth, the cameras continue to serve one "client" - my server, and my server just replicates the feeds out.

Problem is, this isn't very mobile-app friendly for my Android phone or my tablet. I'd like to figure out a way, someway, somehow to incorporate that kind of idea to span all devices. Does anybody know of a service I can run on my server which can basically replicate the IP surveillance camera's feed out to a mobile friendly app? Perhaps something more that can work in conjunction with my laptop/desktop systems as well? Not that the HTML file is broken, or a pain, but ya know... I'd like to stay consistent if at all possible.

The end goal is to have the cameras serve one stream and one stream only: my server. Then my server can replicate the feeds to whichever client is connected. That way if 10 clients connect, it's demanding 10 feeds from the server instead of overloading each camera with 10 stream requests.

---

### Post by tgalati4 on 2014-10-31
I have installed Avertx systems and they basically have 2 streams from IP cameras:  high definition and 640x480.  Whenever there is a call to the mobile app (Android or iOS), the small stream is used.  You can see the HD stream if you click on a thumbnail and hit HD--good when you are local and on wifi.

I have not used *zoneminder* recently, but I presume that you can set up virtual cameras with different resolutions.  You would have to do some html coding to provide the low-bandwidth stream to a mobile device.  You can probably do the same with *motion*, but I have only played with it.

What is your specific Use Case?  What do you need to observe on your phone?

---

### Post by Roasted on 2014-10-31
My basic use case is that I'm a home owner with some outdoor IP cameras. They dual stream motion detect jpg's of movement as well as 24/7 H264 recordings straight to my server. Right now my wife and I have them rigged up on our phones with TinyCam Pro, but this pulls the streams directly from the cameras. Maybe I'm going over-kill on this, but I like the idea of our phones, any tablets, laptops, computers, etc pulling the stream from the server. My server would be able to respond much better if a number of devices are connected as opposed to each camera trying to push out 5 streams to 5 devices at once. I'd rather them pipe 1 stream into the server, and that's it, then from there devices pull the stream from the server itself.

It just makes sense to me from a network bandwidth allocation standpoint. I'd rather the server do the heavy lifting if it ever becomes a need; not the cameras.

I did look into ZoneMinder, but I wasn't too thrilled with the amount of demand that ZoneMinder requires as far as resources go. Motion provides me with a really basic no frills way to acquire JPG's based on movement. That's really all Motion does in my current implementation. The full time 24/7 recordings just dump to a different directly over Samba. Two cameras saving 24/7 around the clock at 1280x800 10 FPS H264 feeds is wildly light while giving me a guarantee they didn't miss any movement. So Motion provides me with JPGs as an idea of what happened, but when I reference the time stamps on the full time recordings, I can see the start/finish/everything without skipping a beat. The only downside is disk space, but given that's the only con, it's one I happily accept.

---

