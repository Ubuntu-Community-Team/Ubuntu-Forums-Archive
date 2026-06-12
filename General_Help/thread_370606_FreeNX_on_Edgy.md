---
title: "FreeNX on Edgy"
date: 2007-02-25
forum: General Help
---

### Post by vav on 2007-02-25
how do I install freenx in edgy? 

I tried following two how-tos, including one with the seveas repository and one with the kanotix repository. Both refused to work (seveas doesnt have edgy packages, and the kanotix one says couldnt find packages.gz)  *frustrated*

What's the best way to do this?

Thanks

---

### Post by johnc4510 on 2007-02-25
tar.gz here:[http://freshmeat.net/projects/freenx/](http://freshmeat.net/projects/freenx/)

---

### Post by vav on 2007-02-26
That tarball is for gentoo... mentions some gentoo-nomachine.diff

---

### Post by babyhuey on 2007-02-26
Nomachine now keeps fairly up to date .debs for NX
If it were me, I would install directly from [www.nomachine.com]("www.nomachine.com") 

You'll want to download the NXClient, NXNode, and NXServer. I believe it has to be in that order, if you install with Gdebi it will tell you the order.
Make sure you have SSh installed too.
 
Here's the links in order
[http://www.nomachine.com/download-package.php?Prod_Id=27]("http://www.nomachine.com/download-package.php?Prod_Id=27")
[http://www.nomachine.com/download-package.php?Prod_Id=33]("http://www.nomachine.com/download-package.php?Prod_Id=33")
[http://www.nomachine.com/download-package.php?Prod_Id=3]("http://www.nomachine.com/download-package.php?Prod_Id=3")

---

### Post by vav on 2007-02-26
Ok... got the deb's from nomachine.com, then downloaded the client (version 1.5 since 2.0+ doesnt work as per the ubuntu wiki on freenx) on a windows machine and tried to connect... gets through authentication etc, but then doesnt pop up the desktop - after a while it just times out :(

Oh.. by the way, do I need to log off on the local machine before I try to remote login through freenx using the same user?

Also, my ubuntu doesnt handle 'switch user' too well -i.e. more than one user logging in to X causes problems. How would this affect the operation of freenx?

---

### Post by babyhuey on 2007-02-26
I'm currently using the 2.1.0-11 NXclient off of nomachines website. I can connect fine from my windows box and osx laptop. I'd stick with all up to date NX files. The freenx wiki may mean the new nomachine client won't work with an older freenx server.  

No you don't have to log off. In fact you can log on remotely while someone else is using ubuntu. As to the switch user problem, it shouldn't effect NX.

For good measure I would tunnel all traffic through port 22 by checking the box "Enable SSL encryption of all traffic" on the windows computer.
Make sure you have UNIX and Gnome or KDE selected on your client as well.

Did it ask you to accept an encryption key the first time you tried to login?

---

### Post by vav on 2007-02-26
This is what I had to do:

add to: /etc/ssh/sshd_config:

AuthorizedKeysFile      %h/.ssh/authorized_keys2
AllowUsers nx

restart ssh:

sudo /etc/init.d/ssh restart

run nxsetup:

sudo nxsetup

Then the nx server started. But still no access from the windows machine :(

---

### Post by babyhuey on 2007-02-26
Did you remove your previous freenx files before installing the .debs from Nomachine?
As far as i know nxsetup is not included with nomachine's .debs. Also, you do not need to edit your sshd_config to get this to work. I'm guessing that older guide has caused a conflict somewhere. I'd remove everything that you've done so far with freenx then install the nomachine .debs from scratch. 

Once everything is clean, use gdebi to install the .debs (aka double click on the debs) 
Verify ssh is still installed
 
sudo apt-get install ssh

there should be nothing else to do after that.

---

### Post by vav on 2007-02-26
Thanks babyhuey, that really worked. 
I guess Nomachine's free server makes freenx obsolete?

Thanks

---

### Post by jsgaarde on 2007-03-05
Not at all - last I tried the free server from NoMachine I could only have two user accounts enabled for remote login. And remember NoMachines free server is not open source and not GPL so not free as in freedom only as in "free beer".

---

### Post by Child of Wonder on 2007-03-08
Has anyone had any luck installing the debs from Nomachine on an AMD64 architecture?

The website says it's possible but simply running dpkg -i just fails because the package is i386.

---

### Post by vav on 2007-03-09
You could try alien to convert it to your system type... just a thought

---

