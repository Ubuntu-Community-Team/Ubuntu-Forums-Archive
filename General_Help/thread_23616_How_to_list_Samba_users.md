---
title: "How to list Samba users?"
date: 2005-04-03
forum: General Help
---

### Post by zardoz on 2005-04-03
Hy!

I just installed samba. Everything works fine. I can add users with smbpasswd and can browse those shared directories from my XP Box.
My question: How can I list all added samba users? smbpasswd does not have a list feature. And where are those users + passwords stored?
Some online resources stated, that there should be a file /etc/samba/smbpasswd, where users and passwords are stored. But on my system there isn't one, just the binary /usr/bin/smbpasswd.
Any help?

Greets

---

### Post by hagman on 2005-04-14
Hi,

Samba users and passwords are stored in /etc/samba/smbpasswd.
Just type "sudo cat /etc/samba/smbpasswd".

Cheers,

Helge

---

### Post by lee_connell on 2006-05-01
There is no /etc/samba/smbpasswd

---

### Post by Sniggi77 on 2006-06-22
[QUOTE=lee_connell]There is no /etc/samba/smbpasswd[/QUOTE]
If you use the tdbsam Backend, try "pdbedit -w -L" to get an smbpasswd-like output. Btw read the manual at [www.samba.org](www.samba.org)
ng, sniggi77

---

### Post by thatcooldude on 2007-06-12
On feisty, it'll be under /etc/samba/password/smbpasswd :D

---

### Post by markbnj on 2007-08-28
> **Sniggi77 said:**
> ...SNIP....if you use the tdbsam Backend, try "pdbedit -w -L" to get an smbpasswd-like output. Btw read the manual at [www.samba.org](www.samba.org)
ng, sniggi77


(I've been a SAMBA user since version 1.X, in the early-mid ninties).

I have just switched to uBUNTU, and (apparently )have the tdsam backend, but that command pdbedit -w -L  didnt give me anything except a help page.--need to do CAPITAL L!) doy...

What we need here rather then a RTFM, is a discussion of how the default ubuntu package deals with the tdbsam , as well as the default smbpasswd database

sigh...

oh, and if you aren't getting any response from smbpasswd

Try the pdbedit -w -L (L needs to be CAPITAL)

as well as looking in /var/lib/samba 
for the actual location of the database.

In my samba, it was already there, and I just needed to use pdbedit instead of smbpasswd to control the accounts

THIS NEEDS to be documented (here is a good example!) 
to make it easier for future folks to take care of .

hint: 

ubuntu Samba smbpasswd database shows blank or
where is  tdb database located on UBUNTU 

should index this as the correct answwer

Cheers!

Sorry for yelling...

(signed ...) someone with 16 years of unix/linux/ ADMIN experience that feels like a real newbie again!

3rd edit.

I went to my favorite (15 year old site) samba.org.

Here is the data I was looking at.

It discusses in GREAT detail a secure (= user) implementation of samba on a SUSE Enterprise Linux Server 8.0 server.

