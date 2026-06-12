---
title: "Ubuntu with 1GB RAM can't access https://uobcyberbanking.com but SLAX can?"
date: 2007-09-21
forum: General Help
---

### Post by anchalee on 2007-09-21
My notebook is Lenovo Thinkpad R60 with Ubuntu 7.04, kernel 2.6.20, 1 GB RAM  (512 MB x 2 slots).  I used Firefox 2.0.0.6 and I tried to access [https://uobcyberbanking.com](https://uobcyberbanking.com). It showed an empty page and the status bar showed "Waiting to uobcyberbanking....". Then I tried to access the website by Konqueror, Ephiphany and IE4Linux. They have the same problem. 

Then I tested by take off a 512 MB of RAM because I suspected the amount of RAM may cause the problem. Then I tried to access [https://uobcyberbanking.com](https://uobcyberbanking.com) again, and it's work. Then I tried to access this webpage on many other computers (such as Desktop PCs and Lenovo Y400 with 1 GB of RAM). It still didn't work. I thought it maybe because of RAM or SSL.

I tested it again by a PC with 1 GB of RAM. I used Ubuntu 7.04 LiveCD to boot and tried to access the UOB webpage again, but it didn't work . Then I tested again by booting from SLAX 5.1.8 (kernel 2.6.16), and it's work. Maybe something that is different between the two distros cause the problem.

Any idea?

---

### Post by PreviousN on 2007-09-21
RAM should't affect the ability to go to a website. The only case that I could see it affecting it is if firefox/whatever *crashes*. 

You might have a problem with your ubuntu machine getting proper dns. I'd suggest opening a terminal and typing "ping google.com" if you don't get a reply then that suggests improper configuration. In that case, cliick on the network looking icon in the upper corner and go to manual configuration. Make sure the device you are using (eth0 or eth1 most likely) is set to dhcp. That should help you out a bit. 

BTW: i used to use slackware and to get internet working you had to type "dhcpcd eth0" (or eth1) to work on it. 

Essentially waht I'm saying is that you may have typed that in on slackware but not in ubuntu. Because ubuntu is all guiey it may not have dhcp set by default.

---

### Post by dcstar on 2007-09-21
> **anchalee said:**
> My notebook is Lenovo Thinkpad R60 with Ubuntu 7.04, kernel 2.6.20, 1 GB RAM  (512 MB x 2 slots).  I used Firefox 2.0.0.6 and I tried to access [https://uobcyberbanking.com](https://uobcyberbanking.com). It showed an empty page and the status bar showed "Waiting to uobcyberbanking....". Then I tried to access the website by Konqueror, Ephiphany and IE4Linux. They have the same problem. 

Then I tested by take off a 512 MB of RAM because I suspected the amount of RAM may cause the problem. Then I tried to access [https://uobcyberbanking.com](https://uobcyberbanking.com) again, and it's work. Then I tried to access this webpage on many other computers (such as Desktop PCs and Lenovo Y400 with 1 GB of RAM). It still didn't work. I thought it maybe because of RAM or SSL.
.......
Any idea?

Chances are it is using an encryption algorithm not installed by default in Ubuntu - all you need to do is find out what that particular site requires and then how you can get it to run in Ubuntu.

I have seen this before with sites that use ancient (and insecure) encryption, Ubuntu doesn't use the obsolete methods but some other distros may still have them available.

---

### Post by samphan on 2007-09-24
We've done a lot of test with combinations of RAM size, PCs/Notebooks, browser and OS.
[LIST]
[*]Windows with 1G or 512M RAM - work
[*]Ubuntu any version with 725M, 1G, 1.5G, 2G RAM - don't work on any browser
[*]Ubuntu any version with 512M RAM - work on any browser
[*]Fedora with 1G RAM - don't work
[*]SLAX with 1G RAM - works
[/LIST]

Browsers on Linux are
[LIST]
[*]Firefox
[*]Epiphany
[*]IE4Linux
[*]IE under Windows on VMWare
[/LIST]

This is confirmed by a least two other linux companies.
So I guess it's something to do with the security library for Linux when there're more than
512M RAM on Ubuntu, and it doesn't depend on browsers.

I've tried dcstar idea by apt-get install many SSL/HTTPS related library but it doesn't work.
Any idea?

---

### Post by davidsrsb on 2007-09-24
Is this a Java issue? Banks often use Java and by default Ubuntu does not have sun java installed.
Memory size should have nothing to do with the issue.

---

### Post by davidsrsb on 2007-09-24
Follow up:
If you read the uob entry page link for problems to a pdf file you will read that you MUST set the browser to use Microsoft Virtual Machine and NOT Sun java.
As Microsoft Virtual Machine goes end of life at the end of this year, it looks like the bank has dug itself into a hole.

---

### Post by davidsrsb on 2007-09-24
Another follow up
Slax uses some of its ram for a ramdisk, so it as less ram for applications than a normal installed Linux.
There are switches in the Java applet control panel that could be used to reduce the virtual machine size
System-Pref-Sun Java 6 control panel
eg [http://www.duckware.com/pmvr/howtoincreaseappletmemory.html](http://www.duckware.com/pmvr/howtoincreaseappletmemory.html)
The same method could be used to reduce available memory - worth trying

---

### Post by samphan on 2007-09-24
This is the message from the PDF.
> How to set up UOB CyberBanking
We are delight to inform you that UOB CyberBanking has been upgraded
since 16 January 2006. When you login with your old password, UOB CyberBanking
will automatically request you to change the password
UOB CyberBanking require Microsoft Virtual Machine program to support new
security, please check your PC as describe below:

However, I don't think the website require MS VM because :-
[LIST]
[*]Firefox on Windows - works
[*]Any browser on Ubuntu with 512M RAM - works
[/LIST]
The server is actually WebSphere Application Server 5.0. This is 
a valid request/response from Firefox on Windows.
```
20:24:23.377[672ms][total 735ms] Status: 200[OK]
GET https://uobcyberbanking.com/UOB/EstablishSession Load Flags[INHIBIT_PERSISTENT_CACHING  LOAD_DOCUMENT_URI  LOAD_INITIAL_DOCUMENT_URI  ] Content Size[-1] Mime Type[text/html]
   Request Headers:
      Host[uobcyberbanking.com]
      User-Agent[Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.7) Gecko/20070914 Firefox/2.0.0.7]
      Accept[text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5]
      Accept-Language[en-us,en;q=0.5]
      Accept-Encoding[gzip,deflate]
      Accept-Charset[UTF-8,*]
      Keep-Alive[300]
      Connection[keep-alive]
      Cookie[JSESSIONID=00001r0QfdthCAGMGCqb_n9W7Eb:-1]
   Response Headers:
      Date[Mon, 24 Sep 2007 13:31:19 GMT]
      Server[WebSphere Application Server/5.0]
      Set-Cookie[JSESSIONID=0000gqMiqSaSOrEaKNOK1RDROiB:-1;Path=/]
      Expires[Thu, 01 Jan 1970 00:00:00 GMT]
      Cache-Control[no-store, no-cache, must-revalidate, post-check=0, pre-check=0]
      Pragma[no-cache]
      Keep-Alive[timeout=15, max=100]
      Connection[Keep-Alive]
      Transfer-Encoding[chunked]
      Content-Type[text/html; charset=Cp874]
      Content-Language[th-TH]
```
We're trying to "reduce JVM memory" to various lower sizes but it doesn't seem to help :confused: 
Any comment?

---

### Post by drpaul on 2007-09-24
I just accessed the bank's entry page from Edgy with 2 GB of RAM. 

?????????? 

Paul

---

### Post by samphan on 2007-09-25
I'm trying from another notebook - Ubuntu 7.04, 1.5G. It failed, i.e. forever waiting for the respond.```
11:03:59.950[0ms][total 0ms] Status: pending[]
GET https://uobcyberbanking.com/UOB/EstablishSession Load Flags[INHIBIT_PERSISTENT_CACHING  LOAD_DOCUMENT_URI  LOAD_INITIAL_DOCUMENT_URI  ] Content Size[unknown] Mime Type[unknown]
   Request Headers:
      Host[uobcyberbanking.com]
      User-Agent[Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20061201 Firefox/2.0.0.3 (Ubuntu-feisty)]
      Accept[text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5]
      Accept-Language[en-us,en;q=0.5]
      Accept-Encoding[gzip,deflate]
      Accept-Charset[UTF-8,*]
      Keep-Alive[300]
      Connection[keep-alive]

```

---

### Post by kvonb on 2007-09-25
How do you connect to the Internet?  If it's PPPoE, it could be an MTU setting.  Ask your ISP maybe.  Also maybe try connecting directly, ie not through a router.

---

### Post by samphan on 2007-09-27
> **drpaul said:**
> I just accessed the bank's entry page from Edgy with 2 GB of RAM. 
Paul

There must be some other factors. For example, Ubuntu 6.10 should work with any size of RAM but I still see a notebook with Ubuntu 6.10 and 1G RAM that can't access the website?

I've made a poll to research for the configurations that have the problem with the website.

[CENTER]**[SIZE="5"][Can you access https://uobcyberbanking.com/](http://ubuntuforums.org/showthread.php?p=3428446)[/SIZE]**[/CENTER]

---

### Post by dcstar on 2007-09-28
> **samphan said:**
> There must be some other factors. For example, Ubuntu 6.10 should work with any size of RAM but I still see a notebook with Ubuntu 6.10 and 1G RAM that can't access the website?
..........

You should file this as a bug - I suspect it is somewhere in the particular kernel versions that are being used.

BTW, I have just altered my GRUB /boot/grub/menu.lst file to boot my 2GB RAM PC using only 500MB of RAM and I can now access the website!

If you want to do what I did, just append "mem=500M" to the end of you boot line, or copy your normal boot block and add another boot option with the limited memory use, here's mine as an example:

```
title		Ubuntu, kernel 2.6.20-16-lowlatency 500MB RAM
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=88e2c353-0fc8-4ebf-a9ff-aad9f073d692 ro quiet splash noapic mem=500M
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault
```

---

### Post by rdsii64 on 2007-09-29
> **davidsrsb said:**
> Follow up:
If you read the uob entry page link for problems to a pdf file you will read that you MUST set the browser to use Microsoft Virtual Machine and NOT Sun java.
As Microsoft Virtual Machine goes end of life at the end of this year, it looks like the bank has dug itself into a hole.
That may be true but he can get to that sight when he is only using half a gig of ram
anything more and he has issues. You would think that the ram would not be a problem 
but according to what he is telling us every time he uses more than half a gig he has issues.
may he has a bad ram stick I can't say for sure. just food for thought. By the way.
I am pretty new to linux so If I am wrong don't flame me to bad (LOL)

---

### Post by rdsii64 on 2007-09-29
> **samphan said:**
> I'm trying from another notebook - Ubuntu 7.04, 1.5G. It failed, i.e. forever waiting for the respond.```
11:03:59.950[0ms][total 0ms] Status: pending[]
GET https://uobcyberbanking.com/UOB/EstablishSession Load Flags[INHIBIT_PERSISTENT_CACHING  LOAD_DOCUMENT_URI  LOAD_INITIAL_DOCUMENT_URI  ] Content Size[unknown] Mime Type[unknown]
   Request Headers:
      Host[uobcyberbanking.com]
      User-Agent[Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20061201 Firefox/2.0.0.3 (Ubuntu-feisty)]
      Accept[text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5]
      Accept-Language[en-us,en;q=0.5]
      Accept-Encoding[gzip,deflate]
      Accept-Charset[UTF-8,*]
      Keep-Alive[300]
      Connection[keep-alive]

```
try taking the half gig stick and putting it in one slot reboot and see what happens.
then take the same stick and put it in the other slot and see what happens.

maybe your problem is a hardware problem.

---

### Post by dcstar on 2007-09-29
> **rdsii64 said:**
> try taking the half gig stick and putting it in one slot reboot and see what happens.
then take the same stick and put it in the other slot and see what happens.

maybe your problem is a hardware problem.

Read all the other posts about other people who experience EXACTLY the same thing.

---

### Post by dcstar on 2007-09-29
> **anchalee said:**
> My notebook is Lenovo Thinkpad R60 with Ubuntu 7.04, kernel 2.6.20, 1 GB RAM  (512 MB x 2 slots).  I used Firefox 2.0.0.6 and I tried to access [https://uobcyberbanking.com](https://uobcyberbanking.com). It showed an empty page and the status bar showed "Waiting to uobcyberbanking....". Then I tried to access the website by Konqueror, Ephiphany and IE4Linux. They have the same problem. 
.........
Any idea?

There is something screwy about the login web page HTML code that does get returned in a <512MB system.

For one thing, there is no "</HEAD>" tag in the returned HTML, so while this may not have anything to do with the issue, I suspect that the web site is so badly written that it causes weird problems like you have experienced.

Let the site know about your issues, and also about this discovery.

---

### Post by samphan on 2007-09-30
> **rdsii64 said:**
> try taking the half gig stick and putting it in one slot reboot and see what happens.
then take the same stick and put it in the other slot and see what happens.
maybe your problem is a hardware problem.

Yes, we've done that. We've tried many combinations of rams and even purchase a new ram stick.
We've sent a notebook to Lenovo service center to try even more combinations and the 
result is the same. Please note that the lenovo notebook is only the beginning of this suspicion.
Now we can confirm the problem with many notebooks and PCs in our company and a few [B]other
companies[/B]. So this problem is **not relate to hardware problems**. It only relates to[B] ram size (and
distro version).[/B]

---

### Post by samphan on 2007-09-30
> **dcstar said:**
> You should file this as a bug - I suspect it is somewhere in the particular kernel versions that are being used.
I think so. I should file a bug. I'm trying to confirm that everyone elsewhere have the same problem.
> BTW, I have just altered my GRUB /boot/grub/menu.lst file to boot my 2GB RAM PC using only 500MB of RAM and I can now access the website!
Thanks for trying to confirm this problem, and show me the new way to try different size of ram w/o getting my hand dirty.

---

### Post by dcstar on 2007-10-03
> **samphan said:**
> I think so. I should file a bug. I'm trying to confirm that everyone elsewhere have the same problem.

Thanks for trying to confirm this problem, and show me the new way to try different size of ram w/o getting my hand dirty.

Another thread with exactly the same problem:

[http://ubuntuforums.org/showthread.php?t=549758](http://ubuntuforums.org/showthread.php?t=549758)

---

### Post by davidsrsb on 2007-10-23
The bug is still there with Ubuntu 7.10. Firefox 2.0.0.8 and JRE1.6u3
1GB ram

---

### Post by Zeroangel on 2008-02-17
My machine only has 512MB of RAM and cannot access the site.

Suggest you bug the website owners, since I can access *every other website* just fine in firefox. They must be doing something really unstandard if it doesnt work in Ubuntu.

---

