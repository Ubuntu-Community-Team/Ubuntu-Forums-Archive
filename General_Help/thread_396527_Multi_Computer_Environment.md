---
title: "Multi Computer Environment"
date: 2007-03-29
forum: General Help
---

### Post by axsvl on 2007-03-29
Hi, I am building a 10 computer network (It will be a free, after school homework center for inner city youth) and I want each user to have only one username and one password.

How do I make it so their username and password is available on all 10 machines? 

What is this username / password system called?

Do I need to use a specific software?

Or can I just copy the username and password information to all 10 machines manually?

Thanks,

Steve

---

### Post by Scunizi on 2007-03-29
You might want to look at Edubuntu.  It is set up for just this type of environment.  One computer will be a server and the rest will be pulling their information from there.  User names/passwords are held on the server and accessable from any of the machines.  There is lots more to this environment.  I suggest looking at [http://www.edubuntu.org/](http://www.edubuntu.org/).  One of the side benefits is the machines that the students use can basically be shells without a harddrive.  You do have to have a NIC card that will allow network booting.  They're cheep though and most current ones already will do this.

---

### Post by axsvl on 2007-03-29
I read about Edubuntu, it looks cool.  This is definately close to what I am looking for, but I have a couple of questions.

All 10 boxes are complete and functional.  None of them is fast, none of them are slow either.  They have 10 G drives and 1 G processors.  If they all boot off one machine, I think it may be slow with a lot of wasted resources.

Are my concerns valid?

---

### Post by Gordy on 2007-03-29
> **axsvl said:**
> I read about Edubuntu, it looks cool.  This is definately close to what I am looking for, but I have a couple of questions.

.  If they all boot off one machine, I think it may be slow with a lot of wasted resources.

Are my concerns valid?

What are you saying when you mean "boot off one machine?" 

You have 10 computers and each would have Edubuntu on them and would be networked to share files and printers. Is this what you want?

---

### Post by afoglia on 2007-03-29
Scunizi was describing a thin client solution where all but one of the computers would be nothing more than clients for the remaining.  All applications would run directly on that.  Simple, but if, as in your case, all the computers are comparable, a waste of resources.

The other option is to set up one computer as an LDAP server and bind the remaining to it for authentication purposes.  It's more complex to set up, but it should be what you want.

If you get that working, the next step would be to move all the users home directories to an NFS server so their files will be with them no matter what computer they go on.  You might need to buy a bigger hard drive for this purpose, but that shouldn't be too much.  Assuming you let the students save to their home directories, that is.

I've never set up either, so you'll have to start googling.  This result's directions looked simple and straightforward.

[http://www.debuntu.org/ldap-server-and-linux-ldap-clients](http://www.debuntu.org/ldap-server-and-linux-ldap-clients)

---

### Post by axsvl on 2007-04-03
Thanks for your answers - sorry it took so long to respond; I wanted to read more about it but I got absolutely slammed at work and have not had time to follow the link.

Afoglia, you seem to have grasped my problem very well.  I don't want a thin client solution; I want to maximize the resources we have. I need to research LDAP and bind.

One more question:

Should I use Ubuntu or Edubuntu?  I have the Ubuntu cd's here already, and I assume LDAP is in the Ubuntu package.  However, if Edubuntu is significantely easier to implement, then perhaps I should do that instead.

Ideas?

---

### Post by afoglia on 2007-05-05
Sorry for the late (and useless) response, but I've really only read about the problem, never did it myself.  (I was recently considering replacing the domain controller functionality of a Windows server with an extra Ubuntu box we have, but decided it wasn't worth the risk of screwing up an essential network to try.  And the NFS stuff is the way the computers at my grad school were setup.)  As for which Edubuntu vs. Ubuntu, I doubt it matters much.  I might be easier to start with Edubuntu for the extra packages, but there's no reason you couldn't start with Ubuntu and install any packages from the repository (start with edubuntu-desktop).  I'm not LDAP is standard in any flavor of Ubuntu, so either way you'll probably have to apt-get it.)

---

