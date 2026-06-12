---
title: "Sprint Wireless Broadband Card"
date: 2007-01-06
forum: General Help
---

### Post by Captiivus on 2007-01-06
Can anyone tell me if it's supported by (K)Ubuntu?

---

### Post by Captiivus on 2007-01-07
bump

---

### Post by RandomJoe on 2007-01-07
I've been wondering the same thing (have a Merlin S720 card for work) and did some Googling just now.  The answer is YES! :mrgreen: 

Here's a HOWTO:
[http://www.cs.drexel.edu/~kfu22/evdo/](http://www.cs.drexel.edu/~kfu22/evdo/)

From that, it sounds like there are others out there as well, but I quit digging with it...

---

### Post by peterLinux on 2007-01-07
Take a peek here,
it is for another distro (one I left behind)
but may help

[http://www.novell.com/coolsolutions/tip/17600.html](http://www.novell.com/coolsolutions/tip/17600.html)

Peter

---

### Post by tube013 on 2007-01-10
I just got an S720 from sprint, and after activating it on Windows it works fine with edgy and the scripts available over on evdoforums.com

You have to modprobe usbserial with some product and vendor info... Does anyone know how to get his to be done automagically when the card is installed?   I've tried adding it to /etc/modprobe.d/options and to /etc/modprobe.d/usbserial, but no go.  Just trying to automate as much as I can.  But I'm likely to get a linksys or kycera router to use with it and this will all be moot.

---

### Post by peterLinux on 2007-01-10
Put the modprobe cmds in a script.
call the file start1x.
put it in /usr/local/bin
make sure it is executable (chmod 755)

Do you want to start this every time your boot?
let your ~/.bash_profile call the start1x script.

Hope this helps

Peter

---

### Post by SonWon on 2007-01-12
How do I do the ~/.bash_profile part?  I tried running in a term and no work?

Thanks,

---

### Post by peterLinux on 2007-01-13
You know how to edit that file?

bash_profile should run automagically each time you start up.

Maybe there is an error in your start1x script.
Here is mine:
#!/bin/bash

# Start the Kyocera 1X aircard

modprobe ohci-hcd
modprobe usbserial vendor=0x0c88 product=0x17da
pppd call 1x


in /etc/ppp/peers
I got 2 files
as explained in the Novell article.

vi /etc/ppp/peers/1x

ttyUSB0
115200
debug
noauth
defaultroute
usepeerdns
connect-delay 10000
user [email]9999999999@bellmobility.ca[/email]
show-password
crtscts
lock
lcp-echo-failure 0
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1x_chat'

Replace the [email]9999999999@bellmobility.ca[/email] with the area code and phonenumber assigned to your Bell Canada card.

Not using Bell Canada? Google for the right domainname!

Some examples I found @vzw3g.com for Verizon Wireless in the US and @1x.telusmobility.com in Canada)

The first line ttyUSB0 can also be ttyAMD0 depending on were things mount on your o.s.

Time to create the second file that we need.

vi /etc/ppp/peers/1x_chat

ABORT 'NO CARRIER' ABORT ERROR ABORT 'NO DIALTONE' ABORT BUSY ABORT 'NO ANSWER'
'' 'ATTEV1&F&D2&C1&C2S0=0S7=60'
'OK-ATTEV1&F&D2&C1&C2S0=0S7=60-OK-ATTEV1&F&D2&C1&C2S0=0S7=60-OK' 'AT+CSQ;D#777'
TIMEOUT 70
'CONNECT-AT+CSQ;D#777-CONNECT'

---

### Post by SonWon on 2007-01-13
I am a bit of a newb.  What is the bash_profile and where does the file go so it will auto run?  If I had to guess bash_profile is a script file that the OS auto runs on startup?

I am using Edgy.

Thanks for your patience with me.

---

### Post by peterLinux on 2007-01-14
The file already exists,
it sits in your home folder but start with a "." (dot) so it is hidden
you can see it if you do an 
ls -la
from the command line.

In my case I see
-rw-r--r--  1 peter peter      414 2007-01-13 20:14 .bash_profile
amongst other things

cat ./.bash_profile
prints the content of the file in the console.

---

### Post by SonWon on 2007-01-14
Found it, thank you very much.

Later today I am going to give all of this a try.

Is there a .bash_profile file for all users so every user would get the same treatment?

Thanks again.

---

### Post by peterLinux on 2007-01-14
Inspect the file /etc/profile

Google for 'Linux boot sequence' to learn which bash script is run when.

Peter

---

### Post by SonWon on 2007-01-14
Thank you.

I was looking for this information about a month ago and never found my answer.  Now with the boot sequence info I have I think I can piece it all together.

Thanks again,

---

### Post by Rick Z on 2007-08-15
I am a new user in Ubuntu 7.04.  I am not able to setup Sprint Boardband Pantech PX500 Data Card.  Can anyone please guide me through the steps.  I have found the pdf file post it from Sprint's website, but it doesn't help.

---

### Post by Rick Z on 2007-08-16
--------------------------------------------------------------------------------

I have been googling around for the a week and finally I found the answer I am looking for. I am able to setup my pantech PX500 data card. I found this website extremely helpful. I post here in case if anyone else is encounter the same problem I had.

[http://www.raincitystory.com/wp/2007...inux/#comments](http://www.raincitystory.com/wp/2007...inux/#comments)

---

### Post by Rick Z on 2007-08-16
[http://www.raincitystory.com/wp/2007/05/31/pantech-px-500-evdo-rev-a-card-on-linux/#comments](http://www.raincitystory.com/wp/2007/05/31/pantech-px-500-evdo-rev-a-card-on-linux/#comments)

---

