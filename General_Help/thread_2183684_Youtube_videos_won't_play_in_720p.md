---
title: "Youtube videos won't play in 720p"
date: 2013-10-25
forum: General Help
---

### Post by mark2741 on 2013-10-25
I have a fairly recent PC - Intel 3225 i3 with 8GB RAM. Graphics on the processor.

I have, for the past 6 months, been running Ubuntu 64-bit 13.04 and now 13.10 and the same problem: when I try to watch youtube videos in 720p they won't load. Not simply loading slow - they just won't load at all. Just a black screen or if I start the video at 480p it will play fine but then when I switch to 720p it just stops and never starts (no, it's not simply paused). I am running chromium but same thing happens with Firefox.

I thought it might be my ISP throttling youtube but this past week I tried Manjaro linux and it streamed youtube video at 1080p perfectly with no problems.

I have a Verizon FiOS broadband connection of 75mbps download and 50mbps upload. Speed tests confirm it. Every other site is fine except youtube.

Any ideas?

---

### Post by mark2741 on 2013-10-26
An update on this...even though it's been annoying me for months I just now am dedicating time to solve it...

Some more things I've noticed:
- it's a chromium specific problem now. Videos are working fine in 720p in Firefox now.
- in chromium, the same exact video will not work at 720p in regular browsing mode but if I open an incognito window and load the video it works fine! 
- the above led me to believe that an extension was causing the problem (since incognito mode disables extensions), but unfortunately no - disabling all extensions and restarting chromium results in same problem

So I wound up finding this article on lifehacker and saw there is an extension for tweaking youtube settings:
[http://lifehacker.com/5906775/how-to-fix-all-of-your-biggest-youtube-annoyances-hide-comments-turn-off-autoplay-and-more](http://lifehacker.com/5906775/how-to-fix-all-of-your-biggest-youtube-annoyances-hide-comments-turn-off-autoplay-and-more)

I am very uncomfortable with the TOS of the extension - basically it's a tracking extension. But it is working perfectly now in 720p. And the extension allows me to default to 720p for all youtube videos on load, which is nice. YMMV, but I watch enough youtube videos that for now this trade-off is worth it.

---

