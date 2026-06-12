---
title: "new to ubuntu and got a problem conecting via ethernet"
date: 2006-12-10
forum: General Help
---

### Post by garylouden on 2006-12-10
hello, i just got given a dell laptop which didnt have an OS on it

P4 1.8ghz mobile
256mb ddr
20gig hdd
ati 7500

anyway i find the OS amazing as i will only be using it fr web browsing and maybe word proccesing. so far i find it so fast compared to windows especially with the low end spec of the laptop.

my problem is when i plug my ethernet cable in to the laptop nothing hapends (normally with windows and linux it will automaticly connect) so im looking round all the settings and cant find out a way to connect.

if its possable could someone maybe help me?

thanks :D

---

### Post by bscbrit on 2006-12-10
Go to System->Administration->Networking to see if your ethernet card has been recognised.  If it has, it will probably need configuring for your modem/router/gateway/DNS.  If it hasn't, we will have to set up the hardware first.

Come back once you know which of the above we are trying to solve.

---

### Post by garylouden on 2006-12-10
well yes it has 2 options "modem connection" and "wired conection" the wired conection is eth0 so it has been recognised.

i have no router i only have a modem and its going straight into the laptop. when i enable eth0 it sends and recieces bytes also but nothing can use the conection :S

---

### Post by bscbrit on 2006-12-10
What make and model of modem is it?  How does it connect to the computer?  Does the modem have its own configuration page, usually accessible via a browser (perhaps 192.168.0.1 or 192.168.1.1?).  If it does, can you get to it via your browser?

---

### Post by garylouden on 2006-12-10
its a motorola sb4200 and dont really know about config page.....:S

---

### Post by bscbrit on 2006-12-10
OK, I'll go and google for some information on it.  Back in a while.

---

### Post by garylouden on 2006-12-10
ok found this

