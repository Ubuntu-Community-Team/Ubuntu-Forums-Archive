---
title: "DVD::RIP transcode problems"
date: 2006-10-16
forum: General Help
---

### Post by summersab on 2006-10-16
Hey, I'm running Dapper and I have the newest version of DVD::RIP installed with the transcode libraries. The program runs just great - it rips all of the data to raw files (I've even opened them to be sure). However, whenever I go to transcode the files, nothing happens. I have everything set right. I tried DivX, but aparently that's all outdated (on a sidenote, any news on when DivX will work? If that would be "now," how do I do it? Otherwise, I'll Xvid). I get the Xvid plugin setup with mp3 audio and click transcode (I'm setup for just one file - no need for splitting). The computer does nothing. No progress bar, no files created. What do I need to do to get transcoding to work?

Also, I'm ripping episodes of a TV show season. I'd rather each episode not be 700 mb - can I slim that down? Do I need an extra program? What do you recommend?

Lastly, is there a program out there better than DVD::RIP?

Sorry for so many questions, but I'm trying to be specific.

---

### Post by jocheem67 on 2006-10-20
Did you check the dependencies? It's under the " debug " tab...

If you've got transcode installed properly, there shouldn't be a problem. 

My setup with dvd::rip:

using xvid4, I transcode my movies to about 1500 mb avi-files. I use mp3 160 kbps for audio and use one post-processing filter, the mplayer one.

I do extract subs ( being dutch ) and convert them in XP with ' vobsub' to .srt format.

This all works very well.

About your last question. You could try avidemux, it might be a bit more accessible. Dvd::rip uses transcode as you know, avidemux uses ffmpeg and I think mencoder, but I might be wrong here.

Concluding: if you check your dependencies you should be allright. You don't need to solve them all by the way. The tool shows the mandatory ones. I 'm not using the burn-function by the way.

Cheers.

---

### Post by jocheem67 on 2006-10-20
hmmmm, reading yor question again it seems transcode is already properly installed. Still I think that the problem lies in that library....

---

