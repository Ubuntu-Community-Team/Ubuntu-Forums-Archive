---
title: "Issues with Gammu SMS"
date: 2020-09-30
forum: General Help
---

### Post by etagnirps on 2020-09-30
Hi all,

New to the forums, so hopefully I have this in the right place! This could be a long winded post, but the more info the better I guess!?

I am currently banging my head against a desk over an issue with gammu and SMS messages using a virtual server to send the messages through a physical server acting as a relay. The reason for this setup is we have a virtual monitoring box connected to the physical server that needs to send out messages without having to rely on the rest of the network, so we have directly attached the VM (server2) to the physical GSM server (server1, hopefully this makes sense!)

The setup I have is:

server1 - physical server with the USB GSM modem installed - running Ubuntu 16.04.1 LTS
server2 - a virtual machine connected directly to server1 via a Hyper-V switch - also running Ubuntu 16.04.1 LTS

SMS messaging works locally on the server with the USB modem in, the config file is as below:
[gammu]

port = /dev/ttyUSB0
#model = at
connection = at
#synchronizetime = yes
logfile = /user1/gammurc_log
logformat = textalldate
use_locking = no
gammuloc = no

user1@server1:~# gammu sendsms TEXT XXXXXXXXXX -text "Test system message"
If you want break, press Ctrl+C...
Sending SMS 1/1....waiting for network answer..OK, message reference=217

And the message comes through to my phone pretty much instantly


=====
However on remote server2 that I want to use to send SMS' using the physical server above as the relay point it fails.  It apears to send the command through fine but seems to think ttyUSB0 is unplugged?

I can run a gammu identify and it reads the correct information below:
user1@server2:~# gammu identify
user1@server1's password:
Device               : ssh user1@server1 /usr/local/bin/gammu-backend /dev/ttyUSB0
Manufacturer         : Huawei
Model                : unknown (E122)
Firmware             : 11.005.00.04.21
IMEI                 : <IMEI matches>
SIM IMSI             : <IMSI matches>


When I send a test SMS command the below is the output that I get:
user1@server2:~# gammu sendsms TEXT XXXXXXXXXX -text "Relay messaging test"
user1@server1IP password:
If you want break, press Ctrl+C...
Sending SMS 1/1No response in specified timeout. Probably phone not connected.

The config file on server2 is below:
[gammu]
#port =
model = at
device = ssh user1@server1 /usr/local/bin/gammu-backend /dev/ttyUSB0
connection = proxyat
#synchronizetime =
logfile = /root/gammurc_log
logformat = textalldate
#use_locking =
#gammuloc =




