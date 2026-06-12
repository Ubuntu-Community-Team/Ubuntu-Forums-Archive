---
title: "VMWare installation problem."
date: 2005-03-24
forum: General Help
---

### Post by wk1989 on 2005-03-24
Hi, when i'm try to install vmware 4.5, i get this. Can you tell me how to fix it??? This is urgent!
Thx!!!

> 
What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.


---

### Post by soul_rebel on 2005-03-28
vmware install has worked for me, try to cd to the directory before running the script

---

### Post by kassetra on 2005-03-28
[QUOTE=wk1989]Hi, when i'm try to install vmware 4.5, i get this. Can you tell me how to fix it??? This is urgent!
Thx!!![/QUOTE]

Are you running this install with "sudo" ...?

---

### Post by pinecone on 2005-04-03
[QUOTE=kassetra]Are you running this install with "sudo" ...?[/QUOTE]
 I'm having the same problem.  I am running with sudo

---

### Post by kmf on 2005-04-04
It worked fine for me
"sudo su"
then ./vmware-install.pl
I have a issue building vmmon :(

Any ideas
I have installed the headers

Karl

---

### Post by Zyko on 2005-04-09
I'm Here:

(At the vmmon module)

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


I have no idea where my kernel-header files are, anyone got an idea?

Edit: My first post by the way :)


Alright. EDIT NR 2..

Solved it.
 
  What i had to do were to install the kernel packade 

I have '2.6.8.1-5-386' version of my kernel.

So i downloaded that with synaptic, then i used the directory:
 
  /usr/src/linux-headers-2.6.8.1-5-386/include

-.. Hope this can help you other guys =)..

(And yes, my description were terrible)

---

