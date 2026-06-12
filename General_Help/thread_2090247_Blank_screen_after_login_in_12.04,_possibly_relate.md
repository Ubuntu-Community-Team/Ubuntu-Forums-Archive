---
title: "Blank screen after login in 12.04, possibly related to Thunderbird"
date: 2012-12-01
forum: General Help
---

### Post by NateP on 2012-12-01
I've hit an issue that's been hard to troubleshoot. I've googled around a bit and searched the forums, but no luck so far. 

I'm using Ubuntu 12.04. This morning I started using Thunderbird for the first time (previously relying on internet mail). I created an account and the first thing I tried to do was search for a Lightning add-on. Thunderbird crashed in the process, and my computer froze. I couldn't get it to recover and ended up using  CTR+ALT+SysRq+REISUB  to gently reboot. 

However the next time I tried to log in, as soon as I got past the login screen, I only saw a blank bright blue screen with my Cinnamon bar along the bottom, and my mouse. I could interact with the bar but start nothing. When I tried to start a terminal, nothing happened. When I tried to start Firefox, after a few seconds a crash report would pop up. Nothing else seemed to have any effect.

I restarted a few times, and shut down, waited, and booted a few times. The result is always the same, although every once in a while, the screen following login is black with nothing else, or just my regular desktop picture with nothing else.

I (fortunately) have another account on this computer, which I can log into just fine (I'm using it now). It's only when I log into my usual account that it appears to freeze in this strange way. 

Any thoughts? I've spent a bit of time looking around for this happening elsewhere, but not much luck (many "blank screen" problems, but they all seem different than what I am experiencing, since my second account is working fine).

*Edit: If there is a better place to post this, please let me know!

---

### Post by ohnonot on 2012-12-03
it does sound creepy.

you can try this: exit thunderbird and firefox.
rename your ~/.mozilla and/or .thunderbird or .firefox folders. (as backup)
uninstall thunderbird and firefox.
log out/in-->better???

---

