---
title: "Ideas For Setting Up a Single PC Internet Station for Public Use"
date: 2007-06-21
forum: General Help
---

### Post by mtn on 2007-06-21
Hi,

I would like to set up a single PC internet station for public use in a small hotel. I am trying to figure out the best way to do this and would really appreciate thoughts people might have.

I'm not sure at the moment whether to have the PC as an internet only (i.e only access to a web browser) or more of a mutli purpose station (access to Open Office, xpdf, aMSN, Google Earth, calculator etc). Part of the reason I would rather not just lock users to a full screen Epiphany, using for example Pessulus, is I would like people to have a chance to have a play with Ubuntu and experience  Beryl etc.

What I envisage at the moment is a locked down desktop so data cannot be saved to the system but the applications mentioned above can be used - for example to read a .doc linked to in a web page.

I was thinking one way of approaching might be to refresh the system every time a guest user logged in. People could be reminded to log out once they have finished and then the system would atomatically log the guest user back in and in the process delete and restore with a configured backup copy all the folders/files in ~/home.

It would also be very useful to keep a log of all URLs accessed. I have looked at squid but didn't get that far really.

I'm not sure what the best, most secure and easiest way to set up a public use PC is so I would be really interested in any ideas about how to approach this and specifically how to implement a solution.

Cheers

---

### Post by panso on 2007-06-21
I have no experience of this but one configuration seems to lend itself to a kiosk based machine that auto refreshes on logout.

How about a flash based box? i.e. no hard drive.

One flash based drive for the OS and another flash for /home.
On logout the /home refreshes in a few seconds and the user only has write permissions to the /home flash.
This means of course a fast user experience, security and also its less cpu/power hungry. Even more importantly very low maintenance as flash is less likely to fail that hd.

The /home flash could be 1-2Gb allowing users to download docs/videos etc and create content. Regular users might even be given a script to store their home to their own stick which they could bring with them. 

The additional benefit would that you would be able to easily reconfigure the system by replacing the flash with own you 'prepared earlier' of a usb stick. In theory should make it a snip to reconfigure. All you need is an area on the file system that replaces/updates the current flash on reboot. I say a snip, but its probably a lot of work to make it seamless :)

Panso

---

