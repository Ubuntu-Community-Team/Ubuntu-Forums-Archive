---
title: "Problem with Sudo. I think I may have mistakenly deleted the hosts"
date: 2006-11-29
forum: General Help
---

### Post by impakt on 2006-11-29
Problem above. I found this in another post so i tried it. When i use 

nano ect/hosts in recovery,root prompt, i get nothing in the page to edit or add my host name too

This is the post below. a response to the exact issue im having. 

Please help:) im having all sorts of problems lately after a year of trouble free use. 

It sounds like your /etc/hosts file is misconfigured.

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

Code:

nano /etc/hosts

The /etc/hosts file normally looks something like this...

Code:

127.0.0.1 localhost.localdomain localhost slave # The following lines are desirable for IPv6 capable hosts ::1 ip6-localhost ip6-loopback fe00::0 ip6-localnet ff00::0 ip6-mcastprefix ff02::1 ip6-allnodes ff02::2 ip6-allrouters ff02::3 ip6-allhosts

What you need to do is to edit the first line so that it contains a hostname for your computer. Mine is called 'slave' as you can see above. You can choose any name you like. The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

Code:

127.0.0.1 localhost.localdomain localhost ubuntu

An additional command you can look at with regards to hostnames is this command below.

Code:

hostname #returns the current hostname hostname <hostname> #sets the hostname according to the value entered for <hostname>

---

### Post by scxtt on 2006-11-29
**nano ect/hosts** is wrong ... you'd want to type **nano /etc/hosts** ... what you typed earlier is the equivalent of **vi `pwd`ect/hosts** which will be a new, empty file in the directory you happen to be in ...

---

### Post by CatKiller on 2006-11-29
> **impakt said:**
> Problem above. I found this in another post so i tried it. When i use 

nano ect/hosts in recovery,root prompt, i get nothing in the page to edit or add my host name too

It should be ```
nano /etc/hosts
``` Assuming you did type it correctly at the terminal, and you have deleted it, you might still be able to recover it - if you deleted it through the GUI, it might be in /root/.Trash/. Or if you were using GEdit to edit it, you may have a file called /etc/hosts~ that is a backup of the file before you last saved it. Otherwise, you could boot from the live cd, mount your hard drive, and copy the file from the live cd to the appropriate place on your hard drive. Don't forget to change the hostname to whatever the contents of your /etc/hostname file are.

---

### Post by impakt on 2006-11-30
I actually did type i wrong:) ooops 

Here is what i get. 

I get a window in terminal with the following

"
GNU NANO 1.3.10 File /etc/hosts

# The following lines are desirable for ipv6 capable hosts.






Read 2 lines
^G ^O ^R ect.ect..

"

but i get no lines in the box other than whats above

