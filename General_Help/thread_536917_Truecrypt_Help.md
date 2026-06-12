---
title: "Truecrypt Help"
date: 2007-08-28
forum: General Help
---

### Post by InGunsWeTrust on 2007-08-28
Alright, I have an easy question (or what I think is easy seeing how much discussion on this there has been).

I already have an install of Ubuntu and I want to convert that volume to truecrypt encryption. All of the truecrypt tutorials I have seen have shown how to make a new encyrpted volume. I already have the command line version installed and I am simply looking for lines of code to enter into the command line.

Do not suggest I install the graphic interface because one of the dependencies wants me to uninstall beryl. So I will not intsall the GUI.

---

### Post by digitalbenji on 2007-08-28
I wasn't aware that TrueCrypt had a GUI for linux.  

As far as I know, what you are describing can't be done.  It sounds like you want to encrypt your entire Ubuntu partition using truecrypt.  That can't be done, because Truecrypt would live within that partition.  Even if you put TC outside that partition, it is a userspace application that makes kernel calls, and interacts with the operating system - the given of which is that the operating system is booted and functional.  As far as I know, the initial ram image needs to be unencrypted, or at least contain the instruction for decryption.  I could be wrong (and would be very interested to learn so, because that would be dope).  

There are some systems that you can set up, not truecrypt, for total disc encryption.  An easier solution would be to create a TrueCrypt volume, and then create a virtual machine that is saved within that truecrypt volume, thus you could boot Ubuntu normally, and then decrypt and mount your volume, and boot a virtual ubuntu that is encrypted otherwise.


Hope that helps,

---

### Post by InGunsWeTrust on 2007-08-28
Basically the reason I want to encrypt the hard drive is I have a bet with a security specialist friend of mine that says he can break into my linux drive easily. I am just making a few more impediments haha. The hole I am trying to close is replacing the password file with that of a known password. So what files/folders would I have to encrypt to make sure I completely close that hole. In addition what commands at the command line would I have to use to do so.

---

### Post by digitalbenji on 2007-08-28
Hi again,
   I'm not 100% sure I follow.  Linux passwords are stored in the /etc/passwd file, but because Debian based systems, like Ubuntu, use shadow password, this file gets moved to /etc/shadow.  The /etc/passwd file contains a list of all users, but the passwords are in the /etc/shadow file.  However, since the passwords are stored as a hash, they can't be decrypted.  Hashing is a process of taking a piece of data, and performing an operation on it that guarantees a unique piece of data be generated.  No 2 pieces of data will have the same hash, but a hash can't be reversed (it's a mathematical fact). 
  I think what you are suggesting is that he replace the /etc/shadow file with a /etc/shadow file with one he has generated, however, this assumes that he already has root access, as the /etc/shadow file is only writeable by root.  
  Am I off the mark?  Does anyone have corrections for what I've said?  Did I miss your point?

Regards,

---

### Post by InGunsWeTrust on 2007-08-28
You are correct but if I used a live CD such as BackTrack you are loaded into a filesytem as root. Since you are root you can simply mount the Ubuntu partition and create a etc/shadow file of your own. Say you login to backtrack with the credentials root pass password. and you copy the shadow file from backtrack to the ubuntu partion. This would essentially make the password password and thus they have access to the system. At first I thought that changing the boot order would circumvent this but with physical access to the machine he can pull out the CMOS battery and reset the bios password and change the boot order from the bios. Essentially what I am looking for is for a way to prevent even root from changing the password unless he is logged into the actual filesystem to which the password file belongs (say by encryping it using Truecrypt and password protecting the encryption on the /etc/ folder

---

### Post by digitalbenji on 2007-08-30
That's an interesting approach, although I suspect that the /etc/passwd and /etc/shadow files are checksummed, so that replacing them would cripple the ability of anyone to log in.  I don't know this for sure though (if not, it would probably be arbitrary to implement and a good idea).  

I guess you could set up a task that runs at boot that automatically moves a file to /etc/passwd or /etc/shadow.  That way, you could copy the good password file, name it something meaningless, like .DKE-temp-8993 or something, and stash it somewhere random, then just have the cron task move the file into place when the system comes up.  This isn't really a great solution though.  I'm going to try to research the checksum thing.  I'll let you know.

---

