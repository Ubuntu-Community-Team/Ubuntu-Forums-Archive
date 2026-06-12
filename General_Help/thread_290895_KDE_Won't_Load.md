---
title: "KDE Won't Load"
date: 2006-11-01
forum: General Help
---

### Post by DMPineau on 2006-11-01
First time posting here, I'm a newer Linux user having some trouble with Kubuntu 6.10.

Here's whats going on: I've been trying to get my ATI drivers installed, and I was editing the xorg.conf file. I had some trouble with write protection and I couldn't save some changes I made to the file using the text editor. So I set up a root password using the su command in terminal, then I used the chmod 777 xorg.conf command and that seemed to work - the file finally saved. 

Then I reboot my computer, and now when Kubuntu loads I'm stuck in a fullscreen prompt which asks for my username and password - but the desktop wont load. This prompt seems to be the kterminal.

How can I load KDE from the prompt?

---

### Post by DMPineau on 2006-11-01
bump :???:

---

### Post by podunk on 2006-11-01
When you want to edit a file you can type
```
sudo nano /path/to/file
```

or (once your desktop is up)
```
kdesu kate /path/to/file
```

This will avoid all the chmod stuff, it'll be easy to save your files.

To try and get out of your fix you might try
```
startx
```
and when that doesn't work you could try
```
sudo dpkg-reconfigure xserver-xorg
```
If you don't know the answer to something just press enter to accept the default.

I haven't tried 6.10 yet - I'm waiting for the dust to settle and letting everyone else work the kinks out. :) But ATI in Dapper is a bugger bear. I have an older card (9200) and when I got to the point where you're at there was no recovery, the set up was borked.

I found it best to just do the set up over, back up the xorg.conf, then try a different tutorial. It took me 4 or 5 tries to get one that works. For me, the page here
[www.wiki.cchtml.org](www.wiki.cchtml.org) 
Dapper Drake method one worked.

---

### Post by DMPineau on 2006-11-02
Ah, thanks for the feedback. It was just a matter of resetting xserver.
Oh and thanks for posting that 'kdesu kate /path/to/file' command line, that's been a lifesaver.

---

