---
title: "ubuntu doesnt run my vlc or you tube,or mp3,s without problems"
date: 2014-04-12
forum: General Help
---

### Post by drew14 on 2014-04-12
Im runnning this 12. on same pc w xp. on the xp side, everything runs as it should both music and video. 
Here on the Ubuntu side, video & or music (flac or mp3) staggers and hesitates,  speeds up. 
Any suggestions? aside from buying another pc?

  I installed something called* 'Wine*' thinking it would help. Guess I misunderstood its purpose.
(*Ihave no idea what it supposed to do for ubuntu on my pc*).

[FONT=comic sans ms]*THANK YOU IN ADVANCE*[/FONT]

---

### Post by kwasek2 on 2014-04-12
pc stats?

---

### Post by imblack on 2014-04-12
Ubuntu by default comes with no support for Flash and MP3 and a bunch of other proprietary codecs, if you install VLC in ubuntu (through Software center, NOT wine) it can run almost all the formats fine. And on top of that you can also install the [Ubuntu Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by grier-devon on 2014-04-12
I am also curious about system specs as flac should be supported out of the box.

---

### Post by drew14 on 2014-04-13
ub 12.04/ Acer one Intel Atom cpu 1.33 / 2g mem /32 bit / 18 gig hd. video and sound are on motherboard. please, dont laugh, im currently unemployed so I cant upgrade these days, also on the windows xp os, all media works fine ( vlc ,you tube , etc)

---

### Post by drew14 on 2014-04-28
[COLOR=#000000]this is kind of a re-post,since the issue still remains, any clue how to get my medai to play ? music and video unusable on ubuntu and when i reboot to the xp side, vlc runs normal, so does youtube.  just not on the ubuntu side.

'Im running this 12. on same pc w xp. on the xp side, everything runs as it should both music and video. [/COLOR]
[B][COLOR=#000000]Here on the Ubuntu side, video & or music (flac or mp3) staggers and hesitates, speeds up. Media unable to be played.'
([/COLOR][/B][COLOR=#000000]ub 12.04/ Acer one Intel Atom cpu 1.33 / 2g mem /32 bit / 18 gig hd. video and sound are on motherboard.)
[/COLOR][B][COLOR=#000000]
thanks and have a good day

[/COLOR][/B]

---

### Post by sudodus on 2014-04-28
I would use a lighter flavour of Ubuntu on that computer. Try Xubuntu (medium light) or Lubuntu (ultra light). Those desktop environments are lighter, and also the default media players are lighter. Lubuntu uses mplayer2, which is ultra light, and can play smoothly, where other players have problems.

You probably know already that you should install the restricted extras, for Lubuntu

```
sudo apt-get install lubuntu-restricted-extras
```

But there are problems with flash video, because linux is not well supported by the the owner and developer of Flashplayer.

---

### Post by oldos2er on 2014-04-28
Threads merged. Instead of starting a new thread for the same issue, feel free to bump your older one (which is only two weeks old, not old at all really), but not more than once every 24 hours or so. We encourage people not to create more than one thread for the same or similar questions, because it's less confusing for both you and those trying to help you.

---

