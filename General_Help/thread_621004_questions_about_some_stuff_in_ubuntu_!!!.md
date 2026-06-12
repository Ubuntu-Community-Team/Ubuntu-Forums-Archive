---
title: "questions about some stuff in ubuntu !!!"
date: 2007-11-23
forum: General Help
---

### Post by Amebaid on 2007-11-23
right his moment i'm running win 2000 and burning ubuntu [downloaded yesterday] 
so i'm wondering about few stuff , simple , may be already answered in the faqs [so forgive me if it is ]

how much space does the installation need ?
will i have any troubles in mounting NTFS on it ?? [Old Open Suse user]
and about the locales .. does it support Arabic and other herbew languages ?

i'm sure i'll be having lots of questions .. 

but the first on is the more imprtant one as it'll start every thing else 

how much space does i need and what is the best portioning for it 
regarding i'm installing windows on 10 GB C: drive 

thanks ..

---

### Post by banewman on 2007-11-23
Are you dualbooting windows and ubuntu?
Doing that on a 10 gig drive I'd recommend you have 4 gig for ubuntu - 500mb for swap and the rest for your windows.
If you had more space I'd recommend having a  partition for /home - if you need to reinstall most of your settings will be saved. :)

---

### Post by mellowd on 2007-11-23
I know of a ubuntu muslim edition of you're looking for a complete muslim overhaul complete with languages and everything.

But if you just wanted the interface in arabic with normal ubuntu that isn't a problem

---

### Post by Amebaid on 2007-11-23
> **banewman said:**
> Are you dualbooting windows and ubuntu?
Doing that on a 10 gig drive I'd recommend you have 4 gig for ubuntu - 500mb for swap and the rest for your windows.
If you had more space I'd recommend having a  partition for /home - if you need to reinstall most of your settings will be saved. :)

no you got me wrong i meant that i'm installing windows on 10 GB C: drive ,, i've over 150 GB free for anything else 

so can you please give me the instructions for the /home type installation 

i've acronis CD ready to work .. 

thanks

---

### Post by Amebaid on 2007-11-23
> **mellowd said:**
> I know of a ubuntu muslim edition of you're looking for a complete muslim overhaul complete with languages and everything.

But if you just wanted the interface in arabic with normal ubuntu that isn't a problem

well i don't want the interface to be in arabic .. i just wanna be able to read files which names written in arabic and the system identify them 

yet if you have a link of that edition that would be good 

thanks

---

### Post by mellowd on 2007-11-23
[http://www.ubuntume.com/](http://www.ubuntume.com/)


I haven't tried opening an arabic document in normal ubuntu but to be honest I don't see any reason why it wouldn't open and display. At most you might need to just add the fonts

---

### Post by Amebaid on 2007-11-23
well . i've allready faced that problem with open suse and it reallt made me turn back to windows .. 
but i hope that it can work good on ubuntu

---

### Post by banewman on 2007-11-23
There is a good partitioner on the live cd - gparted. Only one I use.
With that space I'd make a 10 gig partition for ubuntu, 1gig for swap and make /home as large as you need it.
To read ntfs you will need to install a program -   ntfs-3g
Write support to ntfs isn't great as windows won't give out how the file system works...
but the windows volume will be mounted if it is installed before you install ubuntu. :)

---

### Post by Nunu on 2007-11-23
I currently run a dual boot between ubuntu and windows and so far i have had no issues connecting to both my NTFS partitions from ubuntu... It worked straight out the box

---

