---
title: "When booting Kubuntu it prompts me back :("
date: 2007-01-18
forum: General Help
---

### Post by LilaQ on 2007-01-18
Hey guys,

I'm having a problem with Kubuntu 6.10. It was running flawlessly until yesterday. I had some problems with a hard disc drive which I used for storing several data under linux, but no programs or else was stored on it. So i took the drive out, it was kinda crashed and is not useable anymore. But after I booted again, the normal login screen appeared and I entered my password. It looked like Kubuntu booted normal, but then a window popped up with a pretty long error message (`? I can not read fast enough to get the point of the message) and then it prompted me back to the login screen. This happens every time I try to login with my default user name. When I try to login as root there is no problem.
But I have no idea how to get rid of that problem, generally I try to solve problems by myself, but I'm pretty new to Linux and don't have enough knowledge yet to deal with such problems. So I'm hoping to get your help guys.

Thanks in advance,

LilaQ

---

### Post by tronica on 2007-01-18
if you added that drive to fstab, you need to remove it from there.

---

### Post by LilaQ on 2007-01-18
Ahh, yes. That should do it. Thanks, I'll try that right away :)

---

### Post by LilaQ on 2007-01-18
Hey,

i deleted the entry of the hard disc drive in the fstab, but there was no change at all. Still when I try to login with my default user I'm prompted back to the login screen, right after I can see my desktop for ~3 seconds.

Any other ideas?

LilaQ

---

### Post by tronica on 2007-01-18
hmm... So it kicks you to the prompt. When your there try this
> 
sudo cat /var/log/syslog

and see what is going on.

---

### Post by khedron on 2007-01-18
As root, check the** /var/log** directory for logs. I'm not sure exactly which one, try **user.log** or **kdm.log **to see if there are any weird messages. There tend to be quite a few there, so try seeing if you can see any messages that looked like your error.

[EDIT]ooo... beat me

---

### Post by LilaQ on 2007-01-18
Since I have no idea what the output means, I'll just post what came out:

