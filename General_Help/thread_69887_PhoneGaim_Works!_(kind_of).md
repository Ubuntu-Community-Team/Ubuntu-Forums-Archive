---
title: "PhoneGaim Works! (kind of)"
date: 2005-09-28
forum: General Help
---

### Post by Zachs23 on 2005-09-28
Before I go all-out and write a howto about how to install phonegaim, I am having an issue that makes it unusable. The reason I really tried to get Phonegaim to work was the fact that I have to use two IM clients at once, one for VOIP and gaim for everyone who uses AIM or yahoo, etc.
First of all, you have to add
deb [http://people.debian.org/~smimram/debian](http://people.debian.org/~smimram/debian) unstable main
deb-src [http://people.debian.org/~smimram/debian](http://people.debian.org/~smimram/debian) unstable main 
to your /etc/apt/sources.list file. It will now be installable via apt-get or synaptic (be sure to unisntall gaim first:) ) The other problem is, when you attempt to create an account for the Sipphone service, it states the version of phonegaim is too old. The way I figured out to get around this:
1. Download and install Gizmo Project ([www.gizmoproject.com/](www.gizmoproject.com/)) 
2. Register for an account through that software.
3. Once the account is created, go to [www.sipphone.com](www.sipphone.com) and log in using the email address you just created an account with
4. Copy and paste the phone number you see at the top of the members page into phone>Preferences (or something similar) in phonegaim
5. Now if you log out and log back in to sipphone.com, you should see that it now says that your virtual number is "online"
Now there is one more minor problem, the default sound (for me) did not work, and everytime I received a message, phonegaim spat an error message back at me :o . The easy fix is to go into the setting and disable the receive sound, or choose a new sound for it. After doing all this, phonegaim crashes at (what appears to be) random intervals. Sometimes it will do it almost instantly after starting it, sometimes it will take an hour. If you run phonegaim by console (the command to run it is still "gaim"), it only displays a generic "Gaim has crahsed" message, with no specifics. So what I am asking the community is for someone who is more knowledgable about coding please install phonegaim and see if it crashes for you (as I said, it might take a while), and if so, try to figure out why. Phonegaim is the perfect app for me and for a lot of others who have to cater to those using AIM, but would still like to use VOIP technology in linux.
Thank You very much for your help in this matter, good luck!
P.S. I am going to be honest, since I have been having problems with phonegaim, I have not had any of my friends try the VOIP with me, so I do not even know if that will work. However, the text IM features work perfectly.

---

