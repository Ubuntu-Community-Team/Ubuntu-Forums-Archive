---
title: "updated ubuntu 22.04.3LTS not working"
date: 2023-11-16
forum: General Help
---

### Post by sir.Evan on 2023-11-16
I have had some problems lately with my laptop version of ubuntu. It seems to have escalated to a point now where even login is problematic and when logged in the system wants another login if you try to start anything.
in desperation i managed to start the terminal. but as soon as i try to start a browser or anything else a new login is required .

I think there is serious trouble with my ubuntu.

Help is definitely needed.

I am writing this message on my desktop updated version of ubuntu 22.04.3LTS (same as the laptop) and it seems to work perfect.

---

### Post by Rubi1200 on 2023-11-17
Start with these steps.

1. open a terminal with Ctrl+Alt+T and run these commands:
```
sudo apt update
sudo apt upgrade
```

if there are errors, post the output here for analysis

2. if there are no errors, then do this:
```
sudo passwd -S <username>

```

Replace username with your actual username. This will check if your account is somehow locked or disabled. If it returns L or NP then you can unlock it with this command:
```
sudo passwd -u <username>



```

Let's first see if any of this helps before considering next steps.

---

### Post by sir.Evan on 2023-11-21
Thank you for your reply.

since i posted about my faulty system it has started to work but with software updates etc in between.
it would still suddenly stop working and require a new login after some waiting with a blinking _ in the top left corner of a black screen.

after your suggested commmands 

9 apps needed to be upgraded and it was done with no errors.

I am surprised that the normal software app hasnt done these upgrades.

maybe it better to do the udate and upgrade command instead ?????



sudo passwd -S <passw>
created this message
bash: syntax error near unexpected token `newline'

I am sure the system will work perfect now even if the above commands didnt work.

i will run the system for a while and give feedback.

thanx a lot

---

### Post by ian-weisser on 2023-11-21
> **sir.Evan said:**
> 
it would still suddenly stop working and require a new login after some waiting with a blinking _ in the top left corner of a black screen.


Possible desktop crash or video card crash.
Look in /var/crash for .crash files. The creation dates should match the "suddenly stop working" times.
Also check your syslog and journal for those times.

.crash files, if they exist, are text, You can read them. They contain tremendous technical detail about what went wrong.
log errors at the time of crash often contain highly useful troubleshooting information. That's what the logs are for.
If neither .crash files nor useful log clues exist, then the culprit is likely a hardware fault.

---

### Post by sir.Evan on 2023-11-22
Hi all,
my system has been running perfect since the update upgrade command.

I believe my case to be closed.

Thanx [COLOR=#000000]ian-weisser for your advise but at the moment i dont know how to get to the crash-files.  Need more education......!

I have saved your response and will look for the files if the error re-appears.


Thanx everybody for your fantastic help.[/COLOR]

---

