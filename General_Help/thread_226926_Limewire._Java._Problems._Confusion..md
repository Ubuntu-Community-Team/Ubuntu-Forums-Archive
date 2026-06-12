---
title: "Limewire. Java. Problems. Confusion."
date: 2006-07-31
forum: General Help
---

### Post by Roasted on 2006-07-31
I did a search and people kept telling this dude to install the JAVA plugins. When he got confused they said use Automatix to install it. Well, that's what I did. But what do I do? Maybe I'm not completely sure of how to install limewire.

If I want to install limewire from the terminal, what do I type?

If I want to install limewire in another way, how do I do it? 

I did manage to get frostwire to work, though. Downloading now. But it bugs me that limewire isn't working... so I'd like to get it to work mostly for my satisfaction that I conquered it. :)

---

### Post by DJ Scribblinni on 2006-07-31
Hopefully you downloaded the "Other (OS/2, Solaris, Linux)" from Limewire.  Extract the contents. From the command line, go to that folder, and do ```
sh runLime.sh
```

That makes it work for me...

---

### Post by Ziox on 2006-07-31
Limewire is not in the repositories, meaning that you can't install limewire from terminal.

why don't you try gtk-gnutella, it's clean, fast, and simple (gui)

sudo aptitude install gtk-gnutella

but if you really want to have limewire, then download a rpm file (google it, or search in the forums) and then use alien to convert it (in the forum, i'll provide a link)

---

### Post by Roasted on 2006-07-31
What? It sounds like limewire isn't even fully compatible with linux, and you have to do all of this extra work to make it work. Why?

btw - was frostbite developed by anybody affiliated with the linux team?

---

### Post by Ziox on 2006-07-31
frostbite? do you mean frostwire? anyhoo...they are built by a group of people who does not want to see Limewire gone (from legal battles and such) Since Limewire is open source, they were able to use that source to make frostwire.

"It sounds like limewire isn't even fully compatible with linux"

if Linux = only Ubuntu, then yes. But since Fedora is Linux, then no.

the RPM file is especially for Fedora, but you can use alien to convert it (like i said b4) People don't seem to be having trouble with it, so...

---

### Post by Ziox on 2006-07-31
google "fedora limewire rpm" 
then follow this short guide to install limewire (if you are this desperate)

[http://www.ubuntuforums.org/showpost.php?p=1301787&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1301787&postcount=9)

---

### Post by Roasted on 2006-08-01
Bam. Installed. Thanks.

It wasn't so much I wanted limewire. I just wanted to figure it out and get it installed so I... well, felt better about being me!!

Being a new linux user I just hate it when I feel like linux gets the best of me, so I do what I can to learn what I can and conquer these installation issues that arise.

Quick, but probably a dumb question. Limewire is installed. When I search for it in my home folder and come across the folder, I'm trying to find the file to double click to open it (assuming I didn't want to use the Alt F2 route to open it). Which file is it? :confused:

---

### Post by Ziox on 2006-08-01
uhh...not sure, but there isn't any .exe or .msi after it...so that's hard to notice...uh try typing limewire in the terminal

---

### Post by Roasted on 2006-08-01
Limewire just opens up.

I'm just curious to know WHAT file actually opens Limewire, that's all. And how the hell would the terminal know which file to pick to open if all I do is type LIMEWIRE in the terminal?

---

### Post by Roasted on 2006-08-01
By the way, when I open limewire with the terminal, once I close the terminal limewire shuts off. Why?

---

### Post by Ziox on 2006-08-01
well...if i can answer your questions with lots of details, then I won't have just 260 some beans, but i know the basics...there is one folder where dpkg (the package management utility) keep a list of all the app's "start" icons, so whenever you use either GUI or terminal to open any app, dpkg will search that folder alone, and look for the necessary name, if it finds it then i'll launch that file (most likely a shortcut file), if not, then i'll return an error.

as for why terminal and limewire shuts off together.  I think by using terminal to open limewire, you've linked them together, causeing terminal to spit out/back any errors or comments that limewire will output.  When you close terminal, you are sending a "kill" signal to limewire, causing it to close.  Some apps i know will break themselves away from terminal after they've been started, but lots of them are bind to terminal when opened by terminal.

Some times when you use GUI to open a file, it also opens a "termina", but i think's invisible that's all.  But i can be wrong with that...

Hope this helps

---

### Post by Roasted on 2006-08-01
Thanks Boss. :cool:

---

### Post by adamkane on 2006-08-01
This be what you need:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_P2P_Gnutella_Client_.28FrostWire.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_P2P_Gnutella_Client_.28FrostWire.29)

---

