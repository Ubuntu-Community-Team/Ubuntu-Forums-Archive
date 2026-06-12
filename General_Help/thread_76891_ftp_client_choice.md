---
title: "ftp client choice"
date: 2005-10-15
forum: General Help
---

### Post by SuperCzar on 2005-10-15
I'm looking for a REALLY light ftp client for an old laptop that i sometimes use for web development when im on the go.  I'm running a server install with enlightenment, so the nautilus client is a no go, and the gftp client is pretty good, but I'm sure there's something better out there. 

I'd prefer a command line client i could run under aterm, but a graphical one would work too.

I've tried several command line clients. I  like ncftp2 but i cant seem to figure out how to transfer whole directories. That's an essential feature for club stuff at school.

Also it would be nice if i could find ANY linux client that supports overwrite if newer.  Filezilla will do this on windows, and its REALLY handy for updating a couple of pages and not having to deal with uploading ALL the files.  I'm not new to linux by any means so if any of you have an shell scriptable tricks up your sleeve i can handle that, but i dont know enough to actually program anything to do it for me with the standard ftp client.

Any idea folks?

-- SuperCzar


P.S. any one got any ideas for AIM clients that are lighter than GAIM? its more than i need... i just need chat, no file transfer or anything like that.

---

### Post by taurus on 2005-10-15
Personally, I use gftp and if you want to upload/download a whole directory, you just hightlight it and click the arrow in the middle of the two windows.  That's it.  

Are you talking about xchat???

---

### Post by SuperCzar on 2005-10-16
[QUOTE=taurus]Personally, I use gftp and if you want to upload/download a whole directory, you just hightlight it and click the arrow in the middle of the two windows.  That's it.  [/QUOTE]

Yeah i know how to use GFTP, but i was looking to see if there was anything out there that is text based. ncurses, something like that.

[QUOTE=taurus]Are you talking about xchat???[/QUOTE]

Unless XCHAT got AIM support....  I need an AIM client. 

Has anyone here ever used a jabber server to crossover into an AIM network? Are there public ones out there that can do this?

---

