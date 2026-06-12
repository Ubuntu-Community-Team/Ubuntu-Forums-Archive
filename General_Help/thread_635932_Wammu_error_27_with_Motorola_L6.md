---
title: "Wammu error 27 with Motorola L6"
date: 2007-12-09
forum: General Help
---

### Post by Raval on 2007-12-09
I keep getting an error 27 when I try to read my phone book.

here is my log file:

```
--------------- System information ----------------
Platform     linux2
Python       2.5.1
wxPython     2.6.3.2
Wammu        0.22
python-gammu 0.22
Gammu        1.13.0
Bluetooth    None
locales      en_US (UTF8)
connection   at19200
device       /dev/ttyACM0
model        auto
[Gammu            - 1.13.0 built 14:58:05 Oct  9 2007 using gcc 4.1]
[Connection       - "at19200"]
[Connection index - 0]
[Model type       - ""]
[Device           - "/dev/ttyACM1"]
[Runing on        - Linux, kernel 2.6.22-14-generic (#1 SMP Sun Oct 14 23:05:12 GMT 2007)]
[System error     - open in serial_open, 2, "No such file or directory"]
Setting speed to 19200
[Module           - "auto"]
Escaping SMS mode
Sending simple AT command to wake up some devices
Enabling echo
[Gammu            - 1.13.0 built 14:58:05 Oct  9 2007 using gcc 4.1]
[Connection       - "at19200"]
[Connection index - 0]
[Model type       - ""]
[Device           - "/dev/ttyACM1"]
[Runing on        - Linux, kernel 2.6.22-14-generic (#1 SMP Sun Oct 14 23:05:12 GMT 2007)]
[System error     - open in serial_open, 2, "No such file or directory"]
Setting speed to 19200
[Module           - "auto"]
Escaping SMS mode
Sending simple AT command to wake up some devices
1 "AT"
2 "OK"
Enabling echo
1 "ATE1"
2 "OK"
Trying Motorola mode switch
1 "AT+MODE=2"
2 "OK"
Works, will use it
Enabling CME errors
Already in mode 2
1 "+MBAN: Copyright 2000-2002 Motorola, Inc."
2 "AT+CMEE=1"
3 "OK"
1 "AT+CMEE=1"
2 "OK"
Already in mode 2
1 "AT+CSCS?"
2 "+CSCS: "ASCII""
3 "OK"
Already in mode 2
1 "AT+CSCS=?"
2 "+CSCS: ("8859-1","ASCII","GSM","UCS2","UTF8")"
3 "OK"
Already in mode 2
1 "AT+CSCS="GSM""
2 "OK"
Already in mode 2
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
Getting model
Already in mode 2
1 "AT+CGMM"
2 "+CGMM: "GSM900","GSM1800","GSM1900","MODEL=L6""
3 "OK"
[Module           - "sonyericsson|ericsson|atobex"]
Escaping SMS mode
Sending simple AT command to wake up some devices
1 "AT"
2 "OK"
Enabling echo
1 "ATE1"
2 "OK"
Trying Motorola mode switch
1 "AT+MODE=2"
2 "OK"
Works, will use it
Enabling CME errors
Already in mode 2
1 "AT+CMEE=1"
2 "OK"
Already in mode 2
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
Already in mode 2
1 "AT+CSCS=?"
2 "+CSCS: ("8859-1","ASCII","GSM","UCS2","UTF8")"
3 "OK"
Already in mode 2
1 "AT+CGMI"
2 "+CGMI: "Motorola CE, Copyright 2000""
3 "OK"
Manufacturer info received
Getting firmware versions
Already in mode 2
1 "AT+CGMR"
2 "+CGMR: "R3517_G_0A.63.12R""
3 "OK"
Received firmware version: ""R3517_G_0A.63.12R""
Getting model
Already in mode 2
1 "AT+CGMM"
2 "+CGMM: "GSM900","GSM1800","GSM1900","MODEL=L6""
3 "OK"
Already in mode 2
1 "AT+CGMI"
2 "+CGMI: "Motorola CE, Copyright 2000""
3 "OK"
Manufacturer info received
Getting available SMS memories
Already in mode 2
1 "AT+CPMS=?"
2 "+CPMS: ("MT","ME","SM","IM","OM","BM","DM"),("MT","ME","SM","OM","DM"),("MT","ME","SM","IM")"
3 "OK"
Available SMS memories received: read: ME : ok, SM : ok, save: ME : ok, SM = ok
Setting SMS memory type to ME
Already in mode 2
1 "AT+CPMS="ME""
2 "+CPMS: 18,254"
3 "OK"
Already in mode 2
1 "AT+CNMI=?"
2 "+CNMI: (0,3),(0-2),(0),(0),(0)"
3 "OK"
Disabling incoming call
GSM_SetIncomingCB failed with error 21: Function not supported by phone.
Terminating possible incoming USSD
Nothing known about AT+CUSD=2  command, using current mode
1 "AT+CUSD=2"
2 "+CME ERROR: 100"
CME Error 100: "unknown"
Disabling incoming USSD
Nothing known about AT+CUSD=0  command, using current mode
1 "AT+CUSD=0"
2 "+CME ERROR: 100"
CME Error 100: "unknown"
GSM_SetIncomingUSSD failed with error 21: Function not supported by phone.
[Closing]
Setting speed to 19200
[Module           - "auto"]
Escaping SMS mode
Sending simple AT command to wake up some devices
1 "AT"
2 "OK"
Enabling echo
1 "ATE1"
2 "OK"
Trying Motorola mode switch
1 "AT+MODE=2"
2 "OK"
Works, will use it
Enabling CME errors
Already in mode 2
1 "AT+CMEE=1"
2 "OK"
Already in mode 2
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
Already in mode 2
1 "AT+CSCS=?"
2 "+CSCS: ("8859-1","ASCII","GSM","UCS2","UTF8")"
3 "OK"
Getting model
Already in mode 2
1 "AT+CGMM"
2 "+CGMM: "GSM900","GSM1800","GSM1900","MODEL=L6""
3 "OK"
[Module           - "sonyericsson|ericsson|atobex"]
Escaping SMS mode
Sending simple AT command to wake up some devices
1 "AT"
2 "OK"
Enabling echo
1 "ATE1"
2 "OK"
Trying Motorola mode switch
1 "AT+MODE=2"
2 "OK"
Works, will use it
Enabling CME errors
Already in mode 2
1 "AT+CMEE=1"
2 "OK"
Already in mode 2
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
Already in mode 2
1 "AT+CSCS=?"
2 "+CSCS: ("8859-1","ASCII","GSM","UCS2","UTF8")"
3 "OK"
Already in mode 2
1 "AT+CGMI"
2 "+CGMI: "Motorola CE, Copyright 2000""
3 "OK"
Manufacturer info received
Getting firmware versions
Already in mode 2
1 "AT+CGMR"
2 "+CGMR: "R3517_G_0A.63.12R""
3 "OK"
Received firmware version: ""R3517_G_0A.63.12R""
Getting model
Already in mode 2
1 "AT+CGMM"
2 "+CGMM: "GSM900","GSM1800","GSM1900","MODEL=L6""
3 "OK"
Already in mode 2
1 "AT+CGMI"
2 "+CGMI: "Motorola CE, Copyright 2000""
3 "OK"
Manufacturer info received
Getting available SMS memories
Already in mode 2
1 "AT+CPMS=?"
2 "+CPMS: ("MT","ME","SM","IM","OM","BM","DM"),("MT","ME","SM","OM","DM"),("MT","ME","SM","IM")"
3 "OK"
Available SMS memories received: read: ME : ok, SM : ok, save: ME : ok, SM = ok
Setting SMS memory type to ME
Already in mode 2
1 "AT+CPMS="ME""
2 "+CPMS: 18,254"
3 "OK"
Already in mode 2
1 "AT+CNMI=?"
2 "+CNMI: (0,3),(0-2),(0),(0),(0)"
3 "OK"
Disabling incoming call
GSM_SetIncomingCB failed with error 21: Function not supported by phone.
Terminating possible incoming USSD
Nothing known about AT+CUSD=2  command, using current mode
1 "AT+CUSD=2"
2 "+CME ERROR: 100"
CME Error 100: "unknown"
Disabling incoming USSD
Nothing known about AT+CUSD=0  command, using current mode
1 "AT+CUSD=0"
2 "+CME ERROR: 100"
CME Error 100: "unknown"
GSM_SetIncomingUSSD failed with error 21: Function not supported by phone.
[Closing]
[Gammu            - 1.13.0 built 14:58:05 Oct  9 2007 using gcc 4.1]
[Connection       - "at19200"]
[Connection index - 0]
[Model type       - ""]
[Device           - "/dev/ttyACM0"]
[Runing on        - Linux, kernel 2.6.22-14-generic (#1 SMP Sun Oct 14 23:05:12 GMT 2007)]
Setting speed to 19200
[Module           - "auto"]
Escaping SMS mode
SENDING frame type 0x00/length 0x02/2
1B |0D                                                         ..              
Sending simple AT command to wake up some devices
SENDING frame type 0x00/length 0x03/3
41A|54T|0D                                                     AT.             
1 "AT"
2 "OK"
RECEIVED frame type 0x00/length 0x09/9
41A|54T|0D |0D |0A |4FO|4BK|0D |0A                             AT...OK..       
Enabling echo
SENDING frame type 0x00/length 0x05/5
41A|54T|45E|311|0D                                             ATE1.           
1 "ATE1"
2 "OK"
RECEIVED frame type 0x00/length 0x0B/11
41A|54T|45E|311|0D |0D |0A |4FO|4BK|0D |0A                     ATE1...OK..     
Trying Motorola mode switch
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                         AT+MODE=2.      
1 "AT+MODE=2"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=2...OK..
Works, will use it
Enabling CME errors
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|4DM|45E|45E|3D=|311|0D                         AT+CMEE=1.      
1 "AT+CMEE=1"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|43C|4DM|45E|45E|3D=|311|0D |0D |0A |4FO|4BK|0D |0A AT+CMEE=1...OK..
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|53S|3F?|0D                             AT+CSCS?.       
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
RECEIVED frame type 0x00/length 0x1F/31
41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53 AT+CSCS?...+CSCS
3A:|20 |22"|47G|53S|4DM|22"|0D |0A |0D |0A |4FO|4BK|0D |0A     : "GSM"....OK.. 
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|53S|43C|53S|3D=|3F?|0D                         AT+CSCS=?.      
1 "AT+CSCS=?"
2 "+CSCS: ("8859-1","ASCII","GSM","UCS2","UTF8")"
3 "OK"
RECEIVED frame type 0x00/length 0x41/65
41A|54T|2B+|43C|53S|43C|53S|3D=|3F?|0D |0D |0A |2B+|43C|53S|43 AT+CSCS=?...+CSC
53S|3A:|20 |28(|22"|388|388|355|399|2D-|311|22"|2C,|22"|41A|53 S: ("8859-1","AS
43C|49I|49I|22"|2C,|22"|47G|53S|4DM|22"|2C,|22"|55U|43C|53S|32 CII","GSM","UCS2
22"|2C,|22"|55U|54T|46F|388|22"|29)|0D |0A |0D |0A |4FO|4BK|0D ","UTF8")....OK.
0A                                                             .               
Getting model
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|4DM|0D                                 AT+CGMM.        
1 "AT+CGMM"
2 "+CGMM: "GSM900","GSM1800","GSM1900","MODEL=L6""
3 "OK"
RECEIVED frame type 0x00/length 0x40/64
41A|54T|2B+|43C|47G|4DM|4DM|0D |0D |0A |2B+|43C|47G|4DM|4DM|3A AT+CGMM...+CGMM:
20 |22"|47G|53S|4DM|399|300|300|22"|2C,|22"|47G|53S|4DM|311|38  "GSM900","GSM18
300|300|22"|2C,|22"|47G|53S|4DM|311|399|300|300|22"|2C,|22"|4D 00","GSM1900","M
4FO|44D|45E|4CL|3D=|4CL|366|22"|0D |0A |0D |0A |4FO|4BK|0D |0A ODEL=L6"....OK..
[Connected model  - "L6"]
[Module           - "sonyericsson|ericsson|atobex"]
Escaping SMS mode
SENDING frame type 0x00/length 0x02/2
1B |0D                                                         ..              
Sending simple AT command to wake up some devices
SENDING frame type 0x00/length 0x03/3
41A|54T|0D                                                     AT.             
1 "AT"
2 "OK"
RECEIVED frame type 0x00/length 0x09/9
41A|54T|0D |0D |0A |4FO|4BK|0D |0A                             AT...OK..       
Enabling echo
SENDING frame type 0x00/length 0x05/5
41A|54T|45E|311|0D                                             ATE1.           
1 "ATE1"
2 "OK"
RECEIVED frame type 0x00/length 0x0B/11
41A|54T|45E|311|0D |0D |0A |4FO|4BK|0D |0A                     ATE1...OK..     
Trying Motorola mode switch
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                         AT+MODE=2.      
1 "AT+MODE=2"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=2...OK..
Works, will use it
Enabling CME errors
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|4DM|45E|45E|3D=|311|0D                         AT+CMEE=1.      
1 "AT+CMEE=1"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|43C|4DM|45E|45E|3D=|311|0D |0D |0A |4FO|4BK|0D |0A AT+CMEE=1...OK..
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|53S|3F?|0D                             AT+CSCS?.       
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
RECEIVED frame type 0x00/length 0x1F/31
41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53 AT+CSCS?...+CSCS
3A:|20 |22"|47G|53S|4DM|22"|0D |0A |0D |0A |4FO|4BK|0D |0A     : "GSM"....OK.. 
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|53S|43C|53S|3D=|3F?|0D                         AT+CSCS=?.      
1 "AT+CSCS=?"
2 "+CSCS: ("8859-1","ASCII","GSM","UCS2","UTF8")"
3 "OK"
RECEIVED frame type 0x00/length 0x41/65
41A|54T|2B+|43C|53S|43C|53S|3D=|3F?|0D |0D |0A |2B+|43C|53S|43 AT+CSCS=?...+CSC
53S|3A:|20 |28(|22"|388|388|355|399|2D-|311|22"|2C,|22"|41A|53 S: ("8859-1","AS
43C|49I|49I|22"|2C,|22"|47G|53S|4DM|22"|2C,|22"|55U|43C|53S|32 CII","GSM","UCS2
22"|2C,|22"|55U|54T|46F|388|22"|29)|0D |0A |0D |0A |4FO|4BK|0D ","UTF8")....OK.
0A                                                             .               
Setting date & time
Already in mode 2
SENDING frame type 0x00/length 0x1F/31
41A|54T|2B+|43C|43C|4CL|4BK|3D=|22"|300|377|2F/|311|322|2F/|30 AT+CCLK="07/12/0
399|2C,|311|300|3A:|300|322|3A:|344|311|2B+|300|300|22"|0D     9,10:02:41+00". 
1 "AT+CCLK="07/12/09,10:02:41+00""
2 "OK"
RECEIVED frame type 0x00/length 0x25/37
41A|54T|2B+|43C|43C|4CL|4BK|3D=|22"|300|377|2F/|311|322|2F/|30 AT+CCLK="07/12/0
399|2C,|311|300|3A:|300|322|3A:|344|311|2B+|300|300|22"|0D |0D 9,10:02:41+00"..
0A |4FO|4BK|0D |0A                                             .OK..           
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|49I|0D                                 AT+CGMI.        
1 "AT+CGMI"
2 "+CGMI: "Motorola CE, Copyright 2000""
3 "OK"
RECEIVED frame type 0x00/length 0x36/54
41A|54T|2B+|43C|47G|4DM|49I|0D |0D |0A |2B+|43C|47G|4DM|49I|3A AT+CGMI...+CGMI:
20 |22"|4DM|6Fo|74t|6Fo|72r|6Fo|6Cl|61a|20 |43C|45E|2C,|20 |43  "Motorola CE, C
6Fo|70p|79y|72r|69i|67g|68h|74t|20 |322|300|300|300|22"|0D |0A opyright 2000"..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          
Manufacturer info received
Getting firmware versions
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|52R|0D                                 AT+CGMR.        
1 "AT+CGMR"
2 "+CGMR: "R3517_G_0A.63.12R""
3 "OK"
RECEIVED frame type 0x00/length 0x2C/44
41A|54T|2B+|43C|47G|4DM|52R|0D |0D |0A |2B+|43C|47G|4DM|52R|3A AT+CGMR...+CGMR:
20 |22"|52R|333|355|311|377|5F_|47G|5F_|300|41A|2E.|366|333|2E  "R3517_G_0A.63.
311|322|52R|22"|0D |0A |0D |0A |4FO|4BK|0D |0A                 12R"....OK..    
Received firmware version: ""R3517_G_0A.63.12R""
[Firmware version - ""R3517_G_0A.63.12R""]
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=0...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|53S|51Q|0D                                     AT+CSQ.         
1 "AT+CSQ"
2 "+CSQ: 27,99"
3 "OK"
RECEIVED frame type 0x00/length 0x1C/28
41A|54T|2B+|43C|53S|51Q|0D |0D |0A |2B+|43C|53S|51Q|3A:|20 |32 AT+CSQ...+CSQ: 2
377|2C,|399|399|0D |0A |0D |0A |4FO|4BK|0D |0A                 7,99....OK..    
Signal quality info received
SENDING frame type 0x00/length 0x0A/10
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D                         AT*EBCA=1.      
1 "AT*EBCA=1"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D |0D |0A |45E|52R|52R|4F AT*EBCA=1...ERRO
52R|0D |0A                                                     R..             
Getting battery charge
Switching to mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                         AT+MODE=2.      
1 "AT+MODE=2"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=2...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "+MBAN: Copyright 2000-2002 Motorola, Inc."
2 "AT+CBC"
3 "+CBC: 0,60"
4 "OK"
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

UNKNOWN frame. If you can, please report it (see <http://cihar.com/gammu/report>). Thank you
LAST SENT frame type 0x00/length 7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

[Retrying 2 type 0x00]
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "AT+CBC"
2 "+CBC: 0,60"
3 "OK"
RECEIVED frame type 0x00/length 0x1B/27
41A|54T|2B+|43C|42B|43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |30 AT+CBC...+CBC: 0
2C,|366|300|0D |0A |0D |0A |4FO|4BK|0D |0A                     ,60....OK..     
Battery level received
Getting date & time
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D                             AT+CCLK?.       
1 "AT+CCLK?"
2 "+CCLK: "07/12/09,10:02:48+00""
3 "OK"
RECEIVED frame type 0x00/length 0x30/48
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D |0D |0A |2B+|43C|43C|4CL|4B AT+CCLK?...+CCLK
3A:|20 |22"|300|377|2F/|311|322|2F/|300|399|2C,|311|300|3A:|30 : "07/12/09,10:0
322|3A:|344|388|2B+|300|300|22"|0D |0A |0D |0A |4FO|4BK|0D |0A 2:48+00"....OK..
Parsing +CCLK: "07/12/09,10:02:48+00" with +CCLK: @d
Grabbed string from reply: "07/12/09,10:02:48+00" (parsed 22 bytes)
Parsed string for date "07/12/09,10:02:48+00"
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|50P|42B|53S|3D=|3F?|0D                         AT+CPBS=?.      
1 "AT+CPBS=?"
2 "+CPBS: ("ME","SM","MT","ON","DC","MC","RC","EN","AD","QD","SD","FD")"
3 "OK"
RECEIVED frame type 0x00/length 0x58/88
41A|54T|2B+|43C|50P|42B|53S|3D=|3F?|0D |0D |0A |2B+|43C|50P|42 AT+CPBS=?...+CPB
53S|3A:|20 |28(|22"|4DM|45E|22"|2C,|22"|53S|4DM|22"|2C,|22"|4D S: ("ME","SM","M
54T|22"|2C,|22"|4FO|4EN|22"|2C,|22"|44D|43C|22"|2C,|22"|4DM|43 T","ON","DC","MC
22"|2C,|22"|52R|43C|22"|2C,|22"|45E|4EN|22"|2C,|22"|41A|44D|22 ","RC","EN","AD"
2C,|22"|51Q|44D|22"|2C,|22"|53S|44D|22"|2C,|22"|46F|44D|22"|29 ,"QD","SD","FD")
0D |0A |0D |0A |4FO|4BK|0D |0A                                 ....OK..        
PBK memories received: AT+CPBS=?  
+CPBS: ("ME","SM","MT","ON","DC","MC","RC","EN","AD","QD","SD","FD") 
 
OK 

Setting memory type
Already in mode 2
SENDING frame type 0x00/length 0x0D/13
41A|54T|2B+|43C|50P|42B|53S|3D=|22"|4FO|4EN|22"|0D             AT+CPBS="ON".   
1 "AT+CPBS="ON""
2 "OK"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|43C|50P|42B|53S|3D=|22"|4FO|4EN|22"|0D |0D |0A |4F AT+CPBS="ON"...O
4BK|0D |0A                                                     K..             
Getting memory information
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|50P|42B|52R|3D=|3F?|0D                         AT+CPBR=?.      
1 "AT+CPBR=?"
2 "+CPBR: (1-2),20,14"
3 "OK"
RECEIVED frame type 0x00/length 0x26/38
41A|54T|2B+|43C|50P|42B|52R|3D=|3F?|0D |0D |0A |2B+|43C|50P|42 AT+CPBR=?...+CPB
52R|3A:|20 |28(|311|2D-|322|29)|2C,|322|300|2C,|311|344|0D |0A R: (1-2),20,14..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          
Memory info received
Parsing +CPBR: (1-2),20,14 with +CPBR: (@i-@i), @i, @i
Parsed int 1
Parsed int 2
Parsed int 20
Parsed int 14
Already in mode 2
SENDING frame type 0x00/length 0x0F/15
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|55U|43C|53S|322|22"|0D     AT+CSCS="UCS2". 
1 "AT+CSCS="UCS2""
2 "OK"
RECEIVED frame type 0x00/length 0x15/21
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|55U|43C|53S|322|22"|0D |0D AT+CSCS="UCS2"..
0A |4FO|4BK|0D |0A                                             .OK..           
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|53S|3F?|0D                             AT+CSCS?.       
1 "AT+CSCS?"
2 "+CSCS: "UCS2""
3 "OK"
RECEIVED frame type 0x00/length 0x20/32
41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53 AT+CSCS?...+CSCS
3A:|20 |22"|55U|43C|53S|322|22"|0D |0A |0D |0A |4FO|4BK|0D |0A : "UCS2"....OK..
Getting phonebook entry
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|50P|42B|52R|3D=|311|0D                         AT+CPBR=1.      
1 "AT+CPBR=1"
2 "+CPBR: 1,"5926268784",129,0052002E002000530065006F006A0061007400740061006E"
3 "OK"
RECEIVED frame type 0x00/length 0x5E/94
41A|54T|2B+|43C|50P|42B|52R|3D=|311|0D |0D |0A |2B+|43C|50P|42 AT+CPBR=1...+CPB
52R|3A:|20 |311|2C,|22"|355|399|322|366|322|366|388|377|388|34 R: 1,"5926268784
22"|2C,|311|322|399|2C,|300|300|355|322|300|300|322|45E|300|30 ",129,0052002E00
322|300|300|300|355|333|300|300|366|355|300|300|366|46F|300|30 2000530065006F00
366|41A|300|300|366|311|300|300|377|344|300|300|377|344|300|30 6A00610074007400
366|311|300|300|366|45E|0D |0A |0D |0A |4FO|4BK|0D |0A         61006E....OK..  
Phonebook entry received
Parsing +CPBR: 1,"5926268784",129,0052002E002000530065006F006A0061007400740061006E with +CPBR: @i, @p, @i, @s
Parsed int 1
Grabbed string from reply: "5926268784" (parsed 12 bytes)
Parsed phone string "5926268784"
Parsed int 129
Grabbed string from reply: "0052002E002000530065006F006A0061007400740061006E" (parsed 48 bytes)
Parsed generic string "0052002E002000530065006F006A0061007400740061006E"
Generic AT reply detected
Already in mode 2
SENDING frame type 0x00/length 0x0E/14
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|47G|53S|4DM|22"|0D         AT+CSCS="GSM".  
1 "AT+CSCS="GSM""
2 "OK"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|47G|53S|4DM|22"|0D |0D |0A AT+CSCS="GSM"...
4FO|4BK|0D |0A                                                 OK..            
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|53S|3F?|0D                             AT+CSCS?.       
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
RECEIVED frame type 0x00/length 0x1F/31
41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53 AT+CSCS?...+CSCS
3A:|20 |22"|47G|53S|4DM|22"|0D |0A |0D |0A |4FO|4BK|0D |0A     : "GSM"....OK.. 
Getting SMSC
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|41A|3F?|0D                             AT+CSCA?.       
1 "AT+CSCA?"
2 "+CSCA: "+5926400003",145"
3 "OK"
RECEIVED frame type 0x00/length 0x2B/43
41A|54T|2B+|43C|53S|43C|41A|3F?|0D |0D |0A |2B+|43C|53S|43C|41 AT+CSCA?...+CSCA
3A:|20 |22"|2B+|355|399|322|366|344|300|300|300|300|333|22"|2C : "+5926400003",
311|344|355|0D |0A |0D |0A |4FO|4BK|0D |0A                     145....OK..     
SMSC info received
Parsing +CSCA: "+5926400003",145 with +CSCA: @p, @i
Grabbed string from reply: "+5926400003" (parsed 13 bytes)
Parsed phone string "+5926400003"
Parsed int 145
Getting IMEI
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|53S|4EN|0D                                 AT+CGSN.        
1 "AT+CGSN"
2 "+CGSN: IMEI353277010846589"
3 "OK"
RECEIVED frame type 0x00/length 0x2C/44
41A|54T|2B+|43C|47G|53S|4EN|0D |0D |0A |2B+|43C|47G|53S|4EN|3A AT+CGSN...+CGSN:
20 |49I|4DM|45E|49I|333|355|333|322|377|377|300|311|300|388|34  IMEI35327701084
366|355|388|399|0D |0A |0D |0A |4FO|4BK|0D |0A                 6589....OK..    
Received IMEI 353277010846589
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|49I|0D                                 AT+CGMI.        
1 "AT+CGMI"
2 "+CGMI: "Motorola CE, Copyright 2000""
3 "OK"
RECEIVED frame type 0x00/length 0x36/54
41A|54T|2B+|43C|47G|4DM|49I|0D |0D |0A |2B+|43C|47G|4DM|49I|3A AT+CGMI...+CGMI:
20 |22"|4DM|6Fo|74t|6Fo|72r|6Fo|6Cl|61a|20 |43C|45E|2C,|20 |43  "Motorola CE, C
6Fo|70p|79y|72r|69i|67g|68h|74t|20 |322|300|300|300|22"|0D |0A opyright 2000"..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          
Manufacturer info received
Getting model
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|4DM|0D                                 AT+CGMM.        
1 "AT+CGMM"
2 "+CGMM: "GSM900","GSM1800","GSM1900","MODEL=L6""
3 "OK"
RECEIVED frame type 0x00/length 0x40/64
41A|54T|2B+|43C|47G|4DM|4DM|0D |0D |0A |2B+|43C|47G|4DM|4DM|3A AT+CGMM...+CGMM:
20 |22"|47G|53S|4DM|399|300|300|22"|2C,|22"|47G|53S|4DM|311|38  "GSM900","GSM18
300|300|22"|2C,|22"|47G|53S|4DM|311|399|300|300|22"|2C,|22"|4D 00","GSM1900","M
4FO|44D|45E|4CL|3D=|4CL|366|22"|0D |0A |0D |0A |4FO|4BK|0D |0A ODEL=L6"....OK..
[Connected model  - "L6"]
Getting firmware versions
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|52R|0D                                 AT+CGMR.        
1 "AT+CGMR"
2 "+CGMR: "R3517_G_0A.63.12R""
3 "OK"
RECEIVED frame type 0x00/length 0x2C/44
41A|54T|2B+|43C|47G|4DM|52R|0D |0D |0A |2B+|43C|47G|4DM|52R|3A AT+CGMR...+CGMR:
20 |22"|52R|333|355|311|377|5F_|47G|5F_|300|41A|2E.|366|333|2E  "R3517_G_0A.63.
311|322|52R|22"|0D |0A |0D |0A |4FO|4BK|0D |0A                 12R"....OK..    
Received firmware version: ""R3517_G_0A.63.12R""
[Firmware version - ""R3517_G_0A.63.12R""]
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=0...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|53S|51Q|0D                                     AT+CSQ.         
1 "AT+CSQ"
2 "+CSQ: 27,99"
3 "OK"
RECEIVED frame type 0x00/length 0x1C/28
41A|54T|2B+|43C|53S|51Q|0D |0D |0A |2B+|43C|53S|51Q|3A:|20 |32 AT+CSQ...+CSQ: 2
377|2C,|399|399|0D |0A |0D |0A |4FO|4BK|0D |0A                 7,99....OK..    
Signal quality info received
SENDING frame type 0x00/length 0x0A/10
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D                         AT*EBCA=1.      
1 "AT*EBCA=1"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D |0D |0A |45E|52R|52R|4F AT*EBCA=1...ERRO
52R|0D |0A                                                     R..             
Getting battery charge
Switching to mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                         AT+MODE=2.      
1 "AT+MODE=2"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=2...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "+MBAN: Copyright 2000-2002 Motorola, Inc."
2 "AT+CBC"
3 "+CBC: 0,60"
4 "OK"
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

UNKNOWN frame. If you can, please report it (see <http://cihar.com/gammu/report>). Thank you
LAST SENT frame type 0x00/length 7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "AT+CBC"
2 "+CBC: 0,60"
3 "OK"
RECEIVED frame type 0x00/length 0x1B/27
41A|54T|2B+|43C|42B|43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |30 AT+CBC...+CBC: 0
2C,|366|300|0D |0A |0D |0A |4FO|4BK|0D |0A                     ,60....OK..     
Battery level received
Getting date & time
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D                             AT+CCLK?.       
1 "AT+CCLK?"
2 "+CCLK: "07/12/09,10:02:51+00""
3 "OK"
RECEIVED frame type 0x00/length 0x30/48
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D |0D |0A |2B+|43C|43C|4CL|4B AT+CCLK?...+CCLK
3A:|20 |22"|300|377|2F/|311|322|2F/|300|399|2C,|311|300|3A:|30 : "07/12/09,10:0
322|3A:|355|311|2B+|300|300|22"|0D |0A |0D |0A |4FO|4BK|0D |0A 2:51+00"....OK..
Parsing +CCLK: "07/12/09,10:02:51+00" with +CCLK: @d
Grabbed string from reply: "07/12/09,10:02:51+00" (parsed 22 bytes)
Parsed string for date "07/12/09,10:02:51+00"
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=0...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|53S|51Q|0D                                     AT+CSQ.         
1 "AT+CSQ"
2 "+CSQ: 27,99"
3 "OK"
RECEIVED frame type 0x00/length 0x1C/28
41A|54T|2B+|43C|53S|51Q|0D |0D |0A |2B+|43C|53S|51Q|3A:|20 |32 AT+CSQ...+CSQ: 2
377|2C,|399|399|0D |0A |0D |0A |4FO|4BK|0D |0A                 7,99....OK..    
Signal quality info received
SENDING frame type 0x00/length 0x0A/10
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D                         AT*EBCA=1.      
1 "AT*EBCA=1"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D |0D |0A |45E|52R|52R|4F AT*EBCA=1...ERRO
52R|0D |0A                                                     R..             
Getting battery charge
Switching to mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                         AT+MODE=2.      
1 "AT+MODE=2"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=2...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "+MBAN: Copyright 2000-2002 Motorola, Inc."
2 "AT+CBC"
3 "+CBC: 0,60"
4 "OK"
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

UNKNOWN frame. If you can, please report it (see <http://cihar.com/gammu/report>). Thank you
LAST SENT frame type 0x00/length 7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

[Retrying 2 type 0x00]
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "AT+CBC"
2 "+CBC: 0,60"
3 "OK"
RECEIVED frame type 0x00/length 0x1B/27
41A|54T|2B+|43C|42B|43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |30 AT+CBC...+CBC: 0
2C,|366|300|0D |0A |0D |0A |4FO|4BK|0D |0A                     ,60....OK..     
Battery level received
Getting date & time
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D                             AT+CCLK?.       
1 "AT+CCLK?"
2 "+CCLK: "07/12/09,10:03:24+00""
3 "OK"
RECEIVED frame type 0x00/length 0x30/48
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D |0D |0A |2B+|43C|43C|4CL|4B AT+CCLK?...+CCLK
3A:|20 |22"|300|377|2F/|311|322|2F/|300|399|2C,|311|300|3A:|30 : "07/12/09,10:0
333|3A:|322|344|2B+|300|300|22"|0D |0A |0D |0A |4FO|4BK|0D |0A 3:24+00"....OK..
Parsing +CCLK: "07/12/09,10:03:24+00" with +CCLK: @d
Grabbed string from reply: "07/12/09,10:03:24+00" (parsed 22 bytes)
Parsed string for date "07/12/09,10:03:24+00"
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=0...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|53S|51Q|0D                                     AT+CSQ.         
1 "AT+CSQ"
2 "+CSQ: 27,99"
3 "OK"
RECEIVED frame type 0x00/length 0x1C/28
41A|54T|2B+|43C|53S|51Q|0D |0D |0A |2B+|43C|53S|51Q|3A:|20 |32 AT+CSQ...+CSQ: 2
377|2C,|399|399|0D |0A |0D |0A |4FO|4BK|0D |0A                 7,99....OK..    
Signal quality info received
SENDING frame type 0x00/length 0x0A/10
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D                         AT*EBCA=1.      
1 "AT*EBCA=1"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2A*|45E|42B|43C|41A|3D=|311|0D |0D |0A |45E|52R|52R|4F AT*EBCA=1...ERRO
52R|0D |0A                                                     R..             
Getting battery charge
Switching to mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                         AT+MODE=2.      
1 "AT+MODE=2"
2 "OK"
RECEIVED frame type 0x00/length 0x10/16
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |4FO|4BK|0D |0A AT+MODE=2...OK..
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "+MBAN: Copyright 2000-2002 Motorola, Inc."
2 "AT+CBC"
3 "+CBC: 0,60"
4 "OK"
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

UNKNOWN frame. If you can, please report it (see <http://cihar.com/gammu/report>). Thank you
LAST SENT frame type 0x00/length 7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
RECEIVED frame type 0x00/length 0x46/70
2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74 +MBAN: Copyright
20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72  2000-2002 Motor
6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A |41A|54T|2B+|43C|42 ola, Inc...AT+CB
43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |300|2C,|366|300|0D |0A C...+CBC: 0,60..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          

[Retrying 2 type 0x00]
SENDING frame type 0x00/length 0x07/7
41A|54T|2B+|43C|42B|43C|0D                                     AT+CBC.         
1 "AT+CBC"
2 "+CBC: 0,60"
3 "OK"
RECEIVED frame type 0x00/length 0x1B/27
41A|54T|2B+|43C|42B|43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |30 AT+CBC...+CBC: 0
2C,|366|300|0D |0A |0D |0A |4FO|4BK|0D |0A                     ,60....OK..     
Battery level received
Getting date & time
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D                             AT+CCLK?.       
1 "AT+CCLK?"
2 "+CCLK: "07/12/09,10:03:54+00""
3 "OK"
RECEIVED frame type 0x00/length 0x30/48
41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D |0D |0A |2B+|43C|43C|4CL|4B AT+CCLK?...+CCLK
3A:|20 |22"|300|377|2F/|311|322|2F/|300|399|2C,|311|300|3A:|30 : "07/12/09,10:0
333|3A:|355|344|2B+|300|300|22"|0D |0A |0D |0A |4FO|4BK|0D |0A 3:54+00"....OK..
Parsing +CCLK: "07/12/09,10:03:54+00" with +CCLK: @d
Grabbed string from reply: "07/12/09,10:03:54+00" (parsed 22 bytes)
Parsed string for date "07/12/09,10:03:54+00"
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
1 "AT+MODE=22"
2 "ERROR"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D |0D |0A |45E|52R|52 AT+MODE=22...ERR
4FO|52R|0D |0A                                                 OR..            
GSM_GetMemoryStatus failed with error 27: Unknown error.
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
1 "AT+MODE=22"
2 "ERROR"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D |0D |0A |45E|52R|52 AT+MODE=22...ERR
4FO|52R|0D |0A                                                 OR..            
GSM_GetNextMemory failed with error 27: Unknown error.
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|49I|0D                                 AT+CGMI.        
1 "AT+CGMI"
2 "+CGMI: "Motorola CE, Copyright 2000""
3 "OK"
RECEIVED frame type 0x00/length 0x36/54
41A|54T|2B+|43C|47G|4DM|49I|0D |0D |0A |2B+|43C|47G|4DM|49I|3A AT+CGMI...+CGMI:
20 |22"|4DM|6Fo|74t|6Fo|72r|6Fo|6Cl|61a|20 |43C|45E|2C,|20 |43  "Motorola CE, C
6Fo|70p|79y|72r|69i|67g|68h|74t|20 |322|300|300|300|22"|0D |0A opyright 2000"..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          
Manufacturer info received
Getting model
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|4DM|0D                                 AT+CGMM.        
1 "AT+CGMM"
2 "+CGMM: "GSM900","GSM1800","GSM1900","MODEL=L6""
3 "OK"
RECEIVED frame type 0x00/length 0x40/64
41A|54T|2B+|43C|47G|4DM|4DM|0D |0D |0A |2B+|43C|47G|4DM|4DM|3A AT+CGMM...+CGMM:
20 |22"|47G|53S|4DM|399|300|300|22"|2C,|22"|47G|53S|4DM|311|38  "GSM900","GSM18
300|300|22"|2C,|22"|47G|53S|4DM|311|399|300|300|22"|2C,|22"|4D 00","GSM1900","M
4FO|44D|45E|4CL|3D=|4CL|366|22"|0D |0A |0D |0A |4FO|4BK|0D |0A ODEL=L6"....OK..
[Connected model  - "L6"]
Getting firmware versions
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|4DM|52R|0D                                 AT+CGMR.        
1 "AT+CGMR"
2 "+CGMR: "R3517_G_0A.63.12R""
3 "OK"
RECEIVED frame type 0x00/length 0x2C/44
41A|54T|2B+|43C|47G|4DM|52R|0D |0D |0A |2B+|43C|47G|4DM|52R|3A AT+CGMR...+CGMR:
20 |22"|52R|333|355|311|377|5F_|47G|5F_|300|41A|2E.|366|333|2E  "R3517_G_0A.63.
311|322|52R|22"|0D |0A |0D |0A |4FO|4BK|0D |0A                 12R"....OK..    
Received firmware version: ""R3517_G_0A.63.12R""
[Firmware version - ""R3517_G_0A.63.12R""]
Getting IMEI
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|47G|53S|4EN|0D                                 AT+CGSN.        
1 "AT+CGSN"
2 "+CGSN: IMEI353277010846589"
3 "OK"
RECEIVED frame type 0x00/length 0x2C/44
41A|54T|2B+|43C|47G|53S|4EN|0D |0D |0A |2B+|43C|47G|53S|4EN|3A AT+CGSN...+CGSN:
20 |49I|4DM|45E|49I|333|355|333|322|377|377|300|311|300|388|34  IMEI35327701084
366|355|388|399|0D |0A |0D |0A |4FO|4BK|0D |0A                 6589....OK..    
Received IMEI 353277010846589
GSM_GetOriginalIMEI failed with error 21: Function not supported by phone.
Getting SIM IMSI
Already in mode 2
SENDING frame type 0x00/length 0x08/8
41A|54T|2B+|43C|49I|4DM|49I|0D                                 AT+CIMI.        
1 "AT+CIMI"
2 "738002000883050"
3 "OK"
RECEIVED frame type 0x00/length 0x21/33
41A|54T|2B+|43C|49I|4DM|49I|0D |0D |0A |377|333|388|300|300|32 AT+CIMI...738002
300|300|300|388|388|333|300|355|300|0D |0A |0D |0A |4FO|4BK|0D 000883050....OK.
0A                                                             .               
Received IMSI 738002000883050
Getting SMSC
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|41A|3F?|0D                             AT+CSCA?.       
1 "AT+CSCA?"
2 "+CSCA: "+5926400003",145"
3 "OK"
RECEIVED frame type 0x00/length 0x2B/43
41A|54T|2B+|43C|53S|43C|41A|3F?|0D |0D |0A |2B+|43C|53S|43C|41 AT+CSCA?...+CSCA
3A:|20 |22"|2B+|355|399|322|366|344|300|300|300|300|333|22"|2C : "+5926400003",
311|344|355|0D |0A |0D |0A |4FO|4BK|0D |0A                     145....OK..     
SMSC info received
Parsing +CSCA: "+5926400003",145 with +CSCA: @p, @i
Grabbed string from reply: "+5926400003" (parsed 13 bytes)
Parsed phone string "+5926400003"
Parsed int 145
GSM_GetHardware failed with error 21: Function not supported by phone.
GSM_GetManufactureMonth failed with error 21: Function not supported by phone.
GSM_GetPPM failed with error 21: Function not supported by phone.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Setting memory type
Already in mode 2
SENDING frame type 0x00/length 0x0D/13
41A|54T|2B+|43C|50P|42B|53S|3D=|22"|53S|4DM|22"|0D             AT+CPBS="SM".   
1 "AT+CPBS="SM""
2 "OK"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|43C|50P|42B|53S|3D=|22"|53S|4DM|22"|0D |0D |0A |4F AT+CPBS="SM"...O
4BK|0D |0A                                                     K..             
Getting memory status
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|50P|42B|53S|3F?|0D                             AT+CPBS?.       
1 "AT+CPBS?"
2 "+CPBS: "SM",0,200"
3 "OK"
RECEIVED frame type 0x00/length 0x24/36
41A|54T|2B+|43C|50P|42B|53S|3F?|0D |0D |0A |2B+|43C|50P|42B|53 AT+CPBS?...+CPBS
3A:|20 |22"|53S|4DM|22"|2C,|300|2C,|322|300|300|0D |0A |0D |0A : "SM",0,200....
4FO|4BK|0D |0A                                                 OK..            
Memory status received
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
1 "AT+MODE=22"
2 "ERROR"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D |0D |0A |45E|52R|52 AT+MODE=22...ERR
4FO|52R|0D |0A                                                 OR..            
GSM_GetMemoryStatus failed with error 27: Unknown error.
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
1 "AT+MODE=22"
2 "ERROR"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D |0D |0A |45E|52R|52 AT+MODE=22...ERR
4FO|52R|0D |0A                                                 OR..            
GSM_GetNextMemory failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
Setting memory type
Already in mode 2
SENDING frame type 0x00/length 0x0D/13
41A|54T|2B+|43C|50P|42B|53S|3D=|22"|4FO|4EN|22"|0D             AT+CPBS="ON".   
1 "AT+CPBS="ON""
2 "OK"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|43C|50P|42B|53S|3D=|22"|4FO|4EN|22"|0D |0D |0A |4F AT+CPBS="ON"...O
4BK|0D |0A                                                     K..             
Getting memory information
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|50P|42B|52R|3D=|3F?|0D                         AT+CPBR=?.      
1 "AT+CPBR=?"
2 "+CPBR: (1-2),20,14"
3 "OK"
RECEIVED frame type 0x00/length 0x26/38
41A|54T|2B+|43C|50P|42B|52R|3D=|3F?|0D |0D |0A |2B+|43C|50P|42 AT+CPBR=?...+CPB
52R|3A:|20 |28(|311|2D-|322|29)|2C,|322|300|2C,|311|344|0D |0A R: (1-2),20,14..
0D |0A |4FO|4BK|0D |0A                                         ..OK..          
Memory info received
Parsing +CPBR: (1-2),20,14 with +CPBR: (@i-@i), @i, @i
Parsed int 1
Parsed int 2
Parsed int 20
Parsed int 14
Already in mode 2
SENDING frame type 0x00/length 0x0F/15
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|55U|43C|53S|322|22"|0D     AT+CSCS="UCS2". 
1 "AT+CSCS="UCS2""
2 "OK"
RECEIVED frame type 0x00/length 0x15/21
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|55U|43C|53S|322|22"|0D |0D AT+CSCS="UCS2"..
0A |4FO|4BK|0D |0A                                             .OK..           
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|53S|3F?|0D                             AT+CSCS?.       
1 "AT+CSCS?"
2 "+CSCS: "UCS2""
3 "OK"
RECEIVED frame type 0x00/length 0x20/32
41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53 AT+CSCS?...+CSCS
3A:|20 |22"|55U|43C|53S|322|22"|0D |0A |0D |0A |4FO|4BK|0D |0A : "UCS2"....OK..
Getting phonebook entry
Already in mode 2
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|43C|50P|42B|52R|3D=|311|0D                         AT+CPBR=1.      
1 "AT+CPBR=1"
2 "+CPBR: 1,"5926268784",129,0052002E002000530065006F006A0061007400740061006E"
3 "OK"
RECEIVED frame type 0x00/length 0x5E/94
41A|54T|2B+|43C|50P|42B|52R|3D=|311|0D |0D |0A |2B+|43C|50P|42 AT+CPBR=1...+CPB
52R|3A:|20 |311|2C,|22"|355|399|322|366|322|366|388|377|388|34 R: 1,"5926268784
22"|2C,|311|322|399|2C,|300|300|355|322|300|300|322|45E|300|30 ",129,0052002E00
322|300|300|300|355|333|300|300|366|355|300|300|366|46F|300|30 2000530065006F00
366|41A|300|300|366|311|300|300|377|344|300|300|377|344|300|30 6A00610074007400
366|311|300|300|366|45E|0D |0A |0D |0A |4FO|4BK|0D |0A         61006E....OK..  
Phonebook entry received
Parsing +CPBR: 1,"5926268784",129,0052002E002000530065006F006A0061007400740061006E with +CPBR: @i, @p, @i, @s
Parsed int 1
Grabbed string from reply: "5926268784" (parsed 12 bytes)
Parsed phone string "5926268784"
Parsed int 129
Grabbed string from reply: "0052002E002000530065006F006A0061007400740061006E" (parsed 48 bytes)
Parsed generic string "0052002E002000530065006F006A0061007400740061006E"
Generic AT reply detected
Already in mode 2
SENDING frame type 0x00/length 0x0E/14
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|47G|53S|4DM|22"|0D         AT+CSCS="GSM".  
1 "AT+CSCS="GSM""
2 "OK"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|43C|53S|43C|53S|3D=|22"|47G|53S|4DM|22"|0D |0D |0A AT+CSCS="GSM"...
4FO|4BK|0D |0A                                                 OK..            
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|53S|3F?|0D                             AT+CSCS?.       
1 "AT+CSCS?"
2 "+CSCS: "GSM""
3 "OK"
RECEIVED frame type 0x00/length 0x1F/31
41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53 AT+CSCS?...+CSCS
3A:|20 |22"|47G|53S|4DM|22"|0D |0A |0D |0A |4FO|4BK|0D |0A     : "GSM"....OK.. 
Getting SMSC
Already in mode 2
SENDING frame type 0x00/length 0x09/9
41A|54T|2B+|43C|53S|43C|41A|3F?|0D                             AT+CSCA?.       
1 "AT+CSCA?"
2 "+CSCA: "+5926400003",145"
3 "OK"
RECEIVED frame type 0x00/length 0x2B/43
41A|54T|2B+|43C|53S|43C|41A|3F?|0D |0D |0A |2B+|43C|53S|43C|41 AT+CSCA?...+CSCA
3A:|20 |22"|2B+|355|399|322|366|344|300|300|300|300|333|22"|2C : "+5926400003",
311|344|355|0D |0A |0D |0A |4FO|4BK|0D |0A                     145....OK..     
SMSC info received
Parsing +CSCA: "+5926400003",145 with +CSCA: @p, @i
Grabbed string from reply: "+5926400003" (parsed 13 bytes)
Parsed phone string "+5926400003"
Parsed int 145
Getting signal quality info
Switching to mode 0
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0A/10
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                         AT+MODE=0.      
1 "AT+MODE=0"
2 "ERROR"
RECEIVED frame type 0x00/length 0x13/19
41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |45E|52R|52R|4F AT+MODE=0...ERRO
52R|0D |0A                                                     R..             
GSM_GetSignalQuality failed with error 27: Unknown error.
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
1 "AT+MODE=22"
2 "ERROR"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D |0D |0A |45E|52R|52 AT+MODE=22...ERR
4FO|52R|0D |0A                                                 OR..            
GSM_GetMemoryStatus failed with error 27: Unknown error.
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
[Retrying 1 type 0x00]
SENDING frame type 0x00/length 0x0B/11
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D                     AT+MODE=22.     
1 "AT+MODE=22"
2 "ERROR"
RECEIVED frame type 0x00/length 0x14/20
41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|322|0D |0D |0A |45E|52R|52 AT+MODE=22...ERR
4FO|52R|0D |0A                                                 OR..            
GSM_GetNextMemory failed with error 27: Unknown error.
```

---

