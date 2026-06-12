---
title: "Rhapsody on firefox."
date: 2007-12-09
forum: General Help
---

### Post by coolgreen1 on 2007-12-09
Hi,

Every time I try to get the 25 free songs a month on rhapsody's website it asks for me to install a plugin. So I tell it to install the plugin but when it is finished downloading it cannot install because I get the error Insufficient disk space. Error code -235. But I have over 9 gigs left on my hard drive for ubuntu. Any help would be appreciated. Thank you.

P.S. I have ubuntu gutsy amd 64

---

### Post by Eion on 2007-12-11
I get the exact same problem.  Anybody have any idea how to fix this?

---

### Post by emptymind on 2007-12-26
I have this problem too ... I don't think their plugin work works on AMD64. I have installed Firefox for Windows using Wine and the plugin "works" there but there are several problems with that ... sometimes I have trouble logging in, sometimes the songs just skip without playing. I am hoping to somehow get the plugin to work natively on Firefox on AMD64.

---

### Post by GSands on 2007-12-26
Hey everyone:)
I got the following from Rhapsody thought I would pass it on.

My name is Mike. I am a Real Networks Tier 2 Technical Support Representative. Your case has been escalated to our department due to severity. Thank you for your continued patience, and I would like to apologize for any inconvenience you may have experienced so far. 

I have followed this thread since the day you initiated it. As I understand it you wish to know when a Linux Rhapsody client will be available. I can help you with this.

Unfortunately I do not have a ETA on even a beta test version of a Linux compatible Rhapsody client. I know the Rhapsody developer's are working on it but do not have any information as to when to expect it's release.

---

### Post by GSands on 2007-12-26
Ah a second thought I haven't been able to run Rhapsody with wine either.  I'll wait for the Linux version I have no desire to even dual boot my computer.

---

### Post by dasunst3r on 2007-12-26
The Rhapsody plugin installs to ~/.mozilla/plugins.  Make sure that your plugins directory exists and is chmodded to 755: *chmod 755 ~/.mozilla/plugins*.  Try again after that and see if it works.  Real should consider teaming up with Songbird ([www.songbirdnest.com](www.songbirdnest.com)) and let them do some of the dirty work.

---

### Post by emptymind on 2007-12-28
I noticed that I didn't have a .mozilla/plugins directory and creating that got rid of the insufficient disk space error. The rhapsody plugin installation goes through smoothly and there is a pop-up message which says something like "thanks for installing the rhapsody plugin". 

Unfortunately, the sign-in screen never comes. It keeps going back to the screen which asks you to install the plugin.

I looked in the .mozilla/plugin directory and see the nprhapengine.so library file. It was not executable so I did a "chmod +x nprhapengine.so" and restarted firefox, but still to no avail. Everytime you re-install the plugin, it will replace the nprhapengine.so file with executable rights turned off.

Seems like it's getting closer ... any ideas? Anyone?

---

### Post by emptymind on 2007-12-30
Update: I had an old copy of Windows 2000 lying around and installed it using VMWare. Rhapsody works perfectly now. I know this isn't really a solution but I wanted to try VMWare out anyway. i had spoken to a Rhapsody tech rep earlier and he had no clue whether the plugin works with AMD64. Hopefully, they come out with a full-fledged Linux client soon, as they have promised.

---

### Post by mrgnash on 2007-12-30
Last.FM?

---

