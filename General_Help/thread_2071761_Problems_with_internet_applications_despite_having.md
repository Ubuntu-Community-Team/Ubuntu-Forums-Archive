---
title: "Problems with internet applications despite having the required packages - 12.04"
date: 2012-10-16
forum: General Help
---

### Post by paranat on 2012-10-16
Hello!

I did not find any search results for this constellation of problems, so I decided to post a new thread for this.

Despite a working broadband connection (I have already checked this with my ISP), I have problems with the following Internet applications:


[LIST]
[*]**Flash videos** (such as Youtube) do not work despite having installed the correct flash plugins.  When trying to play a video, the browser becomes very choppy with a never-ending "transferring data from address x" or "awaiting response from address x" at the bottom of the screen.
[*]Gmail (through browser) works slowly and **sending any e-mails** does not work at all. When trying to send an e-mail, the browser gets stuck as with Youtube. I have an e-mail account to my university on a browser-based Outlook Web Application. The same problem appears: I can read my e-mail quite well (apparently because the application is lighter) but sending e-mails is impossible.
[*]**Facebook** works very choppily and certain functions, such as accepting friend invitations, work on a very long delay or not at all (same as with Gmail)
[*]**Submitting filled-out forms** (such as when registering an account on some website) works often very slowly or not at all. The same symptoms as with e-mail and Facebook.
[*]In general, **heavy pages** with lots of content, such as newspaper homesites, work slower than my bandwidth (1 Mbit ADSL) should allow. They work nevertheless, although surfing is sometimes frustrating because of the delays. The **general working of the operating system** is also quite slow: there is a noticeable delay when launching applications from the left-side menu (I am using the Unity desktop).
[/LIST]
I mostly use my computer for videos/e-mail/Facebook, so these are the problems I encounter.

I am running Ubuntu 12.04 with all the latest updates installed and the latest version of Firefox. I have tried different browsers, such as Opera and Epiphany, and the problem persisted. Earlier I had Ubuntu 8.04. It worked overall faster, but the problems with Internet were exactly the same. I used to have a parallel installation of **Windows XP Pro with Internet Explorer, which had no problems** with the above mentioned functions. It was a bit slow compared to the previous connection, but everything did work.

My computer has a **1.8 GHz AMD Athlon 1800 XP+ CPU and 1.5 GB of RAM**. I suppose this should be enough for Ubuntu 12.04 to work smoothly, but I'm not sure.

My overview of the possible diagnostics:

[LIST]
[*]Internet connection. It should be OK, because according to my ISP the line works smoothly and the speed is a full ~120 KB / sec. A curious coincidence, however, is that **the Internet problems first appeared when I moved to a new apartment** and at the same time changed the ISP. At that time I was still on 8.04. It is difficult to explain the Internet problems with the ISP, however, because with Windows everything worked alright even in the new place.
[*]Operating system / browser. I have installed all the relevant plugins mentioned in the Ubuntu FAQ and Ubuntu Wiki, so I don't know what could be wrong.
[*]Hardware?
[/LIST]
I am now considering switching my OS to Windows. I suppose other options could be finding a fix on 12.04 or finding some better (lighter?) Linux distro.

I'd appreciate any suggestions/questions/help!


_**EDIT:**_ The problems with sending e-mails / Facebook and the general slowness of the OS were solved. The former was solved by setting the appropriate MTU in the network settings and the latter by changing to Lubuntu desktop. The problem with Flash remains, for which I started a new thread [here]("http://ubuntuforums.org/showthread.php?p=12308257").

---

### Post by paranat on 2012-10-18
One more try...

---

### Post by mikewhatever on 2012-10-18
It's hard to tell what's wrong with one's internet connection without knowing the details. Generally, Ubuntu seems to work well for many, and not very well for some, in which case, we would need info on the type of connection, the ISP, networking hardware, etc, to be able to help.
What kind of modem/router do you use? What's the name of the ISP. Are you behind a proxy (for example, on a university campus)? Is the line shared with other people? 
What's the output of 'lspci -nnk | grep -iA2 net' from a terminal window.

---

