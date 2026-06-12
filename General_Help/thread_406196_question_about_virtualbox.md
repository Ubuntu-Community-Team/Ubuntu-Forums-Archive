---
title: "question about virtualbox"
date: 2007-04-10
forum: General Help
---

### Post by toketin on 2007-04-10
hi, i have a question, i'm using ubuntu and i'd know if is it possible to copy a file from the virtual partition for example of windows on virtualbox to my ubuntu's partition??

---

### Post by pirothezero on 2007-04-10
That is a mighty damn good question, curious myself now.

---

### Post by jimbob on 2007-04-10
I would like to know how to add my second CDROM drive to Virtualbox.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

 *[SIZE="1"]... when the game is over the king and pawn go in the same bag ...[/SIZE]*

---

### Post by toketin on 2007-04-11
nobody knows how??

---

### Post by spankymasterc on 2007-04-11
i dont know if its possible with virutal box but i do it all the time with my vmware workstation..... this is what i do....

Share hardrive to my virutal machin (xp)

then copy what ever file i want and paste it in the shared hardrive and it shows up . then i can just get it trough ubuntu....

if you could share folder in virtual box then yes...

---

### Post by naseem on 2007-04-11
here there is something but it's not too clear to me how to go throught it...
[http://ubuntuforums.org/showthread.php?t=340113&page=8&highlight=virtualbox]("http://ubuntuforums.org/showthread.php?t=340113&page=8&highlight=virtualbox")

---

### Post by naseem on 2007-04-11
ok here how I managed it:

in the os guet window on top left clik devices and clik add guest additions
then open a terminal in the host "ubuntu"
```
 VBoxManage sharedfolder add "winxpsp2" -name "XP" -hostpath "/home/name_of_user/XP"

```
where winxpsp2 is the name I gave to my windows guset installed via virtualbox  XP is a folder I created in my home "in ubuntu" and this: /home/name_of_user/XP is the path to get to the XP folder

then on the XP guest open a prompt and type:
net use x: \\vboxsvr\xp

in your case just put the folder name you created

and if you don't see errors you'll find in computer resources a share folder connected connection pointing to your folder in ubuntu. it works just fine for me

---

### Post by jimbob on 2007-04-11
Naseem:  I tried following your post but here is the error I get -

> root@FF4:/home/jaspmatt/.VirtualBox/Machines# VBoxManage sharedfolder add "Vbox_XP" -name "XP" -hostpath "/home/jaspmatt/XP"
VirtualBox Command Line Management Interface Version 1.3.8
(C) 2005-2007 InnoTek Systemberatung GmbH
All rights reserved.

[!] FAILED calling aVirtualBox->FindMachine(Bstr(argv[1]), machine.asOutParam()) at line 5453!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true
[!] Result Code = 0x80070057
[!] Text        = Could not find a registered machine named 'Vbox_XP'
[!] Component   = VirtualBox, Interface: IVirtualBox, {e1d95593-f579-4f47-b489-0b67181014e1}
[!] Callee      = IVirtualBox, {e1d95593-f579-4f47-b489-0b67181014e1}


Vbox_XP is the correct name of the guest machine I created but for some reason it can"t find it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

 *[SIZE="1"]... when the game is over the king and pawn go in the same bag ...[/SIZE]*

---

### Post by raja on 2007-04-11
The manual of Vbox gives the detailed instructions. I could get it working that way. Another sort of hack (though inefficient) is to create a .iso from the files in Ubuntu (with mkisofs) and then mount it in Vbox as a cd. It is a quick way of getting some data there when you are having problems.

---

### Post by naseem on 2007-04-11
if the host name is correct than I don't know...it worked for me, but what I did was lounching the comand stright away, not as root and not in the .VirtualBox/Machines so maybe you can try that way or find out in the manual.

---

### Post by Olmen on 2007-04-24
Correct - you cannot be root while doing the above... It worked fine for me when I was just normal user.

---

### Post by jimbob on 2007-04-25
Hey thanks guys, I finally got it to work by doing it from my user account instead.   Now I have to figure out how to add my second CDROM drive.

---

### Post by mdurham on 2007-04-25
Why not set up a SMB 'shared folder' on Ubuntu and use the network? It works fine for me . I can access all my other drives from VBox through /media on Ubuntu.

---

