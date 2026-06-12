---
title: "Epson stylus wireless printer and a netbook = no hair"
date: 2013-01-07
forum: General Help
---

### Post by Athena's Owl on 2013-01-07
I've been fighting with this for a couple of days now.

I have an Epson Stylus NX-330 that worked perfectly well with my windows machine.

the windows machine is a brick right now.

I bought an acer netbook a couple of months ago, tore windows 8 off it and installed 12.10 as the only operating system. My intent was simply to have a light, portable machine that I could take with me and write on. it's heavier than a transformer tablet but it was also half the price. I've added LXDE because ... well, it's poky. It's slow. I don't think my netbook can handle 12.10. If I could drop back to say 10 point something I think it would perform nicely. But I'm willing to put up with slow right now because my windows machine is a BRICK and I can't print anything, and I need to be able to print things for my work.

I've searched around looking for solutions. I run into a few barriers with this. They explain things at a level higher than my understanding, so the help isn't helping me because I don't have a firm grasp on the language.

so. Epson Stylus NX-330 Small in one? no usb connection. it is wireless only.

also. Acer A-100 netbook? no DVD or CD capability whatsoever. I used a cd to load the drivers on my windows machine; I cannot use that solution with my netbook.

I've seen this already. [epson's page for printer drivers](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

I've gone to that page. I dont understand anything there. there's no explanation for anything. there are links for a ESC/P Driver (full feature), a ESC/P-R Driver (generic driver), a core package&data package, and a network plugin package. the first two are printer drivers; the second two are scanner drivers.

let's use just the ESC/P-R Driver (generic driver) as an example for now. I click the link that says "download" and it takes me here:

[an incredibly long lists of all the printers these drivers support. I have no faith that this is true.](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19825&DSCCHK=5c7b4ff541de9a525dc84fb439258ab38e7fefd2)

because I am a lazy person I just searched for NX330, and sure enough, it's in that huge list. I accept the agreement.

I then see 


File name	                                      File size	 
epson-inkjet-printer-escpr-1.2.2-1lsb3.2.i486.rpm	1.43 MB	
epson-inkjet-printer-escpr_1.2.2-1lsb3.2_i386.deb	1.73 MB	
epson-inkjet-printer-escpr-1.2.2-1lsb3.2.x86_64.rpm	1.43 MB	
epson-inkjet-printer-escpr_1.2.2-1lsb3.2_amd64.deb	1.73 MB	
epson-inkjet-printer-escpr-1.2.2-1lsb3.2.src.rpm	1.38 MB	
epson-inkjet-printer-escpr-1.2.2-1lsb3.2.tar.gz	        1.45 MB

and I suppose i'm to download all of those, so I do.

THEN WHAT? they don't do anything! I click them, they do nothing. obviously i'm missing something that it's already assumed that I know, but I DON'T. and there's no easy way to find it out. I've been trying. 

I've had an account here for years. I'm only on 25 posts. I hven't been using linux solidly in all that time, because every time i run into a problem like this I stop using linux and stick to what I know how to deal with. Windows may be frustrating but I've been using IBM machines since before windows was even a thing, so when something goes wrong I can often figure out how to even start looking for a solution just because my computer experience is saturated through years of exposure. but linux is just not that easy to learn, and so I've never spent a lot of time with it.

It's because I don't even have the most basic understanding, and while I know that I don't know, i don't know how to start knowing. I know that this is totally basic, and I'm stupid for not knowing it, but I don't know it, and I haven't been able to find a way to learn it.

---

### Post by Athena's Owl on 2013-01-08
All right. I have managed to install the .deb packages; that wound up being a simple matter of clicking on them twice *quickly* which is difficult on a netbook.

the .rpm files? still no luck figuring out how to open those. I checked to see if simply installing the .deb files would solve my problem but my printer is still not detected.

so I'm guessing I have to figure out how to install the .rpm files? I'm trying to look that up but I still haven't found a site that explains how without assuming a knowledge of linux language, which I still don't have.

ETA: I found [this page]("http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/") which got me to install Alien and dpkg and dephelper, so I managed that

but the next step was to use alien to open a specific package name, which I painstakingly copied from the filename. but command line came back saying that the package didn't exist. what? am I doing wrong? is it like DOS where you have to "be" in the correct directory in order for alien to find the package? I assumed that wasn't so because I've merrily obeyed command line instructions just straight from opening a terminal, so I don't know what went wrong here.

ETA2: I just typed "Alien" in a terminal and it wants the switch -d and the command also has to be at root, so I tried

sudo alien -d epson-inkjet-printer-201105w-1.0.0-1lsb3.2.i486.rpm

and it still tells me File Not Found, even though I'm staring right at the file, and I copied the file name and pasted the exact file name into the command, so I still don't know what I could possibly be doing wrong. Seriously need help here.

---

### Post by xc3RnbFO8P on 2013-01-08
Ubuntu 12.10, did you install 64 bit or 32 bit?

---

### Post by Athena's Owl on 2013-01-08
OMG THANK YOU FOR REPLYING TO ME

i installed 64-bit.

---

### Post by xc3RnbFO8P on 2013-01-08
This is the package that you should install
> epson-inkjet-printer-escpr_1.2.2-1lsb3.2_amd64.deb	1.73 MB

---

### Post by xc3RnbFO8P on 2013-01-08
and you should remove this package
**epson-inkjet-printer-escpr_1.2.2-1lsb3.2_i386.deb**

> sudo dpkg -r epson-inkjet-printer-escpr_1.2.2-1lsb3.2_i386.deb

---

### Post by Athena's Owl on 2013-01-08
\tried that, and got 

dpkg: error: you must specify packages by their own names, not by quoting the names of the files they come in

for my trouble

and I can't seem to get the software center to load the package so i can uninstall it from there no matter how I try and i've rebooted twice

is that the reason why the computer can't see my printer?

---

### Post by Calinou on 2013-01-08
"that wound up being a simple matter of clicking on them twice *quickly* which is difficult on a netbook."

Select it then press Enter...

Anyway, you should only install the Ubuntu package, not the Fedora/Red Hat/Debian packges.

Also, Xubuntu 12.10 runs pretty well on a slow netbook (Atom N455, 1GB RAM), so you're doing it wrong.

---

### Post by xc3RnbFO8P on 2013-01-08
Is your printer connected via usb cable?

---

### Post by Athena's Owl on 2013-01-08
> **Ringi said:**
> Is your printer connected via usb cable?

No, and what's more, it's not possible to do so. the printer doesn't have so much as a port to connect such a cable; it's wireless only.

i'm not having any luck attempting to remove the x86 packages. when I was trying to get all those packages installed, the software center would pop up to tell me that a given package was already installed, and gave an option to remove it, but now that I want that back it won't even completely load. I've left it alone for seven minutes, and surely it couldn't take that long to do? but 12.10 is very slow and congested in general, which is why I usually do things in LXDE - it's a lot faster.

---

### Post by xc3RnbFO8P on 2013-01-08
Here is a how to connect wireless printer 
[http://ubuntuforums.org/showpost.php?p=11667856&postcount=12]("http://ubuntuforums.org/showpost.php?p=11667856&postcount=12")
> You do NOT need windows to use Wi-Fi, but you do need a wireless router/access point which supports WPS (and a wired/wireless connection from your PC to the router). I think that's part of the problem for some people here.

I had the printer setup and working (scanning/printing) over the wireless network in 15 minutes.

I'll describe the steps from beginning to end, these should apply to other Epson models such as the SX230:

1. First you need to setup the printer, install the cartridges and wait until the power light stops flashing.

2. Go to [http://download.ebz.epson.net/dsc/se...search/?OSC=LX](http://download.ebz.epson.net/dsc/se...search/?OSC=LX)
and type "Stylus SX235" exactly as written into the search box. Don't include the 'w' at the end!

3. Downloading and install ALL four packages shown in the list

4. Cups should be restarted automatically, but if not do so manually

5. Press the WPS button on your wireless router and then within 30 seconds press and hold the WiFi button on the printer until the wifi light on the printer starts flashing. The light should turn steady green if it's connected, your router should confirm that this has been successful.

5. Go to [https://127.0.0.1:631](https://127.0.0.1:631) in the browser, Select Administration, Find Printer. (Disconnect usb first if you've previously connected it)

6. Click on the printer name, select Epson as the make and then Epson Stylus SX235 from the list of models. Click through the remaining dialogues and the printer will be added.

7. Print a test page just to make sure

Scanner

8. Assuming you know about Sane/iscan, the only step required here is to edit as root (sudo) /etc/sane.d/epkowa.conf - add the line "net {IP of printer}" (Cups will mention the IP during setup, otherwise check your router for the assigned address.

---

### Post by Athena's Owl on 2013-01-08
yes, I found that message. it is the very first message that appears when you google "install epson stylus wireless printer linux," in fact. It's where I began this hair-tearing adventure.


This message is why I got hung up on "Download and install ALL packages on the list." I took that instruction absolutely literally, resulting in me trying to figure out how to install .rpm files as well as the .deb ones, and installing 32-bit drivers when I have a 64-bit system and have installed 12.10 as 64 bit. (I still haven't managed to remove the 32-bit packages, same problem as I reported before, several reboots now.)

what I don't know how to do:

> 4. Cups should be restarted automatically, but if not do so manually

but I'm going to assume that cups got restarted when my computer was restarted - if this is not true, then I'll need to find out how to restart cups manually.

> 5. Go to [https://127.0.0.1:631](https://127.0.0.1:631) in the browser, Select Administration, Find Printer. (Disconnect usb first if you've previously connected it)

when I attempt to do this step, there are no printers found. And I can't add one, because when I try it asks for a login, and I don't have that information. It could be a very simple combination that everyone except me knows, but I assure you that I don't know it, heh!

---

### Post by Athena's Owl on 2013-01-10
I still don't have a working printer. every help instruction i've tried hasn't worked. The netbook just won't see that there is a printer on my network and now I'm days overdue on my document. I've installed the drivers and uninstalled them and reinstalled them but nothing works. I would just add the printer if I knew what "Host" meant but I can't find an article that will tell me what my add printer program is asking for here. is it the address of the printer? if it is, how do I find out what that is?

---