### Post by steeldriver on 2012-10-18
If you are sure that it's not just a bandwidth issue (I have seen very similar problems on a DSL connection with marginal SNR) then the next thing that comes to mind is some kind of MTU conflict - sometimes referred to as 'black hole router' - pretty good explanation here (it's MS but the behavior is not OS specific)

[http://support.microsoft.com/kb/159211](http://support.microsoft.com/kb/159211)

What kind of network hardware do you have (router / modem etc.)?

---

### Post by paranat on 2012-10-18
Thanks for the answers!

> It's hard to tell what's wrong with one's internet connection without knowing the details. Generally, Ubuntu seems to work well for many, and not very well for some, in which case, we would need info on the type of connection, the ISP, networking hardware, etc, to be able to help.
What kind of modem/router do you use? What's the name of the ISP. Are you behind a proxy (for example, on a university campus)? Is the line shared with other people? 
What's the output of 'lspci -nnk | grep -iA2 net' from a terminal window.
I am using a Finnish ISP called Elisa Saunalahti. The modem/router model is BeWAN IAD A2100N ELISA. I'm not behind a proxy and the line is not shared with other people. It's a direct broadband connection via telephone line, speed is 1 Mbit down and something (less) up.

The building is quite old and I'm wondering if poor condition of the line might be the reason, but the ISP did some remote measurements and they said the line is working well. One possible reason is that the phone cable running between the telephone plug and the modem is about 5 meters long, while according to the ISP it should be a maximum of 3 meters. According to them, the modem should be right next to the plug, while the cable from the modem to the computer can be longer. I still have this setting, because a) it is very difficult to have the modem next to the plug, b) I once tried moving the computer and the modem right next to the plug and the problem remained exactly the same, and c) with Windows the connection worked as it is.

Output of "lspci -nnk | grep -iA2 net":
```
00:04.0 Ethernet controller [0200]: NVIDIA Corporation nForce2 Ethernet Controller [10de:0066] (rev a1)
    Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard onboard nForce2 Ethernet [1043:80a7]
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

```> If you are sure that it's not just a bandwidth issue (I have seen very similar problems on a DSL connection with marginal SNR) then the next thing that comes to mind is some kind of MTU conflict - sometimes referred to as 'black hole router' - pretty good explanation here (it's MS but the behavior is not OS specific)