### Post by Hikaru79 on 2005-10-16
You could simply use 'ftp' if you want text-based :) It's installed by default.```
man ftp
```

---

### Post by yage on 2005-10-16
I recommend ncftp```
sudo apt-get install ncftp
```
For AIM support you can use gaim ```
sudo apt-get install gaim
```

---

### Post by lithorus on 2005-10-16
Someone really needs to make a GOOD gui ftp client for linux/X. Sure there's gftp, but it crashes if you just look at it. Iglooftp is an alternative, but is commercial and quickly gets outdated.

---

### Post by dspp on 2005-10-16
[QUOTE=lithorus]Someone really needs to make a GOOD gui ftp client for linux/X. Sure there's gftp, but it crashes if you just look at it. Iglooftp is an alternative, but is commercial and quickly gets outdated.[/QUOTE]

I have used gftp for quite a while and have never had a crash. Normally I ftp only small image files (under 1MB) or web pages. Just curious, does the app crash when sending large files?

---

### Post by m0biu5 on 2005-10-16
Here here. We really do need a good one...

---

### Post by taavi on 2005-10-16
[QUOTE=Hikaru79]You could simply use 'ftp' if you want text-based :) It's installed by default.```
man ftp
```[/QUOTE]And if you like more advance text based clients take a look onto **lftp** or **ncftp**, what was mentioned before.

---

### Post by taurus on 2005-10-16
[QUOTE=lithorus]Someone really needs to make a GOOD gui ftp client for linux/X. Sure there's gftp, but it crashes if you just look at it. Iglooftp is an alternative, but is commercial and quickly gets outdated.[/QUOTE]
I have no idea how you look at it but it never crashes on me even if I download/upload large files--iso images...

---

### Post by anacron on 2005-10-16
I have no clues with that ftp-client, but if you want really REALLY light way to chat with everyone, then how 'bout doing that just normally with irc? 

There's a thing called [bitlbee]("http://www.bitlbee.org") which allows using msn, aim, icq, yabber and maybe others from your _any_ irc-client, there are two way how to use it 
```
a) make your own server 
b) connect one of the public servers (which are like normal irc-servers) 
```

Im using im.bitlbee.org right now, only problem is, that there are huge ammount of people etc, so it disconnects sometimes and I have to reconnect, also it won't work with any filetransfers. But still bitlbee is one for me.;)

---

### Post by BIGtrouble77 on 2005-10-16
gfpt crashes like mad if you try and transfer a directory stucture with files.  I can't transfer my emulator files from my xbox because of this.

---

### Post by Lord Illidan on 2005-10-16
Actually, gftp doesn't work that good for large files or directory structures....I speak from dire experience..

---

### Post by irusun on 2005-10-16
gFTP is very erratic... I've had periods of good luck with it and periods where it crashes at whim...

Any suggestions for gtk/gnome (or others) ftp alternatives?

---

### Post by sizzam on 2005-10-17
[QUOTE=lithorus]Someone really needs to make a GOOD gui ftp client for linux/X. Sure there's gftp, but it crashes if you just look at it. Iglooftp is an alternative, but is commercial and quickly gets outdated.[/QUOTE]

I have a feeling this problem is going to be resolved soon.

In my opinion, Filezilla is absolutely the best freeware FTP client on Windows.   I've read articles that say they are working on a Linux version, and I see that they are still posting [nightly builds]("http://www.filezilla-project.org/nightly.php") for it, however I don't know how stable it is and I haven't heard much about it recently.

---

### Post by bryan986 on 2005-10-19
[QUOTE=Lord Illidan]Actually, gftp doesn't work that good for large files or directory structures....I speak from dire experience..[/QUOTE]

Yea I know the feeling, I had to switch clients because everytime I tried to delete/transfer 500+ folders/files it would crash

---

### Post by bertilow on 2005-10-20
I just use Konqueror. It works just perfectly for me. (It used to have weird problems with passive mode, but that bug seems to be long gone.)

---

### Post by ember on 2005-10-20
[QUOTE=sizzam]I have a feeling this problem is going to be resolved soon.

In my opinion, Filezilla is absolutely the best freeware FTP client on Windows.   I've read articles that say they are working on a Linux version, and I see that they are still posting [nightly builds]("http://www.filezilla-project.org/nightly.php") for it, however I don't know how stable it is and I haven't heard much about it recently.[/QUOTE]

Yes, it looks like they are. The only thing is - it looks very ugly at the moment ;)

---

### Post by vampire_janus on 2005-12-08
did anybody notice that there is already a cool graphical client installed by default for ubuntu?

see places -> connect to server :D

---

### Post by DrBair on 2005-12-08
For gui stuff, maybe give nautilus a try as mentioned.  

Theres also a lot of other stuff out there thats not prepackaged, but available.  Filerunner doesn't seem too terrible and a lot of people say good things about it. Very X-looking though.  

For console stuff theres always everyones favorite, GNU Midnight Commander!

---

### Post by DrBair on 2005-12-08
For gui stuff, maybe give nautilus a try as mentioned.  

Theres also a lot of other stuff out there thats not prepackaged, but available.  Filerunner doesn't seem too terrible and a lot of people say good things about it. Very X-looking though.  

For console stuff theres always everyones favorite, GNU Midnight Commander!

---

### Post by SuperCzar on 2005-12-08
[QUOTE=vampire_janus]did anybody notice that there is already a cool graphical client installed by default for ubuntu?

see places -> connect to server :( [/QUOTE]

I think you missed the part where i said that I was running enlightenment, so nautilus was out of the question.....:???: 

Since this post, I've learned to adapt and just use text clients.

---

### Post by hav0x on 2005-12-08
nautilus FTP thingie is borked. It messes up everytime here.
Go Go gFTP ;)

---

### Post by jasidog on 2005-12-11
For GUI  client you could try Firefox and [fireFTP](https://addons.mozilla.org/extensions/moreinfo.php?id=684&application=firefox). 

I tried it on windows a good while back and it seemed pretty good, should work just as well in Linux I'd think.

---

### Post by M3ta7h3ad on 2005-12-11
No idea on what could solve your needs, however I want something like SmartFTP or FlashFXP for linux... both of those clients kicked ass on windows. GFTP is a pain in the ballsack after a while.

---

### Post by Haegin on 2006-01-02
I use gFTP but I'm desperate for a replacement. I have tried fireFTP - you need firefox 1.5 for the latest version (easy enough to get) and its fine as far as I can tell - you just get timeout messages all the time in your browser window (popups) which annoyed me and I switched back to gftp. Maybe ncurses is the way...

---

### Post by Haegin on 2006-01-02
I use gFTP but I'm desperate for a replacement. I have tried fireFTP - you need firefox 1.5 for the latest version (easy enough to get) and its fine as far as I can tell - you just get timeout messages all the time in your browser window (popups) which annoyed me and I switched back to gftp. Maybe ncurses is the way...

---

### Post by pinoyskull on 2006-01-04
after using gftp for several week, i want to replace it ASAP, I need a better alternative

---

### Post by morrigan456 on 2006-07-25
Try Gproftpd and proftpd theyre ya best choice been using them commercially for 12 months. Bit of a pig to setup but fine when working. (Easy if your used to conf files) :KS 8)

---

### Post by leohart on 2006-07-27
I use gFTP quite a lot and I truly feel the pain of it. Not only does its interface responses slowly but it cannot look any worse. Pair gFTP with a compiz desktop and you feel like looking at a picture of sexy gal and an old guy.

Anyway, the previous paragraph has made me look like a 10-year-old. We simply just need something that is responsive and allows me to drag-and-drop for Christ sake.

---

### Post by ifokkema on 2006-07-28
> **SuperCzar said:**
> Since this post, I've learned to adapt and just use text clients.
Although it's a super-old thread, I believe sitecopy has all that you need. Text-based, it allows you to transfer the changes (new/changed/deleted files/dirs) per configured website through FTP, with just one command. Just:
```
sudo apt-get install sitecopy
```
It used to have a GTK client, but that's no longer maintained.

---

