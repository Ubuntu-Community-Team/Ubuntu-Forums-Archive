---
title: "pppd daemon died unexpectedly"
date: 2007-08-18
forum: General Help
---

### Post by mykrob on 2007-08-18
Hey-

I performed a clean Kubuntu installation on a friend's computer last night.I got his Agere/Lucent Winmodem working for the most part. It gets a dial tone, it tries to dial, attmepts a handshake..

But then it stops, stating the pppd daemon died unexpectedly.

He is using KPPP to dial up to his Earthlink account. 

What can we do to resolve this?

Thanks,
-myk

---

### Post by mykrob on 2007-08-19
bump

---

### Post by mykrob on 2007-08-20
bump

---

### Post by mykrob on 2007-08-22
would a moderator move this to **General Help** so it can get more exposure, please?

Thanks,
-myk

---

### Post by jimbob on 2007-08-22
Don't really know specifically but try installing Gnome-ppp via Synaptic and see if that treats you any better.

It should work fine with Kubuntu.  I had a similar but reverse problem a couple of years ago in that Gnome-ppp would drop the line but KPPP worked just fine.
 &#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by RJARRRPCGP on 2007-08-22
> **mykrob said:**
> Hey-

I performed a clean Kubuntu installation on a friend's computer last night.I got his Agere/Lucent Winmodem working for the most part. It gets a dial tone, it tries to dial, attmepts a handshake..

But then it stops, stating the pppd daemon died unexpectedly.

He is using KPPP to dial up to his Earthlink account. 

What can we do to resolve this?

Thanks,
-myk


*Known issue* Also, it's not because of EarthLink. Had the same problem with SoVerNet (Vermont), too! 

That was when using Kubuntu Dapper Drake.

Also, it's not because of the modem. 

Apparently, KPPP needs major work!

---

### Post by cebobbitt on 2007-08-23
Have you tried pppconfig? That worked for me even when gnome-ppp wouldn't. Just go to the terminal and type pppconfig and follow the setup. I use gkrellm for the pon and poff. Good Luck

---

### Post by maxrisc on 2007-08-23
On the latest Gutsy this is still a problem.

I am using a Sprint EVDO network card that uses pppd.  Kppp was working fine until I did the latest update.  Now there are all kinds of problems with staying connected.   It is very random.

I am going to the console to set this up in daemon mode and try it for a couple of hours.  I will report back with my findings.

---

### Post by maxrisc on 2007-08-23
Configured it and setup a connection.  It doesn't work.  It still dies out.

Hmmm

---

### Post by maxrisc on 2007-08-23
KPPP uses connect script /etc/ppp/peers/ppp0 on boot.

I edited this file and added a "noauth" message at the top.  This was a bug back in 6.06.

Current ppd version is 2.2.4

---

### Post by maxrisc on 2007-08-23
That died too.

Problem is still unresolved with PPPD 2.2.4

I have tried Gnome, KDE and Direct Dial with pon

I have tried setting noauth but it didn't make a difference.

Even with active keepalive ping going the connect still drops at 7 minutes maximum connection time.

Card doesn't drop on Windows (cringe) box at all.  

Ideas?

---

### Post by maxrisc on 2007-08-23
[SOLVED]

I didn't think I would have to resort to hacks to keep the connection up.

The problem is pppd wants to be run as root.  If I start it as root then it stays up and running.  If I start it as a user it stays up between 5 and 10 minutes then throws "error 16 pppd died unexpectedly"

So I got under the hood and did it old school.

Steps

1. Calm down. No one needs to die just yet.

2. Setup your connection using KPPP.  (Skip this if you already got it setup.)

3. Open a terminal and do the following:

```

sudo chmod u+s /usr/sbin/pppd
sudo chmod 666 /dev/ttyACM0
sudo chmod u+s /usr/bin/kppp
sudo poff -a

```

Change your /dev/tty in the second statement to use the serial port you are on.  Mine is a Sprint EVDO connection and uses ACM.  If you are dialup it will look something like /dev/ttyS4.

Once all that is sorted then fire up your kppp connection as a regular user.   Mine has been up almost 15 minutes now and working fine.

Enjoy your stable internet connection.

(This is a security issue in that you are allowing anyone on the machine to effectively run these things directly as root so if they are hackable then someone could pwn your box)

I highly suggest running a firewall when being connected to the Internet even over dialup.

---

### Post by maxrisc on 2007-08-23
Yes this can be done with the above and yes I can do sudo kppp but I spend a lot of time on console outside of X.

The above allows the pppd to load on boot and corrects a problem with my Xgl sessions hanging.

---

### Post by mykrob on 2007-08-23
thanks for the responses, guys!

I will try your suggestion and see what happens.. On a side note, please keep it coming!

-myk

---

