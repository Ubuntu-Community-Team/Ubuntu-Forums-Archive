---
title: "How BEST to transfer files from 1 pc to another pc?"
date: 2018-03-22
forum: General Help
---

### Post by maxoa on 2018-03-22
I want to transfer about 80-100 gigs of music from one computer to another.  Luckily the computers both sit on my desktop. Also, BOTH computers are Ubuntu 16.04.

Problem:
1-Computer 1 has Ethernet port while computer 2 does NOT.
2-Both computers have USB and firewire. Both computers have Wifi too. 
3-In a perfect world I would like to plug a USB cable into both BUT I know better.
4-BIG Problem, my external drive just pooped the bed.

How do you guys/gals transfer your music back i and forth.  What internet sites do 80-100 file transfers?  

How come, in 2018, I am dealing with the same issue that I had in 1995 with PCAnywhere???

Cheers,

---

### Post by Holger_Gehrke on 2018-03-22
Both Machines have WLAN and are connected the same access point ? Then - if 16.04 is anything like the 12.04 on which I last used main line Ubuntu (have switched to Xubuntu since) - you can just right click in nautilus (the file manager) on the folder with the files you want to transfer, select "share", give a name for the share, then on the other computer select network, windows network, the network name of the other machine and you should see the name of the  share you've just set up. You should now be able to just copy the files across the network.

If setting up the share does not work, you probably need to install ('sudo apt install samba') and configure (instructions in the [community help wiki]("https://help.ubuntu.com/community/Samba?action=show")) samba, a server for sharing files across the network.

If they aren't connected to an access point and you don't have one at hand, you should look into setting up an [ad-hoc wifi network]("https://help.ubuntu.com/community/WifiDocs/Adhoc").

Holger

---

### Post by sudodus on 2018-03-22
I have computers with ethernet (cable) network access, and I use sftp or rsync to transfer files. But one of your computers has no ethernet, and maybe your wireless network is flaky. Otherwise, **if your wireless network works well (in 'the other computer'), you can still use sftp or rsync** (slower than via ethernet). In both cases I would work via a router. In this case, install openssh-server in one of the computers.

If a local network connection is not an alternative, I would **unplug the internal drive containing the music files, and connect it to the other computer**

- internally if possible or via eSATA, which makes the transfer fast, or

- via a USB adapter or SATA to USB box. If all USB 3, the transfer will be fast, otherwise slow but it should work (overnight if necessary).

---

### Post by Dennis N on 2018-03-22
Lacking an external drive to transfer data with, are these computers connected to a router? If so, install openssh-server on one machine, and move the files over the local network.

---

### Post by maxoa on 2018-03-22
Hi Dennis, 
Yes both are on my home router.  I would like to try open-ssh. Do you know of any websites with steps written out or in this forum?

Do both computers need to running openssh? I would assume so but wanted to make sure. One as server and the other as client.

---

### Post by ajgreeny on 2018-03-22
There are lots of links to details about using ssh on [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) from which you can read all you need.

The package openssh-client is installed by default, I think in all the *ubuntu family, but you will need to install openssh-server, and then for best security read the appropriate link from those mentioned above.

---

### Post by sudodus on 2018-03-22
> **ajgreeny said:**
> There are lots of links to details about using ssh on [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) from which you can read all you need.

The package openssh-client is installed by default, I think in all the *ubuntu family, but you will need to install openssh-server, and then for best security read the appropriate link from those mentioned above.

+1

It is very easy to use sftp or rsync via ssh 'one-off' with password login.

After the **installation of openssh-server** in one computer, which becomes the server, you connect to it from the other computer with sftp or rsync or some built-in GUI method, for example via the file browser Files alias nautilus in Ubuntu.

See this link for some details, [Remote access Ubuntu Server filesystem through GUI](https://askubuntu.com/questions/964957/remote-access-ubuntu-server-filesystem-through-gui/964972#964972)

If you want to use it regularly, particularly in a network, where other users have access, you should use authentication with keys, which is a bit complicated the first time, but @ajgreeny's link and links from it describes how to make it work.

---

### Post by Dennis N on 2018-03-22
> **maxoa said:**
> Hi Dennis, 
Yes both are on my home router.  I would like to try open-ssh. Do you know of any websites with steps written out or in this forum? Do both computers need to running openssh? I would assume so but wanted to make sure. One as server and the other as client.

You need to install **openssh-server** on just one computer (the host). Use the other one (the client) to initiate the connection. You just need the IP address of the host computer to connect. Run ifconfig on the host  to find it before connecting.  

I personally use **gigolo** to manage the file transfers - install it on the client to establish the connection to the host and login with host password, after which it opens a file manager window on the host. You can then use copy and paste or drag and drop to move files and folders between computers. Check it out.

---

