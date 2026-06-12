---
title: "should I make /etc writeable for my account?"
date: 2008-04-06
forum: General Help
---

### Post by glisignoli on 2008-04-06
I'm having a few problems with some of my applications trying to save settings into /etc. Currently /etc can only be edited by root while all other users can access files but not edit them.
Is it going to break my system if I make /etc writeable by my main user as well?

---

### Post by dasunst3r on 2008-04-06
**Don't do it!**  By doing this, you could open yourself up to some security breaches.  Programs typically write your preferences and other data into your home directory, not /etc.  What programs are giving you grief on this?

---

### Post by glisignoli on 2008-04-06
qtnethack and urban terror so far, but I'm sure I could find more.
What about making a link (I have no idea if that would work)

---

### Post by danwood76 on 2008-04-06
changing the permissions of the /etc folder will break your system.
a guy recently did this on his system on these forums and he ended up reinstalling.

like previously stated most apps dont store their settings in the /etc folder but in your home folder instead.

did you install these two apps from source?
you may need to pass them extra settings upon building to make them put the settings in the correct place.

---

### Post by glisignoli on 2008-04-06
urbanterror I install from the ut site. But qtnethack was from the package manager.
There doesn't seem to be anything in my /home folder for configuring either.

---

### Post by kerry_s on 2008-04-06
have you checked the man pages?

man qtnethack
man ntterror

---

### Post by glisignoli on 2008-04-06
I solved the problem by making symbolic links to the same files in my /home/.qtnethack dir. Although It would have been nice if those files where there all ready

---

### Post by brian_p on 2008-04-06
> **glisignoli said:**
> I solved the problem by making symbolic links to the same files in my /home/.qtnethack dir. Although It would have been nice if those files where there all ready

There isn't a single program in a Linux distribution which writes to its configuration files in /etc and there are excellent reasons for that that you really should investigate. if you have made the files in /etc writable to you have undermined the multi-user nature of the OS and it is an abuse of the sudo command. If you did it on my machine your privileges would be much reduced or removed.

If you want a configuration file in your /home directory it is very often the case that it can be copied from /etc and customised to your needs. For example, xpdf has xpdfrc in a directory in /etc. It can be copied to /home/user/somewhere. Reading the manual for an application will inform you of your options.

---

