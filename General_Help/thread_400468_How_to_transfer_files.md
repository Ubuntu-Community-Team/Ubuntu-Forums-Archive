---
title: "How to transfer files"
date: 2007-04-03
forum: General Help
---

### Post by gil michael on 2007-04-03
hi,

i've just installed ubuntu on my computer.
i want to connect to a Linux server to get some files from there, but i don't know how to do that.
i mannaged to get the files using Windows XP OS (using a program named 'putty').

can someone help?

---

### Post by dannyboy79 on 2007-04-03
does the server run an ssh server? does it run an ftp server? is it a windows server that you know the username and password for it? please be a little more specific. I can help than. if you know the fully qualified domain name (ie: ubuntu.coolserver.org) or you know the ip. you can always nmap it to see what ports are open than we can figure it out from there also.

the sommand would be

nmap -P0 56.134.43.54

or 

nmap -P0 ubuntu.coolserver.org

this will take awhile. that is a ZERO after the "P". good luck and make sure you answer all my questions so I can help without having to ask them over again.

---

### Post by gil michael on 2007-04-03
hi,

as much as i know it is an ftp server. i have a username and a password. the domain is:

t2.technion.ac.il.

(when i use 'putty' in windows xp i mannge to connect using the command:
 open t2.technion.ac.il

and i manage to transfer files using:
get <filename> )

what is nmap?

---

### Post by dannyboy79 on 2007-04-03
you can use gftp then. if it's not installed (it would be under your pull down "start" menu, under networking), then go to synaptic package manager, under system , admin, then do a search for "gftp" then chose to install it. then once it's installed it should show up in your menu. then simply use it just like any other ftp client. good luck!!

---

### Post by gil michael on 2007-04-04
hi,

i installed gFTP, but still i can't connect.
how do i know which port should i use?

---

### Post by ewankho on 2007-04-04
I think the default port for FTP is 21.

---

### Post by dannyboy79 on 2007-04-04
that's if his server is listening on port 21. use the nmap command I have already informed you of to see what port the ftp is listening on since you know the server's domain name. actually I just did it myself. Here's what nmap returns


22/tcp  open   ssh
25/tcp  closed smtp
80/tcp  open   http
110/tcp open   pop3
113/tcp closed auth
143/tcp open   imap
443/tcp open   https
791/tcp open   unknown
993/tcp open   imaps
995/tcp open   pop3s


so it appears as though it MAY be running on port 791? you can also copy files thru ssh (port 22) using scp. the problem with that is I don't know how to transfer folders, only files. here is a guide for that. [http://help.ischool.washington.edu/faqs/14_32_en.html](http://help.ischool.washington.edu/faqs/14_32_en.html)

OR 
you can use gftp but use the ssh port. do this:
Steps to perform on the client system running gFTP
1. Start gFTP.

2. Select FTP, Options...

3. Select the SSH tab.

4. In the SSH2 sftp-server path: dialog box, enter the path to your sftp subsystem determined in the steps above. In my case, the path is /usr/libexec/openssh/

5. Click Apply.

6. Click OK.

7. Enter 22 in the Port: dialog box.

8. Change the value of the rightmost drop-down box from FTP to SSH2.

9. Enter your host, username, and password, and click on the connection icon.



GOOD LUCK and let us know how it goes and what you did.

---