The logs for this duration are below:
Wed 2020/09/30 15:08:35: [Gammu            - 1.37.0]
Wed 2020/09/30 15:08:35: [Connection       - "proxyat"]
Wed 2020/09/30 15:08:35: [Connection index - 0]
Wed 2020/09/30 15:08:35: [Model type       - "at"]
Wed 2020/09/30 15:08:35: [Device           - "ssh user1@server1 /usr/local/bin/gammu-backend /dev/ttyUSB0"]
Wed 2020/09/30 15:08:35: [Running on       - Linux, kernel 4.4.0-31-generic (#50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016)]
Wed 2020/09/30 15:08:35: [Module           - "A2D|iPAQ|at|M20|S25|MC35|TC35|C35i|S65|S300|5110|5130|5190|5210|6110|6130|6150|6190|6210|6250|6310|6310i|6510|7110|8210|8250|8290|8310|8390|8850|8855|8890|8910|9110|9210"]
Wed 2020/09/30 15:08:35: Escaping SMS mode
Wed 2020/09/30 15:08:35: SENDING frame type 0x00/length 0x02/2
Wed 2020/09/30 15:08:35: 1B |0D                                                          ..
Wed 2020/09/30 15:08:35: Sending simple AT command to wake up some devices
Wed 2020/09/30 15:08:35: SENDING frame type 0x00/length 0x03/3
Wed 2020/09/30 15:08:35: 41A|54T|0D                                                      AT.
Wed 2020/09/30 15:08:39: 1 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x04/4
Wed 2020/09/30 15:08:39: 4FO|4BK|0D |0A                                                  OK..
Wed 2020/09/30 15:08:39: Enabling echo
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x05/5
Wed 2020/09/30 15:08:39: 41A|54T|45E|311|0D                                              ATE1.
Wed 2020/09/30 15:08:39: 1 "ATE1"
Wed 2020/09/30 15:08:39: 2 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x0B/11
Wed 2020/09/30 15:08:39: 41A|54T|45E|311|0D |0D |0A |4FO|4BK|0D |0A                      ATE1...OK..
Wed 2020/09/30 15:08:39: Trying Motorola mode switch
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0A/10
Wed 2020/09/30 15:08:39: 41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                          AT+MODE=2.
Wed 2020/09/30 15:08:39: 1 "AT+MODE=2"
Wed 2020/09/30 15:08:39: 2 "COMMAND NOT SUPPORT"
Wed 2020/09/30 15:08:39: Checking line: COMMAND NOT SUPPORT
Wed 2020/09/30 15:08:39: AT reply state: 3
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x21/33
Wed 2020/09/30 15:08:39: 41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |43C|4FO|4DM|4DM AT+MODE=2...COMM
Wed 2020/09/30 15:08:39: 41A|4EN|44D|20 |4EN|4FO|54T|20 |53S|55U|50P|50P|4FO|52R|54T|0D  AND NOT SUPPORT.
Wed 2020/09/30 15:08:39: 0A                                                              .
Wed 2020/09/30 15:08:39: Seems not to be supported
Wed 2020/09/30 15:08:39: Enabling CME errors
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0A/10
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|4DM|45E|45E|3D=|311|0D                          AT+CMEE=1.
Wed 2020/09/30 15:08:39: 1 "AT+CMEE=1"
Wed 2020/09/30 15:08:39: 2 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x10/16
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|4DM|45E|45E|3D=|311|0D |0D |0A |4FO|4BK|0D |0A  AT+CMEE=1...OK..
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x09/9
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|53S|43C|53S|3F?|0D                              AT+CSCS?.
Wed 2020/09/30 15:08:39: 1 "AT+CSCS?"
Wed 2020/09/30 15:08:39: 2 "+CSCS: "GSM""
Wed 2020/09/30 15:08:39: 3 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x1F/31
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53S AT+CSCS?...+CSCS
Wed 2020/09/30 15:08:39: 3A:|20 |22"|47G|53S|4DM|22"|0D |0A |0D |0A |4FO|4BK|0D |0A      : "GSM"....OK..
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0A/10
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|53S|43C|53S|3D=|3F?|0D                          AT+CSCS=?.
Wed 2020/09/30 15:08:39: 1 "AT+CSCS=?"
Wed 2020/09/30 15:08:39: 2 "+CSCS: ("IRA","UCS2","GSM")"
Wed 2020/09/30 15:08:39: 3 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x2F/47
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|53S|43C|53S|3D=|3F?|0D |0D |0A |2B+|43C|53S|43C AT+CSCS=?...+CSC
Wed 2020/09/30 15:08:39: 53S|3A:|20 |28(|22"|49I|52R|41A|22"|2C,|22"|55U|43C|53S|322|22" S: ("IRA","UCS2"
Wed 2020/09/30 15:08:39: 2C,|22"|47G|53S|4DM|22"|29)|0D |0A |0D |0A |4FO|4BK|0D |0A      ,"GSM")....OK..
Wed 2020/09/30 15:08:39: Chosen GSM as normal charset
Wed 2020/09/30 15:08:39: Chosen UCS2 as unicode charset
Wed 2020/09/30 15:08:39: Getting model
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x08/8
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|47G|4DM|4DM|0D                                  AT+CGMM.
Wed 2020/09/30 15:08:39: 1 "AT+CGMM"
Wed 2020/09/30 15:08:39: 2 "E122"
Wed 2020/09/30 15:08:39: 3 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x16/22
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|47G|4DM|4DM|0D |0D |0A |45E|311|322|322|0D |0A  AT+CGMM...E122..
Wed 2020/09/30 15:08:39: 0D |0A |4FO|4BK|0D |0A                                          ..OK..
Wed 2020/09/30 15:08:39: Unknown model, but it should still work
Wed 2020/09/30 15:08:39: [Model name: `E122']
Wed 2020/09/30 15:08:39: [Model data: `']
Wed 2020/09/30 15:08:39: [Model data: `unknown']
Wed 2020/09/30 15:08:39: [Connected model  - "E122"]
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x08/8
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|47G|4DM|49I|0D                                  AT+CGMI.
Wed 2020/09/30 15:08:39: 1 "AT+CGMI"
Wed 2020/09/30 15:08:39: 2 "huawei"
Wed 2020/09/30 15:08:39: 3 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x18/24
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|47G|4DM|49I|0D |0D |0A |68h|75u|61a|77w|65e|69i AT+CGMI...huawei
Wed 2020/09/30 15:08:39: 0D |0A |0D |0A |4FO|4BK|0D |0A                                  ....OK..
Wed 2020/09/30 15:08:39: Manufacturer info received
Wed 2020/09/30 15:08:39: [Manufacturer: Huawei]
Wed 2020/09/30 15:08:39: Checking for OBEX support
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0B/11
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|50P|52R|4FO|54T|3D=|3F?|0D                      AT+CPROT=?.
Wed 2020/09/30 15:08:39: 1 "AT+CPROT=?"
Wed 2020/09/30 15:08:39: 2 "COMMAND NOT SUPPORT"
Wed 2020/09/30 15:08:39: Checking line: COMMAND NOT SUPPORT
Wed 2020/09/30 15:08:39: AT reply state: 3
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x22/34
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|50P|52R|4FO|54T|3D=|3F?|0D |0D |0A |43C|4FO|4DM AT+CPROT=?...COM
Wed 2020/09/30 15:08:39: 4DM|41A|4EN|44D|20 |4EN|4FO|54T|20 |53S|55U|50P|50P|4FO|52R|54T MAND NOT SUPPORT
Wed 2020/09/30 15:08:39: 0D |0A                                                          ..
Wed 2020/09/30 15:08:39: Checking for SYNCML/OBEX support
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0C/12
Wed 2020/09/30 15:08:39: 41A|54T|2B+|53S|59Y|4EN|43C|4DM|4CL|3D=|3F?|0D                  AT+SYNCML=?.
Wed 2020/09/30 15:08:39: 1 "AT+SYNCML=?"
Wed 2020/09/30 15:08:39: 2 "COMMAND NOT SUPPORT"
Wed 2020/09/30 15:08:39: Checking line: COMMAND NOT SUPPORT
Wed 2020/09/30 15:08:39: AT reply state: 3
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x23/35
Wed 2020/09/30 15:08:39: 41A|54T|2B+|53S|59Y|4EN|43C|4DM|4CL|3D=|3F?|0D |0D |0A |43C|4FO AT+SYNCML=?...CO
Wed 2020/09/30 15:08:39: 4DM|4DM|41A|4EN|44D|20 |4EN|4FO|54T|20 |53S|55U|50P|50P|4FO|52R MMAND NOT SUPPOR
Wed 2020/09/30 15:08:39: 54T|0D |0A                                                      T..
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0D/13
Wed 2020/09/30 15:08:39: 41A|54T|24$|54T|53S|53S|50P|43C|53S|57W|3D=|3F?|0D              AT$TSSPCSW=?.
Wed 2020/09/30 15:08:39: 1 "AT$TSSPCSW=?"
Wed 2020/09/30 15:08:39: 2 "COMMAND NOT SUPPORT"
Wed 2020/09/30 15:08:39: Checking line: COMMAND NOT SUPPORT
Wed 2020/09/30 15:08:39: AT reply state: 3
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x24/36
Wed 2020/09/30 15:08:39: 41A|54T|24$|54T|53S|53S|50P|43C|53S|57W|3D=|3F?|0D |0D |0A |43C AT$TSSPCSW=?...C
Wed 2020/09/30 15:08:39: 4FO|4DM|4DM|41A|4EN|44D|20 |4EN|4FO|54T|20 |53S|55U|50P|50P|4FO OMMAND NOT SUPPO
Wed 2020/09/30 15:08:39: 52R|54T|0D |0A                                                  RT..
Wed 2020/09/30 15:08:39: Getting firmware versions
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x08/8
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|47G|4DM|52R|0D                                  AT+CGMR.
Wed 2020/09/30 15:08:39: 1 "AT+CGMR"
Wed 2020/09/30 15:08:39: 2 "11.005.00.04.21"
Wed 2020/09/30 15:08:39: 3 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x21/33
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|47G|4DM|52R|0D |0D |0A |311|311|2E.|300|300|355 AT+CGMR...11.005
Wed 2020/09/30 15:08:39: 2E.|300|300|2E.|300|344|2E.|322|311|0D |0A |0D |0A |4FO|4BK|0D  .00.04.21....OK.
Wed 2020/09/30 15:08:39: 0A                                                              .
Wed 2020/09/30 15:08:39: Received firmware version: "11.005.00.04.21"
Wed 2020/09/30 15:08:39: Number version is "11.005000"
Wed 2020/09/30 15:08:39: [Firmware version - "11.005.00.04.21"]
Wed 2020/09/30 15:08:39: [Connected]
Wed 2020/09/30 15:08:39: Checking used: UDH len 0, UsedBytes 0, FreeText 160, UsedText 0, FreeBytes 140
Wed 2020/09/30 15:08:39: Adding text
Wed 2020/09/30 15:08:39: Copy 160 (max 20)
Wed 2020/09/30 15:08:39: Defalt text, length 20 20
Wed 2020/09/30 15:08:39: Text added
Wed 2020/09/30 15:08:39: Checking at the end: UDH len 0, UsedBytes 18, FreeText 140, UsedText 20, FreeBytes 122
Wed 2020/09/30 15:08:39: 20 20
Wed 2020/09/30 15:08:39: Entering GSM_GetSMSC
Wed 2020/09/30 15:08:39: Getting SMSC
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x09/9
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|53S|43C|41A|3F?|0D                              AT+CSCA?.
Wed 2020/09/30 15:08:39: 1 "AT+CSCA?"
Wed 2020/09/30 15:08:39: 2 "+CSCA: "+447802002606",145"
Wed 2020/09/30 15:08:39: 3 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x2D/45
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|53S|43C|41A|3F?|0D |0D |0A |2B+|43C|53S|43C|41A AT+CSCA?...+CSCA
Wed 2020/09/30 15:08:39: 3A:|20 |22"|2B+|344|344|377|388|300|322|300|300|322|366|300|366 : "+447802002606
Wed 2020/09/30 15:08:39: 22"|2C,|311|344|355|0D |0A |0D |0A |4FO|4BK|0D |0A              ",145....OK..
Wed 2020/09/30 15:08:39: SMSC info received
Wed 2020/09/30 15:08:39: Parsing +CSCA: "+447802002606",145 with +CSCA: @p, @i
Wed 2020/09/30 15:08:39: Grabbed string from reply: "+447802002606" (parsed 15 bytes)
Wed 2020/09/30 15:08:39: Parsed phone string "+447802002606"
Wed 2020/09/30 15:08:39: Phone string decoded as "+447802002606"
Wed 2020/09/30 15:08:39: Parsed int 145
Wed 2020/09/30 15:08:39: Leaving GSM_GetSMSC
Wed 2020/09/30 15:08:39: Entering GSM_SendSMS
Wed 2020/09/30 15:08:39: Trying SMS PDU mode
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0A/10
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|4DM|47G|46F|3D=|300|0D                          AT+CMGF=0.
Wed 2020/09/30 15:08:39: 1 "AT+CMGF=0"
Wed 2020/09/30 15:08:39: 2 "OK"
Wed 2020/09/30 15:08:39: Checking line: OK
Wed 2020/09/30 15:08:39: AT reply state: 1
Wed 2020/09/30 15:08:39: RECEIVED frame type 0x00/length 0x10/16
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|4DM|47G|46F|3D=|300|0D |0D |0A |4FO|4BK|0D |0A  AT+CMGF=0...OK..
Wed 2020/09/30 15:08:39: SMS Submit
Wed 2020/09/30 15:08:39: Recipient number "07940303515"
Wed 2020/09/30 15:08:39: SMSC number "+447802002606"
Wed 2020/09/30 15:08:39: SMS class -1
Wed 2020/09/30 15:08:39: SMS validity ff
Wed 2020/09/30 15:08:39: TPMR: 00 0
Wed 2020/09/30 15:08:39: 7 bit SMS, length 18, 20
Wed 2020/09/30 15:08:39: Relay messaging test
Wed 2020/09/30 15:08:39: Waiting for modem prompt
Wed 2020/09/30 15:08:39: SENDING frame type 0x00/length 0x0B/11
Wed 2020/09/30 15:08:39: 41A|54T|2B+|43C|4DM|47G|53S|3D=|333|322|0D                      AT+CMGS=32.
Wed 2020/09/30 15:09:08: Escaping SMS mode
Wed 2020/09/30 15:09:08: SENDING frame type 0x00/length 0x02/2
Wed 2020/09/30 15:09:08: 1B |0D                                                          ..
Wed 2020/09/30 15:09:08: GSM_SendSMS failed with error TIMEOUT[14]: No response in specified timeout. Probably phone not connected.
Wed 2020/09/30 15:09:08: Leaving GSM_SendSMS
Wed 2020/09/30 15:09:08: [Terminating]
Wed 2020/09/30 15:09:08: [Closing]


====
Any help appreciated as I am out of ideas at this point and almost convinced the fix is staring me in the face!

---

