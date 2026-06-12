---
title: "Can't update Synaptic"
date: 2007-01-11
forum: General Help
---

### Post by Wise_One on 2007-01-11
Hi there. I just registered to this forum and please excuse me if I posted in a wrong category or if the things I'm asking have been mentioned before.

For starters, I'm really new to linux. This means I don't know any commands or any other stuff about it. To the point now.

I installed Kubuntu 6.10 on my 40Gb hd.Everything worked fine, but I couldn't get any updates from Adept Manager. The funny thing is that I was able to get on the internet since Konqueror had no problem. 

When I tried to install automatix, the **apt-get update** command wouldn't do. I kept having connection timeouts.

With the help of some other guys from a greek forum, I tried every possible way to make it work but to no avail.

So I decided to get rid of Kubuntu. I installed mintLinux (which as far as I know is based on Kubuntu) just to have Flash Player installed to be able to connect to a chat room of this greek forum to get instant help by others.

The problem is the same. Firefox can get online, but still I cannot get updates from Synaptic Manager. I feel that the repositories are ok because for three days I've been trying to connect to them but to no avail.

I connect to the internet by a router (Telindus 1130) which doesn't have any firmware updates (I thought that this might get it to work). The router is connected to my roomate's pc, but I don't think that it makes any difference.

Maybe the router doesn't allow the **apt-get update** ports to connect, so is there a way to change these ports?

Generally, if you can help me even a bit I'll be glad. The way I see it, you guys are the only hope left:-|

---

