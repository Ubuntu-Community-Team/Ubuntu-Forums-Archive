---
title: "aMule doesn't load servers list"
date: 2005-08-03
forum: General Help
---

### Post by frank_b on 2005-08-03
Hi all. Great OS.

I've just installed aMule and when I run it and press the button to update the servers list I get the message "Failed to download the server list from http://www.srv1000.com/azz/server.met" (and the program doesn't explain why)...

I'm, obviously, connected to the Internet.

When I run the program it also shows (when it starts) two other error messages:


something like "/.xMule/Temp directory couldn't be created (error 2 no such file or directory)"

and

"failed to get file system statistics (error 2 no such file or directory)"...


About the first message: I've tried and uninstalled xMule before I installed aMule... could that be causing any trouble?...


I've used aMule in another linux distro before this one and it didn't give me any trouble...


Any help would be much apreciated.

Thank you in advance.

---

### Post by frank_b on 2005-08-04
UPDATE


The two error messages at start still appear, but now I can already update the servers list, I'm able to connect to one of them and make a search. (don't know why... I haven't done anything but to restart the computer today...)

The problem is that, when I choose to download a file it gives me the same error as in the second error message at start,


"Failed to get file system statistics (error 2: No such file or directory)"


and the file doesn't download.


(aMule Log)

2005-08-04 16:24:44: Saving of server-list completed.
2005-08-04 16:24:59: ERROR: Failed to create part file
2005-08-04 16:24:59: ERROR: Failed to open partfile)
2005-08-04 16:24:59: ERROR while saving partfile: .part file not found

---

### Post by frank_b on 2005-08-04
UPDATE 2


Yeahhh! :)

I suspected this to be some kind of problem in configuration files because of the previous one (configuration) that existed for xMule, so I decided to look for some sort of "left-over" xMule files and to take a look at the aMule ones.

Didn't find any xMule ones (I had deleted even the hidden ones in my home folder) but I then found a file named "amule.conf" and decided to take a peek at it and found some "xMule" configurations still(?) there. (I suspect that when aMule installed, it decided to keep the previous eMule client configurations then...)

All I have to do then, I guessed, was to change (or adapt) the specific xMule configurations to aMule ones and, hopefully, this will make it work.

And it did! :)

I am happily now already downloading a music file and everything seems to be "OK". :)

In case someone has the same problem: what I did was to change the "Incoming" and "Temp" directories from "/.xMule/..." to "/.aMule/..." and (I don't think this is important) the web site from "www.xMule.ws" to "www.aMule.org" in the configuration file.


PROBLEM SOLVED!  ;-)

---

### Post by krige on 2007-06-20
I am facing the same problem: aMule can't load a server list, either at start up or manually from the Network/ED2K Servers address bar. I always get the error:

"Failed to download the server list"

The address of the servers list loads fine inside Firefox.
The Incoming and Temp directories are correctly set in the aMule.conf file.
I have already opened the needed ports both in the router and firewall settings and I am already getting an high id.

I don't know what to do to solve the problem.
Could it be due to some firewall setting?

---

### Post by Hallvor on 2007-06-21
You don`t need to download a server list at all. (I only have 4-5 servers in my list, and you only need to connect to one of them to be able to get results from all the others on a global search.) Just add the servers manually on the same page. You only need the IP and port number, and click "add server" if I remember correctly.

[http://www.gruk.org/list.php](http://www.gruk.org/list.php)

This list is safe and has no fake MPAA servers. I mostly connect to the three largest on top of the list.

Be careful with adding large lists found on the internet, unless you just add a few safe ones to your static server list with a right click, and then choose "only connect to static servers" in the options menu.

---

### Post by efe on 2008-01-05
Hallvor

i ad one of the server's manually, like you said, and just like magic another 26 appeared ...

Everything is working perfectly.
Thanx

---

### Post by Hallvor on 2008-01-05
OK. I recommend going to Preferences -> Server and untick the Update Serverlist boxes, as you are bound to get fake servers that way. It is better to add the servers you want manually, imho. Good to hear that it works, though.. :)

---

