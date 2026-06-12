---
title: "Please help with aMule"
date: 2006-07-29
forum: General Help
---

### Post by seshomaru samma on 2006-07-29
I apt-get aMule but can't set it up
It doesn't come with a list of servers but offers to download it from [http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz) when i click download it starts downloading and then freezes. I downloaded the file with Firefox and tried to get aMule to take it from my home folder but it froze again. any advices?

---

### Post by loell on 2006-07-29
what's the output, when you execute it via terminal?

---

### Post by seshomaru samma on 2006-07-29
```
sesho@ubuntu:~$ amule
GTK Accessibility Module initialized
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Loading temp files from /home/sesho/.aMule/Temp.

All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /home/sesho/.aMule/Incoming shared

```

---

### Post by jeremy on 2006-07-30
You could try to close amule, then delete the folder; /home/sesho/.aMule
(it is a hidden folder), the try to start amule again.

---

### Post by mlind on 2006-07-30
You can use eMule server list(s) with amule. Just search 'emule server list' using google, and you'll find links to different server.met files.

---

### Post by seshomaru samma on 2006-07-30
Thanks but the problem is that amule freezes everytime it tries to download the server list whether its from the net or from my home folder.....

---

### Post by adamkane on 2006-07-30
It doesn't freeze, it just takes forever.

Use the Kademlia protocol, and press the update nodes button on the Kademlia tab (the little blue arrow that updates the Kademlia list).

It works friggin' great, but you gotta get comfortable with it. It doesn't function like any other program out there. You've tried the rest, now use the best.

If you have a router, you need to enable access to the correct ports. This is a whole other issue.

---

### Post by seshomaru samma on 2006-07-31
please look at my attachment screenshot to understand what I mean by freezing
It can stay like that for hours...
I tried running it after deleting /home/sesho/.aMule with similar results..
It happens with the Kademila protocol as well
when I try to download the server list I get this output in the terminal :
```
HTTP download thread started
Host: download.overnet2000.de:80
URL: http://download.overnet2000.de/nodes.dat
Response: 200 (Error: 0)
Download size: 3654
HTTP download thread end
```
then it just stays like that for hours (see the screenshot)

I'm no stranger to aMule - I've used it on Breezy before but then it came with a preconfigured servers list.

help......

---

### Post by mlind on 2006-07-31
amule version 2.1.1 [release notes]("http://www.amule.org/wiki/index.php/Changelog_2.1.1") mention a HTTP related fix
[LIST]
[*]Fixed the HTTPDownload dialog by using events rather than relying on being able to pause the main loop when sending notifications. Also properly aMulified the dialog.
[/LIST]

You can try if newer amule fixes this issue, see thread [http://www.ubuntuforums.org/showthread.php?t=224474](http://www.ubuntuforums.org/showthread.php?t=224474). 
If not, then it's something else.

---

### Post by adamkane on 2006-07-31
Do you use a router? Do you know whether you have enabled port forwarding?

---

### Post by seshomaru samma on 2006-07-31
Sorry ...double posting

---

### Post by seshomaru samma on 2006-07-31
All ports are forwarded just like they were when aMule ran on Breezy

It must be an HTTP related problem 

this is the terminal output when I try to get it to download the servers list from my home folder :
```
HTTP download thread started
HTTP download thread end
```
I will try to install the newsest version

Will it upgrade my current installation or will I have two versions of aMule on my computer?
If so , how do I install the first one?

---

### Post by mlind on 2006-07-31
> **seshomaru samma said:**
> All ports are forwarded just like they were when aMule ran on Breezy

It must be an HTTP related problem 

this is the terminal output when I try to get it to download the servers list from my home folder :
```
HTTP download thread started
HTTP download thread end
```
I will try to install the newsest version

Will it upgrade my current installation or will I have two versions of aMule on my computer?
If so , how do I install the first one?

It will upgrade your current version. If you want to rollback to earlier version after upgrade, use aptitude to downgrade
(or explicitly install Dapper's version: *sudo aptitude install amule=2.1.0-1ubuntu1*)

---

### Post by seshomaru samma on 2006-07-31
Couldn't install the amule deb file
It asked for libc6 dependency
Libc6 asked for tzdata
tzdata couldn't install because of error : broken cache...

such is life....

---

### Post by seshomaru samma on 2006-07-31
Here is how I solved the problem:
```
apt-get install --reinstall amule
```

:D

btw- my Kad status though connected is firewalled
can anyone tell me how to work it out (disabling my firewall didn't work)

---

### Post by mlind on 2006-07-31
> **seshomaru samma said:**
> Couldn't install the amule deb file
It asked for libc6 dependency
Libc6 asked for tzdata
tzdata couldn't install because of error : broken cache...

such is life....

You have installed something else that requires newer libc6. That's one library that you should avoid upgrading. If some package requires different version of libc6 package, it means it's been compiled with different toolchain. Simply put, not a package compiled for Dapper.

for kad protocol you need to open hole for tcp/udp port 4672.

---

### Post by adamkane on 2006-08-01
How are you connected to the internet?

---

### Post by gesho on 2006-08-11
I am havin similar problems.

just installed amule.

I get high connection ed2k and bunch of people uploading heavily from me.

it took ages for dismall download from 270 sources to start at a rate 1.3 kb/sec.

and Kad is running, connected but firewalled.

I enabled both tcp/udp on 4662, 4665 and 4667. I even allowed remote connection and webserver on tcp 4711 4712 (what is this feature).

Still, kad remains firewalled.

my connection is through wirelass gateway and all firewall allowances are made there. that is, I am allowing ports. I do not see any "forwarding" features mentioned here.

help appreciated

---

### Post by telperion on 2006-08-13
edit

---

### Post by brucewagner on 2008-01-14
> **seshomaru samma said:**
> Thanks but the problem is that amule freezes everytime it tries to download the server list whether its from the net or from my home folder.....

Everyone installing aMule from Ubuntu's Applications --> Add/Remove seems to be having the same problem...

Trying to download the server list using the default server.met file causes the program to crash (just disappear). 

I just found the fix posted by "testube_babies", here:  [http://ubuntuforums.org/showthread.php?t=505884](http://ubuntuforums.org/showthread.php?t=505884)

"Do you have servers in your server.met file?

Close aMule, wget this functioning server.met, then start aMule again:

```
cd ~/.aMule
rm server.met
wget --no-check-certificate http://mywebspace.wisc.edu/kpolicano/web/server.met
```

I had the same problem.  His solution worked perfectly.

Any word on the aMule people implementing this fix into their standard build included with Ubuntu's Applications-->Add/Remove...?

---