### Post by Wise_One on 2007-01-11
Come on guys, no suggestions??:(

---

### Post by Wise_One on 2007-01-11
Still nothing???

---

### Post by PlatinumPlus on 2007-06-05
You are managing to connect but the connection is just slow?

Is your internet also slow?

---

### Post by Claus7 on 2007-06-07
Hello,

my modem is telindus 1133 and my connection is not slow, I face the same problems as Wise_One.

Is there any help? I just came accross this answer. Just minutes ago I have made a new post.

---

### Post by Rui Pais on 2007-06-08
Can you post the exact error output of sudo apt-get update?

---

### Post by Claus7 on 2007-06-08
This is it :
sudo apt-get update
Password:
26% [&#931;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; gr.archive.ubuntu.com (32.1.6.72)] [&#931;&#973;&#957;&#948;&#949;&#963;&#951; .1.6.72)

Before 1.6.72 and gr.archive.ubuntu it sais in english connection. Mine is in hellenic language, yet that doesn't make  any difference. WIth my isdn modem I do not face any such problem. So at first I get this.

Then I get :
&#931;&#966;&#940;&#955;&#956;&#945; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) dapper Release.gpg
  &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#945;&#961;&#967;&#953;&#954;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#964;&#951;&#962; &#963;&#973;&#957;&#948;&#949;&#963;&#951;&#962; &#963;&#964;&#959; gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 &#932;&#959; &#948;&#943;&#954;&#964;&#965;&#959; &#948;&#949;&#957; &#949;&#943;&#957;&#945;&#953; &#960;&#961;&#959;&#963;&#960;&#949;&#955;&#940;&#963;&#953;&#956;&#959;) [IP: 2001:648:2000:de::211 80]
&#931;&#966;&#940;&#955;&#956;&#945; [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; archive.ubuntu.com:80 (32.1.6.72), &#955;&#942;&#958;&#951; &#967;&#961;&#972;&#957;&#959;&#965; &#963;&#973;&#957;&#948;&#949;&#963;&#951;&#962;
&#931;&#966;&#940;&#955;&#956;&#945; [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg .... ..... and so on for the other packages.

In english once again I get :
Error [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) dapper Release.gpg
The initialization of the connection to gr.archive.ubuntu.com:80 is impossible.
(2001:648:2000:de::211). - connect (101 &#932;he network is not accessible) [IP: 2001:648:2000:de::211 80] and so on for the others.

And I get that the time of connection is over. Does this help? Thank you for your anwer Rui Pais, I hope this helps.

Regards!

---

### Post by Claus7 on 2007-06-08
Even right now the command hasn't finished. In some of the packages ti sais also : Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) dapper Release.
The percentage of connection is 22% and it is the same for at least five minutes or so.
Now it is 24%.It doesn't become more. I do not undertsand ... :confused:

Regards!

---

### Post by Rui Pais on 2007-06-08
uauu your apt-get update looks like a page of a math book :)

ok, seriously. There are 2 thing i found strange. 
first are the IP addresses or what appears after an internet address that usually is an IP, like this one "(2001:648:2000:de::211)" have a strange format.
I wonder if its an ipv6 incompatibility (some modems/routers have problem with it)

Another things is this:
> gr.archive.ubuntu.com (32.1.6.72)
gr.archive.ubuntu.com is the National technical university of Athens but this is not the correct ip: 32.1.6.72. (i couldn't not even ping to that) Seems to be 147.102.222.211... so another suspicious is a dns issue.

Check first ipv6. whats the output of ifconfig?
edit the file /etc/modprobe.d/blacklist and add the following:
```
blacklist ipv6
```
reboot, check if 
lsmod |grep ipv6
gives an empty output and try update again, to see what happen.

---

### Post by Claus7 on 2007-06-08
Thank you very much for your immediate answers!!

I also am a little bit confused because when I connect, I do not know whether I connect even with the right provider with all these changes I'm trying. Is it possible that this : de has something to do with Germany and I connect with a different provider??? 
I'm not at my computer at the moment so I'm not able to check the things you are proposing. I'll be able to do that later that night.
I have to inform you that I have tampered with ipv6 both in firefox and with this procedure :
Open a terminal and enter:
sudo gedit /etc/modprobe.d/aliases

Look for the line that reads:
alias net-pf-10 ipv6

Change it to:
alias net-pf-10 off #ipv6

Save and reboot your PC.
I do not know whether this does make any difference or not. I have changed it a lot of times.

I'll start from where you mention Check... and I'll let you know.

Thank you once again for your time!
Regards!

---

### Post by Rui Pais on 2007-06-08
> **Claus7 said:**
> Thank you very much for your immediate answers!!

I also am a little bit confused because when I connect, I do not know whether I connect even with the right provider with all these changes I'm trying. Is it possible that this : de has something to do with Germany and I connect with a different provider??? 
uhmm... i don't think so, why Germany? I think it's just the hard ipv6 terminology, a random set of letters (but i may be wrong... don't know much about ipv6 rules for addressing if its that or some other thing...)
> 
I'm not at my computer at the moment so I'm not able to check the things you are proposing. I'll be able to do that later that night.
I have to inform you that I have tampered with ipv6 both in firefox and with this procedure :
Open a terminal and enter:
sudo gedit /etc/modprobe.d/aliases

Look for the line that reads:
alias net-pf-10 ipv6

Change it to:
alias net-pf-10 off #ipv6

Save and reboot your PC.
I do not know whether this does make any difference or not. I have changed it a lot of times.

well, it depends. Changes to /etc/modprobe.d/aliases stop to work somewhere around edgy/dapper, not sure when. It don't work anymore at least with Edgy and Feisty. The correct way now is not remove the alias but blacklist the module. 
You can check if it's preventing ipv6 or not, by typing
```
ifconfig
``` and check if you have only a inet line and no inet6.
And/or doing:
```
lsmod |grep ipv6
``` and check it it returns ipv6 (loaded) or an empty line (not loaded)


> 
I'll start from where you mention Check... and I'll let you know.

Thank you once again for your time!
Regards!
No problem, 
i'm glad if i can help :)

---

### Post by Claus7 on 2007-06-08
Hello.

I'm trying for at least 2 hours  to connect. At first I opened the ubuntu partition. I did what you informed me to do and I had also written everything down as I do now. I was using firefox because only this browser was woriking. Yet, just before I was able to post, I coulnd't open any page. And not only that, but before I was able to realise it, I closed the tab in which I was writting! Huge disappointment. Yesterday and today only, I 'm in front of a terminal more than 7 hours doing in the end nothing. Anyway, I 'm just a little bit disappointed. Back to your instructions. I 'll try to wright what I remember, because now I' m connected via windows partition. 

I have to say that if I hadn't closed my modem (power off and then on), then I woulnd't have been able to browse even via windows! Maybe the modem "stuck". 

So before I edited with blacklist ipv6 the inet6 line was there. After that it wasn't there. I wasn't able to download via synaptic once again. The messages were the same as before. 
The lsmod |grep ipv6 command gave the same result either I had edited the file or not (with editing I understood writting the blacklist ipv6 as root at the end of the file) : the rusult was an emtpy line in both cases. I was connected via usb all the time. 

You are helpful, yet I wish things were a little bit easier...
Regards!

---

### Post by Rui Pais on 2007-06-09
Hi Claus7.

Sorry things not working yet... network stuff is simple but sometimes one does an error somewhere and it became an hell to find what is wrong. In your case you are working in an OS that you not easy with, that don't make things easier... keep that in mind. I (and others) will try to help and you will only need to do this once.

The base line is ADSL router  are easy. If they don't work is an incorrect config or a hardware failure. 

Don't know if i exactly understand each of your steps... but if you needed to reboot the router when you changed to Windows maybe some hardware failure happened. 

Let's resume. If lsmod| grep ipv6 gives an empty line, then you have blacklist ipv6 (thats one less thing to worry). 

Now we need to check your network configuration. Since you don't have intenet on Linux you need to copy outputs to a floppy or a pen (do you have one of those? i'll assume you do).
Type on a terminal:
```
ifconfig > ifcongig.txt
```
that will make a text file with the output. Copy to your pen, reboot to Windows and, please, post here (sorry the trouble :()

btw you say you connect using USB (and i notest that you post on USB modems thread of Steve Harper).
USB are bad for net connections. You have an adsl router you shouldn't any usb connection. Use network wire to connect your internal net card to the router, and remove the Steven Harper package with purge option (to clean any left conflict files):
```
sudo aptitude purge usbadslmodemmanager
```

---

### Post by Claus7 on 2007-06-09
Hello Rui Pais!

I'm able to connect via ubuntu once again!! And via ethernet as you proposed. I have to say that I had usb, and I changed cables while I was online. With this change I couldn't browse anymore. So I made a restart and now I can browse normaly via ethernet. As I can see opera works too! I removed usbadslmogemmanager as you proposed. Unfortunately I cannot update via synaptic once again. 
Now the code :
ifconfig > ifcongig.txt
gave me an empty line both with usb and ethernet connection.

Yet the output of lsmod| grep ipv6 is the following :
claus@claus-desktop:~$ lsmod| grep ipv6
ipv6                  265856  6
That's because I haven't edited the file you proposed. I changed it back because I thought that this didn't allow me to connect. I post up to now. I will edit, restart and report again (I hope from ubuntu!).

Regards!

---

### Post by Claus7 on 2007-06-09
Sorry, opera doesn't work:( It opens only [www.ntua.gr](www.ntua.gr) But Firefox is ok!

---

### Post by Claus7 on 2007-06-09
Hello once again!

I have edited the file /etc/modprobe.d/blacklist and I'm able to connect with opera too! I'm writting from there right now. Both commands :

ifconfig > ifcongig.txt
lsmod |grep ipv6

give an empty line.

Yet I think that you gave me this command ifconfig > ifcongig.txt so as to have a text file and transfer it to windows. I do not know why this doesn't work.
Oooops!! It works! The output is in my home folder and not in desktop. I'm familiar with ubuntu, yet I have a lot of things to learn still!

So the ifconfig command gives the following :

eth0      Link encap:Ethernet  HWaddr 00:18:4D:E9:54:59
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:837806 (818.1 KiB)  TX bytes:248000 (242.1 KiB)
          Interrupt:177 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

In the inet addr:192.168.1.2 I was expecting 192.168.1.*3*, because this is the IP address of my provider. I know it because in windows I opened command prompt and typed :
ipconfig/all

That's all my output up to now!

---

### Post by Rui Pais on 2007-06-09
Ok, starts to look better. :)

The ifconfig.txt was only for the case you don't have Internet on Ubuntu, to allow you to post the exact output here. Since mean while you got it back, that make things easier. 

Now, you have an ipv4 address (the inet line). Good, too. 
192168.1.2/3 are internal ip addresses. They are not set by your net provider, but by you (static) or by DHCP server. Its not important that ends with 2 or 3 as long it don't ends in 1 (thats the router address) and they starts with 192.168.x.x (meaning they belongs to same net). Everything fine here!

Next suspect is a DNS issue! (a strong suspect).
your 
```
cat /etc/resolv.conf 
```
should give something like this:
> nameserver 192.168.1.1

If so, edit (with root/administrative powers) to this:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

save and do this:
```
sudo /etc/init.d/networking restart
```

try apt-get update again.

---

### Post by ctrl_freak on 2007-06-09
Hi,

I'm also having the same problem with xubuntu Edgy, just to let you know you're helping me too!
However, after this advice, Synaptic nor apt-get are updating their lists.

Cheers

---

### Post by Claus7 on 2007-06-09
I refreshed the page, yet I wasn't able to see the new post of yours. Sorry for the delay. So I exited and logged in again.

Now the code :
```
cat /etc/resolv.conf
```

indeed gave the output you mentioned. 

I edited the file /etc/resolv.conf both erasing the 192.168.1.1 and without erasing it. I coulnd't update with both. 

Now if I type cat /etc/resolv.conf , the output is 192.168.1.1 even if I had edited the file.

---

### Post by Rui Pais on 2007-06-09
Ok,
try then this instructions here:
[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

---

### Post by Claus7 on 2007-06-09
Dear Rui Pais, 	

**dzi&#281;kuj&#281; bardzo!!! **

I have to say that I followed the link. I did the first solution, yet when I rebooted I couldn't update. So I followed the second one and here I 'm! I did all the updates and everyting went normal except 10 of them which refused to be installed out of 277 if I remember correctly. It doesn't matter because when I open synaptic everything goes ok (I installed azureous for example). WIthout your help still I would have tried to find a solution without result.
Thank you for your patience, your immediate responses and above all your valuable time.

Z powa&#380;aniem,
Claus7

---

### Post by Claus7 on 2007-06-09
In case someone wants to follow exactly the commands I wrote, I simply copy and paste them here. Nothing wrong to have in two places something that works. And all thanks to Rui Pais. Here it is then :

$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
(with this I opened the dhclient.conf document and in the end I added the above line, even if almost all the other lines in this document have a #, in front this line you must NOT have one)
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0

Regards!

---

### Post by Rui Pais on 2007-06-09
> **Claus7 said:**
> Dear Rui Pais, 	

**dzi&#281;kuj&#281; bardzo!!! **

I have to say that I followed the link. I did the first solution, yet when I rebooted I couldn't update. So I followed the second one and here I 'm! I did all the updates and everyting went normal except 10 of them which refused to be installed out of 277 if I remember correctly. It doesn't matter because when I open synaptic everything goes ok (I installed azureous for example). WIthout your help still I would have tried to find a solution without result.
Thank you for your patience, your immediate responses and above all your valuable time.

Z powa&#380;aniem,
Claus7

So it was a DNS issue after all :)

Glad you make it. I think your main problem was you mixing things while you trying to solve your issue. Special the USB trial. But you was brave enough to try to solve your problem by yourself and with trial and error. 
Congratulations! Most users are more passive and just wait for answers (or even rant...). 
You didnt required any special amount of patience at all ;)
I checked your posts and you made a several posts on this, some with no answers...  
You may want to post the solution in your [post on Network forum]("http://ubuntuforums.org/showthread.php?t=467513") so others with similar problem can try.

have fun.
:D

edit: btw With dns working you can, of course, browse with any browser, ff or opera.

---

### Post by ctrl_freak on 2007-06-09
Huzzah!

The same solutions worked for me, although I also ran dhclient once through.

Thanks,

Greatly appreciated.

---

### Post by Rui Pais on 2007-06-09
> **ctrl_freak said:**
> Huzzah!

The same solutions worked for me, although I also ran dhclient once through.

Thanks,

Greatly appreciated.

good. 
The reason for this is an annoying problem with routers that seems to be incapable of resolve dns servers IPs correctly.
By default dhcp assigns the nameserver ip to router and should be the router to use the ones that our Internet providers had give us. 
Since they can't, either the user put directly those nameservers ips on resolv.conf or the ones i give you, from the opendns, famous for reliability (and even speed).

The reasons why they are replaced is because they are overwritten by dhcp with the default router ip... so enters the "prepend domain-name-servers" to dhclient.conf to change that behavior :)

clear as mud :lol:

---

### Post by Claus7 on 2007-06-09
Hello, 

> I think your main problem was you mixing things while you trying to solve your issue. Special the USB trial
I wanted to get as much as I could with my existing hardware. That's why I was peristent with usb. I was also seeing that other people were successful. So I said, I will give it a try. I wasn't sure even if I was able to install a network card after all. With this I have two things that I want to say:

i) I learnt that a network card is connected in a pci slot. At first I hadn't connected it correctly so I had troubles from there as well.

ii) The other thing, which I think that will be helpful to others as well, is a kernel panic problem I was facing. I know that this has nothing to do with the subject of this post, yet this was the motiv to solve it (or I think that I have solved it). I just cleaned the memory while I remove it and put it back. More on this to this link :
[http://ubuntuforums.org/showthread.php?t=349575](http://ubuntuforums.org/showthread.php?t=349575)

> You didnt required any special amount of patience at all 

Very kind of you!

> You may want to post the solution in your post on Network forum so others with similar problem can try.

At the time you were writting this, I went in my posts and wrote a link to this post. In one post that I had created myself, I also ticked the option resolved.

> have fun:)
I must say that I'm very relaxed. It was a little bit difficult because that way I couldn't work comfortably. Thank you once again for your help!

Regards!

---

