---
title: "Need help with Radicale, Evolution, CalDav and Android concepts/install"
date: 2019-09-11
forum: General Help
---

### Post by anthonyl2019 on 2019-09-11
Firstly I'm fairly new to Linux but fairly old to the world and the learning curve of terminology means sometimes I can't see the wood for the trees.

I'm running Kubuntu 18.04 on a 64bit HP laptop which is on my small home network comprising of a Win7 netbook, WinXp laptop, NAS and an internet router.  All machines can see each other and where required can share folders/files.

I am aiming to have Calendar/Contacts integration from my HP laptop to my Android smartphone over the LAN (not, at least not at this stage, over the internet).  It would be nice also to have a shared calendar for my wife to access via her Android smartphone.  Basically this, at least for me, replaces my Office Outlook (2002) PIM integration with a Windows CE phone via ActiveSync.  I do not wish to have shared calendars via any internet cloud services.

What I am not understanding is how the information gets shared and I'm hitting confusion with the definition of "server" and the instructions to "ssh".

Broadly I'm trying to follow 

[https://github.com/Kozea/Radicale/wiki/Simple-installation#setup-and-verify-test-server-on-localhost5232](https://github.com/Kozea/Radicale/wiki/Simple-installation#setup-and-verify-test-server-on-localhost5232) but replacing Evolution for Thunderbird.

I have:
1) Installed Radicale

2) Installed Evolution

3) Created a CalDav calendar in Evolution pointing to the URL provided by Radicale 
    (I'm not understanding the requirement to add any "USERNAME@" before "localhost" but it might not be important for me to either)

4) Created an event in the CalDav calendar

5) Tried Verify Modification of CalDAV backend but the ics file seems rather sparse as I expected to see event details (date, times, description):
    BEGIN:VCALENDAR
    VERSION:2.0
    PRODID:-//PYVOBJECT//NONSGML Version 1//EN
    X-WR-CALDESC;VALUE=TEXT:fakecalendar01
    X-WR-CALNAME;VALUE=TEXT:fakecalDAV01
    END:VCALENDAR

Edit:update, don't think I changes anything but the earlier appointment disappeared and new appointments, past and present, appear to give meaningful ics output files.


I also now realise I don't quite understand when and how this URL (or a better one once I proceed) is made available to other devices on the LAN including my Android smartphone.

At the moment my mind is a bit of fog which I hope someone with some experience of Radicale etc will help clear up.

---

### Post by Holger_Gehrke on 2019-09-11
I don't have any experience with Radicale, but I hope I can still clear up a few points for you.

The term "server" has two meanings, on the one hand it means a program that offers a service through a network and on the other hand it means a computer that runs one or more such programs.

"ssh" (secure shell) is a way to remotely -- over a network -- access a shell (command line interpreter). It's called secure because it encrypts all traffic going through it. Because that's considered a good thing in our paranoia inducing times it's basically become the standard way to do remote access in the Linux-world. It can also act as a tunnel, meaning you connect a (non-encrypting) client to ssh on your client which sends the data to the ssh server on the remote machine which hands it over to a (non-encrypting) server-program on the remote machine, thereby turning a non-secure connection into a secure one.

The username in the URL is necessary because Radicale can keep multiple calendar for different users. Without the username it wouldn't know which calendar you want to access.

The URL you're using now (the one with 'localhost' in it) won't work for other machines (like your phone) to access this calender. 'localhost' is a way for the computer to 'talk to itself' through it's network software. That's useful when you're trying to get a server to work or when you're working locally on a machine that also offers it's services on the net. So on a different machine you'd have to enter either the IP-address of the server or a hostname which resolves to that IP-address instead of 'localhost'.

Holger

---

### Post by anthonyl2019 on 2019-09-12
Thank you for attempting to help.  The manual/documentation presupposes a  lot of knowledge and to me in any event is not clear which is a shame  because conceptually it is exactly what I want.  It takes some deduction  nonetheless to realise that the addition of a simple statement in an  appropriate config file makes Radicale work as a web server to machines  on the LAN.  Still more work to do but it seems as if there is little  interest in this forum and so I'll have to look elsewhere.

PS The following errors occurred with your submissionYour submission could not be processed because you have logged in since the previous page was loaded.
Please reload the window.  ????

---

