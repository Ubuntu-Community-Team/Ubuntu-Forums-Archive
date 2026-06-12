---
title: "likewise-open5 is losing the connection to AD and forgetting who I am"
date: 2012-11-19
forum: General Help
---

### Post by rugbert on 2012-11-19
So Im suffering from some serious likewise issues on my work machine. For whatever reason, after I login to the domain, I will lose my AD connection after about a minute.

I can get to the login screen, and my username is in the login box (I changed the greeter to allow for manual login) so I can login just fine. If I pull up the console immediately after I login then I see my username@hostname and can execute commands with sudo. 

But after about a minute, or if I open a new terminal window it seems that likewise forgets who I am and will only show a '$' at bash. If I try to use any sudo commands I get some "cannot find user with uid:43435435. who are you?" Or something like that.

And then it gets even weirder. If I switch users to the computer's local admin, and then try to switch back, the screen is all black unless I move my mouse which causes the screen to flicker on, with no login dialog visible.

edit - Im running Ubuntu 12.10 and likewise-open5

---

### Post by Kirk Schnable on 2012-11-20
We have been running Likewise 6 at my work for some time, and are moving our new 12.04 labs to PowerBroker Identity Services 7 (PBIS-open). (Likewise is no longer maintained under its old name). Is there a reason why you are using such an old version?  These problems may already be fixed in newer versions. 

Kirk

---

