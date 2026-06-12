---
title: "Lost network and internet connection after today's xubuntu update"
date: 2014-05-20
forum: General Help
---

### Post by martago on 2014-05-20
As usual I ran today update-manager in a pc with the latest xubuntu release 14.04.  This pc has only the basic installation, no extra software, I use it exclusively for homebanking, so I only use Mozilla Firefox software, nothing else.  After running xubuntu update as I do it every time I use this pc, after restarting it, I could not access the internet anymore, the pc had lost network access (wired network).

No problem with the internet access on the pc physically accessing the local network.  This same computer has side by side Windows 7 Pro, which I had to use (without any internet access problem) as an alternative to xubuntu.

Anyone had a similar problem recently?  I would thank any suggestions on how to overcome this situation without having to reinstall xubuntu.

Thank you.

---

### Post by varunendra on 2014-05-21
Please follow the instructions in this post to provide us a detailed report of your current wifi settings : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by martago on 2014-05-21
Thank you for your reply.  I will do as instructed, but please notice my previous email where I stated "wired network".  I am not using wireless network in my home, just cabled ethernet network, and besides that this computer is a desktop pc with no wifi port.  As I stated before, that computer was working ok before running update-manager, after I ran it and restarted the computer I lost network connection and the option for restoring wired network was disabled on the top panel.  Afterwards I restarted the same computer choosing to boot Windows 7 and I got no problems in accessing the local network or the internet.

---

### Post by Yellow Pasque on 2014-05-21
At least give output of:
```
lspci -k
ifconfig -a  #remove mac/ip address if you wish
```

---

### Post by varunendra on 2014-05-21
Oops, I admit that I totally overlooked the "wired network" part, usually I don't, but I did.

Still, the script report contains a number of reports that are needed to troubleshoot the wired problems as well, so either post its report anyway, or the outputs of these commands individually (including here what Temüjin suggested above) -
```
uname -mr
sudo lshw -numeric -C network
ifconfig -a
route -n
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
nm-tool
lsmod
```
..and please clarify this part of your first post -
> No problem with the internet access on the pc physically accessing the local network...
Do you mean when using Windows?

---

### Post by martago on 2014-05-21
I have advanced in detailing the problem reported.  First I must add that besides the basic Xubuntu 14.04 installation WITHOUT any extras (codecs, flash, libreoffice, etc.), I had in fact installed just one application - gufw - via apt-get install, then "enable ufw".  Minutes ago I accessed "Settings Manager", followed by "Network" and I noticed all tabs were disabled, so I clicked on the "Unlock" button, entered my root password, restarted the computer and I had again network access and internet.  I restarted the computer a second time, and again all was ok.  But when I accessed Settings manager and network again, the tabs were disabled a second time and when I restarted the computer for the third time, the network and internet were gone again.  However repeating the same procedure - "Unlock" and restarting the computer re-established the network and internet connection.

---

### Post by varunendra on 2014-05-22
Have you configured ufw? By default, it blocks [s]'ALL'[/s] **ALL 'incoming'** traffic. So unless you know how to configure it properly (I don't have any first hand experience with configuring ufw, so can't help with that), it is best to simply turn it off, and play with it again only when you have learnt how to properly use it.

To turn ufw off, either do it from the GUI, or via the command -
```
sudo ufw disable
```

---

### Post by martago on 2014-05-22
I have several desktop pcs, some old and other new, two notebooks (one old and another newer) and a netbook, all with Xubuntu alone or side by side with Windows (XP or 7).  In ALL of them, totaling nine, I have installed gufw without any configuration other the standard/default configuration that comes with this software, and I have been doing it for three years at last.  In no other computer other the one reported and only after running update-manager recently, I had the problem I reported.  However I admit this problem may be related to gufw software.
If there are no other users complaining with a similar problem, I suggest we end this thread now as I have found a fix for the reported problem ("Unlock" in Network - Settings manager).  If for some reason this bug persists, I will reinstall Xubuntu from scratch.  Thank you for your help.

---

### Post by varunendra on 2014-05-22
Just installing ufw or gufw does nothing. Enabling it does. Default option of ufw (to which gufw is just a gui frontend) is to block 'ALL incoming' traffic (outgoing is allowed by default).

While the problem may be more than that, or maybe something totally different, improper and/or unnecessary use of ufw is frequently the problem for inability to use network when it 'appears' to be connected. I don't know about the 'Unlock' option you mentioned (I am on 12.04, and don't see any such option anywhere in my Network settings), so can't even guess what is it related with. But if it is related to ufw settings (just a guess), you can check what it does to the ufw rules by using command -
```
sudo ufw status verbose
```
..before and after using the said 'Unlock' option.

If the rules remain the same, it may be something else, or some additional feature of the gufw gui that gets mixed with Network settings gui. If they change, then it is simply a way to control the rules.

---

### Post by martago on 2014-05-23
If ALL incoming traffic is blocked by default with gufw, how do you explain that in so many computers and for more than three years, I have been using Xubuntu with gufw installed WITHOUT any configuration from my side?  How can I access the internet, update Xubuntu or look at my emails?  Why would anyone create a firewall software that by default blocks computer communications, forcing user to master that software if he/she wants his/her computer to work?  It does not make sense.
The problem with these threads is that anyone that is gracefully replying to them, always assumes that the problem lies with the user doing something wrong, and that the software is ok, there is no bug or malfunction.  As I told you in my initial message, in the minute before running the update-manager the computer was operating ok, with gufw installed and NO post-installation configuration done from my side.  One minuter after the xubuntu software update I had my external communications (network and internet) blocked.  How do you explain this?

---

### Post by varunendra on 2014-05-24
> **martago said:**
> If ALL incoming traffic is blocked by default with gufw, how do you explain that in so many computers and for more than three years... <bla-bla-bla>

I neither have time, nor have desire to explain anything. I suggested you a command, output of which is a proof of my 'Assumption' itself, and if you are really interested in an explanation rather than debate, search and read yourself on how firewalls work (hint : 'requested' vs 'non-requested' traffic. In other words, 'replies' are what you get as 'incoming').

I rarely assume that whatever I'm trying is definitely the right direction towards solving a problem, I just get lucky quite often, who knows why. I don't know if other troubleshooters have magic eyes or can somehow talk to the remote machines, but my way of troubleshooting is to look at available hints, make guesses/assumptions where necessary, and work my way up from there. Looks like we have hit a massive roadblock in that approach - called prejudice, so I humbly accept my stupidity and inability to understand a thing, and give up. Hope you'd be able to get better help from other great minds here or somewhere else. Good luck.

---

### Post by martago on 2014-05-24
Thank you for your time in trying to help with this thread.  I am closing it as solved as a fix has been found.  Thank you again.

---

