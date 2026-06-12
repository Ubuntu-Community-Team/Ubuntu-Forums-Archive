---
title: "The Sacrilegious IE Question"
date: 2007-12-31
forum: General Help
---

### Post by teejay17 on 2007-12-31
I know this is sacrilegious, but in order to do banking online, I need Internet Explorer. I really hate that this is the only reason I have to boot into Windows, so what is the easiest, simplest way to get Internet Explorer on my machine?

---

### Post by AlanR8 on 2007-12-31
Run it under Wine....

OR, I believe there's a Firefox addon called IE Tabs or Explorer tabs that emulates IE inside Firefox.

Have a look

---

### Post by meindian523 on 2007-12-31
Your answer is [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu")

As noted on the page itself,you have to replace edgy with whatever version you are running.

feisty for 7.04 and gutsy for 7.10

---

### Post by teejay17 on 2007-12-31
> **AlanR8 said:**
> Run it under Wine....

OR, I believe there's a Firefox addon called IE Tabs or Explorer tabs that emulates IE inside Firefox.

Have a look
I've tried the extension, but it only works in Windows, sadly.

---

### Post by teejay17 on 2007-12-31
> **meindian523 said:**
> Your answer is [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu")

As noted on the page itself,you have to replace edgy with whatever version you are running.

feisty for 7.04 and gutsy for 7.10
Do I need to install Wine for this?

---

### Post by meindian523 on 2007-12-31
yes,you need wine for that.

---

### Post by teejay17 on 2007-12-31
> **meindian523 said:**
> yes,you need wine for that.
Is the version of Wine available in Synaptic fine then?

---

### Post by perlluver on 2007-12-31
Yes that version is fine, or you can follow the instructions on the IEs4Linux website.

---

### Post by dutchman72 on 2007-12-31
The extension for Firefox only opens that link or bookmark in a version of IE already installed on the system, you'd still need IE for that to work. 

I have gotten ies4linux to work great for me for ubuntu 6.04, 6.10, and 7.04. Like the previous poster, just clarify your version name when selecting the download.

---

### Post by EXCiD3 on 2007-12-31
You can always download and install the newest Wine release from here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by jeffus_il on 2007-12-31
Did you try the User Agent Switcher in firefox, it sometimes helps.

---

### Post by meindian523 on 2007-12-31
Is that available in FF on Ubuntu?I searched the entire preferences and couldn't find it.

---

### Post by mdebusk on 2007-12-31
> **teejay17 said:**
> I know this is sacrilegious, but in order to do banking online, I need Internet Explorer.

I think it would make more sense to switch to a smarter bank.

---

### Post by jeffus_il on 2007-12-31
No, It's a firefox plugin,
type "firefox user agent switcher" in google and it takes you straight there.

---

### Post by meindian523 on 2007-12-31
> **mdebusk said:**
> I think it would make more sense to switch to a smarter bank.

Actually,I should say +1.

---

### Post by teejay17 on 2007-12-31
> **mdebusk said:**
> I think it would make more sense to switch to a smarter bank.
Easier said than done, I'm afraid.

---

### Post by meindian523 on 2007-12-31
That's our opinion,but it's your PC and your choice.Just tell us whether you are going for User Agent Switcher or IEs4Linux

---

### Post by teejay17 on 2007-12-31
> **meindian523 said:**
> That's our opinion,but it's your PC and your choice.Just tell us whether you are going for User Agent Switcher or IEs4Linux
I think I'm going to use IEs4Linux first, see how that goes.

---

### Post by meindian523 on 2007-12-31
w00t!

---

### Post by meindian523 on 2008-01-01
Did IEs4Linux solve your problem?

---

### Post by jamaisvu on 2008-01-01
> **teejay17 said:**
> I know this is sacrilegious, but in order to do banking online, I need Internet Explorer. I really hate that this is the only reason I have to boot into Windows, so what is the easiest, simplest way to get Internet Explorer on my machine?

[FONT=Franklin Gothic Medium]I'd first check, before you start installing things, that you actually need IE and that pretending to be IE isn't good enough.

Open up the bank's website in Konqueror, then go to the Tools menu, select Change Browser Identification, Internet Explorer, Version 6.0 on Windows XP. Then try logging on to your bank account -- you will get past any browser-detection scripts, and the website will probably render even more correctly than IE would manage it.
[/FONT]

---

### Post by teejay17 on 2008-01-01
> **jamaisvu said:**
> [FONT=Franklin Gothic Medium]I'd first check, before you start installing things, that you actually need IE and that pretending to be IE isn't good enough.

Open up the bank's website in Konqueror, then go to the Tools menu, select Change Browser Identification, Internet Explorer, Version 6.0 on Windows XP. Then try logging on to your bank account -- you will get past any browser-detection scripts, and the website will probably render even more correctly than IE would manage it.
[/FONT]
So it might be as easy as downloading Konqueror?
On that note, how does Konqueror run on Gnome?

---

### Post by meindian523 on 2008-01-01
Konqueror will involve getting the KDE-libraries too,which would result in a bloat,though it's no problem if you have more than 512 MB of RAM.

---

### Post by teejay17 on 2008-01-01
> **meindian523 said:**
> Konqueror will involve getting the KDE-libraries too,which would result in a bloat,though it's no problem if you have more than 512 MB of RAM.
I do. I guess I'll give it a shot, if it means I can do online banking.

---

### Post by jamaisvu on 2008-01-01
> **teejay17 said:**
> So it might be as easy as downloading Konqueror?
On that note, how does Konqueror run on Gnome?

[FONT=Franklin Gothic Medium]I've just gone and tested Konqueror in GNOME on my slightly aged test box with 512MB RAM. It's not quite as quick to start as in KDE (more like about how long a vanilla installation of Firefox takes to start), but it functions absolutely fine.

meindian523 is of course absolutely right about dependencies and marginal hardware.

[SIZE=1]PS -- If you do try Konqueror and have five minutes spare, have a look at your home directory in it (type [/SIZE][FONT=Courier New][SIZE=1]/home/[/SIZE][/FONT][SIZE=1]*yourusername*[/SIZE][FONT=Courier New][SIZE=1]/[/SIZE][/FONT][SIZE=1] into the address box) then have a play around with the various things in the View&#8594;View Mode submenu. Also admire the multiple split views (yes, you can have a file manager in one split and a webpage in another). It's a seriously cool app!
[/SIZE][/FONT]

---

### Post by meindian523 on 2008-01-02
That's because Konquerer is a shell,just like IE,the only difference is that IE being a shell is far more insecure because any .exe acquires executable rights in Win,unlike in Linux where you would have to give it execute permission before it can run,therefore even if you download a Trojan or virus by mistake,it won't run till YOU run it.

---

### Post by teejay17 on 2008-01-17
I have a problem. Internet Explorer is now installed, but the toolbars at the top, as well as the address bar, text boxes on web pages, etc. are all gray and the fonts are not appearing. 
How can I fix this?
I'd post a pic of what it looks like, but the forum won't let me link from my machine, only a web based service.

---

