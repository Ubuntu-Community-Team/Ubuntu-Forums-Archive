---
title: "How safe is Chromium from hacking attacks?"
date: 2018-08-16
forum: General Help
---

### Post by webmiester on 2018-08-16
Hi everyone,

I have to log-in my Chromium to a google account so that I retain the settings...  How safe is this?  Is it possible for a hacker to use my google account to take control of my computer?  I remember that Chrome had some sort of remote desktop before, but I think it doesnt work on Chromium.

---

### Post by kc1di on 2018-08-16
Hi Chromium is a bit more secure than Chrome.  I have not heard of any instance where anyones computer has been taken over by someone using a chromium bug.
[This page by Linux insider ]("https://www.linuxinsider.com/story/79510.html")may be of help look at the section entitled security. 
and here is a comparison of[ chrome vs chromium]("https://www.howtogeek.com/202825/what&#8217;s-the-difference-between-chromium-and-chrome/"). The only way to be completely safe on line is to not go online at all.  
But you can take steps - like enable ufw firewall and make sure your system is updated regularly to upgrade security fixes. 
good luck.

---

### Post by missmoondog on 2018-08-16
i guess i have to ask, but why do you HAVE to login chromium to your google account to retain settings? i have never had to do that and in fact, wouldn't do that just because it's google! that right there is a bigger security risk than worrying about your computer getting hacked, IMO. 

i have used chrome, chromium, vivaldi and slimjet (those last 2 are both based on chrome/chromium) and have NEVER logged them into my google and it still retains google setting.

---

### Post by kc1di on 2018-08-16
> **missmoondog said:**
> i guess i have to ask, but why do you HAVE to login chromium to your google account to retain settings? i have never had to do that and in fact, wouldn't do that just because it's google! that right there is a bigger security risk than worrying about your computer getting hacked, IMO. 

i have used chrome, chromium, vivaldi and slimjet (those last 2 are both based on chrome/chromium) and have NEVER logged them into my google and it still retains google setting.

I Think the OP was thinking of syncing with his google account to get save bookmarks ans such.  But you can do the same thing locally by exporting your bookmarks,etc. and importing them from a saved file. 
Just a guess though.

---

### Post by webmiester on 2018-08-31
Hi,

Sorry for the late reply.

Im setting up kiosks for a company system.   The system runs on a local server so I dont want people to use chromium to surf the net, just the system.

Now here is my problem...

I need the pop-ups to be allowed so that the system will work.  Certain features such as printing reports uses the pop-up to work.  Chromium was set to block pop-ups by default.  Whenever I set the pop-up to "allow", and restart, the setting goes back to default.  Same goes with things like remembering passwords (Which is set as ON by default).

So to fix this, I made an account and make a profile there.  The profile is saved and when I load Chromium, I set it to use that profile.  However, the profile requires a google account.  Since the profile is in a directory in my computer, I think it will still be loaded even if the terminal is offline.  However, I am worried that since there was something called Remote Access, someone ,might exploit this to take over Chromium.

Thank you so much for your answers btw!  Its really refreshing to read your posts.

---

### Post by bizhat on 2018-08-31
Remote access in chrome is an extension.

[https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en](https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en)

If you just install this extension, it allow you to connect to remote computers using chrome remote desktop. But to share your PC with others, you need a .DEB file downloaded from google and install. 

If you don't install the extension, you don't have to worry about it,

---

### Post by webmiester on 2018-09-02
Thanks so much.  Its nice to know its just an extension that needs installation.  I think I am just being a bit paranoid knowing that reotely accessing chrome is even possible. Actually, Ive removed the kiosk app for the same reason.  The kiosk app used to be fine, but the kiosk app extension was upgraded and it allowed something that sounded like remote access, so I removed it, but I had to do a lot of reconfiguration for those terminals.

Thanks so much for your replies

---

