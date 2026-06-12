---
title: "Cannot access Desktop contents -- permission denied"
date: 2007-05-04
forum: General Help
---

### Post by B-Con on 2007-05-04
I just upgraded to Feisty Fawn via a clean install. Everything seems fine thus far, but I just lost control of my desktop.

I'm not sure exactly when it happened, but I was messing with some bash login scripts and they weren't working. So after a couple login/outs of testing them, I just said screw it and ditched them. Then I noted that my Recent Documents "feature" under "Places" had recent documents in it, which was weird because I'd disabled write permissions for the .recently-used file in my home directory not long ago. But permissions had been set back to normal. Frustrated, I deleted it and the corresponding .xbel file, re-created them both, set their permissions to 400, then owned them as root. Harmless enough. (Turns out that doesn't work for clear the recent documents feature, I'll have to figure that out later, that's low on my priority at the moment.)

So I mention that only because that's what I did right before I noticed the problem -- I have no idea if it's related or not but my problem seems to be permissions related. 

Right after I did that, I tried to cd into my Desktop directory. I just got an error back:
> bash: cd: Desktop: Permission denied
Apparantly I couldn't "cd" into my own Desktop directory. I tried to "ls" it but got everything in red text with a black background (like a hard link's natural color). (I'm using a standard black on white color scheme, btw.) 
 Baffled, I tried accessing my desktop graphically, but any time I tried accessing a file, I got a 
> Couldn't display "/home/b-con/Desktop/file_name"
The attempt to log in failed.
error.

I checked my Desktop's folder permissions: Yes, I owned it and I had permission to read from it. Just to be sure, as root I owned the Desktop folder and all the contents in my normal user account's name, then set permissions to 644 for the Desktop folder and everything in it. Still nothing.

I tried rebooting and logging in with the Gnome Safe Mode -- no luck.

I tried "ls"ing the Desktop as root and it worked fine. I did a "ls -l" of the folder and everything reported back 

What could cause this? I assume the "failed login attempt" is the biggest clue, and it makes me wonder if I somehow didn't screw with something with a login script, or something. But I only added one line to one file and then removed it -- shouldn't be a big deal.

Any ideas?

[EDIT]

Problem fixed... Apparently a "chmod 755 Desktop" was in order. I could've sworn I already tried that -- I mean, duh. :confused:  :-S

Carry on...

---

