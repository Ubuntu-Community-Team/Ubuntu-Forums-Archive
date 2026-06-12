---
title: "What does this UPS related message mean?"
date: 2013-10-22
forum: General Help
---

### Post by arroy_0209 on 2013-10-22
I am usning ubuntu12.04, and I use APC UPS. apcupsd 3.14.10 is installed. Now a days sometimes I receive a message like: 
```

Broadcast Message from root@desktop                                               
        (somewhere) at 19:08 ...                                               
                                                                               
Communications restored with UPS BACK-UPS-ES500

```
Can anybody please explain its implications? Why does the computer lose communication at times as reported?

---

### Post by tgalati4 on 2013-10-22
How are you connected to the UPS?  Serial cable, USB cable, ethernet cable?  Are there other computers on the same LAN using an APC UPS?  You can set them up as a "Master" and "Slave" and then they computicate with *apcupsd* through the LAN.  If one of the machines goes offline, or if there is a lot of network traffic (like streaming a high definition movie), it's possible to lose communication for a short time.  That would result in such messages.  Check the event logs in /var/log for more information.

---

### Post by SeijiSensei on 2013-10-22
I see this message from apcupsd from time to time.  It seems entirely harmless and is usually quite transitory.

---

### Post by arroy_0209 on 2013-10-22
Thanks for your comments. These details may be of help as you pointed out. I connect the UPS with USB cable and there are no other computers on LAN. So I guess the explanation regarding loss of communication with UPS is not applicable here. However I will note /var/log file and report.

Is it possible that these messages are related to transient power line voltage fluctuations?

---

### Post by SeijiSensei on 2013-10-22
I've considered that a possibility, too.  Maybe the USB port on the UPS can lose power in transients.  You'd think it would be behind the battery and thus protected, but who knows?

---

### Post by tgalati4 on 2013-10-22
My experience with APC UPS's is that they are quite slow to communicate.  If you send a serial command, you sometimes get a response.  When I write APC scripts, I always send commands in triples, with a delay between each, to improve reliability.  I'm not sure about USB communication, but it could simply be USB-to-serial protocol, so the problem is still the same.  If you don't see any errors in the logs, then I wouldn't worry about it.  If you get the errors frequently, then I would change cables or change USB ports and use a strain relief on the USB port on the computer.  The constant vibration can cause data dropouts.

---

### Post by buzzingrobot on 2013-10-22
My UPS goes offline when it does a self-test.

---

### Post by tgalati4 on 2013-10-23
Some UPS's will do a quick self-test once a week or once every other week, so that would explain the loss of communication.  You can sometimes turn off self-test or change the testing interval.

---

### Post by SeijiSensei on 2013-10-23
Aha, that's what it is.  I have a self-test event logged every two weeks at around 7 am.  It seems to be driven by the apcupsd daemon itself.  There are no associated cron files that I can see.  

The USB disconnection events are written directly to the screen in the RedHat/CentOS configuration I'm using.  I would turn on the monitor from time to time and see the notice.  So the link between the notices and the self-tests was not evident.

---

### Post by tgalati4 on 2013-10-23
My APC SMARTUPS has some dip switches in the back that control the self-test interval.  Newer UPS's may have other ways (via configuration webpage) to change the self-test interval.  I don't believe that apcupsd initiates the self test, because otherwise it would have settings in its configuration file.

---

### Post by arroy_0209 on 2013-10-24
I report relevant comments from log file following one such incident. Hope these will help detect the problem precisely.
> 
Oct 24 18:30:42 desktop kernel: [  462.192069] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Oct 24 18:30:42 desktop kernel: [  462.192079] usb 3-1: USB disconnect, device number 2
Oct 24 18:30:43 desktop kernel: [  462.440065] usb 3-1: new low-speed USB device number 3 using uhci_hcd
Oct 24 18:30:43 desktop mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1"
Oct 24 18:30:44 desktop kernel: [  463.246657] generic-usb 0003:051D:0002.0002: hiddev0,hidraw0: USB HID v1.10 Device [American Power Conversion Back-UPS ES 500 FW:850.m3.I USB FW:m3] on usb-0000:00:1d.1-1/input0
Oct 24 18:30:44 desktop mtp-probe: bus: 3, device: 3 was not an MTP device
Oct 24 18:30:49 desktop apcupsd[1108]: Communications with UPS restored.