```
Jan 18 19:43:13 localhost hcid[4261]: name_listener_add(:1.3)
Jan 18 19:43:13 localhost hcid[4261]: Default passkey agent (:1.3, /org/bluez/passkey_agent_4542) registered
Jan 18 19:43:15 localhost kdm[3892]: X server for display :0 terminated unexpectedly
Jan 18 19:43:15 localhost hcid[4261]: :1.3 exited without unregistering the default passkey agent
Jan 18 19:43:16 localhost kernel: [17179632.820000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
Jan 18 19:43:16 localhost kernel: [17179632.820000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
Jan 18 19:43:16 localhost kernel: [17179632.820000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Jan 18 19:43:18 localhost kdm_greet[4577]: Can't open default user face
Jan 18 19:43:29 localhost kdm_greet[4577]: Internal error: memory corruption detected
Jan 18 19:44:13 localhost kdm[3892]: X server for display :0 terminated unexpectedly
Jan 18 19:44:13 localhost kernel: [17179690.264000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
Jan 18 19:44:13 localhost kernel: [17179690.264000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
Jan 18 19:44:13 localhost kernel: [17179690.264000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Jan 18 19:44:15 localhost kdm_greet[4663]: Can't open default user face
Jan 18 19:44:25 localhost kdm_greet[4663]: Internal error: memory corruption detected
Jan 18 19:44:27 localhost kdm[3892]: X server for display :0 terminated unexpectedly
Jan 18 19:44:27 localhost kernel: [17179703.876000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
Jan 18 19:44:27 localhost kernel: [17179703.876000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
Jan 18 19:44:27 localhost kernel: [17179703.876000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Jan 18 19:44:29 localhost kdm_greet[4735]: Can't open default user face
Jan 18 19:44:52 localhost kdm_greet[4735]: Internal error: memory corruption detected
Jan 18 19:44:58 localhost hcid[4261]: name_listener_add(:1.5)
Jan 18 19:44:58 localhost hcid[4261]: Default passkey agent (:1.5, /org/bluez/passkey_agent_4884) registered
Jan 18 19:46:56 localhost kdm[3892]: X server for display :0 terminated unexpectedly
Jan 18 19:46:56 localhost hcid[4261]: :1.5 exited without unregistering the default passkey agent
Jan 18 19:46:56 localhost kernel: [17179853.244000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
Jan 18 19:46:56 localhost kernel: [17179853.244000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
Jan 18 19:46:56 localhost kernel: [17179853.244000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Jan 18 19:46:58 localhost kdm_greet[5157]: Can't open default user face
Jan 18 19:47:04 localhost kdm_greet[5157]: Internal error: memory corruption detected
Jan 18 19:47:09 localhost hcid[4261]: name_listener_add(:1.8)
Jan 18 19:47:09 localhost hcid[4261]: Default passkey agent (:1.8, /org/bluez/passkey_agent_5300) registered
Jan 18 19:47:11 localhost kdm[3892]: X server for display :0 terminated unexpectedly
Jan 18 19:47:11 localhost hcid[4261]: :1.8 exited without unregistering the default passkey agent
Jan 18 19:47:11 localhost kernel: [17179868.624000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
Jan 18 19:47:11 localhost kernel: [17179868.624000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
Jan 18 19:47:11 localhost kernel: [17179868.624000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Jan 18 19:47:14 localhost kdm_greet[5368]: Can't open default user face
Jan 18 19:47:51 localhost kdm_greet[5368]: Internal error: memory corruption detected
Jan 18 19:47:51 localhost kernel: [17179908.416000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
Jan 18 19:47:51 localhost kernel: [17179908.416000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
Jan 18 19:47:51 localhost kernel: [17179908.416000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Jan 18 19:47:54 localhost kdm_greet[5412]: Can't open default user face
Jan 18 19:48:00 localhost kdm_greet[5412]: Internal error: memory corruption detected
Jan 18 19:48:06 localhost hcid[4261]: name_listener_add(:1.11)
Jan 18 19:48:06 localhost hcid[4261]: Default passkey agent (:1.11, /org/bluez/passkey_agent_5560) registered
Jan 18 19:48:07 localhost kdm[3892]: X server for display :0 terminated unexpectedly
Jan 18 19:48:07 localhost hcid[4261]: :1.11 exited without unregistering the default passkey agent
Jan 18 19:48:10 localhost kdm_greet[5620]: Can't open default user face
Jan 18 19:48:22 localhost kdm_greet[5620]: Internal error: memory corruption detected
Jan 18 19:48:27 localhost hcid[4261]: name_listener_add(:1.14)
Jan 18 19:48:27 localhost hcid[4261]: Default passkey agent (:1.14, /org/bluez/passkey_agent_5770) registered
Jan 18 19:48:29 localhost kdm[3892]: X server for display :0 terminated unexpectedly
Jan 18 19:48:29 localhost hcid[4261]: :1.14 exited without unregistering the default passkey agent
Jan 18 19:48:29 localhost kernel: [17179946.424000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
Jan 18 19:48:29 localhost kernel: [17179946.424000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
Jan 18 19:48:29 localhost kernel: [17179946.424000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Jan 18 19:48:32 localhost kdm_greet[5829]: Can't open default user face
Jan 18 19:48:40 localhost kdm_greet[5829]: Internal error: memory corruption detected
Jan 18 19:48:45 localhost hcid[4261]: name_listener_add(:1.18)
Jan 18 19:48:45 localhost hcid[4261]: Default passkey agent (:1.18, /org/bluez/passkey_agent_5978) registered
Jan 18 20:02:38 localhost -- MARK --

```

Hope that helps? (I tried sudo cat /var/log/syslog)

---

### Post by khedron on 2007-01-18
I think the important line is probably 
> Jan 18 19:48:29 localhost kdm[3892]: X server for display :0 terminated unexpectedlyTry /var/run/Xorg.0.log for X problems

---

### Post by tronica on 2007-01-18
This doesn't sound good either

> Jan 18 19:48:22 localhost kdm_greet[5620]: Internal error: memory corruption detected

---

### Post by khedron on 2007-01-18
I get that too, but I'm not sure whether it correlates with a crash. I tend only to check the log when I get a crash, so that might influence my opinion.

---

### Post by tronica on 2007-01-18
did you look at xorg log?  You might try to reconfigure xorg with
> 
sudo dpkg-reconfigure xserver-xorg

---