I think without fixing this, im not going to be able to get my network up again:(

Thanks!

---

### Post by CatKiller on 2006-11-30
> **impakt said:**
> but i get no lines in the box other than whats above

That's alright. Bung ```
127.0.0.1 localhost.localdomain localhost *hostname*
``` at the top of the file, where *hostname* is whatever it says in /etc/hostname and reboot.

---

### Post by impakt on 2006-11-30
Wow thanks for the quick reply. This is probably the most helpful forum I have ever been on. 

Could you please explain a bit further. 

I can type in the box. above and below
"# The following lines are desirable for ipv6 capable hosts."


 But how do you save it? Its probably with the

" Read 2 lines
^G ^O ^R ect.ect.." 

but I want to be positive. And i have to do this all in recovery mode under root right? Or can i change it directly from terminal?

---

### Post by CatKiller on 2006-11-30
> **impakt said:**
> Could you please explain a bit further.

I'll do my best. **nano** is a text editor, like gedit or kate, except that you can use it from the command line.

**/etc/hosts** is just a text file, but it tells the computer the addresses of various other computers - before the advent of DNS it was the way to find other computers, now it's used to find **your** computer. 

Lines that start with a **#** are conventionally regarded as comments and are generally ignored by computers. They are usually there for human consumption, as explanations of what the lines that the computer pays attention to mean.

You probably want the line that you're putting in to be the very first line of /etc/hosts. Putting in the right hostname is of critical importance.

**Ctrl-O** saves. **Ctrl-X** exits. The ^ character often represents the Ctrl key.

> And i have to do this all in recovery mode under root right? Or can i change it directly from terminal?

If your /etc/hosts file has a different name for your computer than the one in /etc/hostname (or indeed, none), then **sudo** won't work. So you'll have to do it from recovery mode (automatically makes you root), or from the live disk (doesn't have a broken /etc/hosts). You won't be able to be root from your normal environment until you fix your hosts file, and you can't change this file unless you're root.

---

### Post by impakt on 2006-11-30
Great.. Your response just clarified a BUNCH of stuff that was going on in my head about this issue. Im at work now without access to the box but when I get home I will attempt this and hopefully it solves this issue and I can continue to try and get my wired internet going. 

Thanks alot for everything. :)

---

### Post by CatKiller on 2006-11-30
> **impakt said:**
> Thanks alot for everything. :)

No worries, and good luck :D

---

### Post by impakt on 2006-11-30
Catkiller: You are my hero. :biggrin: =D> 

You got me going! Now hopefully I can get this damn internet going!:)

Do you think I need to enter all the other hosts i deleted in Network settings>hosts? I may just copy yours and hope for the best?:-D 


[http://ubuntuforums.org/showthread.php?t=309612](http://ubuntuforums.org/showthread.php?t=309612)

I cant thank you enough. I been having so many problems lately with this box its crazy, after a year of awesome performance one day my internet just goes down. Upon trying to solve the issue I accidentaly deleted all the hosts and bam, i cant do anything. This seems like im one step closer! 

Are you from the US? You into fitness/cycling or running? If you are PM me with your address, im gonna send you a gift ! hahah

:mrgreen:

---

### Post by CatKiller on 2006-11-30
> **impakt said:**
> Do you think I need to enter all the other hosts i deleted in Network settings>hosts? I may just copy yours and hope for the best?:-D 

Well, mine's just got the 127.0.0.1 line I gave you, then the comment about IPv6 hosts, then ```
ff00::0 ip6-mcastprefix
``` (other people seem to have more IPv6 stuff, but I have no idea what it means) and then a whole bunch of ad-related aliases from [http://everythingisnt.com/hosts.html](http://everythingisnt.com/hosts.html)

I've always done network configuration through System -> Administration -> Networking, and it's been fine. It's possible that your network card just doesn't work any more - spontaneous hardware failure does happen sometimes. Do you have another that you could try?

---

### Post by impakt on 2006-11-30
What i did was just boot with the live cd. And copy pasted all the ip's and aliases to the host option in the network config. 

Everything seems to be working ok except for the same inital problem with the eth0. I actually am gonna just take your advice and go buy a new network card. The one i have is onboard so it very well may have taken a crap. 

I'll let you know how that goes. 

Thanks again for everything.

---

### Post by impakt on 2006-12-03
Just an update. The problem with the network hasnt be found, but fixed. Strangest thing I have ever seen. 

someone here suggested it could be a hardware problem so i went and bought a new network card. I popped in and went into the bios and disabled the onboard lan. Booted up the machine and it wouldnt work. I got pissed and took the ethernet cable out and plugged it back into the standard ethernet slot and boom, it worked but wouldnt connect with anything. I sudo ifdown eth0'd and sudo ifup eth0'd and here i am. Using the onboard lan, with the PCI network card plugged in and the onboard lan disabled. WTF was the problem? and how is it working now??!>! i cant complain!Im happy as a pig in ****:)

---

### Post by CatKiller on 2006-12-03
I think that what it is, is that you've got one of these new machines that's powered by pixies. They can be a bit mischievous. Next time try one that's powered by fairies - they're more loyal, if a little bit flighty.

:)

I'm glad your network card's working by whatever method. Your PCI card might have needed to be reconfigured as eth1.

---

