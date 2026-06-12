---
title: "What does this mean?"
date: 2007-04-18
forum: General Help
---

### Post by trents on 2007-04-18
I was trying to install the ati firegl 3d accelerator driver with Add/Remove in Ubuntu Ultimate 1.3. Got this error message:

W: Failed to fetch [http://ubuntusoftware.info/./xorg-driver-fglrx_8.33.6-1_i386.deb](http://ubuntusoftware.info/./xorg-driver-fglrx_8.33.6-1_i386.deb)
  302 Moved Temporarily

What does "Moved Temporarily" imply? Will it probably be moved back or is this a permanent situation? I know the community is in the transition between Edgy and Feisty. Does it have something to do with this?

Thaks, Steve

---

### Post by amohanty on 2007-04-18
From:
[http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)

I means that the server says, hey I moved this resource, heres where you can find it. Typically HTTP clients (like web browsers) are supposed to follow the response link and fetch the resource, as most do and firefox will if you click on the link. Apparently the client you are using does not. And so you may have to manually download it and use dpkg to install it.

HTH
AM

---

### Post by Askrates on 2007-04-18
I just tried it. Looks like it is there now!

---

### Post by trents on 2007-04-18
> **Askrates said:**
> I just tried it. Looks like it is there now!

Did you try it through the Add/Remove tool in the Applications menu? I just tried it again and got the same error message.

Steve

---

### Post by amohanty on 2007-04-18
As I mentioned before, its possible that the Add/Remove tool does not handle HTTP 302s properly. File a bug if you can for that. 

Just download the deb file. Open a terminal Application->Accessories->Terminal and type:

sudo dpkg -i /path_where_you_downloaded_file/xorg-driver-fglrx_8.33.6-1_i386.deb

hmm... didnt notice that you were trying to install fglrx. Try using synaptic System->Administration->Synaptic

HTH
AM

---

### Post by ph0neman on 2007-04-20
im having the same issue and i cant seem to snatch this file either... im actually using synaptic

---

### Post by amohanty on 2007-04-21
> im having the same issue and i cant seem to snatch this file either... im actually using synaptic

Synaptic shouldnt even be hitting any urls outside of those specified in /etc/apt/sources.list

Can you post the contents of that file?

AM

---

### Post by ph0neman on 2007-05-03
> **amohanty said:**
> Synaptic shouldnt even be hitting any urls outside of those specified in /etc/apt/sources.list

Can you post the contents of that file?

AM

heya amohanty

i would post the contents of the source.list but i have since attempted an upgrade to Feisty and it borked my box... so I reformatted and got it working. 

i wish i could have posted that... cause I used to get that error when attempting to update fglrx and glx

---

