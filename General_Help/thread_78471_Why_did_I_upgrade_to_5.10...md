---
title: "Why did I upgrade to 5.10..?"
date: 2005-10-18
forum: General Help
---

### Post by floyd27 on 2005-10-18
So far its been a headach and a half...

1- Internet wont stay configured after a reboot. Need to pppoeconf EVERYTIME.

2-Limewire refused to start

3- Opening firefox causes..ubuntu-artwork file cannot be found please try again..(i re-installed the artwork but nothing happens)

4-Cant sudo su to make a root password

The list goes on but these are things iv tried to fix and cant get to work..
I like the new look and feel but....
I am this close - to going back to hoary.....
Any chance of people having/fixing these same problems?
thanx

---

### Post by qalimas on 2005-10-18
I have hte internet problem with normal Ubuntu 5.10 :(

---

### Post by AgenT on 2005-10-18
Probably due to your old configuration files. For the internet, if your network card works fine but you are having software problems, try doing this:
```
mv /etc/network/interfaces /etc/network/interfaces_backup
mv /etc/gnome-system-tools/network/profiles.xml /etc/gnome-system-tools/network/profiles.xml_backup
``` Reboot. When you do, your network will not work because all your settings will be gone. Go into the network-admin (System -> Adminstration -> Networking) tool and reconfigure your network. This is for GNOME. If you are on KDE, you will have to find the equivalent configuration file of profiles.xml for KDE and do the same.

If after you do this and you are still having problems, it may be due to lo not being started. In the interfaces configuration file, make sure you have this line: ```
auto lo
``` For some reason the GNOME network tool does not add this.

---

### Post by floyd27 on 2005-10-18
This is a fresh install..
not and update..
Will that still work?

I have found several more issues..

1- no access to the root folder( the entire disk not there??)

I dont think im gona keep 5.10 its just to crazy..
im gona go back to 5.04 if this keeps up..

---

### Post by floyd27 on 2005-10-18
I have a question..
Is this it for Breezy?
I mean is this the final way it will be? Because I can tdeal with it .. Im sorry but i have to go back to hoary..
Unless there are improvments down the road, I cant get anything..I cant even access my hdd..
this is not just an annoyance but a critical problem..
I did a fresh install but this is not going well at all.
After today i will decide if im going back to 5.04...

---

### Post by treris on 2005-10-18
I'm slightly amazed that you are experiencing so many problems. I did a fresh install too after havinh used Hoary since about may and although I have encountered some issues, nothing was as serious as this.
have you tried editing you fstab file to get access to your hard drives? 
the network problem I don't know nothing about, I just installed breezy and my network was running fine.
what exactly are the benefits of breezy over hoary I can't tell you as yet, but maybe someone else can give some more info on that subject?

---

### Post by Gary Powers on 2005-10-18
[QUOTE=floyd27]I have a question..
Is this it for Breezy?
I mean is this the final way it will be? Because I can tdeal with it .. Im sorry but i have to go back to hoary..
Unless there are improvments down the road, I cant get anything..I cant even access my hdd..
this is not just an annoyance but a critical problem..
I did a fresh install but this is not going well at all.
After today i will decide if im going back to 5.04...[/QUOTE]

Forgive such a basic question, but do the md5sums match up properly?  I have not had the first problem with 3 Breezy installs.

Gary

---

### Post by ykpaiha on 2005-10-18
+1 
3 or 4 install and no prob either ..?
As mentionned watch the md5sums or see your cd or dvd reader; it occure to me once with a defetive combo, ubuntu continue it's install even with some missing package( why I don't know)..:confused:

---

### Post by floyd27 on 2005-10-18
I reinstalled it again and managed to solve most of my problems..
it was not the cd but i just had to configure every little detail to get things going..
It took the better part of 8 hours but its looking better....

Still have that root problem though...
sudo su just logs me on on root? I never set any pw and thats what i was trying to do in the first place??

---

### Post by ltmon on 2005-10-18
[QUOTE=floyd27]I reinstalled it again and managed to solve most of my problems..
it was not the cd but i just had to configure every little detail to get things going..
It took the better part of 8 hours but its looking better....

Still have that root problem though...
sudo su just logs me on on root? I never set any pw and thats what i was trying to do in the first place??[/QUOTE]

To set a root password:

> sudo passwd root

Should do it.

> sudo su

This *should* log you on as root.... no problem there.

L.

---

### Post by AgenT on 2005-10-19
Unless there is a specific reason why you need real root access and need to create the user root, you should not use it or create it. You should use sudo instead as it does more or less the same thing. For those that do not know, you can enter "root mode" using sudo by typing: ```
sudo -s
```

---

### Post by bertilow on 2005-10-20
[QUOTE=AgenT]Unless there is a specific reason why you need real root access and need to create the user root, you should not use it or create it.[/QUOTE]

True. But with Breezy I used the export mode in the installation (in order to be able to choose some different partitioning) and the installer made me pick a root password, and then it created a root account for me. I had no choice. (Although I don't know what would have happened, if I had refused to type in a root password...) And afterwards it turned out that the ordinary user acount had not been given any sudo rights. So everything worked just as it's not supposed to work in Kubuntu!

I've since added me to the sudo list (using the root acount  - how else?), and I now avoid the root acount. I guess I should remove it altogether, but I won't risk doing that. Who knows what will happen to my system if I do. I've already had enough problems with Breezy as it is.

I do like Kubuntu, but in my opinion the talk about "just works" should be silenced for a while. It's simply not true right now.

---

### Post by lorenco on 2005-10-20
U may also try "sudo bash" <- This will give u a root bash session.

I also had problems going up to Breezy by the way  and had to revert back to Hoary. :???:   It took me 10 Hours (not completely wasted) but I had to restore my tar of root (Thanks to a previous failure I leaned my lesson)

The problem :
VMWARE networking fails to start cleanly and hung my e1000 network connection. (Which causes me to "hard reset" can not close any network or shutdown. 

Hope they can fix the niggles...  Will have to wait until more fixes ar in

Lorenco.
Running a T41 IBM Thinkpad.

---

### Post by lorenco on 2005-10-27
I fixed the problem with VMWare Network, for resolution see [here]("http://ubuntuforums.org/showthread.php?t=81748") .

I am now running Breezy like a Breeze.

I Followed the advise of a post to create two Partitions Hoary & Breezy
(Off Topic : Parted works like a dream... Resized a Fat32 Partition without a glitch! :D )

The only thing left to do is to see if I can get Hibernate (Suspend to Disk to work)
Tried it Yesterday and it failed :( 

Well the small glitch left but working like a Breeze !!!;)

---

### Post by Hitman1 on 2005-10-27
[QUOTE=floyd27]
3- Opening firefox causes..ubuntu-artwork file cannot be found please try again..(i re-installed the artwork but nothing happens)
[/QUOTE]
I had the same issue until I finally figured it out. Firefox is trying to load a default homepage that was present from hoary. The fix is simple:

In Firefox, go to Edit/Prefrences/General and change the Homepage location to something else other than the non existant page.

---

