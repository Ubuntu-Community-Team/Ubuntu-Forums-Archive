---
title: "Trouble printing thru XP shared printer"
date: 2005-04-08
forum: General Help
---

### Post by wordsmith on 2005-04-08
I'm fairly new to linux, though Ubuntu is the most user-friendly distro I've used. It set up fine on my IBM Thinkpad 600 but I cannot get it to print from the network printer hosted by my PC running WinXP. I get as far as installing it via CUPS but when I print a test page nothing happens. Any help would be MUCH appreciated as I've wrestled with this more than a bit. ](*,)  ](*,)

---

### Post by orion_114 on 2005-04-09
Have you got samba installed ?
Can you see the windows machine on the network ?

---

### Post by wordsmith on 2005-04-09
Well, I'm pretty sure it's on my system but I don't really know how to work with it. Help?

thanks 8-[

---

### Post by orion_114 on 2005-04-09
Ok lets start at the beginning ....
Can you ping the machine you wish to print to ?
Find the ip address of your windows xp machine by going ...
start --> run 
Then type cmd
type ipconfig in this window and you should see your ipaddress there.
Now on your ubuntu machine goto the command line
and type ping <your windows ip address>
see if you get a response.
Let me know and we can take it from there.

---

### Post by Lamber on 2005-04-09
I've got the same problem. IP2000 on a XPhome machine. I can connect to the pc (smb://192.168.0.1) and even can see the machine's shared folders...

I've tried printing with ipp and smb probocol, but both dont work. Using XPpro (vmware on linux) I get a error that say: RPK can not be found (or something)

////

Do you have a Guest Account Enabled on XPmachine? Can you view the Ubuntu maching (shared folders)?

---

### Post by wordsmith on 2005-04-09
Orion, yes I can ping my IP addy from my Ubuntu machine. 

PS: thanks for the help. I'm kinda at my wits end with this problem.

---

### Post by orion_114 on 2005-04-10
Sorry if I am going through this very basically but I dont know what your knowldge of computers is. Let me know if I am going too slow.

[list]
[*] Check that you have shared your printer on your windows machine.
[*] Right Click - properties on it and goto the sharing tab.
[*] Click on share this printer and type a short name in the share name box.
[*] Now goto your ubuntu machine and goto your printers
[*] Add a new one
[*] Click on network printer.
[*] Select Windows Printer (SMB) from the dropdown.
[*] In the host section type the IP address of your windows machine.
[*] In the printer section type the share name you gave your printer
[*] Now enter your username and password for your ubuntu machine.
[*] Click forward.
[*] Now select the manufacturer and model of your printer.
[*] And finally click on Apply.
[/list]

This should get you up and printing. If not then you might need to change the security settings on your printer. Let me know if this worked and then we can go into that.

---

### Post by wordsmith on 2005-04-10
Thanks Orion, that worked like a charm! I can now print thru my deskjet (color) and my b/w laserjet, both hosted by my XP pro box. After fooling around with Linux since Mandrake 8.0, I've finally found a distro -- Ubuntu -- that's user-friendly, as long as it's with the help of people like you.

BTW, was in SA a few years back and had a wonderful time touring the entire country. A lot of it looked like Montana, except that there were ostriches in the wheatfields instead of elk and antelope. The Wild Coast was my favorite, and I was glad to hear that the attempt to build a highway thru there was halted now now.

Anyhow, thank you again. You've made a significant deposit in the karma piggybank! If you ever get to Montana I'll be glad to show you around. 

Peace,
Kimball

---

### Post by orion_114 on 2005-04-10
Hey wordsmith I am only too glad to help.
I am also glad you had a good time in SA.
Its a really awsome place!!
I hope that I can come to  Montana some day and check it out.

---

### Post by ggeneraux on 2005-04-20
[QUOTE=orion_114]Sorry if I am going through this very basically but I dont know what your knowldge of computers is. Let me know if I am going too slow.

[list]
[*] Check that you have shared your printer on your windows machine.
[*] Right Click - properties on it and goto the sharing tab.
[*] Click on share this printer and type a short name in the share name box.
[*] Now goto your ubuntu machine and goto your printers
[*] Add a new one
[*] Click on network printer.
[*] Select Windows Printer (SMB) from the dropdown.
[*] In the host section type the IP address of your windows machine.
[*] In the printer section type the share name you gave your printer
[*] Now enter your username and password for your ubuntu machine.
[*] Click forward.
[*] Now select the manufacturer and model of your printer.
[*] And finally click on Apply.
[/list]

This should get you up and printing. If not then you might need to change the security settings on your printer. Let me know if this worked and then we can go into that.[/QUOTE]
 I want to add my thanks to this thread of messages also.  Most of the information I've found out there described the opposite scenario of printing to a Linux printer from windows.  Thanks again!

---

### Post by orion_114 on 2005-04-21
Glad I could help! :D

---

### Post by Dex on 2005-05-03
I've done everything 'by the book' as described in this thread - I can see other windoze machines on my LAN - none of them does see my ubuntu laptop, though; I have assigned a permanent IP address to the windoze machine to which my hp printer is attached; all windoze machines can print to it, but I can't print from my ubuntu laptop. No go. Anyone please give me some pointers, appreciate

---

### Post by espiem on 2005-05-03
I've tried the tutorial given by Orion and it's worked. Thanks. I've another problem. How I can share my printer HP Laserjet in my ubuntu machine with another ubuntu machine. I've tried everything... but I couldn't find a good tutorial to work with. Please help.

---

### Post by Dex on 2005-05-04
I have pretty much given up on trying to print to windoze attached hp printer.
I've tried everything that was discussed on the forum, unless I missed something.
I can see all other LAN machines, I have the same workgroup on my ubuntu laptop, I can ping the windoze machine to which the printer is attached. I also installed kde and went that route with auto detect the printer - it was nicely detected. What's happening is the windoze machine printer is actually showing a job sent from ubuntu but it never prints. Not only that it won't print anything from ubuntu, but every time I try this ALL 3 remining windoze computer, AND the main computer can no longer print to this printer. It's impossible to delete that job. The ONLY way I can use the printer again is to uninstall all software, cold reboot without USB cable attached, reloading software. It can only be used by windoze machines. Not sure where to go with this but I've pretty much given up - I will send documents to windoze machines on network and print it from there - shoestring solution.... 
Any ideas appreciated, thx,


 ](*,)

