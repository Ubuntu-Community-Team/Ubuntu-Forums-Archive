---
title: "Setting up Canon ip7250 network printer"
date: 2015-04-08
forum: General Help
---

### Post by jesus_automatic on 2015-04-08
I have been trying to set up a Canon ip7250 over wifion lubuntu 14.04.
I have installed driver cnijfiter v 3.9 from ppa:inameiname/stable.
I added the printer from the cups gui, it found it and all appeared well. But printing a test page just gets held and you can't release it for printing. Also there is no feedback from the printer (ink levels etc.)
The printer works over the network from win7. Everything looks like it should work, but I cant actually get the print job as far as the printer. 
I have found many other posts relating to print jobs being held, but there doesn't seem to a consistent problem causing it.

I have tried
the cnijfilter 3.8 from Canon
installing libtiff4 library package.

I have also just discovered that sending a test page to print with the printer turned off has exactly the same response.
Any help would be gratefully received.

---

### Post by pdc on 2015-04-08
Welcome to the Ubuntu forums

so setting up a printer seems to need 3 steps:

1) establish a connection 
2) install the drivers
3) register the printer on one's system

_______

seems like 1) is done ......... you can confirm it with ```
cnijnetprn --search auto
```

2) if we look to see what drivers are installed; if you can open a terminal............do this by holding down 3 keys: control and alt and t all together ......... and then paste in the commands below; and hit the ENTER key after each paste 

......... to paste into a terminal, it is set up to use 3 keys: control and shift and v (instead of the control and v many programmes use ............_

```
dpkg -l | grep cnijfilter
```

```
dpkg -l | grep libtiff4
```

If you can in turn; paste back here the results you get ..............

_____________

if I were doing the install of an ip7200, I would go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html) and download and SAVE what will be cnijfilter-ip7200series-3.80-1-deb.tar.gz

It needs libtiff4 and I would get that from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and one would go 14 or 17 down the list to get either the 64bit or 32bit variant; as needed

---

### Post by jesus_automatic on 2015-04-09
Thanks for the help.

1. 
```
cnijnetprn --search auto
```
doesn't return anything. I don't know exactly what you mean by 'establish a connection'. From where to where?

2.
```
dpkg -l | grep cnijfilter
ii  cnijfilter-common                          3.90-76~ubuntu14.04.1                 i386         IJ Printer Driver for Linux.
ii  cnijfilter-ip7200series                    3.90-76~ubuntu14.04.1                 i386         IJ Printer Driver for Linux.

```
and
```
dpkg -l | grep libtiff4
ii  libtiff4-dev:i386                          4.0.3-7ubuntu0.3                      i386         Tag Image File Format library (TIFF), transitional package
```

---

### Post by jesus_automatic on 2015-04-09
Okay. Sorry, I was being a bit thick. I did it again but this time with the printer turned on.
```
cnijnetprn --search auto
network cnijnet:/D8-49-2F-25-DF-02 "Canon iP7200 series" "Canon-iP7200-series_D8-49-2F-25-DF-02"


```

---

### Post by pdc on 2015-04-10
thanks; 

when you said it worked on windows, that to me meant you had already established the connection; for anyone coming after, here is a guide from Canon UK on connecting a new ip7250 to a router; [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/ip7250_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/ip7250_printer_wireless_connection_setup/)

so seems like you have a 32bit lubuntu system? as you have the 32bit drivers successfully installed; and libtiff4 as well 

.................should sort of work.........shouldn't it?? ........if you click on this link to open CUPS [http://localhost:631/printers/](http://localhost:631/printers/) in column 4 entitled Make & Model ....... it says something like > Canon ip7200 series Ver.3.90

_________________

if it does, folks sometimes report that if they delete an existing entry; if it is not working; and then create it anew ..........one can use the command ```
system-config-printer
``` to open the printer dialog box ......and hit the ADD button to re-register the ip7200 .......

---

### Post by jesus_automatic on 2015-04-10
Ah, that connection. Printer to router seems ok.
Yes 32bit.

"..should sort of work.."   .Funny, that was exactly my expert diagnosis ( as a carpenter) . I was hoping I had missed something really obvious. Like, I had forgotten to press the big red button marked ' MAKE MY PRINTER WORK' . Sorry - back to reality.

CUPS reports the printer as

Canon iP7200 series - CUPS+Gutenprint v5.2.10-pre2

Tried deleting and adding the printer back and still the same. Everything seems fine. but no print. Print queue shows job held.

Does that Gutenprint driver look right to you? I read somewhere that The driver from canon no longer works with 14.04. I tried it anyway and seems to be the same. Do you think it is a driver issue anyway? Its seems to be the default behaviour of CUPS to withold the print Job if it is not happy with the printer. 

Can it be something else with the printer. As I said it works fine with win7. But on my wife's win8.1 machine it is erratic. She has to turn the printer off and on a lot to connect to it. I assumed it was just because win8 is ****?

I don't know, what do you think? I'm going to work now. I understand wood. It doesn't mess with your head.

---

### Post by pdc on 2015-04-10
It is always a lot harder to work out what is going on; when one is not seated in front of someone else's computer

> Tried deleting and adding the printer back and still the same.  

.............. If I write here what my impressions are:

to set up a printer one needs to do
1) connection 
2) drivers
3) registration

....... so you have 1) and 2) done but for 3) you don't seem to have any entry for > Canon ip7200 series Ver.3.90  ........in CUPS [http://localhost:631/printers/](http://localhost:631/printers/)

