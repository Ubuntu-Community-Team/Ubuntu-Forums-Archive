---
title: "Problems with my hardy update"
date: 2008-04-27
forum: General Help
---

### Post by spider3000 on 2008-04-27
Hi everyone.

Like many of you, I update to Hardy over the last few days. I've got some issues and I wanted to see if anyone else had these and/or if anyone knows how to fix them.

1. When Ubuntu asks for my root password and the screen goes dark around the prompt, after I typed in my password, parts of the screen are still dark until I mouse over them. Areas affected are icons in the panel, and windows borders.

2. When I enable compiz without any custom emerald theme, Hardy gave me some theme with a purple look around the borders. When a window is inactive, the window borders mess up, like there are black and white horizontal lines.

3. When I open the appearance window (gnome-appearance-properties), Hardy takes quite a while to give me thumb preview of my current theme. Also, is it normal that under 'Visual Effects' there's no more a link to the compiz settings window?

4. Amarok - The bottom line in Amarok's main window show information of the current song played. After a while the text in there get 'corrupted', like it looks bold n theres 1 horizontal line going through the text close to the top. After a song or so, it appears that the new text wrote over the old text, and now it's just an unreadable black area. When I double click on a new song, however, the bottom bar gets cleaned up and the new song information gets shown normally.

5. aMSN - The sound sometimes is too loud and sounding corrupted or doesn't play at all. Usually this happens after some time of inactivity, e.g. someone new signing in after 5 minutes of nothing happening in aMSN. I use the Snack Library as the sound server.

Of course all of these worked in Gutsy. Thank you for any replies. If these don't get fixed... I might just reinstall Hardy.

---

### Post by spider3000 on 2008-04-27
Anyone?

---

### Post by Glaxed on 2008-04-27
Hey spider3k, normally your issues would each warrant their own thread, so keep that in mind next time you post - heck you may get more responses.

1. The root prompt thing is a gksudo issue, see if there is a bug report on it. Perhaps your graphics are too slow? Are you running compositing?

2. Go into emerald and pick a different (I like TruGlass) engine and see if you can edit the background/active window color schemes and see if those preferences work.

3. Yeah, I dont have this problem, but I guess it is another hardy bug for you to report :). 

4. This confirms that I think that you are running compiz.. This has happened to me under compiz, at least. Lots if graphics issues (like the gksudo prompt) can be linked to a slow card running compiz.. What are your system specs?

5. Try Pidgin?

Please excuse my bad writing, I'm really sleepy..

---

### Post by spider3000 on 2008-04-29
Thanks for the replay Glaxed. Ok, so I went ahead and did a clean install of Hardy. So far it has been good, however I still experience the Amarok problem.

Yes, I do run compiz, and my laptop is very fast. I'm running on Intel Core 2 Duo 2.2GHz, and a Nvidia Geforce 8600 GT. So I don't think it's my laptop's fault. The fact that this Amarok problem is still around, could it mean that there's a gnome or compiz bug in Hardy?

Oh, and I didn't want to open 5 threats because I thought users and admins will get annoyed by the whole forum being filled by Spider3000's threats.

---

### Post by Sam on 2008-04-29
Same issues here for 1 and 3. Can't confirm the other points.

Upgraded from Gutsy.

---

### Post by spider3000 on 2008-05-01
Good to know I'm not the only one. I hope the Ubuntu team address these issues/bugs soon.

---

### Post by Glaxed on 2008-05-02
Fill out some bug reports :D.

---

