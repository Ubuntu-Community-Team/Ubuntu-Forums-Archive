---
title: "FreeNX server on Colinux on Windows XP box connecting through Hamachi..Possible?"
date: 2008-01-22
forum: General Help
---

### Post by greavette on 2008-01-22
Hello,

Hopefully this is the right forum to ask this question.

I've been searching for a solution that crosses so many different applications, I'm finding it difficult to look for answers.  I've searched the net and bookmarked many sites that might give me what I need, but I still have too many questions.  Seeing as this Ubuntu Forum community has such a diverse knowledge I'm hoping someone here can point me in the right direction.

So, here's my setup.  I have software on a Windows PC (I don't have this PC at my house, it's in another city).  I'm currently connecting from my Ubuntu PC to use this software on the Windows PC.  I've installed the Ultra VNC server on the Windows PC and connected to it from Ubuntu through a Hamachi secure connection.  Connects fine and I can see the Windows PC, but it is very slow.  

Here is what I'm hoping to setup to help me speed up my connection so I can use this software over the Net as if I were sitting in front of it:

Install [Colinux ]("http://www.colinux.org/") on the Windows PC.  Actually, I've found something called [ andlinux ]("http://www.andlinux.org/downloads.php") which is a preconfigured colinux with either a XFCE or KDE front-end.  The current version is ubuntu 6.06.  I plan to upgrade this to Feisty and then Gutsy (read below to see why I want to upgrade)

I'm hoping to use this [ link ]("http://ubuntuforums.org/showthread.php?t=620057") to install the FreeNX server on my Gutsy andlinux (now you see why I wanted to upgrade).  The reason I'm installing FreeNX in colinux is due to this [ thread]("http://lists.kde.org/?l=freenx-knx&m=113279985811581&w=2") that says you can access a windows box from Linux using FreeNX (even though no FreeNX server exists for Windows).  The page is old and I have no idea if this will work.

I then use FreeNX on my Ubuntu box to connect to the FreeNX server on my Windows/Colinx box.

To wrap this all up in a secure connection, I'm planning on using Hamachi on both boxes.

So I've been surfing the net looking for any information I can find on andlinx/colinux, FreeNX, and how to use Hamachi to connect with FreeNX.  I've been using Hamachi for a while on both Windows and Ubuntu so installing Hamachi and using it isn't a problem.  I'm still learning Ubuntu and have been using it since Feisty came out.  I'm not versed at all in figuring out how to fix something in Ubuntu hence my need to find instructions on how to install/configure applications.  I don't mind learning and trial and error so I'm not looking for someone to do all the work for me...just to point me to where I can find the information I need.  Although if someone can tell me what I need to do, I'd be very grateful!

So, here is what I'm looking to find out:

   1. So is this even possible to use FreeNX on colinux/andlinux so I can view an application on a windows PC?
   2. Can I update andlinux to Gutsy and install the Gutsy package of FreeNX?  Is it as simple as adding the Feisty (and then Gusty) repos to my sources.list and then issuing the dist-upgrade command?
   3. Should I use FreeNX or No Machine?  Is one easier to setup than the other?  Which do you think is the best for me to use?
   4. Is it possible to connect to a FreeNX server using a Hamachi IP address.  From everything I've seen, FreeNX always gives instructions to use SSH.  Does anyone have instructions on how to use a Hamachi IP address in FreeNX?
   5. Is there a better way to do this?  What apps would I need to do this?  I'd be willing to use a commercial application (depending on cost) if it was the best way to help me.  I would prefer FOSS, but I will consider all options.

I really hope someone will be able to help me figure this out, or even just help me find where to look for the answers I need. 

Thanks,

Greavette.

---

### Post by bodhi.zazen on 2008-01-22
Well, I have some experience with colinux, but it was some years ago.

First, upgrading to gutsy will require you sequentially upgrade 6.10 -> 7.04 -> 7.10 and may or may not work.

Second, if you install CoLinux and log in via FreeNx you will get the Ubuntu Desktop, not the Windows desktop.

I suggest you install a FreeNx/No Machine server on the Windows box and connect from Ubuntu.

Or, if possible, go for something like VMWare or VirtualBox :)

---

### Post by greavette on 2008-01-22
Hello bodhi.zazen and thank you for the reply!

I wasn't aware that FreeNX had an install for windows.  Can you confirm that this is true that the server can be installed on Windows?

If it can't then that is probably the deal breaker for this setup I'm after.  I wanted to see this Windows application and thought that running the FreeNX server in colinux would allow me to see the Windows side as well as the Ubuntu side of colinux.

Are there any other options to using a super fast 'vnc' like connection where my Ubuntu box  must connect to Windows?

Thanks!

---

### Post by bodhi.zazen on 2008-01-22
Oh, I just looked, there is no FreeNX server for windows.

---

### Post by greavette on 2008-01-22
I've searched on the No Machine website for information on a Windows version of the server and found   
[ this]("http://www.nomachine.com/ar/view.php?ar_id=AR02D00349") post that mentions that version 4.x and beyond will support a Windows server.

This post also mentions something about accessing your terminal services in Windows from linux:

" By installing NX Client on the platform of your choice on your desktops and connecting through the NX Server installed on a Linux/Solaris box, to the Windows Terminal Server, you will be able to run your Windows applications remotely from your Windows machine."

I have no idea what this means?  Can anyone tell me if this is my solution to use "Terminal Services"?  I'll have to do some more research on this to see if this is what I'm looking for.

I've also found a forum for andlinux that I will subscribe too and ask them if they know if it's posible to install a freenx server in colinux to view an application running on the windows side.  

Later,

Greavette.

---

### Post by bodhi.zazen on 2008-01-22
Here is how to use RDP : [http://www.windowsnetworking.com/articles_tutorials/Using-Remote-Desktop-Windows-XP-Pro.html](http://www.windowsnetworking.com/articles_tutorials/Using-Remote-Desktop-Windows-XP-Pro.html)

You can connect from Ubuntu by running the Terminal Server Client :

See also : [http://www.linux.com/feature/54191](http://www.linux.com/feature/54191)

---

### Post by greavette on 2008-01-23
Wow bodhi.zazen,

You are a wealth of information.  Thank You for the links!

I'm still new to how freeNX works, but I'm getting a better understanding of what to do.  From the link I provided previously, I will use the FreeNX server in Colinux to remote into Windows XP Terminal Services (RDP).  I had thought that remoting into the FreeNX server on Colinux would allow me to see programs running on my XP side, but that's not how it works.  It would look like this:

 NX Client ----> NX Server ----> Windows Terminal Server

From the link you provided, tunneling to RDP using FreeNX would accelerate it as well.  Cool.  I'll give this a try.

Thanks,

Greavette.

---

### Post by bodhi.zazen on 2008-01-23
Best of luck, let us know if we can be of assistance.

Is it possible to go

Ubuntu (FreeNX client) -> direct Windows RDP server ?

---