............ I can't think of a good wood example at present!! 

Gutenprint is the open-source printer ....... open-source meaning one can read the code ....... and gutenprint aims to work for many, many printers; ....... the Canon ip7200 is ............. pretty self-explanatory .....but we want it to show up in CUPS so you at least have the choice ...

so we want to have both registered: and for you to know the name the Canon driver is registered as ....... so you can choose it when you wish ............ when you choose to print .................
__________

Let's try and do a manual registration: 2 ways: 

1) Can you go to the PRINTERS section of your system............. I am guessing in lubuntu that you start at some menu button; and then perhaps go into an Adminsitration folder and thence to PRINTERS; there should be an ADD button there ........

2) If not, can you open a terminal ............. hold down 3 keys: the control and alt and t keys ..... and type in the command ```
system-config-printer
``` ........and if it says............what are talking about ............never heard of this then can you issue the command 

```
sudo apt-get install system-config-printer
``` to install what we want; and when that is done, issue the command again............the short-cut way is to hit the UP arrow on your keyboard and that moves backwards in the memory of the terminal to show you all the previous commands; in order; that you have issued ..................

__________

that command should open a dialogue box with an ADD button; ..........follow it through there .......... it should search for what is available to it ....... if it adds the printer, check again on CUPS as to what it has added: 

_____________

if it has not created an entry for the Canon driver, we will get a fresh set of Canon files from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html) and get you to download what is cnijfilter-ip7200series-3.80-1-deb.tar.gz

---

### Post by jesus_automatic on 2015-04-10
If I try to add the printer. it searches, finds it and installs drivers. But in CUPS it shows it as the Gutenprint driver. If I download cnijfilter-ip7200series-3.80-1-deb.tar.gz from Canon, when I try to install it, it doesn't allow it  - 'there is a newer version already installed'. 
It doesn't give me an option to choose which driver to install when I add from the gui. Can I do that from the terminal with some cunning magic commands. Or perhaps just remove the gutenprint driver and see if it finds the canon one.

Also I still have the cnijfilter 3.9. Should I get rid of it and try the 3.8. I think I have tried it but now i'm not so sure

I appreciate all your help. I know how hard it is to visualize a potential problem in a machine you can't see. And without knowing what idiotic things the user might have done

---

### Post by jesus_automatic on 2015-04-10
Haha. Got it. 
Printer properties> make and model >change
that allows you to choose the driver. Installed the cnijffiler 3.9 driver and now I have my very own printer test page. I'm going to make a frame tonight and put it on the wall. I'm not going to attempt printing anything more complicated. Save that excitement for another day.

Thanks once again for all your help. I am always amazed and eternally gratefull that I can run my computer with free stuff, and on top of that people I've never met take the time to help me make it work.

---

### Post by pdc on 2015-04-10
well done; you have taught me something: I have never needed to investigate > Printer properties> make and model >change ...that allows you to choose the driver. Installed the cnijffiler 3.9 driver 

.....that's great; thanks for that; we all learn from each other!

Glad you have got the Canon 3.9 driver installed; and hopefully it can stay installed and will work well! That system-config-printer allows you to tweak settings as you wish

You will feel more able to tackle other issues as they emerge with the system .......... and hopefully you can get some suggestions and ideas on the forum; best wishes

---

### Post by jesus_automatic on 2015-04-11
Well, I've successfully printed a word document with tables graphs and pictures. So i'm very pleased with myself.

Thanks once again for you help. You have a really nice clear way of explaining things. So often I find, as a novice in these things, that I don't even understand the answers to my questions.

Next I have to get a .dwg cad viewer to work...... I might have to ask for help elsewhere, unless of course you are an expert in that as well.

---

### Post by pdc on 2015-04-11
pleased to hear all is good;

no, I don't know about dwg viewers but if you start on google with something like

> ubuntu solved .dwg cad viewer

....... you might have some hits ......... often there are specialist forums and those are the best places to ask ...... 

and when you google on > linux cad forums there seem to be some good hits there ........

_____________

I think this guy [http://forums.linuxmint.com/viewtopic.php?t=129719&f=190](http://forums.linuxmint.com/viewtopic.php?t=129719&f=190) in post #2 would give you the best advice: he seems to know his stuff

---

### Post by jesus_automatic on 2015-04-12
Wow, thanks. You really are too helpful.
I have been round all the sites I can find - have looked at Draftsight, but appears there is no 32bit version available. Installed Teigha Viewer successfully but the program wont run. There doesn't sem to be any support/ forum /discussion of Teigha Viewer anywhere. 

But anyway, don't want to waste any more of your time.
Thanks

---

### Post by pdc on 2015-04-12
I use two programmes to help install packages; and check what is installed; 

gdebi installer ............. installs...............and synaptic package manager ............. checks what is installed;

_________

> Installed Teigha Viewer successfully but the program wont run

out of curiosity I went here [http://www.opendesign.com/guestfiles/teigha_viewer](http://www.opendesign.com/guestfiles/teigha_viewer) and downloaded the QT5 variant; to match our system; when I clicked to download, gdebi installer offered to do the install; which it did; and from the menu, I found the icon for teigha viewer and it opened fine; and asked me which file I wished to open .................. gdebi installer checks for dependencies such as ........ if you choose the QT5 variant; that you have qt5 installed

---

