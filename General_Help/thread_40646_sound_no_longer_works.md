---
title: "sound no longer works"
date: 2005-06-09
forum: General Help
---

### Post by gizban on 2005-06-09
When I first installed Ubuntu last week, the sound worked fine. However, yesterday my  sound stopped working.  I know it's not a hardware problem because sound still works in Windows XP.

I tried "killall esd" and I've made sure that "Enable sound server startup" is selected in the Sound Preferences, but I've run out of ideas.  The sound is not set to mute and I've made sure that that all the volume levels are up in Volume Control.

Any ideas for what could be wrong?

Edit: "killall esd" returns "esd: no process killed"

---

### Post by kvidell on 2005-06-09
[QUOTE=gizban]When I first installed Ubuntu last week, the sound worked fine. However, yesterday my  sound stopped working.  I know it's not a hardware problem because sound still works in Windows XP.

I tried "killall esd" and I've made sure that "Enable sound server startup" is selected in the Sound Preferences, but I've run out of ideas.  The sound is not set to mute and I've made sure that that all the volume levels are up in Volume Control.

Any ideas for what could be wrong?

Edit: "killall esd" returns "esd: no process killed"[/QUOTE]
 what does the following return?:
lsof | grep dsp

- Kev

---

### Post by gizban on 2005-06-09
[QUOTE=kvidell]what does the following return?:
lsof | grep dsp

- Kev[/QUOTE]

It doesn't return anything.

---

### Post by gizban on 2005-06-10
I fixed my problem; by removing Ubuntu.

---

### Post by Joeb on 2005-06-10
[QUOTE=gizban]I fixed my problem; by removing Ubuntu.[/QUOTE]

And that made your sound work, how?

---

### Post by desdinova on 2005-06-10
What happens if you manually start esd from a console - does it dump any errors

Ah ignore me - he's uninstalled

---

### Post by gizban on 2005-06-10
[QUOTE=desdinova]What happens if you manually start esd from a console - does it dump any errors[/QUOTE]

When I manually start esd, no errors are returned, but the sound doesn't work still.

I still have Ubuntu installed, but I can't login because I reintalled Window XP, which got rid of my GRUB setup.  (This I know how to fix, but I haven't done it yet because my internet connection stopped working at home).

---

### Post by Spainface on 2005-07-08
I'm have a similar problem. 

The other day my sound controlled just vanished, having done nothing whatsoever.  I can load the alsomixer from the prompt and change the volume for things like the login sound, but nothing else works.

When I type killall esd I get 
esd: no process killed

But restarting esd I get the test sound, but it freezes and still no sound works for apps.

Thoughts?

---

### Post by GMachine_24 on 2005-07-08
To get the sound to work with RealPlayer, CD Player, XMMS etc. I had to uncheck 'enable sound server startup' under system>preferences>sound. This disables gnome-related sound but allows other programs to use your sound card.

There is one or more message re: a permanent workaround somewhere in this forum but I'm fine without the gnome sounds so I haven't tried it.

Good luck.

GMachine

---

### Post by Spainface on 2005-07-08
But everything was working up until a couple days ago.

The icon at the top for volume control is gone, and nothing happens when I try to re-add it to the bar.

When I use my laptop's function key and the up or down arrows, which previously controlled the volume, the little volume box comes up, but the "progress bar" is empty and the arrows don't chance anything.

Turning off the "enable sound startup" box changes nothing.  

Selecting Volume Control from the Sound/Video menu gives me:
No volume control elements and/or devices found.

Thanks for the help,
 :-?

---

### Post by Spainface on 2005-07-10
Nevermind, I fixed it.  Ends up something changed my access rights and I wasn't given access to sound devices.

---

### Post by filemanager on 2005-07-11
[QUOTE=Spainface]Nevermind, I fixed it.  Ends up something changed my access rights and I wasn't given access to sound devices.[/QUOTE]
 How did you do that?

---