On the terminal as usual I received this message:
> 
Broadcast Message from root@desktop                                               
        (somewhere) at 18:30 ...                                               
                                                                               
Communications restored with UPS BACK-UPS-ES500  


I am unable to follow these so request clarification from experienced users in the forum. Second issue is, I want to know how to do a selftest on my APC-UPS with ubuntu12.04. Can anybody suggest how to do it?

---

### Post by SeijiSensei on 2013-10-24
> **tgalati4 said:**
> My APC SMARTUPS has some dip switches in the back that control the self-test interval.  Newer UPS's may have other ways (via configuration webpage) to change the self-test interval.  I don't believe that apcupsd initiates the self test, because otherwise it would have settings in its configuration file.

The bottom of my version of /etc/apcupsd/apcupsd.conf contains these lines:

```

# Self test interval in hours 336=2 weeks, 168=1 week, ON=at power on
# SELFTEST 336 168 ON OFF  (default = 336)
#SELFTEST 336

```

This is version 3.14.10 running on CentOS 5.8.

> **arroy_0209 said:**
> I want to know how to do a selftest on my APC-UPS with ubuntu12.04. Can anybody suggest how to do it?

If you stop the apcupsd daemon then run the apctest command, you'll get a menu of options.  Item 2 on the list in my version is to perform a self-test.  It takes about a minute and all I got back was "PASSED".   There's also an option to change the self-test interval.

For a snapshot status report, use apcaccess while the daemon is running.

---

### Post by buzzingrobot on 2013-10-24
FWIW, my APC Smart UPS 750 runs its self tests independently of the hardware plugged into it.  I.e., on its own.  Perhaps yours does, as well. There's good documentation for each APS model on their site.

---

### Post by arroy_0209 on 2013-10-24
Thanks for your suggestions. However, besides trying to understand the issue of selftest, I would like to point out that we are still not very clear why I receive the message on terminal. Can somebody please read the details I have given in post #11 (this contains the message on the terminal and relevant comments from the log file) and explain what causes the message on the terminal?

Second, regarding selftest: as SeijiSensei suggested, I tried to use the command: apctest on terminal with the result
> 
2013-10-24 22:10:28 apctest 3.14.10 (13 September 2011) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = Network & ShareUPS Disabled
cable.type = USB Cable
mode.type = USB UPS Driver
Setting up the port ...
apctest FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
apctest error termination completed

This of course without following suggestion of SeijiSensei properly, since I had not first stopped the apcupsd daemon. I do not know how to do it. Should I try > /etc/init.d/apcupsd stop, then run apctest command on terminal, get results and then use > /etc/init.d/apcupsd start (to go back to original configuration)? Please clarify my doubts. I am sorry to ask so many doubts in one thread (rather than breaking in different threads) since my knowledge on these issues is too little to give me confidence.

(I am attaching output of "apcaccess" command, which may be of help:
APC      : 001,038,0957
DATE     : 2013-10-24 22:21:29 +0530  
HOSTNAME : desktop
VERSION  : 3.14.10 (13 September 2011) debian
UPSNAME  : BACK-UPS-ES500
CABLE    : USB Cable
DRIVER   : USB UPS Driver
UPSMODE  : Stand Alone
STARTTIME: 2013-10-24 21:27:34 +0530  
MODEL    : Back-UPS ES 500 
STATUS   : TRIM ONLINE 
LINEV    : 250.8 Volts
LOADPCT  :   0.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT : 182.6 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : High
LOTRANS  : 195.0 Volts
HITRANS  : 255.0 Volts
ALARMDEL : No alarm
BATTV    : 14.4 Volts
LASTXFER : No transfers since turnon
NUMXFERS : 0
TONBATT  : 0 seconds
CUMONBATT: 0 seconds
XOFFBATT : N/A
SELFTEST : NO
STATFLAG : 0x0700000A Status Flag
MANDATE  : 2000-07-30
SERIALNO : NB18008004272 
BATTDATE : 2000-07-30
NOMOUTV  : 230 Volts
NOMINV   : 230 Volts
NOMBATTV :  12.0 Volts
NOMPOWER : 300 Watts
FIRMWARE : 850.m3.I USB FW:m3
END APC  : 2013-10-24 22:21:35 +0530 )

