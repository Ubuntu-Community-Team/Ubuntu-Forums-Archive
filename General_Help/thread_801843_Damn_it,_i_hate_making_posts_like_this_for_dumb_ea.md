---
title: "Damn it, i hate making posts like this for dumb easy tasks (Sharing a USB device) but"
date: 2008-05-20
forum: General Help
---

### Post by DJSchmidty on 2008-05-20
Ok, so what i'm trying to do is just make a simple sharing folder be able to be seen in ubuntu, windows, mac, all of the above....

I know that you have to do something with 'samba' and i've read a few tutorials that i found on here, and on google, but I just CAN"T get it to work.  (Once again, i'll just let this out, i'm a voncerted windows guy, and I just want to know how to do very simple things, like share a folder on a local network, for storage and etc.)

I'm trying to setup a dummy 'office' in my basement, and learn how every function works, because I have alot of people that I do IT stuff for, and they all use crappy windows, and all hate it.  I showed a few of them ubuntu and they couldn't believe how much better it was.  SOOOO what i'm trying to do is make, almost a showroom, but like a working living breathing 'office' of my own, hopefully including even a server that will do the following: print, file, dhcp, dns, and maybe mysql.

Could someone let me know if this is not the right way to go?  I chose kubuntu not only because of its windowish setup, but also it just seems to have the look that people who have NEVER used ubuntu or even linux for that matter could sit down and figure it out in a matter of minutes.

I'd like to run kubuntu on all of the machines, even the server just to keep it consistant, i'm only a week old user of ubuntu, so i'm learning very slowly, but every day so far i've put in about atleast 3 hours a day trying out new things, and learning terminal commands, and such.

So yea, thats it..
Thanx in advance!
-Schmidty
"I hate windows"


Oh shoot, PS!  I would like the server to backup to either a tape drive, or an external usb drive, which I have attached right now, but how do I know if its mounted automatically?  I check the box that says 'mount automatically' but to be honest, i'm not even sure why I have to 'mount' anything, i don't even know what it means!!!

---

### Post by HermanAB on 2008-05-21
Well, the problem is that sharing a folder using Windows Networking (Samba) isn't simple.  The best user guide is on the Samba web site and there is one specifically for Ubuntu too.

If you want a simple way to share folders, then you have to use FTP.  Vsftp and proftp are both good and they are in Synaptic and they work out of the box.  Pick one, install it, start it and have fun.

Cheers,

Herman

---

### Post by theytookpenny on 2008-05-21
I think a very simple way, but probably not the way you're looking for, is to simply chmod the folder's permissions to 777 from the computer where you created it. The folder will accessible on all computers. You may want to chmod the other files/folders to make them only accessable to the owner by chmoding it to 700. These folders will still be visible, but inaccessable by other computers.

---

