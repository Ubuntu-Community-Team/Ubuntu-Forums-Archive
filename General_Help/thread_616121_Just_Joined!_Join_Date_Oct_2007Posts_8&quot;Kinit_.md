---
title: "Just Joined!
 
Join Date: Oct 2007
Posts: 8
	
&quot;Kinit: No resume image...plz help"
date: 2007-11-17
forum: General Help
---

### Post by lilrayray69 on 2007-11-17
When I start I get this whole thing..:

"Starting up...
24.763729] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
24.763786] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.1
24.763739] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.2
24.763792] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.3
Loading, please wait..."

Okay, up to there I normally get that stuff. But then it goes on:

"kinit: name_to_dev_t (/dev/disk/by-uuid/0e68fe63-fb29-4b97-a7ca-15b05859202e) = hld5(22,69)
kinit: trying to resume from /dev/disk/by-uuid/0e68fe6e-fb29-f4b97-a7ca-15b058592(?)2e
kinit: No resume image, doing normal boot....

Ubuntu 7.10 Name tty1

Name login:"

* there may be some letters/numbers missing due to my screen cutting off 1 digit, thats also what the (?) is.

Past this when I login I get:

"password:" (here i log in):

"Last login: Sat Nov 17 18:56:21 EST 2007 on tty1
Linux Name 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
Name@Name:~$"

it gives me the little console thing here, and just sits. I'm not sure how to get to the OS desktop or anything from here, it's just givin me this console.

Does anyone know what this stuff means and how I can get into Ubuntu?

---

### Post by Mike Zimmer on 2007-11-18
I am getting something similar. While doing some de-installs of software with Synaptic Package Manager on 7.10 Gutsy Gibbon, I started getting some messages saying that the Network Manager couldn't get some resources, or some such thing. I got this message several dozen times while synaptic worked, removing software (anything related to Xine that I could find installed). I also think that it automagically installed some upgrades as well, which I puzzled over. When I tried to get back in later, I got the following:
<blockquote>
Starting up ...
Loading, please wait ...
kinit: name_to_dev_t (/dev/sda9) = sda(8,9)
kinit: trying to resume from /dev/sda9
kinit: No resume image, doing normal boot ...
Ubuntu 7.10 Satori tty1
Satori login:
</blockquote>
Where sda9 appears to be my swap partition, and Satori is the name of my Linux install.


When I rebooted, I also got some message saying that it was going to check a file system on some drive, but I didn't write it down. Is this the fsck I have read about on some posts, like chkdsk in windows? Sorry, I don't know much about the language for the shell (BASH?).


It sounds at the least like the same generic class of problem. I am perplexed as to what caused this. I also was getting some strange stuff on a upgrade a few hours before this - unable to access the files or some such thing.


Thanks

---

### Post by Mike Zimmer on 2007-11-18
Here is a solution that worked for me, from another site.

I reinstalled the ubuntu desktop. It looks as if some of my settings were preserved, perhaps all, but some of my menu items may have disappeared. However, I was in the process of disappearing many Xine related ones when I first had the problem, so maybe that is why they are not there.

The directions are as follows:

Boot up so that you get the terminal (tty1?).

Logon, as root if possible I think. You may not know your root password however.

Logon on any other administration account (your original account presumably) if you can't use root.

Do the following:

su -<your password in place of this stuff including the angle brackets>
sudo apt-get install ubuntu-desktop

This may take some time. Mine got stuck at one place, and I got impatient and powered down, then had to restart it later. Be more patient than me and see if it finishes.

If it finishes, reboot.

You may have your desktop back. It worked for me, but not quite in that fashion. I had to finish with another command from a partially installed desktop. I do not seem to have lost my home or my account or my desktop, etc.

Anyone else have more to add?

If you have a way of backing up your stuff first, maybe from a live CD with Qparted(?), you might be advised to do that. There is a CD in ISO format that will allow a partition copy of a linux partition. 

If you are a beginner to Linux, it is still pretty imtimidating. As far as I can see, this Linux stuff is not for the faint of heart. It seems that you always have to issue commands within a shell on a command line when you get in trouble. I read one post yesterday on this forum saying that there was always a GUI alternative. Interesting claim, and I would love to see this type of GUI based-information posted in the normal case of problem resolution, and sudo and apt-get and so on reserved for cases where there really is no alternative. In general the advise given on Linux forums seems to involve opening up a terminal and pasting in some obscure string of commands. Anyway, kudos to all the good souls who do help. This, Linux, Ubuntu, is a great achievement.


Regards
Michael Zimmer

---

### Post by niceguy123 on 2007-11-19
Mike,

Thanks for your help. My Ubuntu is back up and running. Do you have any idea why that happened?

---

### Post by Mike Zimmer on 2007-11-19
Did you do what I suggested to get it back?

I have no idea what happened to corrupt my system, or your. With computers, you often cannot figure out the problem.

Regards
Mike Zimmer

---

### Post by RevolutionMaster on 2007-11-21
any way to get the GUI back WITHOUT a reinstall?

---

### Post by kellyness on 2008-03-20
Mike Zimmer, Thanks...  Saved me a lot of headaches with this one:


su -<your password in place of this stuff including the angle brackets>
sudo apt-get install ubuntu-desktop

---

