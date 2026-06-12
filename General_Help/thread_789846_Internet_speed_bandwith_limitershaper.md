---
title: "Internet speed bandwith limiter/shaper"
date: 2008-05-10
forum: General Help
---

### Post by CameronCalver on 2008-05-10
Hey i am currently on a 1.5mb/s internet speed and download at around 155kbs but we only have a 4gb peak and 8gb off peak limit and when we go over we get shaped to 64k.
So... is there any sort of easy bandwith limiter or shaper so i can set the download speed to a lower level when im just browsing or if one of my computers is downloading i dont want it to use up all the speed.
Is there a solution for this problem

---

### Post by CameronCalver on 2008-05-14
bump? ... kinda urgent?

---

### Post by SpaceTeddy on 2008-05-14
you got your hand full if you really want to do this.

for incoming traffic Download), you will need to recompile your kernel and compile the [[COLOR="Blue"]IMQ[/COLOR]]("http://www.linuximq.net/faq.html") Device into it. This is a lot of work and nothing for the faint hearted.

for outgoing traffic (upload) you can use the tc command. this is not as much work, but still a lot to understand. [[COLOR="Blue"]This[/COLOR]]("http://www.linux.com/base/ldp/howto/Traffic-Control-HOWTO/index.htmlt") is a good starting place for it.

I cannot tell you how exactly it is done, as i am a rookie on this field aswell. I have done it before, but not really all that often or too much. 
Also, this might be better placed in the networking section.

---

