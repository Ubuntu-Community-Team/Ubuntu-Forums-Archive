---
title: "Hardy = Windows 98 ???"
date: 2008-05-17
forum: General Help
---

### Post by SpaceTeddy on 2008-05-17
I am seriously getting p***** off with hardy. Majorly. Since yesterday evening, when the new updates came in, i cannot use any heavy data transfer anymore. Why ? well - the system freezes. just like that. I don't know when, i don't know why. Everything just stops. And there is NO way of getting to back except to cut the power. No consoles will work, not even the mouse moves or the clock runs anymore. It totally dies. And no, this is NOT a kernel panic, as the leds on the keyboard are not blinking (which would indicate a kernel panic) - well, they do not. The system just freezes. 

This has happened to me three times today.

1.) i was watching a video clip via totem from an ssh share. Went for about 5 minutes - then froze.

2.) i mounted a directory via sshfs from another computer and copied a file. I got 50 Megs - then the computer froze

3.) I was downloading a file via http over an openvpn connection. I got 70 Megs - freeze. 

All these have in common that they utilize the openssl libraries which were patched (hastily ?) during the last days. But that is only an assumption to the problem. I have no accurate proof of anything - since the system does not write down any errors. 

If anyone has any idea how to debug this problem, or how to fix it - please tell me so. 

PS: sorry for the bad title, but this is exactly what i am thinking. I NEVER had this many instability problems before. I have not installed anything that does not come from the repos, and i do NOT use any fancy software (except compiz).

---

### Post by kevdog on 2008-05-17
I was surprised to see this title with your name appended to it?!!  I know you are an experienced user -- very experienced.  I haven't upgraded to Hardy yet based on opinions from reputable users like yourself.  In fact I'm contemplating giving Arch a go if I get time.  Hardy seems Hardly like an improvement based on opinions of experienced users -- can't believe its a LTS.

---

### Post by eriqjaffe on 2008-05-17
> **SpaceTeddy said:**
> All these have in common that they utilize the openssl libraries which were patched (hastily ?) during the last days.Well, the quickest test I can think of then would be to downgrade openssl and see if the problems disappear.

---

### Post by SpaceTeddy on 2008-05-18
yes, i've been thinking about that too, but how do i check it. Just because it happened three times with data transfers, does not mean i can force it again to freeze with that. I simply do not know when the freeze will occour or how to force it to occur (which would give me a hint on what is acctually happening).

so, installing the old openssl libraries will not work as i don't know of the problem was fixed or not...

do i make sense ?

---

