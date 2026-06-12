---
title: "Update fails to get several indexes"
date: 2007-03-13
forum: General Help
---

### Post by rabid emu on 2007-03-13
When I run aptitude update, this is what I get as output:

> kevin@EMU2:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg (191B)
Get:2 http://ubuntu.beryl-project.org edgy Release.gpg (191B)                                             
Ign http://ubuntu.beryl-project.orgedgy/main Translation-en_US                                                                                                
Hit http://ubuntu.beryl-project.org edgy Release                                                                                                               
Hit http://ubuntu.beryl-project.org edgy/main Packages                                                                                                         
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                                                                            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                                                                                      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                                                                                        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US                                                                                      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                                                                                        
Hit http://security.ubuntu.com edgy-security Release                                                                                                           
Hit http://security.ubuntu.com edgy-security/main Packages                                                                                                     
Hit http://security.ubuntu.com edgy-security/restricted Packages                                                                                               
Hit http://security.ubuntu.com edgy-security/main Sources                                                                                                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                                                                                                
Hit http://security.ubuntu.com edgy-security/universe Packages                                                                                                 
Get:3 http://security.ubuntu.com edgy-security/universe Sources (3786B)                                                                                        
Hit http://security.ubuntu.com edgy-security/multiverse Packages                                                                                               
Hit http://security.ubuntu.com edgy-security/universe Packages                                                                                                 
Err http://us.archive.ubuntu.com edgy Release.gpg                               
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Fetched 3978B in 44m0s (2B/s)                          
Reading package lists... Done
I've been running Edgy for several months with no problems, and then recently this started happening.  Not sure why.

Here's my sources.list
> deb http://us.archive.ubuntu.com/ubuntu/edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

Any idea what's going on and why is fails on everything from us.archive.ubuntu.com?

---

### Post by llamakc on 2007-03-13
Remove the "us." from the lines in your sources.list file. Reload Synaptic or rerun `apt-get update`.

---

### Post by rabid emu on 2007-03-13
Not working.  Thanks for trying though.

---

### Post by Kateikyoushi on 2007-03-13
Changing the http to ftp in the addresses seems to work.

---

### Post by rabid emu on 2007-03-13
I changed every http:// to ftp:// in my sources.list.  Still getting the same problems.

I should mention that I DO get upgrades this way.  Updating just takes 45 minutes and it always shows those errors.  I might be missing some upgrades.

---

### Post by Kateikyoushi on 2007-03-13
Another thign which used to work is to change the us. to ca. could give it a try.

---

### Post by rabid emu on 2007-03-13
Interesting, it progressed further using the ca mirrors.  I got 2 new updates that I didn't have before.  However, it still started giving me the same error about 'connection timed out to archive.ubuntu.com'

---

### Post by rabid emu on 2007-03-13
bump, because I really want to figure out this problem.

---

### Post by Pikestaff on 2007-03-13
Not sure if this will help or not, but check your internet connection and make sure that your DNS and Gateway aren't the same thing... I had a similar problem once (not exactly the same, but similar) and it ended up being because the DNS and Gateway were set to the same thing and I had to change my DNS to one from [OpenDNS]("http://www.opendns.com/start/ubuntu.php") in order to get it to work.

---

### Post by rabid emu on 2007-03-13
I have it on DHCP for my school's network.  Maybe they're blocking the connection somehow?  I've had Ubuntu at school before and it's never had a problem, so I don't know what would change for them to be causing it now, though.

---

### Post by rabid emu on 2007-03-13
Something else I just noticed, that might be important.  I run Firestarter, and I noticed that in the list of blocked connections is a bunch from canonical that pop up whenever I update (duh).  I tried allowing those connections but it still isn't working.  Is there an option in firestarter to allow all connections from a source, like Canonical, to any port?  And is this a good idea, since it seems rather insecure to me?

---

### Post by rabid emu on 2007-03-14
bump once again...

---

### Post by Kateikyoushi on 2007-03-14
There is a [http://ca.archive.ubuntu.com/](http://ca.archive.ubuntu.com/) as well could use that.

---

### Post by noobuntoo on 2007-03-14
same thing here. glad im not the only one.

been running update manager the same way with the same connection with the same sources.list successfully for a while, and then suddenly bam, failed trying to connect to that website.

on top of that, the latest kernel wont load. progress bar freezes before it even moves and then im staring at a black screen with a cursor blinking unable to type anything. ah well, at least the kernel before it loads.

why does it do that? ive had this happen before. i realize feisty is prone to bugs, but no error message? surely some programmer for ubuntu can write up something to give a text message when ubuntu fails to load, instead of just sending me to a black screen where i cant do anything and have no information.

---

### Post by rabid emu on 2007-03-14
Perhaps you should start a new thread for your kernel problem in the feisty section, I bet you can get some help there.

---

### Post by rabid emu on 2007-03-14
*sigh*

No one has any idea?  This is a very annoying problem.  Just today I tried installing something with synaptic and it couldn't because it was missing the necessary package index.

---

### Post by FidalgoMike on 2007-04-10
FWIW, I installed Firestarter a while back, and started noticing hits in the event log from two IPs that trace back to Canonical.
They would occur in a block around 0740-0750 pacific. If I stopped the firewall, apt-get, aptitude, synaptic would all work fine.
If I turned the firewall back on, the updates fail. For some reason, they fail even if I say allow connection from those two IPs in Firestarter.

Things that make ya go hmmmmm. . .

---

