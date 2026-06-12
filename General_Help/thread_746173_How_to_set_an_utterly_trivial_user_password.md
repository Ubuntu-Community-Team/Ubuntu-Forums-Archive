---
title: "How to set an utterly trivial user password ?"
date: 2008-04-05
forum: General Help
---

### Post by Raptor Ramjet on 2008-04-05
Hello,

I've got a box on which I wish to set an utterly trivial password of say "1Xu" or even "x".  Unfortunately the fresh Gutsy install on the machine wouldn't let me do so as when I use "passwd" this tells me the password entered is too short (I didn't even bother with the GUI as I know this won' let me set such a short password)

I cannot even use "passwd --force" as the version of "passwd" on the box doesn't seem to conform to the version I find MAN information for on the internet.

This is somewhat infuriating as quite frankly it's nobody elses business what sort of password I wish to set on *my* machine !  If I decide to have a stupid password policy that's my business and my business alone :)

For those now thinking "but that's not secure", "your password should be hard to crack" etc. etc. please note that I really, really, REALLY don't care :)  

Why ? Because the machine in question in an old literally "skip recovered", desktop machine (400Mhz) which I wish to use as a dedicated Hydrogen drum machine.   The only reason I'm running a GUI on it at all is to use Hydrogen and, possibly to do a spot of file management.

And the only reason I'm putting a password on it at all that it's left in a shared rehearsal room so I'm using a custom GDM screen which tells people not to try installing Windows on the box and to leave it alone.

So all I require is a minimum nuisance level of password as it *really* doesn't matter. However I don't really want to leave the machine with NO password.  

If this is the only alternative to a "proper" password I'll remove the users password hash from the file (can't remember if that's /etc/shadow ?) but I'd much prefer to set a totally trivial password.

So any ideas how to do this would be most appreciated.

Cheers.

---

### Post by sisco311 on 2008-04-05
```
sudo passwd *username*
```

---

### Post by exodus_ on 2008-04-05
Hey,

Have you tried running passwd with sudo?  I created a trivial user with the password 1Xu successfully.  Using sudo I could change the password to anything I wanted, even a single-character password.

trying to change the password to such a trivial password as an unprivileged user gave me the "too short" error, too.

Hope this helps

---

### Post by aysiu on 2008-04-05
This may help:
[HowTo: Create a Passwordless / Guest Login (Simple Method)](http://ubuntuforums.org/showthread.php?t=513820)

It won't set up a short password, but it'll set up no password.

---

### Post by Raptor Ramjet on 2008-04-05
Thanks all.

And I shall wear my dunces hat for the rest of the afternoon as I simply forgot all about sudo...  D'oh !  

Mind you I was in the middle of configuring three different machines at the time so I have a slight excuse (he says feeling rather sheepish)

Cheers !

---

