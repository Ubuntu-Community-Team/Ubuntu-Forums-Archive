---
title: "Major system glitch after removing library with synaptic, Need help"
date: 2023-03-31
forum: General Help
---

### Post by sofasurfer on 2023-03-31
I removed a library from my system by mistake. Can't remember the actual package name. Tons of stuff was removed. Now every application is inoperable and my applications window shows nothing. 

Question1) Is there a way to find the last couple of items removed with synaptic?

I found that if I run <sudo apt reinstall (app)> the programs will then work and the settings are are intact. I reinstalled firefox, zim and a couple others and all the original settings and configs  were intact.

I then shut off the computer and found that when restarting it the ubuntu splash screen comes up and the I get a user prompt and that gets me nowhere. So basically it looks like ALL applications are glitched until I reinstall them.

Question 2) Would reinstalling my /etc from backup fix these problems?

I have a backintime backup of /Home from yesterday and a /etc and /boot backup from a month ago.
 
More questions... What are my options? 
I am currenty running on a livedvd. I don't know how to repair a system from a livedvd. Would a repair be possible from a livedvd? 
Is it obvious to you people what exactly got glitched from what I have told you?

---

### Post by monkeybrain20122 on 2023-04-01
1) if you can still start synaptic, click File > history and you would see what you have removed.

2) I doubt that restoring /etc only would help since the stuffs there might come from some packages that you have removed and there are components in other places in the file system. The /home is not affected by synaptic or apt upgrade so that part should be ok.

---