[http://192.168.100.1/](http://192.168.100.1/)

tried it on thismachine and works, i swap the cable to the laptop and nothing.

not sure what this means >_<

---

### Post by bscbrit on 2006-12-10
OK, found it.  It looks like it should be fairly easy to set up.

Go to System->Administration->Networking

Select the ethernet card and then click on Properties.  Make sure that:

Enable this connection               - is ticked

Configuration                        - set to DHCP, not Static IP address.

Press OK, OK and see if your connection is established within, say, 30 seconds or so.

If not, come back and tell me what you did see.

---

### Post by garylouden on 2006-12-10
ok done that and still nothing, here is a screen shot of the laptop.

[[IMG]http://img165.imageshack.us/img165/4075/screenshotzm0.png[/IMG]](http://imageshack.us)

---

### Post by bscbrit on 2006-12-10
OK, the problem does not appear to be your internet connection, but it is a Firefox connection problem.  But just to prove it, go to a command line and type

sudo apt-get update

If you see activity, then you have a connection.  From the command line you should also be able to 

ping [www.ubuntuforums.org](www.ubuntuforums.org)

If you see a reply being received, then it proves your connection and that the DNS that your accessing is working.  This link should help you to solve the problem but, as always, come back if it doesn't or you need more advice.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by garylouden on 2006-12-10
nope didnt work, here screen shot

[[IMG]http://img144.imageshack.us/img144/4510/screenshot1xk4.png[/IMG]](http://imageshack.us)

---

### Post by bscbrit on 2006-12-10
Gary, please show me the contents of /etc/network/interfaces

At the commandline, please type ifconfig and show me the results.

---

### Post by garylouden on 2006-12-10
sure here ya go, thx for all your help :D[[IMG]http://img137.imageshack.us/img137/9479/screenshot2pe9.png[/IMG]](http://imageshack.us)

---

### Post by bscbrit on 2006-12-10
Next thing, Gary, on the command line can you please 


ping 82.211.81.186

According to the displays that you have given me, you have already received 2.5 MB of data, and that suggest that you are connected to something but that the DNS might not be working.


Let me know the results please.

---

### Post by garylouden on 2006-12-10
it just sayd network is unreachable, nothing else

---

### Post by bscbrit on 2006-12-10
Have you got a second machine with windows installed on it.  I'm just curious because I cannot figure how this thing should be configured.

The link that I gave you earlier is for disabling IPv6, which is enabled by default in Ubuntu but nobody is using yet.  IPv6 has been found to cause some problems in hardware that is not specifically designed for it, which I suspect might be the case for the SB4200.  It doesn't need it as everyone is still using IPv4 and will be for years to come.

However, just for my peace of mind. please confirm that:

The cable/adsl is connected to the SB4200.  You are using an ethernet cable from the SB4200 to your computer and that you HAVE NOT connected the USB connection also.

I'm offline in about 10 minutes or so, for about 30 - 40 minutes while I have some lunch.  But, fear not, I will be back.

---

### Post by garylouden on 2006-12-10
ok what i have is

cable conection into my model, 1 ethernet going to either laptop or computer and no i dont use the usb.

i swap the ethernet between my pc and laptop everytime you ask me to do something :D

---

### Post by wireddad on 2006-12-10
Are you dual booting on this laptop?  If so, does windows side work?

---

### Post by garylouden on 2006-12-10
no it was given to me with an empty hdd so i just shoved ubuntu on it. if i can get the internet to work it will be AWSOME becuase im finding it so fast and easy to use ;)

---

### Post by bscbrit on 2006-12-10
What OS is the other computer using?  If it is windows, can you go to the command line on that machine and type

ipconfig /all

I'm just curious as to how windows has set it up, although I still think that the network might not be the real problem.

---

### Post by garylouden on 2006-12-10
lol dont hack me *cough* *cough*

[[IMG]http://img228.imageshack.us/img228/756/untitledaz8.png[/IMG]](http://imageshack.us)

---

### Post by bscbrit on 2006-12-10
No, I won't I promise :-D 

The windows output shows that you are using IPv4 addresses for the working machine:  its IP is 80.192.4.57 and the gateway is 80.192.4.1.

The configuration of your ethernet card in the Ubuntu laptop has only given it an IPv6 address, or at least that's the only address I can see.

To prove the hardware is working, what I want to do is tranfer manually the working windows values to your Ubuntu laptop.  As long as only one computer is connected to the modem at any time it will not confuse the DHCP server at your ISP.

So, on the laptop, go to System->Adminstration->Networking, select your ethernet card, select Properties, change it to a static IP address and set the other values as follows:

IP Address 80.192.4.57
Subnet Mask: 255.255.255.0
Gateway: 80.192.4.1

Click OK, and then select the the DNS tab.  Insert the following 2 values

62.31.64.39
62.31.112.39

Click close.

On a command line type

sudo /etc/init.d/networking restart

and, with luck, it should then work.  But we are not finished yet.  Providing it works, we then have to make sure the system configures itself automatically, but that is the next step.

---

### Post by garylouden on 2006-12-10
ok here ya go, not sure if its went well or not :S

[[IMG]http://img154.imageshack.us/img154/5298/screenshot3lz4.png[/IMG]](http://imageshack.us)

---

### Post by bscbrit on 2006-12-10
The error messages that you saw were for the devices listed in /etc/network/interfaces which you do not have - you can ignore them.

Were you able to ping [www.ubuntuforums.org](www.ubuntuforums.org) or ping 82.211.81.186 ?

Did Firefox work?

---

### Post by garylouden on 2006-12-10
well i would say "work" but it didnt not work, when i loaded firefox it hung and didnt show an error message. i didnt try to ping i will go try now.

---

### Post by garylouden on 2006-12-10
ok instaed of an error when pinging it will jut run through it and tell me 100% packet loss and the internet page wouldnt load, it just hung.

so improving :D

---

### Post by bscbrit on 2006-12-10
Are you sure that you have working hardware in the laptop?

---

### Post by garylouden on 2006-12-10
99% sure, it was in use a couple days ago

---

### Post by garylouden on 2006-12-10
i have a usb conection i could use in my modem aswell incase that could be done but i know how crappy usb internet is

---

### Post by bscbrit on 2006-12-10
At the moment I am not confident to set up a USB modem - although there are many others on this forum who can.  

From the command line, try to ping your own ethernet card i.e.

ping 80.192.4.57

You will not need to connect the ethernet cable to do this test.

---

### Post by garylouden on 2006-12-10
ye that pings perfectly, 0.043ms avarage. not sure what that tells us though :S

---

### Post by bscbrit on 2006-12-10
It tells us that the ethernet card is working.  It is receiving the pings and returning them, even though it is all taking place inside the computer.  Please type ifconfig again and double check that the values that we inputted manually are the ones being shown.

Check the contents of /etc/network/interfaces (you can remove eth1, ath1 and the ones that gave error messages.  All you need configured are lo and eth0).

Check also the contents of /etc/resolv.conf to make sure it reflects the correct DNS values that we input.

---

### Post by garylouden on 2006-12-10
in resolv.conf it says

nameserver 62.31.64.57
nameserver 62.31.112.39

---

### Post by bscbrit on 2006-12-10
The first DNS value is wrong - it should be 62.31.64.39    Either edit it directly or go back to your network configuration window and correct it there.  Restart the networking.  Try to ping [www.ubuntuforums.org](www.ubuntuforums.org) or ping 82.211.81.186 both from the commandline.  We are getting closer but not quite there yet.

---

### Post by garylouden on 2006-12-10
pinging them doesnt do anything still. 100 loss.......is this a lost cause?

---

### Post by garylouden on 2006-12-10
maybe a problem i never noticed before. im not sure though


[[IMG]http://img294.imageshack.us/img294/2306/screenshot4rw7.png[/IMG]](http://imageshack.us)

---

### Post by strabes on 2006-12-10
probably a dumb question, but i thought I would ask it since you said you switch the ethernet cord every time. Do you plug the ethernet cord in when the computer is off and then turn it on? Usually that seems to help it connect for me. You can also run ```
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by bscbrit on 2006-12-10
Why should that be a problem - I'm not sure what it is that you have seen in the image that you sent to me.

However, I'm inclined to believe that there is something wrong with the card but I'm not sure.  Have you got a Windows OS on a CD that you can load to see if it helps.  I realise that most computers nowadays come without a CD but I have W95, W98, W2K and XP here but that is not much use to us at the moment. Basically, I would like to have a confidence check that the card is, in fact, working before we spend many hours trying to fix the unfixable. If the card works, I don't mind spending any amount of time getting it to work under Ubuntu.

---

### Post by bscbrit on 2006-12-10
Hello strabe, it's certainly worth a try.

---

### Post by garylouden on 2006-12-10
i have xp, i will try the turn off and on thing and then format and install xp and see if the card will infact work :D

if it doesnt is there any way for me to get the computer conected to the net?

---

### Post by bscbrit on 2006-12-10
Yes, we can always go the USB route but that can be tricky at times.  However, if your ethernet card doesn't work under XP then you may have no option.  If it does work then it's entirely up to you.  I am quite prepared to continue until we have a working Ubuntu system.

---

### Post by garylouden on 2006-12-10
ok turning off thing didnt work, in middle of formating and then install xp.

this is gona take ages as i only got a 24x cdrom...

---

### Post by garylouden on 2006-12-10
ok small questing once the hdd has been formated by ubuntu does it become unformatable by windows becuase now when i put my xp disk in  it gives an error. is there a way to format the disk via linux?

---

### Post by bscbrit on 2006-12-10
It depends what kind of CD you have.  If it is an upgrade, then it expects to find another earlier windows OS on the drive.  If not, it should be able to reformat the drive itself.  Short answer, yes XP will have to reformat because windows can't cope with ext3.

---

### Post by garylouden on 2006-12-10
ok well its a full versio and its erroring but i can install linux fine........

this is getting ridiculas

---

### Post by bscbrit on 2006-12-10
Does the XP disk not allow you to reformat before it tries to install?

---

### Post by garylouden on 2006-12-10
it errors before i have any option....

---

### Post by bscbrit on 2006-12-10
I'm not sure what you mean - does the CD have errors or is it reporting that the drive has errors?

Either way, you can reformat from Linux but only if you have gparted or qtparted already installed.  I don't think Linux can reformat to NTFS although it should be able to do FAT32 and XP can quite happily load to that.

---

