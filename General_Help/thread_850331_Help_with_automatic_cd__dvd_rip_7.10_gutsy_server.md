---
title: "Help with automatic cd / dvd rip 7.10 gutsy server"
date: 2008-07-05
forum: General Help
---

### Post by captlogic on 2008-07-05
Hello all.

I'm trying to setup an unattended server that I can use to rip my cd collection automatically when I insert a cd.  I also want to be able to do this for my dvds.

I'm using 'abcde' to rip the cds and 'dvdbackup' for the dvds.

Everything works except I don't know how to automate the process based on simply inserting the discs.  I've searched around but have not found the last piece.

I am using Ubuntu 7.10 server.

Any suggestions?

---

### Post by scragar on 2008-07-05
System>preferences>Removable Drives and Media
jus check the boxes related to auto playing CSDs and DVDs for the custom command option :P

---

### Post by captlogic on 2008-07-05
I'm using the command line via ssh, no gui.  Is there a config file somewhere that links to those options?

Captlogic

---

### Post by scragar on 2008-07-05
if there is I can't find it, I am searching though, don't know where it will be...


they removed the option in hardy as well, I was going to try and see if I could find the change based on the last modified date and a bit of searching, but that doesn't look likly :(

---

### Post by captlogic on 2008-07-05
I've found a post of someone who seems to be working on a similar idea, the key might be the autorun program he mentions.

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t17100.html]("http://www.hydrogenaudio.org/forums/lofiversion/index.php/t17100.html")

I'm also looking for a how-to I saw at some point in the past for a automated ripping box using command line based solutions.  I seem to recall that the scripts looked for a hardware-event-hook to startup, but being new to linux I didn't really understand the finer details.

---

### Post by notpace on 2008-10-01
Did you have any luck? I'd be interested in doing the same, as I currently have abcde set up just the way I like it :)

---

### Post by sudocode on 2009-06-26
You can use ivman to trigger an action when a CD is inserted. I have abcde and ivman setup to automate audio CD ripping on a headless unattended server. I wrote a post about it [here]("http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html").

---

### Post by nothingspecial on 2009-06-26
> **sudocode said:**
> You can use ivman to trigger an action when a CD is inserted. I have abcde and ivman setup to automate audio CD ripping on a headless unattended server. I wrote a post about it [here]("http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html").

That is absolute genius sir!

---

### Post by mgrosner on 2009-07-09
> **sudocode said:**
> You can use ivman to trigger an action when a CD is inserted. I have abcde and ivman setup to automate audio CD ripping on a headless unattended server. I wrote a post about it [here]("http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html").

I'm very much a newb here, but does that method work with DVDs?  Anyone got a decent method of pulling off auto DVD ripping?

---

### Post by spencerhughes on 2009-12-02
Try Autobrake ([http://autobrake.info/](http://autobrake.info/)). It is a little tricky to install, but it works well.

---

### Post by notpace on 2009-12-02
oooo - I'll have to try that for DVDs.  It looks like all that would require is a few more ivman commands to determine the amount of data on the disk :)

---

