---
title: "cant install vmware server"
date: 2007-02-20
forum: General Help
---

### Post by enterhades on 2007-02-20
hello... 
i am usin ubuntu 6.06.. i had vmware server1.0.1 installed in my system for a while now.. then today i discovered i cant open it anymore.. so i tried re-installin.. then it comes up wit: 

[INDENT]# ./vmware-install.pl

Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

The file /etc/init.d/vmware that this program was about to install already
exists. Overwrite? [yes]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.[/INDENT]

i tried deletin /etc/init.d/vmware directory.. same thing happens.. does anyone knw about this error?
many times before i had re-installed the vmware. never had this [or any] kinda error.. i had done a few security updates 2 days bak.. ther was no other alterations done in the system other than tht.. 
help!! 

thanks a lot.

---

### Post by yabbadabbadont on 2007-02-20
Try this:
Run the uninstall script.
Remove the /etc/vmware directory.
Remove the directory to which you extracted the vmware tarball.  (it is called vmware-server-distrib in the tar archive)
Re-extract the vmware-server tarball.
Run the installation script.

Apparently, the vmware install saves some changes into the directory where you initially extract the tarball when you run the installation script.  Others have had success by removing that directory so that they were starting from a completely clean source.

---

### Post by enterhades on 2007-02-20
i tried all those instructions.. no luck :( am gettin the same messages...

---

### Post by zvacet on 2007-02-20
Did you get kernel update?If you do you have to reconfigure server.Second option is to manualy delete every vm server file in all directories they can be.Chek var,tmp,etc,home...
That´s all crossing my mind right now.

---

### Post by veloce on 2007-02-20
Hate to ask, but you are running the installer as root, yes?

---

### Post by enterhades on 2007-02-20
yes i got the kernel update.. i tried manually deletin most o the vmware files i cud find.. 
n yes im runnin as root :)

---

### Post by enterhades on 2007-02-20
...but still no luck :(.........

---

### Post by veloce on 2007-02-20
Well I for one am scratching at straws on this one.  Going back to the error message:

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware

There are two questions:
Does the file ./installer/services.sh exist?
Is there anything in the directory /etc/init.d/vmware

Try copying the file manually:  cp ./installer/services.sh /etc/init.d/vmware
Does it work?  If not, what error do you get?

---

### Post by enterhades on 2007-02-22
it was quite a small error on my side.. :-| i had to be in  the folder of vmware-server-distrib myself to runt he installer.. totally forgot that..! thanks to veloce's question.... :)

so tht helped me in installing the vmware server, then i configured it, but then again i had the initial problem of the software not opening... somehow i was gettin various error lik kernel source files do not match etc.. 

after rebootin n tryin for a few mre times.. SOMEHOW it jus started workin normally.. :-| i hadnt tried anythin diff.. but again rt now, i can open the vmware only thru console n not thru the menu.. 

thanks for the support.. :) n i am really sorry for the inconvenienc, guys!

---

### Post by enterhades on 2007-02-22
but again.. updates do make a few such problems..?

---

### Post by veloce on 2007-02-22
You're welcome. 

And BTW, it's by no means the silliest question I've answered on this forum, nor is it as silly as some I've asked!

---

