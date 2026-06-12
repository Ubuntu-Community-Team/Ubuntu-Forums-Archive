---
title: "Sound issues"
date: 2019-07-22
forum: General Help
---

### Post by j3el on 2019-07-22
I have a very strange issue with my sound right now. I'm very new to Ubuntu, I just installed it to my PC via flashdrive after Windows (which I've used my entire life) had some kind of catastrophic failure.

I'm still getting used to navigation and the UI (plus this really weird terminal that seems to be required for everything) but other than that everything seems to be going great, and I love Ubuntu so far.

However, it seems every program except for Firefox refuses to provide audio. So far this includes Steam games, Magic: Arena, and Minecraft. But Firefox works just fine.

Honestly, I haven't tried a whole lot of solutions since I don't really know what I'm doing in general, but a few google searches haven't yielded any threads involving this same, oddly specific issue.

My version is "Ubuntu 18.04.2 LTS"

If you need more info for a diagnosis, you might have to tell me how to get it :p Thanks folks!

---

### Post by kesetyan on 2019-07-26
Hi j3el,

I don't know if this will help you but I had a 'no sound' problem with Ubuntu 18.04 which I resolved with the following:


My Line-in was recognized but I could not get any sound. Apparently this was because 'Loopback' was not operating. The solution for me was as follows:
To initiate Loopback for each individual session, I had to open the terminal and type "pactl load-module module-loopback" (don't include speech marks) and press the return key.
This worked for me but would be better if I did not need to do this every new session - the answer was to create a script file to load the module automatically each new session and this was carried out as follows:
Open the terminal and type "sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa ' " and press the return key (do not include the opening and closing speech marks but do include the single and double speech marks within the text - also include the spaces within the text).

I provided this possible solution for another forum member, who had no sound, a couple of weeks ago but there has been no response so I am unable to say whether this worked for him or not.

---

