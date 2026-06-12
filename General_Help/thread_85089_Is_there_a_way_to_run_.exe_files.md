---
title: "Is there a way to run .exe files?"
date: 2005-11-01
forum: General Help
---

### Post by Cidere on 2005-11-01
Is there a way to run windows .exe files on a linux? I have no internet connection on the comp. If there is a way, that would be awesome.

---

### Post by Dracontopes on 2005-11-01
I think your only option is to run Wine/Cedega. Maybe you can grab a .deb from another computer that is connected to the internet and install it on your own.

---

### Post by matthewv on 2005-11-01
There is a way, using a program called WINE to provide a layer between the programs and your os. At the moment this software is in beta, and will not run all .exe's, however, its worth a try. If you don't have an internet connection, you'll probably have to get someone to download it for you.

---

### Post by pauljwells on 2005-11-01
There is an application called Wine that will let you run some windows exe files on linux. I've never tried it but if you search for it you'll find plenty of info in these forums or on the sourceforge site [http://sourceforge.net/projects/wine/](http://sourceforge.net/projects/wine/) . I think it has just made beta so it's reasonably stable now. Without an internet connection it will be dificult to do anything though :( Good Luck

---

### Post by Cidere on 2005-11-01
I just don't have an internet connection on my Linux that doesn't have Wine. Anyways, I'll give wine or cadega a try. I'll tell you how it turns out.

---

### Post by teevee on 2005-11-01
Cedega is for games. If you want to run stuff like Dreamweaver or MS Office, Crossover Office is your friend.

Both Cedega and Crossover are based on Wine but offer additional features (like an improved DirectX implementation in Cedega's case). Wine won't run as much applications as these two but is free.

---

### Post by Kyral on 2005-11-01
Cedega is worth 5 bucks a month. CounterStrike and CS: Source on Linux at native speeds? Hell YAH!

---

### Post by Cidere on 2005-11-01
wil someone point me towards a link of the .deb file for Wine?

---

### Post by felix_stegerman on 2005-11-01
[QUOTE=Cidere]wil someone point me towards a link of the .deb file for Wine?[/QUOTE]

[http://packages.ubuntu.com/breezy/otherosfs/wine](http://packages.ubuntu.com/breezy/otherosfs/wine)


Felix

---

### Post by Cidere on 2005-11-01
Thanks. I'll try this now.

---

### Post by Cidere on 2005-11-01
Hmm, what do i open the wineinstall with? It says the filetype is unkown.

---

### Post by felix_stegerman on 2005-11-01
[QUOTE=Cidere]Hmm, what do i open the wineinstall with? It says the filetype is unkown.[/QUOTE]

What does? Do you know how to install .deb packages ?
If not, (in a terminal) use:
# sudo dpkg -i <debfile>

e.g.
# sudo dpkg -i wine_0.0.20050725-0ubuntu1_i386.deb


Felix

---

### Post by Cidere on 2005-11-01
There is an error when I try to install the deb. Maybe it's not the right one. Which one do I download on that page you gave me?

---

### Post by SickTwist on 2005-11-01
What are you trying to accomplish? What is the program you want to run? We might be able to suggest an alternative.

---

### Post by Cidere on 2005-11-01
I'm trying to run a netgear .exe file to make my internet connection work.

---

### Post by SickTwist on 2005-11-01
What does the program do? What kind of Internet connection do you have?

---

### Post by Cidere on 2005-11-01
I have a wireless internet connection. The USB adapter that I'm trying to install is compatible with windows. I'm pretty sure if I get Winw, it'll work.

---

### Post by BLTicklemonster on 2005-11-01
Get wine from your synaptic package manager. once it's installed, you can go to the terminal, and type winefile and navigate wine from there. 

Seems like there should be a How to: do stuff drunk on wine topic somewhere...

---

### Post by dtfinch on 2005-11-01
On its own, Wine will almost certainly (well, certainly) be inadequate for using Windows drivers. Maybe it'll get as far as extracting the driver to your windows/system folder. After that, there is a program (which I've never tried) called NdisWrapper [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) which is supposed to be able to run some Windows network drivers on Linux.

---

### Post by Lambert on 2005-11-01
if you're looking to get wireless working wine is not what you're looking for.

Look here[http://ubuntuforums.org/showthread.php?t=51993]("http://ubuntuforums.org/showthread.php?t=51993") You may have one of these adapters

besides that you will want to search the forums or google for ndiswrapper and/or the usb adapter you're trying to get to work.

---

### Post by SickTwist on 2005-11-02
[QUOTE=Cidere]I have a wireless internet connection. The USB adapter that I'm trying to install is compatible with windows. I'm pretty sure if I get Winw, it'll work.[/QUOTE]

Like the others said, Wine is not appropriate for this situation. Wine is for running desktop apps/games--not installing drivers.

Try this: Search for the make and model of your wireless USB adapter in the forums. Perhaps somebody has already asked a question about it.

If not, try posting a new thread under the [hardware]("http://www.ubuntuforums.org/forumdisplay.php?f=98") section. That is the correct place to ask about this particular problem. Be as specific about the adapter as you can. (Manufacturer, model, revision, firmware, anything else printed on the adapter or its box).

---

### Post by srawat on 2008-05-22
[FONT="Verdana"]hi
I have just installed ubuntu 8.04 and I am using linux for the first time. 
I am having problems in accessing .exe files. From other threads I came to know that I need to install _wine_ for this. But all the links I got were for installing it directly on ubuntu via internet. My problem is, that my net requires a setup file to run and only then I can access net through that installed file by logging in there. And I can't run .exe files on ubuntu. How can i install wine without net?
please help 
      [/FONT]

---

### Post by KillaW0lf04 on 2008-05-22
you can get a debian file off the computer your using now, transfer it over to your ubuntu computer using a USB pen drive and then installing it.

---

### Post by jolx on 2008-05-22
> **srawat said:**
> [FONT="Verdana"]hi
I have just installed ubuntu 8.04 and I am using linux for the first time. 
I am having problems in accessing .exe files. From other threads I came to know that I need to install _wine_ for this. But all the links I got were for installing it directly on ubuntu via internet. My problem is, that my net requires a setup file to run and only then I can access net through that installed file by logging in there. And I can't run .exe files on ubuntu. How can i install wine without net?
please help 
      [/FONT]

go [here]("http://wine.budgetdedicated.com/archive/index.html") and download the appropriate version

then use a usb drive or something to transfer it to ur ubuntu machine

---

