---
title: "YouTube Sync Error"
date: 2006-10-14
forum: General Help
---

### Post by Leebobs on 2006-10-14
Dear All,

I have switched my Laptop to Ubuntu and am in the process of switching my main machine... But, I keep hitting little bugs:

I have today been trying to watch clips on YouTube, problem is... the video starts then some 0.5~0.7 sec later the audio starts - pressing pause stops the video instantly, however the video continues for some 0.5 seconds.

Has anyone got a fix for this??

Many thanks all

Andy :-k

---

### Post by Fitzcarraldo on 2006-10-14
Hi *Leebobs*,

Try editing the environment file as explained below. I am assuming that you are using Firefox as your browser.

Open a terminal window (Applications -> Accessories -> Terminal). At the command prompt, type the following:

sudo gedit /etc/environment

and then enter your password in response to the prompt for Password.

Add the following as the last line in the environment file:

FIREFOX_DSP="aoss"

Save the edited file. I then logged out and logged in again (but do not know if that is necessary).

In my case, the sync between video and voice on YouTube is better than before.

Hope this helps.

---

