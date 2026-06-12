---
title: "Firefox2.0 and flash 9 aren't playing nice"
date: 2006-11-16
forum: General Help
---

### Post by lckeeper1 on 2006-11-16
I just upgraded to Firefox 2.0 yesterday following the instructions found on [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox). I used the script install, btw.

Everything was looking very good, then I went to youtube. As I was watching videos, mostly music, I began to notice that the audio and video weren't synching. I have flash 9 installed as well. It shows up when I do an about:plugins, so I know it's there. I just looks like flash did when I had flash 7 installed.

I'm just wondering how I can get flash 9 working like it did under firefox 1.5.

Thanks in advance.

---

### Post by ciscosurfer on 2006-11-16
Are you using Dapper or Edgy?

---

### Post by swhit on 2006-11-16
Same problem here (lose audio with flash 9 videos), also on Edgy. But I'm using epiphany rather than firefox. I haven't looked into any fixes, I'm assuming the problem is with the beta status of the linux flash 9 player. I'm certainly interested in a fix if anyone knows how to.

cheers

---

### Post by lckeeper1 on 2006-11-16
I'm using Dapper. Sorry about not stating that earlier.

A new, rather elementary discovery. I was watching a couple movies on newgrounds.com (Adam Phillips' work, if anyone knows of it), and I right clicked on the screen. On the bottom option it states "about Macromedia Flash 7," which is telling me flash 9 isn't installed, though it says it is in about:plugins.

I'm quite confused. Should I hope for a fix, or just downgrade to firefox 1.5?

---

### Post by bg11 on 2006-11-16
I'm using opera 9.02 and found that it crashes often when using the flash9 plugin, whereas it's reasonably steady with flash7.

---

### Post by TheSandman on 2006-11-16
sudo rm /usr/lib/mozilla-firefox/plugins/libflashplayer.so
sudo cp /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/mozilla-firefox/plugins/libflashplayer.so

That did it for me.
I figured it out by deleting the flashplayer from /usr/firefox/plugins/ where the instructions said to install it... and it still ran! ;)
Sounds like you may have the same issue.

But now i have a new one, no sound as usual... blech.

---

### Post by ciscosurfer on 2006-11-17
Folks, Adobe Flash beta 9 (the plugin or the stand-alone player) both have installers.  They are easy to run and put the plugin in the right place -- and sound should no longer be an issue in Edgy (but I suppose some people are having this problem) -- but remember, *it's beta*.

---

### Post by Particle on 2006-11-17
Where are the installers?  Every page on adobe's site that I can find wants to give me a .tar.gz source package.

---

### Post by ciscosurfer on 2006-11-17
Sorry 'bout that.  Look here:
[http://ubuntuforums.org/showthread.php?t=279990&highlight=flash+installer](http://ubuntuforums.org/showthread.php?t=279990&highlight=flash+installer)

---

### Post by TheSandman on 2006-11-17
The manual install instructions that follow in that thread says to install the plugin in the wrong directory though.
It doesn't work, at least didn't for me.

I never tried the .deb installer since the author of the thread says he himself hasn't even tried it and therefore can't validate that it works.

In the thread it also says the same thing i just said. You have to move the plugin to the right place yourself. Atleast for some people it seems.

Running Edgy. Sound's definatly an issue despite investing in a real soundcard.

---

### Post by ciscosurfer on 2006-11-17
The installers work.  I'm running Edgy.

---

### Post by esaym on 2006-11-17
You are saying that you didn't have the sync problem with flash 7?  I had that problem in 7 but not 9.  But now in 9 I am having video and audio problems on youtube.  It was working fine a couple of days ago but now the vids only play 1/4 the way through and I have no sound..

---

