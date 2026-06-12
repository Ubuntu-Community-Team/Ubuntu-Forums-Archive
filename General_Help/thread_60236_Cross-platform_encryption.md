---
title: "Cross-platform encryption"
date: 2005-08-27
forum: General Help
---

### Post by npaladin2000 on 2005-08-27
This is a bit of a wierd question, but every once in a while I need to get onto a windows machine and do things.  Is there a method available for both platofrms (Windows and Linux) that will let me encrypt/decrypt files on a USB key or something?  SO far I haven't found anything.

---

### Post by chiefofthejojos on 2005-08-27
Yep.  And it's very simple.  
I was just looking for the same thing yesterday and I was looking for some nice graphical cross-platform tool on sourceforge and then I had a thought:
gpg?
I was on windows at the time so I opened up a command prompt and typed "gpg --help".

to encrypt you type:
gpg -r <recipient> -e <filename>
where <recipient> is an email or a name, someway to identify the key you're using to encrypt and <filename> can include wildcards.  Of course, you will need to generate a key to use to encrypt the file and you will also need to install the key on the computer(s) you will decrypting on.

to decrypt:
gpg -d <filename>
and it asks for the password.

It's easier than it sounds, really.  On windows "Windows Privacy Tools" or WinPT is a nice gui front end and there's probably something for linux too but I'm not sure what it is.

---

