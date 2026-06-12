---
title: "How To Access Windows Files With Ubunto"
date: 2008-05-26
forum: General Help
---

### Post by ColTom2 on 2008-05-26
I have Ubunto 8.04 installed using WUBI. How can I access my Windows XP Pro Shared Documents and also my Windows Hard Drive (Operating System) Data.

I played around and finally got my Windows Shared Documents on my Ubunto desktop, only to have some way deleted them and now I can't seem to get them back.

I have never been able to access my Windows Hard Drive data.

If anyone has the answers I would be most appreciative.

Thanks....

---

### Post by sweeneytodd on 2008-05-26
might be a mounting problem, so you can't see the windows drive from "places" on the menu bar, i can see mine and go into it know problems, mind you win pro might have some security thing where secondly you could boot pro and disable whatever you can as far as hard drive security is concerned

---

### Post by ColTom2 on 2008-05-26
I at one time could go to Places>Network>Windows Network> and click on it and it would bring up a MSHome icon which would allow me to access shared files. I had to install some update packages with Synaptic Package Manager to be able to see MSHome etc.

But as I say I have done something to where I no longer can access these Windows shared folders and would like to restore them.

---

### Post by DinCahill on 2008-05-26
If you go to the folder /host, you can access the Windows drive Ubuntu is installed on. Shared stuff is in Documents and Settings somewhere.

---

### Post by ColTom2 on 2008-05-26
I know where Ubunto is installed in Windows XP Pro. That is not my question.

My question is how can I reaccess Windows shared folders and also Windows OS data while in Ubunto.

---

### Post by wijotoma on 2008-05-26
tried the following in the terminal window:

sudo aptitude install libdvdcss2

and then

gksu ntfs-config

---

### Post by sweeneytodd on 2008-05-26
my knowledge has come to a halt, but, next thing i would try is starting the live cd up as by the sounds you installed ubuntu on your pro partition, and that may be causing issues with folder protection or something, I seriously doubt you will have issues with the live cd

---

### Post by wijotoma on 2008-05-26
hey i had the same problem, look what i did is the following:

enter filesystem, then host, and maybe there are your files

---

### Post by ColTom2 on 2008-05-26
No candidate found for when I ran your command for that package.

I sued WUBI to install Ubunto and it's installed within a Windows Folder and not partitioned etc.

---

### Post by sweeneytodd on 2008-05-26
live cd didn't work?

---

### Post by ColTom2 on 2008-05-26
I have no idea what Live CD is, as I have never had a CD for the Ubunto 8.04 installed with WUBI. Downloaded everything from the web and have never had a CD per se for this installation.

You might bring me up to date on the term "Live CD".

Thanks

---

### Post by ColTom2 on 2008-05-26
I have no idea what a "Live CD" is, as I installed Ubunto with WUBI with download from website.

You might enlightened me more.

Thanks

---

### Post by sweeneytodd on 2008-05-26
yeah right, live cd is ubuntu on disk that can be run from the cd also, so i'm thinking if u had it u could theoretically run ubuntu from the cd and any issues with ur other installation wouldn't be an issue, if you have a p2p program, search "ubuntu 8.04 i386" the download is 600+mb so i don't know if this is any good

---

