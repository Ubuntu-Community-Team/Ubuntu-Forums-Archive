---
title: "Can't remote login via XDMCP."
date: 2007-04-28
forum: General Help
---

### Post by 0vv1 on 2007-04-28
Hi all. I'm trying to remotely login to my Feisty workstation using XDMCP. I'm doing so from an OSX system with the following:

Xquartz -query <ip addr>

It works this far as I get the GDM login but when I enter my username and password (definately correct) it just refreshes GDM and puts be back to username entry.

If I set automatic remote login, it works fine (as I'm not entering the credentials). 

Any ideas of what's causing this or how to fix it?

Thanks!

---

### Post by raindog21 on 2007-04-30
same problem here.  I was previously using nomachine nx to remote login from my windows box.  Then I bought a mac and have keyboard mapping issues with the os X nomachine client that I couldn't find a fix for.

enabled xdmcp on feisty and tried using X -query <ipaddress>  

I see the login menu but entering username and pwd just brings you back to the username entry.

---

### Post by smm on 2007-05-22
I'm just starting with Linux so this may be too obvious a question; but are you logged-in with the username already?  I believe you cannot have multiple logins with the same username.

Try a different username or logout and try again.

---

### Post by rapchee on 2007-08-31
a thing i missed last time: in the 'general' tab there is an option 'disable multiple logons for a single user', which is on by default., it needs to be disabled in order to log in in paralell.

---

