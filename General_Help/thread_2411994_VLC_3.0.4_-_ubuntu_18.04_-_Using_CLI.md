---
title: "VLC 3.0.4 - ubuntu 18.04 - Using CLI"
date: 2019-02-06
forum: General Help
---

### Post by jaymat on 2019-02-06
Just install 18.04 with VLC 3.0.4 and trying to stream a video using CLI

 /usr/bin/c**vlc** /home/jmm/video.ts --loop --sout '#std{access=udp,mux=ts,dst=239.204.1.2:4000}' --ttl=7



I have also tried just "vlc" with the same parameters.

I also tried

[COLOR=#000000][FONT=Menlo]/usr/bin/c[/FONT][/COLOR][FONT=Menlo]**vlc**[/FONT][COLOR=#000000][FONT=Menlo] -vvv /home/jmm/video.ts --loop --sout '#std{access=udp,mux=ts,dst=239.204.1.2:4000}' --ttl=7

[/FONT][/COLOR]as well as

[COLOR=#000000][FONT=Menlo]/usr/bin/c[/FONT][/COLOR][FONT=Menlo]**vlc **[/FONT][COLOR=#000000][FONT=Menlo]-vvv /home/jmm/video.ts --loop --sout udp:239.204.1.2:4000 --loop --ttl=7
[/FONT][/COLOR]
It simply outputs the VLC version information - VLC media player 3.0.4 Vetinari (revision 3.0.4-0-gf615db6332)

I have used the above commands on previous versions of ubuntu, e.g. 16.04 and even 14.04 without problems.

Any guidance on using the CLI to stream out would be appreciated.

thanks
Jay

---

### Post by HermanAB on 2019-02-07
I have never used VLC to stream video, but I have used gstreamer and ffmpeg to do so:
[https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html](https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html)

Chances are that what you are doing is correct, but that your machine doesn't have a multicast route defined.

Read the examples at the bottom of 'man route'.

---

### Post by jaymat on 2019-02-07
Thank you for the suggestion on checking route.
 I did add the generic MC route as per the "man route" and confirmed it was added via "route -v" but VLC via the command line still does nothing other than displaying the version info.

    I even used an invalid file name on the vlc command line, thinking it would complain/error on that, but it just displays the vlc version info.
    Haven't used ffmpeg, as I was using vlc on previous ubuntu versions without problems and figured it would work in 18.04 ?
     Guess I will look at that since I haven't found any information that points to my particular problem, been searching since yesterday.

Thank you again !
Jay

---

