---
title: "[SOLVED] Hardy Heron Skype won't log in"
date: 2008-06-26
forum: General Help
---

### Post by doubleij on 2008-06-26
I upgraded my Acer Aspire 4315 to Hardy this past weekend. All went well (had to add a madwifi driver, but that's it). I tried to install skype today and ran into a very strange problem.

I had a debian version of skype (2.0.0.6 eight [Note: sorry for the "eight" but there's an emoticon if I type the number 8 next to 6]) and I also tried the repo version from medibuntu (2.0.0.72). In both cases, the installation went fine but I could not get past the skype welcome screen. I have an account already, so I attempted to enter my username and password but the login button remained grayed out and I couldn't click it. I fiddled with options and everything I could think of, but I still couldn't click the login button.

I am aware that some Hardy users have had issues with PulseAudio, but i can't imagine that the sound driver is not allowing me to login. A friend of mine has put -0.68 from debian on his computer (running Hardy) without troubles. This points to an Acer-specific issue, but again I can't understand why it would keep me from logging in.

BTW, skype worked fine on the same machine in Gutsy. Thanks for any help or ideas...I couldn't find a similar problem anywhere on the net or forums, so I'm feeling really stuck.

---

### Post by PmDematagoda on 2008-06-26
Open a terminal and execute:-
```
strace skype 
```
then at the place where it freezes, post the outputs of the command here.

---

### Post by doubleij on 2008-06-26
See the attached readout. I have no idea what it's talking about! I had to edit the readout pretty heavily to get it below the forum's limit for txt attachments. It was long but it was repeating the same stuff over and over.

---

### Post by PmDematagoda on 2008-06-26
There doesn't seem to be anything wrong, except that "Resource is temporarily unavailable" error is a bi suspicious. Now, if you start Skype by executing it in the terminal, does it turn up any errors?

---

### Post by doubleij on 2008-06-26
I wonder if the issue mentioned over here might be related. I have my Skype set to autodetect, so that may not be a problem. However, my password is quite long and is very garbled with numbers, characters, etc. 

[http://ubuntuforums.org/showthread.php?t=104311](http://ubuntuforums.org/showthread.php?t=104311)

I may try to reset the password and see if a simple password will work. 

Another possibility is that I have been pasting the password into the box because of its length. Perhaps I need to type it for Skype to recognize the password?

Just simple stuff, but that might be all that's needed. I'll fiddle with it tonight, hopefully.

---

### Post by doubleij on 2008-06-29
Solved! I changed the password to letters and numbers only and typed it in by hand. As soon as I got halfway through the password, the login button became clickable. Thanks for the ideas...

---

