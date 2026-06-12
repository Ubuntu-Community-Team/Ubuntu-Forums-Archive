---
title: "firefox gives me an error on startup"
date: 2008-01-22
forum: General Help
---

### Post by Zeenomorph on 2008-01-22
I have a problem with Firefox that I was hoping that you would be able to help me with.

My computer froze while firefox was running, and I was forced to do a hard reboot.

When I came back, and tried to start firefox I got this error;

"Could not initialize the browser's security component.  The most likely cause is problems with files in your browser's profile directory.  Please check that this directery has no read/write restrictions and your hard disk is not fill or close to full.  It is recomended that you exit the browser and fix the problem.  If you continue to use this browser session, you might see incorrect browser behaviour when accessing security features."

I was shocked to see this.  It was working fine before the hard reset.  So the first thing that I did was reset again.  --Same error message.

I then checked my firefox profile directory under /etc/firefox and the owner seems to be root.  Is that normal?  I'm not very computer savy, and could not figure out how to change the ownership, and couldn't get online to ask all of you, so I did the only thing that I could think of -- reinstal.  --Same error.

I then thought that maybe it was something to do with the reinstal, so I completely removed everything firefox from my computer.  (Took me a long time to figure out how to rm a directory, but eventually got it).  I then installed firefox from scratch thinking that the problem couldn't possible persist through that.  --Same error.

Now I'm using a browser called Epiphany.  I installed it so that I could at least get here to ask all of you, but I sure would like firefox back!

---

### Post by sports fan Matt on 2008-01-22
When you say "froze" what exactly do you mean?  No mouse actvity, cant click on things? Have you looked in your Firefox folder to see if things are still intact?  

Sorry, but I cant remember where the Firefox folder is

---

### Post by Zeenomorph on 2008-01-22
The problem is no longer the freeze.  The problem is starting firefox.

But as to the freeze, I meant that I couldn't click anything, and the computer was completly unresponsive.  

The Firefox directory is in /etc/firefox

---

### Post by sports fan Matt on 2008-01-22
If you open places>home folder>view>Show hidden files (CTRL +H) then look in the mozilla folder what is in the folder?  Im not sure what all is supposed to be there but if files are still intact, id take that as a good sign...

---

### Post by Zeenomorph on 2008-01-22
There are 2 directories firefox and plugins as well as 2 files mozer.dat and pluginreg.dat

---

### Post by sports fan Matt on 2008-01-22
like i said , im not totally sure but id look in the firefox directory and maybe, just maybe its a plugin thats misbehaving?  Its happened to me once or twice..:)

---

### Post by Zeenomorph on 2008-01-22
That would be strange since I completly removed firefox and installed it clean.  I can't see how there could possibly be a problem of any kind.  I'm baffled.

---

### Post by sports fan Matt on 2008-01-22
Yeah, me too, but computers can sometimes hiccup..:)

---

### Post by Zeenomorph on 2008-01-22
I have the solution:

ctrl +h to show your hidden files in your home directory.
rename the .mozilla folder to .mozillaOLD.

You'll lose all of you profile information, but you'll be back online, and able to do it again.

It's a pain in the *ss, but it gets it done.

---

### Post by sports fan Matt on 2008-01-22
its better then having to take more drastic measures...:)

Edit: 301 posts:)

---

### Post by Zeenomorph on 2008-01-22
A little further information;

This problem seems to be related to the Firefox extension called "AllPeer".  It was after installing this that the problems started.

I spent some time trying to get my firefox back the way that it was, and as soon as I put "AllPeer" on, the problem happened again.  AllPeer removed -- problem removed.

---

### Post by BobLand on 2008-01-22
All of your files should be owned by you unless you are running as root.

---

