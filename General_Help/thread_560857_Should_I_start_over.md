---
title: "Should I start over?"
date: 2007-09-26
forum: General Help
---

### Post by william_hunter on 2007-09-26
OK, I have been running Edgy for a while now (6 months) and I have learned a bit, but not as much as I would have liked to learn about how to do it right. I am not afraid of this, I just don't have the time I expected to devote to it. 

I am having crashing issues now, and usually it starts with a warning that "sleep" has unexpectedly quit. I host a game server on the machine as well as a web forum and I host files for my students (yes, I teach high school) to download, so I need this machine to be as stable as possible. I cannot afford to have it go down for a weekend when I am away, and as expected, thats when the worst crashes occur. 

I have been thinking I should wipe one of the two HDDs and reinstall the OS and start over, but I am not sure I am really up for that unless I get some moral support..thats why I am posting! What would be the best advice for someone obviously struggling with this?

---

### Post by Dark Hornet on 2007-09-26
--well, I am not sure that reinstalling everything is the answer....first try to figure out why you are having this issue....check logs, etc.  You wouldn't want to reinstall only to have the same issues...just a thought....good luck.

---

### Post by william_hunter on 2007-09-27
I can't figure out whats going on, but I got an error message last night about drive errors and broken dependencies. I didnt take screenshots because I wasn't thinking, but I now suspect the main HDD is dying. I saw somewhere on here about something very similar. Looks like I might not have a choice, eh?

---

### Post by kaptengu on 2007-09-27
My experience from when I was very new to Linux is that the problems started when I started to compile and install things from outside the repositories. I now realize you should know what you are doing before installing to avoid strange errors.

---

### Post by tszanon on 2007-09-27
If you don't have the time to figure out the problem, then I'd say reinstall. But I would install Dapper or Feisty, because both have longer support then Edgy.

---

### Post by notwen on 2007-09-27
Generally a re-install shouldn't hurt anything as long as you back up your needed data, possibly your /home folder should you need it.  That said, I would try to figure out your issue first, to see if a re-install is actually needed.  Run fsck to see if any of your file system may be going bad.

---

### Post by william_hunter on 2007-09-27
I tried to do an upgrade first, thinking it might fix my issues, and that failed. NOw I get the following error:

---

### Post by william_hunter on 2007-09-27
Something that just dawned on me...

MySQL databases. I have several and I need to keep the info in them. How hard is it to save that info and re-install it following an OS re-install?

Also, if I only use this machine for the web forum, hosting the game server, and the FTP server, should I go with the server edition?

Sorry I am acting like such a noob. I am much more Ubuntu illiterate than I ought to be, sadly. I am trying, I promise.

---

### Post by daveshields on 2007-09-27
If the machine has been stable for a long time and has only recently started behaving oddly, it is more likely due to a hardware problem than a software problem. If you have enough free space on the disk, say a few gigs, then you could create a new partition, do an Ubuntu install on just that partition. You could then test by booting up that fresh version before you go to sleep at night and let it run overnight to see if the machine still shows the same odd behavior.

I had a bizarre series of errors in a machine last July that I eventually traced to having a motherboard with an out-of-date BIOS version. Once I updated the BIOS the went away. But this for a machine I had just built. But this was for a machine I had just built, as I wrote about in one of my Ubuntu posts.

---

### Post by william_hunter on 2007-09-27
I have a second HDD in the machine with almost nothing on it. I was thinking about installing the OS there anyhow, as it is a much better HDD (faster and bigger) anyhow. Sounds like I will in fact be doing just that.

---

### Post by william_hunter on 2007-09-27
I wonder if it is due to the BIOS...I never thought of that. I had trouble updating it, and quit trying a while ago.

---

### Post by william_hunter on 2007-09-30
Put feisty server on my second HDD, and everything seems kosher now..I am betting its a failing HDD, which really peeves me as it is about 6 months old. Anyhow, I was really pleased with the ease of moving things around and making them work as they did before in Ubuntu. I can't imagine trying what I just did within Windows! The regediting alone would make me feel ill. 

Here's to Ubuntu!=D>

---

### Post by Sef on 2007-09-30
I would have gone into Synaptic > Edit > Fix Broken Packages.

---

### Post by megamania on 2007-09-30
> **william_hunter said:**
> Put feisty server on my second HDD, and everything seems kosher now..I am betting its a failing HDD, which really peeves me as it is about 6 months old. 
The last and only time I had freeze/crash problems with Ubuntu, I literally went crazy. I ended up thinking it was the hard disk and even considered changing it.

After a long while and as a last resort, I tried changing the SATA cable and... everything is fine now!

You may want to try it, as it's a 1-euro bet.

---

### Post by william_hunter on 2007-09-30
> **Sef said:**
> I would have gone into Synaptic > Edit > Fix Broken Packages.

Tried it. No joy

---

