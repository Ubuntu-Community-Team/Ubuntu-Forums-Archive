---
title: "Not sure what i need to do for the file sharing i want to do"
date: 2007-03-15
forum: General Help
---

### Post by inthepit on 2007-03-15
We desperately need a file server here at work. so i am taking it upon myself to set up a ubuntu server here.  i am going to install it on a P3 with a 40Gb harddrive.  but my main questions is do i need to set up a LAMP server or just a standard install with SAMBA.  all it will be for is for forms and documents that we constantly use and my boss wants everything in a central location so that we all use the same forms.  there will be 6 of us accessing this and 2 of us are the only ones that are really computer literate.  so i would prefers somthing that i can create a shortcut for on their desktops and they not have to log in or anything.  I would also like this to be read only access so that they dont overwrite any of the files.  there will be 6 windows pc's connecting to this linux pc and possibly 1 ubuntu machine.  hope someone can help.

thanks

pit

---

### Post by peabody on 2007-03-15
You should only need Samba, although how you setup Samba depends on your current Windows environment.  Domain or AD or none of the above?  These questions are important when setting up Samba.

Out of curiosity, why the PS3?  In a manner of speaking, there's cheaper computers out there :).

---

### Post by inthepit on 2007-03-15
its a pentium 3 not a playstation 3.

back on topic it we dont run on a domain or AD.  just windows workgroups.

---

### Post by peabody on 2007-03-15
My bad, I'm tired if you can tell :)


For workgroups you'll need to add users and then make sure they have a password with the smbpasswd command.  Passwords for samba have to be kept separate from the unix password for technical reasons (although there is a samba setting that can syncronize the two once the initial adding of a user to smbpasswd takes place).

---

### Post by inthepit on 2007-03-18
ok.  well set up a server with samba. and all runs perfectly...  i'll wait and see that i can still connect after the weekend.  glad i got this working...  saves everyone at work a lot of trouble.

---

