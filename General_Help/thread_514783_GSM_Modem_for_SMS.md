---
title: "GSM Modem for SMS"
date: 2007-08-01
forum: General Help
---

### Post by Peque on 2007-08-01
Hey THere. 

I have an SiemensTC35 Terminal that I would like to use for sending out SMS. 

First of all - Would like to be able to send system messages out for my servers - if somethings fails - like Nagios etc . 

Options 1:
I have downloaded smssend and GSM-utils and the libary. 
This is working just great - BUT not with the danish letters - Æ Ø Å ! And I read in the documentation - that smssend is not supporting this ???? 
UNFORTUNABLY - but have anyone find a way around....

Options 2: 
I also tried with smsclient - but that is not working at all - And I cannot find anything to make those changes that I would like to - each time I try sending a SMS using sms_client : sms_client Phonenumber 'Testing testing. ' (And have tried most of the different providers:) I'll get this : 
Dialing SMSC 08XXXXXXXXXX (different from each provider) 
WARNING: read() TIMEOUT
ERROR: Timeout: searching for +<CR>>LF>+ failed after 10 seconds
ERROR: MODEM: Setting local echo Failed 
total elapsed time: 16seconds


What can I do to make the letters become normal (So danish people can read the messages)  and send using sms_client

THanks
P

---

### Post by be4truth on 2007-08-02
Can't help you with this but found an interesting link:
[http://digitalife.wordpress.com/2007/07/31/using-your-mobile-phone-as-a-gprs-modem-with-ubuntu-linux-via-dku-2-usb-cable/]("http://digitalife.wordpress.com/2007/07/31/using-your-mobile-phone-as-a-gprs-modem-with-ubuntu-linux-via-dku-2-usb-cable/")

---

