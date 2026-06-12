---
title: "A couple of questions,"
date: 2007-08-28
forum: General Help
---

### Post by layst on 2007-08-28
Hey, i am a newb and i just have a couple of problems that i've encountering with Ubuntu at the moment. sorry if it all sounds so simple to fix, but im still trying to get the hang of it. Ive been searching the forums for answers but have not been so lucky, so i have decided to post a few questions in a hope that someone will be able to help me. ok... here goes

1. I have D/L AVIDEMUX but i cant get it to convert video files for me, Can someone please tell me a god program to convert video files, ie .avi to mpeg.

2. I have been having problems using my s-video cord to watch movies through my computer onto my tv with Ubuntu, the problem that im having is that it just isnt working. Is there something that i need to enable, ie do i need to configure my graphics if so how do i do this?

3. WINE - i know that some programs run quite unsteady through wine, but im having problems, with getting sound to work when im running a program through it. for example i got a little nostalgic the other day so i thought i would replay WC 2, but the sound didnt work through it. how can i fix this?

Im sorry to go on guys and gals, i must seam a lil dumb but im a newb:):):)

4. Is there any generic VNC servers that will pic up virtual networks. at my uni i havnt been able to gonnect to the host as i need their VNC program. but can i just get one of the net and use that instead?


Cheers for all the help sorry if i sound like a fool...

---

### Post by Wolki on 2007-08-28
> **layst said:**
> 
1. I have D/L AVIDEMUX but i cant get it to convert video files for me, Can someone please tell me a god program to convert video files, ie .avi to mpeg.


This should work. Note that video encoding can rather difficult, as there are a lot of formats and details.
To change formats, you'll have to select output format and codec at the left-hand sidebar. See also the avidemux documentation wiki at [http://www.avidemux.org/admWiki/index.php?title=Main_Page](http://www.avidemux.org/admWiki/index.php?title=Main_Page) for various tutorials and explanations.

There's also the command line tool mencoder, which is very powerful if you're willing to invest the time in learning it. If you're not, I'm sure if you can give detailed specifications of your requirements, someone will be able to help you how to do it, possibly even with gui integration into the file managerso you'll have the recoding available from your file manager. Simply saying .avi to .mpeg is not enough, as .mpeg can be various things. Also, I'd ask people in the muslitmedia subforums.

> 2. I have been having problems using my s-video cord to watch movies through my computer onto my tv with Ubuntu, the problem that im having is that it just isnt working. Is there something that i need to enable, ie do i need to configure my graphics if so how do i do this?


This depends on your graphics card, and may or may not be easy or possible at all.

> 4. Is there any generic VNC servers that will pic up virtual networks. at my uni i havnt been able to gonnect to the host as i need their VNC program. but can i just get one of the net and use that instead?


VNC is a protocol, and all servers and clients should be more or less compatible.

I assume you don't mean  VNC (which is a remote desktop method) but VPN (a method of establishing a trusted network through untrusted transports, often used by universities to secure wireless access and/or allow students to access services from home as if they were inside the university network). There are many different variants of VPN that are not compatible, but you should be able to use a lot of them with ubuntu. This depends on the used VPN solution though, if it's e.g. the cisco variant, vpnc should work, and there's graphical configuration support via a network-manager plugin.

---

### Post by K.Mandla on 2007-08-28
I think No. 1 is the only one I can help with. I belive mplayer can convert between formats, if you channel the output into another file type. I haven't done that in years, but I'm sure if you search around, you'll find some answers. Good luck!

P.S.: You might try the wine forums for an answer to No. 3. ;)

---