---

### Post by tgalati4 on 2013-10-24
This is troubling:

Oct 24 18:30:42 desktop kernel: [ 462.192069] hub 3-0:1.0: port 1 **disabled by hub (EMI?)**, re-enabling...

Does EMI mean electro-magnetic interference?  Or Cosmic Rays?  Does anyone know why the kernel would issue such a log?

I think that the USB hub on the computer is having problems and the kernel is resetting it.  That results in a lack of USB communication and thus the APC communication logs.

Has the computer been cleaned recently?  If not, then it is due for cleaning and reseating of all cables and power connections.  All it takes is some conductive dust to mess up the on-board USB controllers.

The fact that *apctest* does not work points to a communication problem.  It could also be dust inside the UPS.  They can get dirty since they are usually on the floor.  Any electronics needs to be a least 1 foot off of the floor to reduce dust intrusion.

Pull both apart and inspect for dust and critters.

---

### Post by SeijiSensei on 2013-10-24
If apcupsd has been converted to work with the [Upstart](http://upstart.ubuntu.com/) method that Ubuntu now uses to manage daemons, then the proper command sequence would be:

```
sudo service apcupsd stop
sudo apctest
sudo service apcupsd start

```

If the init scripts for apcupsd are not configured for upstart then you should use "/etc/init.d/apcupsd start|stop" instead as you suggest.

---

### Post by arroy_0209 on 2013-10-25
Thanks. The result of sudo apctest is as follows:
> 
2013-10-25 12:50:54 apctest 3.14.10 (13 September 2011) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = Network & ShareUPS Disabled
cable.type = USB Cable
mode.type = USB UPS Driver
Setting up the port ...
Doing prep_device() ...

You are using a USB cable type, so I'm entering USB test mode
Hello, this is the apcupsd Cable Test program.
This part of apctest is for testing USB UPSes.

Getting UPS capabilities...SUCCESS

Please select the function you want to perform.

1)  Test kill UPS power
2)  Perform self-test
3)  Read last self-test result
4)  View/Change battery date
5)  View manufacturing date
6)  View/Change alarm behavior
7)  View/Change sensitivity
8)  View/Change low transfer voltage
9)  View/Change high transfer voltage
10) Perform battery calibration
11) Test alarm
12) View/Change self-test interval
 Q) Quit

Select function number: 2


This test instructs the UPS to perform a self-test
operation and reports the result when the test completes.

Clearing previous self test result...CLEARED
Initiating self test...INITIATED
Waiting for test to complete...ERROR READING STATUS
29.768 apcupsd: linux-usb.c:784 HIDIOCGREPORT for function SelftestStatus failed. ERR=No such device

It is surprising that this results in "No such device". What would be the next step?

*****
Just after posting the report above, I did selftest again, but this time without first using command: "sudo service apcupsd stop" and surprisingly this time the result was: > 
Clearing previous self test result...CLEARED
Initiating self test...INITIATED
Waiting for test to complete...COMPLETED
Result of last self test: PASSED
. But I am not sure if this is the correct way (i.e., without first stopping service apcupsd); as I confessed before my knowledge is too little. Anyway what conclusion is to be drawn? We are still not sure what causes the problem I first stated. I will of course do the cleaning as suggested by tgalati4.

---

### Post by tgalati4 on 2013-10-25
What is the manufacturing date of the UPS?  Can you read the other values from *apctest*?  

It's possible that *apctest* now allows operation with *apcupsd* still running.  Since you would want to test the UPS without disrupting operations, although if your UPS is defective, then it helps to stop the service so that anyone else that relies on the shutdown notice would not be disturbed during testing.

I'm guessing the age and condition of the UPS are a factor.

---

### Post by arroy_0209 on 2013-10-25
Thanks. the apcaccess command gives "MANDATE  : 2000-07-30" if this denotes date of manufacturing date, then it is quite old. But I have doubt about that. I purchased it during 2004 perhaps.

---

