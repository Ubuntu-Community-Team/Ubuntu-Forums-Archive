---
title: "Firefox and Spellbound"
date: 2005-03-23
forum: General Help
---

### Post by DrMoxie on 2005-03-23
Hi all, hoping that you might have an answer to my dilemma.  I recently upgraded my Ubuntu distro to Hoary and everything went smoothly with the exception of installing the Spellbound extension for Firefox--I had it installed and working under Warty.  

The spellbound site states, “Your user account will need write access to your Firefox application's components directory to install the spell check libraries,”  so I went ahead and changed the permissions on the folder /usr/lib/mozilla/compoments to the following: drwxrwxrwx  2 root root   4096 2005-03-22 17:35 components.  However, when I attempt to install spellbound everything looks like it is going smooth but nothing gets dropped in the components directory and spellbound returns an error stating that I need to re-install the libraries.  

Caveat, I am a total n00b coming to Linux from a Windows environment but am really willing to learn and understand.  Two months on Ubuntu and I'm loving it. 

Thanks!

---

### Post by Bob D. on 2005-03-23
I just successfully installed Spellbound for Firefox on Hoary. I'll walk you through what I did and then what I might do different next time.

What I did was:

1)  Launched Firefox from a terminal using "sudo -H firefox". Now Firefox is launched for root.

2) Went to the Spellbound site. Download and installed all 3 packages (Spellbound, libraries, and dictionary.

3) Closed Firefox, launched again as a non-root user.

4) Repeated #2 above.

5) Closed Firefox, relaunched again.

6) Right clicked on a toolbar, selected Customize...

7) Added Spelbound icon to toolbar.

That's it. Spellbound is now working just fine.

What I did is most likely overkill. I think the only files you really need to install when Firefox is run from sudo is the dictionary file(s) and the libraries. Installing the Spellbound extension from root is not necessary.

Bob

---

### Post by DrMoxie on 2005-03-23
Thanks so much Bob!  That worked like a charm and now no one has to suffer the manner in which I butcher the English language!   =D>

---

### Post by Red Knuckles on 2006-01-14
[QUOTE=Bob D.]I just successfully installed Spellbound for Firefox on Hoary. I'll walk you through what I did and then what I might do different next time.

What I did was:

1)  Launched Firefox from a terminal using "sudo -H firefox". Now Firefox is launched for root.

2) Went to the Spellbound site. Download and installed all 3 packages (Spellbound, libraries, and dictionary.

3) Closed Firefox, launched again as a non-root user.

4) Repeated #2 above.

That worked for me in Breezy!:smile:

5) Closed Firefox, relaunched again.

6) Right clicked on a toolbar, selected Customize...

7) Added Spellbound icon to toolbar.

Bob[/QUOTE]

That's it. Spellbound is now working just fine.

What I did is most likely overkill. I think the only files you really need to install when Firefox is run from sudo is the dictionary file(s) and the libraries. Installing the Spellbound extension from root is not necessary.:smile:

---

