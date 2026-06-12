---
title: "Cant get plex to work properly"
date: 2021-10-09
forum: General Help
---

### Post by fjd02 on 2021-10-09
Hi,
I am pretty used to how Plex works in Windows.  
In Ubuntu, I get playback errors on all my Plex served videos.  Video content from the web through Plex is working great.

I am new to Ubuntu and managed to get all but one of my favorite media programs working.  Will work on that other and hope for some wisdom from experts here.

Frank

---

### Post by TheFu on 2021-10-10
You'll need to be much more specific.
Which version of Ubuntu - release and DE?
How is the media accessed - DLNA, network storage (CIFS or NFS?), some other way?
How do the client(s) connect to Plex?  Web app, DLNA, some other method?
What is the source of the content ... is it a streaming service using plex as the middleman or all local or broadcast TV off your antenna or something else?

I've never seen or used plex on Windows, so that point of reference will be lost on me, but I did run 7MC for about a decade.

How's the networking setup?  All wired ethernet - GigE or 10GigE?  What are the clients?  
As for content, which file types are actually stored inside which media containers?  Does Plex have to transcode to a different format for the plex client systems?  If the plex server is a Raspberry Pi and the content is h.265 bluRay movies connected over wifi - you can forgetaboutit.

Avoid using wifi.
Avoid forcing plex to transcode as needed for each client.  I've standardized on h.264 video because all my playback devices support that, but almost none support h.265 video. It just takes too much processing power to decode.  Even live TV, I have a different system from my plex server transcode the mpeg2/ts streams into h.264/mkv streams because my playback devices easily handle h.264, but not 4x larger files that mpeg2 creates, if that makes sense.  h.264 decoding is handled by almost all streaming sticks, rokus,  raspberry-pi devices and tablets/smartphones too.  h.265 ... not so much.

So ... it could be that your local content is stored in the wrong format for the playback devices.  Now, if your plex server is a 10th-gen Core i5 with a $350 GPU that you've setup to use GPU encoding for video, then that's a completely different issue, but if your plex server is a 10 yr old celeron barely able to transcode anything at 4x playback speed, then there's the place I would begin looking.

The great thing about Linux is we have lots of options.
The terrible thing about linux is that we have lots of options and most of what we need aren't the default, for our specific, systems.  To be really flexible and easy, the default is to do transcoding all with the CPU, not the GPU.  For playback, about 50% of the time, decoding of video doesn't use our hardware either. WE have to take specific steps to make that happen for our specific hardware.

---

### Post by fjd02 on 2021-10-16
thanks TheFu for the detailed effort in responding.
I only get a chance to play with new stuff on the weekends, and had considerred all your questions.  Also did some reading on other forums and I appologize for not making note of whch forum I found a piece of advice aimed at my specific quesiton.  As it turns out in Plex Server on Windows, in Settings/Network, changing Secure Connections from "preffered" to "disabled", did did the trick and I am finally able to get plex able to play on this new build of Ubuntu that I put together about a week ago.

the benefit of my effort is that this old laptop now plays 720 content without choking.  It is a dual boot set up now and Plex performance at the client level is deffinately improved on Ubuntu 20 over Windows 10.  Now with this figured out, I am motivated to convert some other old machines.

Great support in forums, thanks

---

