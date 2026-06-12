---
title: "Crontab &amp; Audacious audtool"
date: 2008-06-07
forum: General Help
---

### Post by rmflagg on 2008-06-07
Hi everyone,

   I have a script that pulls the name of the currently playing song from Audacious and creates an image file from it to use in a slideshow.  
   The script works just fine except when the script runs from crontab, I get this error:
 "In program audtool:
  * While attempting to connect to the D-Bus session bus
Error: D-Bus Error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
The command in the script that's generating the error is 'audtool --current-song'.  I get the same error if I try to run the script or the audtool command as root.  So, is the crontab running my script as root?  If so, how can I get around this?
   I really don't understand what's going on at all, so it's really hard for me to figure a way to get it to work!

   I had the same script running, but it used Xmms and Xmms-shell to get the song info.  It worked to perfection!

Thanks, 
RM Flagg

---

### Post by politas on 2008-09-01
I get the same message trying to use audtool from a ssh session or  from a crontab. Xmms used to happily let me change the current playlist from a cron command, but now xmms is gone, uninstalled by the latest Ubuntu upgrade and no longer available as a package. And there isn't a single music player available that does what XMMS did for me!

Rythmbox can't load a playlist without creating a new playlist every time. Audacious doesn't accept remote commands at all! I tried Amarok a while ago, but it crashed too often.

Why did they take away my XMMS? It worked perfectly!

---

### Post by simonthesorcerer on 2009-08-13
Hi i dont know if this problem is still up to date for you ... but audtool from an ssh session works for me only if i put export Display =:0 
before the actual audtool command.For example:

```

export Display =:0 && audtool --playback-play
export Display =:0 && audtool --playlist-advance

```

I hope this is helpful.

Greetings :popcorn:

---

