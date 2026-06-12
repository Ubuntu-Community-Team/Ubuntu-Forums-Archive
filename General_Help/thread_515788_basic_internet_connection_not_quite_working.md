---
title: "basic internet connection not quite working"
date: 2007-08-02
forum: General Help
---

### Post by chris_n00b on 2007-08-02
Hello all,

I am running ubuntu 6.06 and am just trying to get the internet working on it. At one point it was working, then I moved to a new place and can't  get it working. 

The steps I have taken are this:

Went into Administration> Networking.....

Activated the eth0 wired connection.

'Enabled'

Set it to DHCP

Now its not working I tried rebooting but then it hangs the bootprocess OR sometimes just says 'failed' on starting basic networking and network interfaces.  

I would then unplug the cable and restart, then have to redit the /etc/network/interfaces file back to default before it will boot properly.

I have been trying to get it working this way after unsuccessfully getting my wireless to work in unsecured mode OR WEP mode.

Is there anything else I need to check or do to get things going? I mean normally you can set it to dhcp and enable the connection and your computer should get an IP and then youe set right? Why after I change the networking settings does the system hang? Or fail the networking check?

It does the same when I try to give it a static IP and fill in the fields?

Anyone else have this problem?

---

### Post by Theimon on 2007-08-02
What is/are the exact error message(s)? And what do you edit in  /etc/network/interfaces?

---

### Post by chris_n00b on 2007-08-02
Well I'm not getting a specific message persay, I just can't load any pages.  Basically what I mean by 'editing' my /etc/network/interfaces is that when I tried to setup my network settings that file changes by adding a few lines. I know what that file is at default so when the system hangs I just revert it by deleting the 'auto ra0' or 'eth0' from that last few lines and any IP addresses it may have added. That seems to do the trick.

I just plug the ethernet cable in from the modem, go to Network Settings and then make sure my wired connection is enabled, and set it to DHCP instead of Static IP.  That should work shouldn't it?

I eventually want to get this working with a wireless card using WEP with 128 bit encryption, but for now Im just trying to get it to work at all.

[B]Maybe I should just be trying to get it going with WEP anyway right at this point. 

I have read through 30 + pages tryin to find the answer and the only thing I can find out is that 6.06 comes with the RT61 chipset driver already installed, BUT it needs a firmware update to make it work? Is this the case?  Another thing I read is that I should not use the Networking interface under Administration from the drop down menu since it can cause a 'hang' in the boot up from a wrong /etc/network/interfaces file.

I was trying  a few things that people suggested in other threads but nothing worked. Im getting the same errors they are getting, like no DHCP offered or whatever and segmentation fault.



What do you need to know to help with me with this problem.  as everyone knows if you cant get internet working with ubuntu its basically useless.  Some of the tutorials and step by steps tell you to go to synaptec to down load some packages, but thats the problem, I can't get online with it to download anything. Setting up a wireless connection with WEP with a chipset that is supported should not be this hard. Im just too new to it to know what to look for and dont know where to look to find the problem.  People instruct to use certain commands, but Im not good enough so I need the exact command to type so I can learn what im doing.  :(

Other people with these cards and the same version im running (6.06) are gettin it to work so I know its possible. If i end up not getting it online Im going to have to switch back to Windows unfortunately.[/B]

---

