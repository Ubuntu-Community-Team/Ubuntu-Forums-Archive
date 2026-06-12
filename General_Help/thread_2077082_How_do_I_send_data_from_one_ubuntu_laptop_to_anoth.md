---
title: "How do I send data from one ubuntu laptop to another via wireless or LAN?"
date: 2012-10-27
forum: General Help
---

### Post by Ulysses1994XF04 on 2012-10-27
I'm trying to pull off data from my old dying laptop to my new one. They're both ubuntu. They're both on and connected to my wireless but I can't "sense" the other computer on either and transfer the data. I tried finding an old LAN cable and connecting them together but they still can't detect eachother. 

What do I do?

---

### Post by *^kyfds( on 2012-10-27
network sharing would be one idea.

right click on a folder, and press 'sharing options'.

You'll have to install a windows adapted sharing utility on both computers, but it should work.

They both need to be on the network, not directly connected to each other.

---

### Post by Ulysses1994XF04 on 2012-10-27
> **Thehumorouscheese said:**
> network sharing would be one idea.

right click on a folder, and press 'sharing options'.

You'll have to install a windows adapted sharing utility on both computers, but it should work.

They both need to be on the network, not directly connected to each other.

How do you do that? I thought windows programs don't run on ubuntu.

---

### Post by cwsnyder on 2012-10-27
You are looking for the **samba** utility for Windows type sharing of files/folders, or NFS for a Linux/BSD/Unix approach.

---

### Post by AlexDudko on 2012-10-27
ssh, ftp protocols should be added. I prefer ftp with login (installing of vsftp and some configuring is required).

---

### Post by Ulysses1994XF04 on 2012-10-27
I don't understand. I have ubuntu, not windows or unix.

I just have an ordinary Comcast home wireless set. 

Both my laptops are open and connected to the internet wirelessly. I just want to see the other computer in my top-right corner Networks icon, click and drag some files and have the files go to the other computer, either through my wireless or through a short LAN cable. 

Is there anyway to do that?

---

### Post by jerome1232 on 2012-10-27
Use samba or ssh to share files easily. Samba is a Linux implementation of a windows protocol for file sharing, works pretty good. It's what is installed automatically if you share a folder from the gui.

To use Samba, just open nautilus, right click a folder you want to share, click sharing options, check share this folder, follow any one screen instructions. You may be asked to log out then log back in after it installs samba for the first time. Repeat to make sure the folder is shared.

Goto the other computer and do the same thing, you should be able to see the shares by opening nautilus, pressing "alt", type "net" then press enter, you should see both computers in here.

---

### Post by Ulysses1994XF04 on 2012-10-27
I tried going on the files in my old laptop and clicking right-click -> Sharing Options -> Share this folder. 

A message came up that said "You need to install the Windows networks sharing service in order to share your folders." I tried clicking "Install Service," and a download window appeared to pop up for a second, but an error message appeared. It says...

"W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.8_i386.deb).
 404 Not Found [IP: 91.189.92.181 80]"

The message is repeated 5 times. What do I do?

---

### Post by Ulysses1994XF04 on 2012-10-27
Also, what is Nautilus? I don't see anything named "Nautilus" when I right click on a file, in my top toolbar or icons or when I search both computers.

---

### Post by jerome1232 on 2012-10-27
Is the laptop connected to the internet? If so which version of Ubuntu is it running?

---

### Post by Ulysses1994XF04 on 2012-10-27
Yes, both laptops are on and connected to the internet right now. My old laptop (the one that has the files I want to transfer) has the 2010 version. My newer laptop has the 2011 version.

---

### Post by jerome1232 on 2012-10-27
There are two versions every year, one in april and one in october.

If you have 10.10, the one that came out in october, it has reached it's End of Life and won't be able to contact the update servers.


If you have 10.04 LTS (Long-term support) it is still in support to 2013 and you shouldn't be getting that error.


Assuming you have 10.10 on your old computer, your going to have to swap it's repositories in order to install anything.

Based on this guide [http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)

You have edit your sources.list file run the below command from a terminal

```
gksu gedit /etc/apt/sources.list
```

In the file that opens up, replace all the occurrences of *archive.ubuntu.com* with [I]old-releases.ubuntu.com

[/I]After that's done run the command below, and samba should install successfully

```
sudo apt-get update
```

---

### Post by cwsnyder on 2012-10-28
You also may want to read this thread on file sharing in Ubuntu: [http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)

---

### Post by AlexDudko on 2012-10-28
It's not a problem you can't install it on old and not supported system. It's enough to install it on one PC which will act as a server. If you need it, I can give you detailed instructions how to do it with the help of ftp server.

---

### Post by Lars Noodén on 2012-10-28
The fastest and easiest way I use is to put openssh-server on one machine and then connect from the other using sftp or rsync.  OpenSSH-server requires no additional configuration to use with sftp and that includes the clients built into the graphical file managers Nautilus and Dolphin.  So if you want, you can use a graphical interface or a text interface, your choice.

---

### Post by jerome1232 on 2012-10-28
Yes, why didn't I think of that, you only need to enable the sharing on one computer. I get zeroed in on things sometimes. :D

---

