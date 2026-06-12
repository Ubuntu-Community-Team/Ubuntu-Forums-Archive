---
title: "FF freezes on one site"
date: 2006-10-31
forum: General Help
---

### Post by canadianwriterman on 2006-10-31
I'd like to know if this site:

[http://news.com.com/]("http://news.com.com/")

freezes in anyone else's Firefox (Edgy). It also freezes on me in Epiphany on Edgy, but not in Opera. Thanks.

---

### Post by dringess on 2006-10-31
Works OK in Firefox 2 in Edgy for me...

---

### Post by matthewstory on 2006-10-31
epiphany uses the same engine as firefox . . . so it's not surprising that it froze both.  Though the site doesn't freeze my firefox 1.5 in breezy, or firefox 2.0 in OS X . . . if that helps.

---

### Post by canadianwriterman on 2006-10-31
Interesting. Sounds like I might have a plug-in conflict, perhaps.

---

### Post by lazy13 on 2006-10-31
Freezes for me too.  Console out put as it freezes is:

> 
THttpSocket::Connect attempt
THttpSocket::Connect opened
THttpSocket::Connect done error 0

I have no idea what it could be.

---

### Post by tmahmood on 2006-10-31
I'm having some serious problems... In some websites Firefox causes X server to restart :( Edgy here with ff2.

---

### Post by canadianwriterman on 2006-10-31
Found the problem. It was the beta of Flash player 9 that I installed through Automatix. When I uninstalled it and used Add/Remove to install the older version 7 that Ubuntu supports, everything is fine.

---

### Post by Senak^2 on 2006-10-31
On some websites my xserver dies and tty freezes while other times the computer shuts down invountarily. This always happens on specific websites and I've had these problems in both Firefox 1.5 and Opera 9. What the hell is up with that?

---

### Post by canadianwriterman on 2006-11-01
Automatix2 has now been updated with a fix to the problem of Flash beta 9 crashing Firefox on some sites. I changed back to beta 9 and everything works perfectly now.

---