---

### Post by orion_114 on 2005-05-05
Hey Dex.
I haven't experienced the problems you are having at the moment.
My only suggestions could be:

1.) Try see if there are any aditional drivers you can add to your windows machine.
      - goto printers & faxes
      - Click File -> Server
      - Here you should find under one of the tabs the option to add aditional drivers.

2.) Try installing different drivers on your ubuntu machine.

3.) Maybe disable your windows firewall or any other firewall software and see if that is having an impact.

---

### Post by Nu-Buntu on 2005-05-05
Orion, I must add, very clear, step-by-step directions. You should consider adding this to the How-To's. Great job!

---

### Post by orion_114 on 2005-05-06
hey Nu-Buntu,

I took your advice and added a howto.  :D 
Thanks.

You can find it here:
[http://www.ubuntuforums.org/showthread.php?p=161112#post161112](http://www.ubuntuforums.org/showthread.php?p=161112#post161112)

---

### Post by webbie180 on 2005-07-23
I followed all the steps but got an error message, connection failed with error NT_STATUS_LOGON_FAILURE.  Wat's wrong and what should I do?

---

### Post by glnnrl on 2006-06-09
I just installed Dapper and really like it. Haven't played much other than with Mandrake. The only problem I'm haveing is with printing. I can connect to my windows 2000 server and access all the shared folders and pass files back and forth. I installed a windows SMB printer. It automatically pulled the server in the list and then the shared printer. It had me log in which I did and then saw the two shared printers. I have a Brother HL-5150D and an HP-1220C. The printers initally say they are ready but when I print a test page...nothing.

I get the following mesages after waiting a few minutes:

Printing: Unable to connect to CIFS host, will retry in 60 seconds...

Paused: /usr/lib/cups/backend/smb failed

Seeing that I can connect to the Win server I'm not sure why I'm having the printing problems. I also haev Unix printing services running on the w2k box.

Any insight would be appriciated.

Thanks,
Glenn

---

### Post by mrhirsh on 2007-10-12
Orion,

I am having  the same problem that wordsmith was.

I went through the sequence that you have listed and I am still having the same problem.  When I attempt to print in XP Pro, I get the little icon at the bottom indicating that it is being sent to the printer, which quickly disappears (as is normal), but nothing prints. 

Any other suggestions?  

Thanks,

---

### Post by jdlongmire on 2007-10-20
I believe I am having the exact same issue...no joy, thus far...

---

### Post by Jiipbe on 2007-10-28
Hi I'm having a bit of another problem with this. 

As you can guess I'm the newbie of all newbies with Linux but I'm beginning to get a hang of it (and I love it). Though... here's the deal: I had to disable the network manager because I want to run XP seamless according to this thread:
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)
(still have a long way to go with the bridge though)

Apparently nmapplet gets in the way and the network has to be configured manually. I don't have a problem with that. So I followed the instructions:

```
sudo gedit /etc/default/NetworkManager
sudo gedit /etc/default/NetworkManagerDispatcher
```
and wrote exit as the only thing in these files

After disabling the network manager, everything that was running just fine before, I could print on the windows shared printer and most of all I could ping it, stopped working. I'm still capable of accessing the Internet though :confused:

Now I have the problem that I can see the computer on our shared network but funnily enough when I try to add a printer, as described elsewhere, the network, to which we both belong to under Network -> Places, appears but then only my own computer is visible.

By the way we're communicating through a wireless network (WEP protected) with fixed IPs determined from the computers themselves (my router cannot send out fix IPs)

Can someone please help me with this I'm beginning to despair a little.

Thank you

Edit: Tried tweaking smb.conf and now I can't even see the network in places!!! I'm going banana!!!!

Edit: Forget about it. Changed the router configurations. Went back to DHCP. Everything works again

---

### Post by brennydoogles on 2007-10-29
> **Dex said:**
> I have pretty much given up on trying to print to windoze attached hp printer.
I've tried everything that was discussed on the forum, unless I missed something.
I can see all other LAN machines, I have the same workgroup on my ubuntu laptop, I can ping the windoze machine to which the printer is attached. I also installed kde and went that route with auto detect the printer - it was nicely detected. What's happening is the windoze machine printer is actually showing a job sent from ubuntu but it never prints. Not only that it won't print anything from ubuntu, but every time I try this ALL 3 remining windoze computer, AND the main computer can no longer print to this printer. It's impossible to delete that job. The ONLY way I can use the printer again is to uninstall all software, cold reboot without USB cable attached, reloading software. It can only be used by windoze machines. Not sure where to go with this but I've pretty much given up - I will send documents to windoze machines on network and print it from there - shoestring solution.... 
Any ideas appreciated, thx,


 ](*,)


I am having this problem as well.

---

