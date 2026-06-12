---
title: "Unable to record audio using Cron"
date: 2015-01-12
forum: General Help
---

### Post by rmcellig on 2015-01-12
I have had this issue for quite some time. At the moment I have Crunchbang 11 on my old Dell 3000 desktop computer. I installed various ubuntu based distro's dual booting with Crunchbang. Every Ubuntu distro I have installed including Xubuntu 14.04 (which I just installed today), does not recordaudio when I run it from my Crontab. As a side note, when I installed a Lubuntu based distro like Zorin Lite, everything works fine.

I tried the three codes below which have always worked for me in Puppy Linux, Crunchbang, and other non xfce based distros. I like xfce and I also want to have an ubuntu based distro on my Dell 3000 alongside my Debian based Crunchbang.

```

*/30 * * * * /usr/bin/arecord -t wav -f cd -d 840 /home/randy/music/TEST$(date "+\%^b\%d\%y").wav
* * * * * /usr/bin/arecord -t wav -f cd -d 840 /home/randy/music/test.wav
10 20 * * 3 arecord -t wav -f cd -d 840 /home/randy/music/test2.wav



```

When i run these directly from the terminal they work fine. When I run them from Crontab, the file is created but there is no audio that is recorded. Is this a Pulseaudio issue? Crunchbang uses Pulseaudio and recording through Crontab works great.

Because I also am using Nano from the terminal I made sure that there is a carriage return after the code.

Should I try purging Pulseaudio and just using  Alsamixer?

---

### Post by TheFu on 2015-01-13
When a userid logs in at the console, certain additional groups are added to the userid because she/he is a local user. Access to the audio devices is one of those.  It is a security thing.  In the old days, we'd share systems and I could remote into a machine, then tell it to playback some music/sounds and the person sitting there would hear those. It was disturbing, which was part of the joke.

So ... you can manually add your userid to the **audio** group and recording should work - however, if it doesn't, don't forget that cron doesn't inherit any environment (not even $HOME). You'll need to set any environment variables needed for those programs to work.  Hope this makes sense.

Of course, we all need to keep our jazz smooooth.

---

### Post by rmcellig on 2015-01-13
One thing I forgot to mention is that when I booted from the xubuntu 14.04  CD, I was able to use the above code in cron and everything worked fine. I was able to record with audio.

Is this because of adding a user to the audio group after installing Xubuntu as mentioned in the last post?

Still not clear why when I install a distro based on lxle recording works fine.

I'll try the above suggestion and post back with the results. Thanks!!

---

### Post by TheFu on 2015-01-13
Linux permissions matter.  Once you master those, things like this make sense.
Use the **id** command to see your groups and look at the /dev/aud* and /dev/dsp* device permissions. 

I'm uncomfortable making absolute comments without any facts. What I have now is hearsay. ;)  Forgetting to mention things means we don't have all the facts.

---

