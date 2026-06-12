---
title: "Vonage Softphone Support on Ubuntu"
date: 2005-09-03
forum: General Help
---

### Post by mcguigan_3d on 2005-09-03
Not a question, more a partial solution.

I signed up for a Vonage softphone line as a supplementary service to the hardware based residential line they provide me. On Windows, Vonage supplies a customized version of the Xten X-Pro softphone.

I use a Windows laptop for work but try to stick to Ubuntu outside office hours and so wanted to be able to use a softphone client on Unix. Vonage uses SIP so it needed to be a SIP based client.

I found information on the net suggesting the use of kphone.
This is available as a package via Synaptic and requires the installation of the Qt graphical toolkit because it is a KDE application.
This wasn't inserted automatically as an application in the menu system and I had to start it from the command line by opening a terminal window ( Applications -> System Tools -> Terminal ) and entering "kphone &".

I initially had issues with the client, complaining that it could not gain access to the sound card. I eventually learned that a program "esd" ( Enlightenment Sound Daemon ) was taking control of the sound card on startup. I found the process with "ps -ef | grep esd" and then killed the program with "kill -TERM <pid>".

I have attached screenshots for my setup.

When making your first call you will be prompted for authentication parameters which are your Vonage softphone number and a password issued for the softphone account by Vonage.

You will have to log into the Vonage web site using your global Vonage login credentials, then go to the "Features" page and scroll to the bottom for a link to the Manage Softphone Lines page.  Pick the softphone line to be managed and you will be taken to a page where your password is provided.

#--------------------------------

I was also able to get the beta Xten-lite softphone working.
This is downloadable in a compressed tarball.

I downloaded it into the tmp file, uncompressed and untarred the file ( tar -xzvf <filename> ) . I then copied the file xtensoftphone into my user account bin directory ( /home/emcg/bin ).

I will attach some screenshots for the SIP proxy setup required to connect to the Vonage service

---

### Post by Tim___ on 2006-04-13
Can you explain how it is you got vonage softphone to work on ubuntu. 

I was unable to locate the register address anywere. I called vonage and they refused to give them to me. 

I still have their service and would like to get it working asap if you have any suggestions as to have to make the softphone work on ubuntu.

---

