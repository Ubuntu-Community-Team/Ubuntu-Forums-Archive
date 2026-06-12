---
title: "Brother 2070N Problem"
date: 2008-01-01
forum: General Help
---

### Post by Aaronsgwc on 2008-01-01
I've got a minor problem with my Brother 2070N network printer. I installed it according to a tutorial on this forum and it seems to be working. The problem is that when it prints anything the margins are all screwed up. When I print a test page it says that the page size is 8.29in by 11.69in. That doesn't seem right. The bottom is also cut off.

Oddly enough it will only print through the KOffice suite, it won't print through Open Office at all. When I print through KWord it puts about a two inch margin on top of the page, and the bottom is right at the bottom of the paper. It doesn't really lose anything, but the margins are really screwed up and I do a lot of business through my laptop. I can't seem to find a fix that works for this. Any suggestions?

I'm using Kubuntu 7.10 (Gutsy), and my driver versions are:

Cups wrapper: 2.0.1-2
LDR: 1.1.2-3

I'm using a Dell Inspiron 1501

I got them from the Brother site, I did all the symbolic linking and everything.

Thanks,

Aaron

---

### Post by RelativelyQuantum on 2008-01-01
You probably already tried this, but can't you change the margin settings right from within your word processing program? If it's a consistent margin error, you could just adjust the print margin settings to compensate.

Just a thought.

---

### Post by Shazaam on 2008-01-01
If the cups daemon is running you might be able to configure the settings you need. Open a webbrowser and type this into the address box (without the quotes):

"http://localhost:631/"

---

### Post by dcstar on 2008-01-02
> **Aaronsgwc said:**
> I've got a minor problem with my Brother 2070N network printer. I installed it according to a tutorial on this forum and it seems to be working. The problem is that when it prints anything the margins are all screwed up. When I print a test page it says that the page size is 8.29in by 11.69in. That doesn't seem right. The bottom is also cut off.

Oddly enough it will only print through the KOffice suite, it won't print through Open Office at all. When I print through KWord it puts about a two inch margin on top of the page, and the bottom is right at the bottom of the paper. It doesn't really lose anything, but the margins are really screwed up and I do a lot of business through my laptop. I can't seem to find a fix that works for this. Any suggestions?
........

[http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N)

---

### Post by Aaronsgwc on 2008-01-03
That link above ([http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N)) did the trick. I kinda figured the settings were off in some other file I didn't know about. It was defaulting to A4 in the /usr/local/Brother/inf/brHL2070Nrc file, even though I had changed it to Letter everywhere else. All I had to do was change the paper type A4 to "Letter" and it works just fine now. 

The CUPS Daemon and everything else was also working fine beforehand. 

Thanks for the help!

-Aaron

---

### Post by Aaronsgwc on 2008-01-03
Problem Solved. Do I need to change the subject to SOLVED or something?

---

