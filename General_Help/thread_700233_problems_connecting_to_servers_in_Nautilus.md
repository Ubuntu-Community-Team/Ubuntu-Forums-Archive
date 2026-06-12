---
title: "problems connecting to servers in Nautilus"
date: 2008-02-18
forum: General Help
---

### Post by Peter_P on 2008-02-18
I'm a migrant from XP and am having problems connecting to remote servers. 
For example, 
from the Terminal I have no problem
ftp <server> followed by <name> and <password> all works fine.
In nautilus, 
Connect to Server
I select FTP with login and enter Server an supply a name and click Connect
this provides a link in the 'My Places' menu
I click on the link and get a window "Authentication required"
click 'Connect as user'
enter username and password (as previously done in Terminal)
click remember forever (or another option - it makes no difference)
and click 'Connect'
all that happens is that the same window pops up saying 'You must log in to <server>'
with the name filled in an password blank.

In summary, I know I have the right connection parameters because it all works in terminal with 'ftp' but I can't connect using Nautilus. The FTP example given is repeated when trying to attach to other types of server such as MS systems.

Any help would be greatly appreciated.

---

### Post by ryanhaigh on 2008-02-18
personally i do not use the connect to server method but rather just enter the address as in windows explorer perhaps you may have more luck doing it this way.

[ftp://username@serveraddress.com](ftp://username@serveraddress.com)
and put in the password info when prompted.

sometimes, but mostly for ssh:// for sftp:// i will have to put the username and password in a couple of times but after that it works well.

for samba/MS shares use smb://user@computername. strangely enough I just tried this on a server with public shares and it kept bringing up the authentication box seemingly because I am try to access as a specific user where none is needed, accessing a private share which did require auth didn't exhibit the same behaviour

---

### Post by Peter_P on 2008-02-18
Well - oddly, that is even less successful! I just get "Couldn't display <name@server>" check that your proxy settings are correct. 
When trying to connect with Nautilus, it does allow me to navigate the server when I reselect the link from a Nautilus window but when I try to, for example, edit a file, it pops up the "authentication required" dialog again.

hmmmm.

---

### Post by vagus on 2008-02-24
Hi,

I am having similar problems with connecting to ssh servers in Nautilus. I have tried connecting via 'Connect to Server' and it just keeps asking me for the password (the 'Authentication Required' box keeps coming back if I try to open the ssh folder). 

If I try to connect via the address line inside Nautilus (ssh://username@address) then it gives me the message "Nautilus cannot display...... Please select another viewer type..."

I have tried deleting known_host file, but no use. I can connect fine via the shell, so I know the servers etc. are at least working. I would find it useful to connect via nautilus to move/copy various files. 

Any help will be greatly appreciated :-)

---

### Post by augias on 2008-06-23
I thought i'd bump this thread in the hopes that someone might be able to offer a solution. (This is my first post, be kind) 

I'm on 8.04 hardy heron and installed the curl and curlftps repo a few minutes back, if that info is any help. 

I'd really like to use nautilus to browse my ftp servers but it simply won't click: I choose "Connect to server..." and pick *ftp (with login)* on the drop down menu; I type in the simple web address (eseme.cl) and the username, expecting to be prompted for my password later. Then i invariably get the error message 

can't display location "ftp://username@eseme.cl/" Invalid reply

So, what's up. Am I doing something wrong?

Fernando
:popcorn:

---

### Post by ftmichael on 2008-06-26
I don't know about the FTP issue, but for more general Connect to Server issues in Nautilus, particularly the timeout error, see [http://ubuntuforums.org/showthread.php?t=554555](http://ubuntuforums.org/showthread.php?t=554555) . The advice in that thread fixed the problem for me, but interestingly it didn't help on my boyfriend's computer at all, even though we have the same setup. Still trying to figure out what the issue is on his system.

Michael

---

