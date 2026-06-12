---
title: "Help with internet"
date: 2007-02-12
forum: General Help
---

### Post by scannerman on 2007-02-12
Hi, i am a complete 100% newbie when it comes to Linux but was advised to try it a few days ago. 

I was told that ubuntu was an easy os to start Linux with, so i downloaded ubuntu and burnt it onto a disk.

Now i have been running ubuntu from the live cd just to get a feel for the system, but the problem i have been having is that when ever i press the firefox button i cannot connect to the internet? A bit confusing so if anyone can shed any light on the subject i would be grateful for there advice.

Thanks

---

### Post by phiphedog on 2007-02-12
Are you able to access the internet through any other applications or is it just firefox?

---

### Post by scannerman on 2007-02-12
I have not tried getting onto the internet with any applications as being completely new to ubuntu i am not entirely sure what i am doing!!

Whenever i reboot back to windows i can go online ok and when i check my setting of my modem everything is working and says i am online on ubuntu so i am not sure where i am making the mistake?

It is a bit daunting for a newbie i must admit as i have only ever used windows and i dont really want to stop trying linux so early on.

---

### Post by phiphedog on 2007-02-12
Try another appliaction like GAIM (an instant messaging client) Feel safe you will not do any harm to your system using the live CD.

Go to Applications-->Accessories-->terminal and type [COLOR="Red"]ifconfig /all[/COLOR] and see if you have an IP address. Also see if you can ping your default gateway/router

---

### Post by scannerman on 2007-02-12
I tried what you said but all it says is that there is no such file or folder

---

### Post by seppo on 2007-02-12
ifconfig /all is not correct. I should be:

/sbin/ifconfig

Do you know if you're router provides a DHCP address or did you configure a static IP address?

---

### Post by scannerman on 2007-02-12
I have no idea what a DHCP is??

When i configure my router i type in the ip given on the router box and then type in my log in details provided by my internet provider. I have checked this when i have been running ubuntu and it says that i am connected but when i click on firefox i still cannot connect to any web pages.

I tried typing in /sbin/ifconfig and was given alot of information which i have to say does not mean alot to me!! It did say eth and it did give the ip that i use to configure my router, but i dont know how to translate it into what i can understand!!

Told you i was a newbie!!!

---

### Post by seppo on 2007-02-12
> **scannerman said:**
> I have no idea what a DHCP is??

When i configure my router i type in the ip given on the router box and then type in my log in details provided by my internet provider. I have checked this when i have been running ubuntu and it says that i am connected but when i click on firefox i still cannot connect to any web pages.

I tried typing in /sbin/ifconfig and was given alot of information which i have to say does not mean alot to me!! It did say eth and it did give the ip that i use to configure my router, but i dont know how to translate it into what i can understand!!

Told you i was a newbie!!!

Every beginning is difficult. Lets see if we can get your box running :-)

I assume you have one networkcard which is called eth0 in your pc. The atual interesting part is: /sbin/ifconfig eth0

It should give you something like this:

```

eth0      Link encap:Ethernet  HWaddr 00:15:60:95:9B:4E
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:60ff:fe95:9b4e/64 Scope:Link

```

inet addr is the ip address of your pc. Please post your output

---

### Post by poise on 2007-02-12
I have had the same problem, 
I did have a Kingstone 10/100 adapter card installed and have had no end of trouble trying to use it on my linux system, it seems Linux dvrs were the problem, they switched my cnx from 100 to 10 and then complained that the connection was too slow lol. I replaced the card with a Realtek one costing £4 and now have no problems at all.

I have read that some hardware does have problems with linux dvrs

---

### Post by scannerman on 2007-02-12
This is what i get when i type in /sbin/ifconfig

etho   link encap: etherner    hwaddr 00:20:ed:b4:ef:de
         inet addr:   192.168.1.2   bcast: 192.168.1.255
         mask: 255.255.255.0

         inet6 addr: fe80::220:edff:feb4:efde/64 scope:link

I tried to print this off but the printer would not work either!! It feels terrible when you not in control!!!

---

### Post by phiphedog on 2007-02-12
ok, so you seem to have an IP address that has been assigned to your computer by your router (via DHCP) and you mentioned that you are able to access the router from your linux machine. Let's see if your DNS is working. In A terminal type [COLOR="Red"]whois [www.google.com](www.google.com) [/COLOR]and see if it resolves the address to an IP address.

---

### Post by scannerman on 2007-02-12
Am pretty sure i inputted it right but when i did it did not come up with anything?

I went to accessories then to terminal and typed whois [www.google.com](www.google.com)

Is there anything else i need to be doing in order to get this woring? Should i be able to connect to the internet from ubuntu using the live cd?

Sorry if this is taking a while to work it out but as i said before its a killer when you new to a new operating system.

---

### Post by phiphedog on 2007-02-12
Yeah the internet should work from the live cd.

While you are in windows, find out your DNS server by going to START-->RUN and typing cmd to get a dos prompt. Then type [COLOR="Red"]ipconfig /all [/COLOR] and take note of your DNS server.

Then in Ubuntu run the command [COLOR="Red"]sudo gedit /etc/resolv.conf[/COLOR] and add the line [COLOR="Red"]nameserver *dns server ipaddress*[/COLOR]

My resolv.conf file only has the line
[COLOR="Red"]nameserver 10.1.1.1[/COLOR]

then test it out with the command
[COLOR="Red"]dig [www.google.com](www.google.com)[/COLOR]

let us know how this goes

---

### Post by scannerman on 2007-02-13
I tried typing  sudo gedit /etc/resolv.conf as you said but it kept saying bad command, so i typed in dig [www.google.com](www.google.com) to see what it said, this is waht came up:

;<<>>Dig 9.3.2 <<>>[www.google.com](www.google.com)
;;global options: printcmd
;;Got answer:
;;->>HEADER<<-opcode: QUERY, status: NOERROR, id: 14735
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;;QUESTION SECTION:
;[www.google.com](www.google.com).    IN  A

;;ANSWER SECTION:
[www.google.com](www.google.com).       603512 IN  CNAME  [www.1.google.com](www.1.google.com).
[www.1.google.com](www.1.google.com).    78        IN    A   216.239.59.103
[www.1.google.com](www.1.google.com).    78        IN    A   216.239.59.104
[www.1.google.com](www.1.google.com).    78        IN    A   216.239.59.99
[www.1.google.com](www.1.google.com).    78        IN    A   216.239.59.147


;;Query time: 34msec
;;SERVER:192.168.1.1#53(192.168.1.1)

Does this provide any clues as to why its not connecting??
ANy help is greatly appreciated as i must admit i am starting to really like ubuntu, it seems as if everything is to hand and much easier than windows!!

---

### Post by phiphedog on 2007-02-13
I'm fresh out of ideas. It seems like from your last post that your DNS is working correctly, it is accessing the interent to resolve [www.google.com](www.google.com) into an IP address. 

I'd assume by this that you can update your system using synaptic or from a terminal windows using [COLOR="Red"]apt-get update [/COLOR]and [COLOR="red"]apt-get upgrade[/COLOR]. If this is the case then I'd suggest you try another browser like Mozilla or Opera to see if the problem is just related to Firefox.

---