### Post by RJARRRPCGP on 2007-08-23
> **cebobbitt said:**
> Have you tried pppconfig? That worked for me even when gnome-ppp wouldn't. Just go to the terminal and type pppconfig and follow the setup. I use gkrellm for the pon and poff. Good Luck

I agree. pppconfig and pon (ISP name) worked fine for me when I used to have POTS.

---

### Post by mykrob on 2007-08-24
still having trouble.. KPPP and Gnome PPP and wvdial all will dial out and connect, then crash.. KPPP complains that it timed out waiting on ppp interface to start.. The others dont provide enough of a message to help..

Anyone?

thanks,
-myk

---

### Post by mykrob on 2007-08-24
here's a little more info:

```

Aug 24 18:36:51 ubuntu pppd[6177]: pppd 2.4.4 started by sherwin, uid 1000
Aug 24 18:36:51 ubuntu pppd[6177]: using channel 9
Aug 24 18:36:51 ubuntu pppd[6177]: Using interface ppp0
Aug 24 18:36:51 ubuntu pppd[6177]: Connect: ppp0 <--> /dev/ttyLTM0
Aug 24 18:36:51 ubuntu pppd[6177]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xd305a1cf> <pcomp> <accomp>]
Aug 24 18:37:08 ubuntu pppd[6177]: Hangup (SIGHUP)
Aug 24 18:37:08 ubuntu pppd[6177]: Modem hangup
Aug 24 18:37:08 ubuntu pppd[6177]: Connection terminated.
Aug 24 18:37:08 ubuntu pppd[6177]: Exit.

```

---

### Post by mykrob on 2007-08-24
lemme change this up a bit...

I need information on internal modems that DEFINITELY work with Ubuntu/Kubuntu

I have an opportunity to visit a friend's computer shop tomorrow and he has boxes upon boxes of modems to choose from..

I'd like to have somewhat of a listing or working modems before i go.
Thanks,
-myk

---

### Post by cebobbitt on 2007-08-24
If you have a serial port you might want to consider a hardware modem.  I use a Modem Blaster by Creative on ttyS0. I got it at Best Buy for about 60 bucks and it has worked flawlessly. If you dont' have a serial port then I don't know if you can use a dongle or not. Best of Luck

---

### Post by mykrob on 2007-08-25
i ordered a BestData external serial modem that says it works with LInux. Ubuntu will not even recognize it for some reason..

go figure.

---

### Post by _duncan_ on 2007-08-25
what dialer program are you using?

Sometimes a hardware modem will still work even if it's not recognized, as long as you specify the correct port. If you only have one serial port then it's probably /dev/ttyS0.

---

### Post by mykrob on 2007-08-25
i get similar results using KPPP, Gnome-PPP or wvdial

---

### Post by maxrisc on 2007-08-25
It's hard to troubleshoot a modem remotely without being able to see the output or run AT commands on it.

Have you tried the manufacturer's website?  Some internal modems require configuration (read AT initialization) before you can use them with your dialer.

---

### Post by jimbob on 2007-08-25
Post a link that gives the specs on the BestData modem.

---

### Post by mykrob on 2007-08-25
[http://www.geeks.com/details.asp?invtid=56SX92WB-BULK&cat=MDM](http://www.geeks.com/details.asp?invtid=56SX92WB-BULK&cat=MDM)


thanks for helping me out, guys.

---

### Post by cebobbitt on 2007-08-25
when you say Ubuntu won't recongize it, do you mean autodetect? If so, It didn't in my case either, but you can just type in the location and proceed on. I first tested mine on wvdial and then later gnome-ppp. It will work with pppconfig also. With the modem on and connected to the serial port, type in the terminal, sudo wvdial and see if it sees it. Good Luck

---

### Post by jimbob on 2007-08-25
Couple of thoughts here.

Make sure you are root when running according to some posts I have read.

Also, do you have another dialup number from another ISP you could try temporarily?  I had trouble with Verizon a couple of years ago but it would work ok with other ISP's.

---

### Post by mykrob on 2007-08-25
i tried some free ISP's and got the same result (with the PCI internal modem)


As for the BestData serial modem, it does not show up when I run lspci or check KInfoCenter, which leads me to believe it is simplynot detected. I tried KPPP using every single entry they had listed for a modem to try, and all of them claimed there was no modem..

How can i gain access to this modem? I guess it is not autodetecting, as you said... but how can i make it detect? It is definitely a hardware serial modem i have.

thanks,
-myk

---

### Post by jimbob on 2007-08-26
Have you tried the BestData modem with another operating system to make sure it is not the modem or your other hardware?

I have read some other posts that claim early versions of that modem worked great but later hardware/firmware releases failed to work at all.

---

### Post by mykrob on 2007-08-26
i tried it booting from a KNoppix CD, and it didnt seem to detect it either. I have a friend from Massachussetts who is mailing me some PCI modems that work with the Linuxant driver. Hoping that will solve my problem.

-myk

---