Certain changes are needed (someone needs to look at this...
example.. ubuntu commands for adduser vs suse command

NOTE HERE is the chapter from the samba website (chapter 3 secured network example)
[http://samba.org/samba/docs/man/Samba-Guide/secure.html](http://samba.org/samba/docs/man/Samba-Guide/secure.html)


This chapter needs to be customized  for ubuntu!
especially the parts that have the adduser/addgroup/deluser/delgroup scripts


(from my configuration, I discovered I already did have a tdb secure database configured, it was just that NO ONE around here bothered to mention that smbpasswd was useless, that the tdbedit command superceeded the smbpasswd command. (since it knows about how to change ALL password accounts, regardless of thedatabase store


-----------following examples in tne pageabove (chapter 3-secure) page  need to be updated for UBUNTU

Procedure 3.2. Samba Configuration Steps
(insert  apt-get commands for package instead of rpm...)


Example 3.4. 130 User Network with tdbsam [globals] Section
add/delete/etc scripts

Example 3.7. Script to Map Windows NT Groups to UNIX Groups

Step 4: 
Create the username map file

Step 6
One last step, without which you will not have a working Samba network environment. You must add an account for each network user!

step 7:
Using the preferred tool for your UNIX system, add each user to the UNIX groups created previously

Step 9:
Create the top-level file storage directories for data and applications as per the smb.conf directory points

Optional: create roaming profiles!
Step 10.

Step 11:
setup the login script (use net time as a basic script:
you can also copy the current def files to the target workstation.)


That should help ...
hope someone (else) can successfully make this updated guide for ubuntu.

ALSO:
Need to discuss ubuntu server vs ubuntu desktop as server base install.
verify command to add groups

---

### Post by markbnj on 2007-08-28
> **zardoz said:**
> Hy!

...Some online resources stated, that there should be a file /etc/samba/smbpasswd, where users and passwords are stored. But on my system there isn't one, just the binary /usr/bin/smbpasswd.
Any help?

Greets

Quick answer

see my discussion at end...

bottom line, you are likely using the pdb front end... and need to "ignore"
/etc/samba/smbpasswd

it iwll be in a file in /var/files/samba....

cheers

---

### Post by MacDuff on 2007-10-02
I cannot find the file smbpasswd despite having read all the above postings. 
Being a newbie, I have no idea what frontend nor backend I have (can't find the latter with both hands :D) but tried "pdbedit -w -L" and it produced a  listing with a huge bunch of XXXXXXs.  I can make out the user names and blocks of numeric characters among the XXXXXXs but I am wondering if this is what it should look like?  Can I delete anything in this file?  Will the file be rebuilt if I delete the entire contents? 

Can anyone shed light on these questions?

Thanks

---

### Post by SteveHillier on 2007-10-03
All this seems fine but it does not help with what I am trying to do.
I am trying to set up a domain server.
All my books and notes say you have to create both a ubuntu user and a smb user in order to make it work.  There are options in smb.conf to synchronise the samba password db with the user db.  The default smb.conf has a line for backend '   passdb backend = tdbsam'.
Does that mean that I should ignore smbpasswd and use tdbsam instead.
Hint, I am trying to get a script set up so that I can set users up in one process as an administrator without having to go through several processes (and then forgetting to do one of them!!).
Any clues would be useful

---

### Post by pcarr on 2007-10-12
Lost ! I am lost! I am working in a Windows small business network with 23 work stations and i Hate Windows! so I want to start using Ubuntu for some things. all is good and this could be possible but for one thing. I am using 7.04 and i have the network up and i can get into the Windows SB 2003 with no problems it worked perfect.  but i want to use this pc for an FTP site and i can't get any windows computer to open a shared file on the Ubuntu box i have worked on this on and off in my free time for 2 weeks and got to this point. Ubuntu Needs to look at small Business and have a good GUI for Samba sharing to a windows environment i can't change all of the pc's at one time i need baby steps. and this is a good start. I am a new to Linux and have no time or way to learn the "code" for using a terminal to do things.  frustrated rant pleas ignore have to get back to work windows broke again.  PS i love Ubuntu!:confused:

---

### Post by lee_connell on 2007-10-14
Have you used Places -> Network to browse the windows shares?

Also you want to set your workgroup or domain to be the same as the SBS server.

Click System -> Administration -> Shared Folders -> General Properties

---

### Post by nrasch on 2008-04-07
> **zardoz said:**
> Hy!

I just installed samba. Everything works fine. I can add users with smbpasswd and can browse those shared directories from my XP Box.
My question: How can I list all added samba users? smbpasswd does not have a list feature. And where are those users + passwords stored?
Some online resources stated, that there should be a file /etc/samba/smbpasswd, where users and passwords are stored. But on my system there isn't one, just the binary /usr/bin/smbpasswd.
Any help?

Greets

OK, here is what I'm doing to list the users, and I believe it answers the q's in this forum:

1. Go to the command line (term)
2. Enter in the following command:
<code>
sudo pdbedit -w -L | awk -F: '{print $1}'
</code>

That will list -ALL- the users w/out those ugly XXX characters.

Now, if you want to find a specific user you can do this:
<code>
sudo pdbedit -w -L | awk -F: '/nrasch/ {print $1}'
</code>

That would find the user nrasch is this example.

Want to send all that output to a text file for messing about with?  No problem:

<code>
sudo pdbedit -w -L | awk -F: '{print $1}' >> smb_users.txt
</code>

To learn more about AWK you can check out this URL here:  [http://www.vectorsite.net/tsawk_2.html#m1](http://www.vectorsite.net/tsawk_2.html#m1)

Like many on this board, I'm new and setting up SAMBA.  If anyone else has any questions I'll be happy to answer where I can.

Many thanks!
Nathan
__________________________

Want to learn Chinese?  [www.gatewaychina.net](www.gatewaychina.net)

---