[http://support.microsoft.com/kb/159211](http://support.microsoft.com/kb/159211)

What kind of network hardware do you have (router / modem etc.)? The only reason to think it's not a bandwidth issue is that I talked to the ISP customer service on the phone and they appeared to do some remote measurements and said the connection works fine... So I'm not sure. How do I test for SNR?

 I probably don't understand what the article is talking about, but I tried measuring the MTU with this command: ”sudo ping (my ip address) -f -l 1472”. The output is:
```
WARNING, probably rcvbuf is not enough to hold preload.
 PING 192.168.100.10 (192.168.100) 56(84) bytes of data.

```  And below there is a flashing line of dots, and it seems to be going on and on with no result. I shut down the terminal after 10-15 minutes. Did I do something wrong – how to identify a black hole router?

---

### Post by steeldriver on 2012-10-18
My apologies - since that's a Microsoft article the version of the 'ping' command will be slightly different for Linux - maybe try something like 

```
ping -s 1472 -c 4 -M do google.com
```This is what I get:

```
$ ping -s 1472 -c 4 -M do google.com
PING google.com (74.125.226.9) 1472(1500) bytes of data.
1480 bytes from yyz06s05-in-f9.1e100.net (74.125.226.9): icmp_req=1 ttl=56 time=17.6 ms
1480 bytes from yyz06s05-in-f9.1e100.net (74.125.226.9): icmp_req=2 ttl=56 time=17.6 ms
1480 bytes from yyz06s05-in-f9.1e100.net (74.125.226.9): icmp_req=3 ttl=56 time=20.0 ms
1480 bytes from yyz06s05-in-f9.1e100.net (74.125.226.9): icmp_req=4 ttl=56 time=18.1 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 17.609/18.348/20.021/0.994 ms

```whereas if I try MTU > 1500 I get

```
$ ping -s 1474 -c 4 -M do google.com
PING google.com (74.125.226.3) 1474(1502) bytes of data.
From 192.168.1.102 icmp_seq=1 Frag needed and DF set (mtu = 1500)
From 192.168.1.102 icmp_seq=1 Frag needed and DF set (mtu = 1500)
From 192.168.1.102 icmp_seq=1 Frag needed and DF set (mtu = 1500)
From 192.168.1.102 icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- google.com ping statistics ---
0 packets transmitted, 0 received, +4 errors

```

---

### Post by paranat on 2012-10-19
> **steeldriver said:**
> 

```
ping -s 1472 -c 4 -M do google.com
```This is what I get:


With the code ```
ping -s 1472 -c 4 -M do google.com
``` I get:

```
atte@aten:~$ ping -s 1472 -c 4 -M do google.com
PING google.com (173.194.32.0) 1472(1500) bytes of data.
From aten.Elisa (192.168.100.10) icmp_seq=1 Frag needed and DF set (mtu = 1460)
From aten.Elisa (192.168.100.10) icmp_seq=1 Frag needed and DF set (mtu = 1460)
From aten.Elisa (192.168.100.10) icmp_seq=1 Frag needed and DF set (mtu = 1460)
From aten.Elisa (192.168.100.10) icmp_seq=1 Frag needed and DF set (mtu = 1460)

--- google.com ping statistics ---
0 packets transmitted, 0 received, +4 errors

```Whereas if I set the MTU value 100 lower, I get:

```
atte@aten:~$ ping -s 1372 -c 4 -M do google.com

PING google.com (173.194.32.9) 1372(1400) bytes of data.
1380 bytes from arn06s01-in-f9.1e100.net (173.194.32.9): icmp_req=1 ttl=56 time=42.2 ms
1380 bytes from arn06s01-in-f9.1e100.net (173.194.32.9): icmp_req=2 ttl=56 time=42.2 ms
1380 bytes from arn06s01-in-f9.1e100.net (173.194.32.9): icmp_req=3 ttl=56 time=41.7 ms
1380 bytes from arn06s01-in-f9.1e100.net (173.194.32.9): icmp_req=4 ttl=56 time=41.4 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 41.462/41.926/42.299/0.344 ms

```So  it appears that my MTU is between 1400 and 1500, when the maximum for  an Ethernet cable should be 1500 (right?). What to make out of this?

**Edit:**
Out of this...
```

From aten.Elisa (192.168.100.10) icmp_seq=1 Frag needed and DF set (**mtu = 1460**)
```

...I could assume that my MTU is 1460. Is this normal - could it cause the problems?

---

### Post by mikewhatever on 2012-10-19
Yes, many DSL modems don't use the 1500 MTU. Try setting yours to 1460 and see what happens. You can do it by editing the wired connection in the network manager GUI.

---

### Post by paranat on 2012-10-20
> **mikewhatever said:**
> Yes, many DSL modems don't use the 1500 MTU. Try setting yours to 1460 and see what happens. You can do it by editing the wired connection in the network manager GUI.

I did it and sending e-mails + Facebook started working! Thank you!

I'm still struggling to fix the Flash and the general slowness of the OS... I'm downloading Lubuntu now to see if it's faster. I'm not sure if it's about the hardware requirements though - output of "top":

```
top - 11:17:13 up  3:33,  2 users,  load average: 0.78, 1.25, 1.29
Tasks: 143 total,   3 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.2%us,  9.1%sy,  0.0%ni, 66.3%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1543416k total,  1336912k used,   206504k free,    50760k buffers
Swap:  1570812k total,    45252k used,  1525560k free,   646844k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1025 root      20   0  223m 103m 3844 R 11.5  6.9  19:47.96 Xorg               
 1761 atte      20   0  690m 155m  19m R  8.6 10.3   8:10.92 compiz             
22263 atte      20   0  629m 155m  35m S  7.9 10.3   9:15.12 firefox            
 5998 atte      20   0 89236  14m  10m S  4.3  0.9   0:12.33 gnome-terminal     
22595 atte      20   0  198m  30m  14m S  0.7  2.0   0:57.93 transmission-gt    
 2267 atte      20   0 34676 3428 2880 S  0.3  0.2   0:00.13 deja-dup-monito    
23639 atte      20   0  2852 1108  828 R  0.3  0.1   0:00.26 top                
    1 root      20   0  3668 1772 1148 S  0.0  0.1   0:01.32 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:01.12 ksoftirqd/0        
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.80 kworker/u:0        
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.96 watchdog/0         
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper            
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs          
   11 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns     
```For Flash I have no idea how to proceed. Flash screens in Youtube etc. still freeze when trying to load them. I tried all the solutions [here]("https://help.ubuntu.com/community/RestrictedFormats/Flash") except for #4, because I couldn't figure how to add/change a line with the editing program.

> 1. Restart your web browser and try the flash test page again 
... ...
3. Install the **alsa-oss** package.

4. If you are using Firefox, edit the Firefox rc script and add or change the line FIREFOX_DSP="aoss" 

```
sudo nano /etc/firefox/firefoxrc

```[Here]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=1949605") someone suggested that...
> There is a known bug with Nvidia cards and hardware acceleration with  the latest version of flash. If this is your situation you can try right  clicking and disabling it in the flash settings. If that fails then  have a look in the Multimedia & Video section of these forums. There  are quiet a few threads about it with a few different solutions on the  first page.I have an Nvidia card, but I don't know how to find the flash settings. At least in the browser (Firefox) settings I see nothing like that. I'm using the Nvidia proprietary drivers.

---

### Post by mikewhatever on 2012-10-20
To deal with the interface sluggishness, I'd try logging out, and selecting Ubuntu2d as sessions. You can do that by clicking on the cog wheel next to the username rectangle. It uses a more lightweight window manager and should feel snappier.
PS: Which model of Nvidia graphics card is there?

As for flash, first, it doesn't have hardware acceleration on Linux, but even if it did, it wouldn't apply to old hardware. Troubleshooting flash sound also seems irrelevant, unless of cause, there are sound problems. Try turning off Transmission, as it can use a lot of bandwidth, and thus interfe with streaming videos.
PS: To find flash settings, right click inside a flash video window.

---

### Post by paranat on 2012-10-20
> **mikewhatever said:**
> ... ...
PS: Which model of Nvidia graphics card is there?

As for flash, first, it doesn't have hardware acceleration on Linux, but even if it did, it wouldn't apply to old hardware. Troubleshooting flash sound also seems irrelevant, unless of cause, there are sound problems. Try turning off Transmission, as it can use a lot of bandwidth, and thus interfe with streaming videos.
PS: To find flash settings, right click inside a flash video window.

I installed the Lubuntu desktop and switched it on from the login window. It's much better now, nearly no lag at all. General sluggishness solved!

Now the only remaining problem is with flash. I'm using a Geforce 6600 GT graphics card. It's rather old - bought some seven years ago, I think. Flash doesn't work even when Transmission is off. The problem clearly has nothing to do with bandwidth.

Here's how it looks when I try to load a Youtube video:

[IMG]http://ubuntuone.com/59Efaz1bSY9bZxGVea9HdS[/IMG]

This is all that happens. As you can see, there's no "loading" type of message at the bottom of the browser screen. However, the computer seems to be doing something all the time when on the page (the memory keeps making its sounds and the system slows down). There seems to be no flash window at all at the blank spot, since no menu appears when right-clicking on it.

Edit:
To clarify, the package that I have installed is "ubuntu-restricted-extras", since I'm using a 32-bit system. I also tried "flashplugin-installer", but there was no difference.

---

### Post by mikewhatever on 2012-10-20
Odd, I don't know why it does that. This is a new problem (at least, I don't think you've mentioned it before), so you might want to open a new thread, because not many will see the description on page 2.

---

### Post by steeldriver on 2012-10-20
Hmmm... that's not a flashblock plugin icon at the top right of your  browser window by any chance?

Another thought is you might want to see if there's a specific lubuntu-extras - I seem to remember it making a difference on Xubuntu whether I chose xubuntu-extras or plain ubuntu-extras (I don't remember the details sorry - just a note in the back of my mind)

---

### Post by paranat on 2012-10-21
I started a separate thread [here]("http://ubuntuforums.org/showthread.php?p=12308257").

---

