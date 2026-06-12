---
title: "Script to check gmail account with LED notification (Laptop users...)"
date: 2008-05-30
forum: General Help
---

### Post by El_Belgicano on 2008-05-30
Here is the script I'm using to check my gmail account automatically and give me a notification by the LED on my laptop, if you don't know how to enable your LED, I refer to the Pedric's Howto (see credits) 

```
#!/bin/bash
gmail_login="xxxxxx"
gmail_password="xxxxx"
mails="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"
if [ "$mails" -gt "0" ];
then
	for ((i = 0; i < 10; i++)) do
		echo 1 > /proc/acpi/asus/mled;
		sleep 0.8;
		echo 0 > /proc/acpi/asus/mled;
		sleep 0.5;
	done
fi
exit
```
save the script somewhere and make it executable.

You also need to create a crontab entry for this to run every time you define:
(I'm running it every 5 minutes)
```
00 * * * * .scripts/gmailLED.sh
05 * * * * .scripts/gmailLED.sh
10 * * * * .scripts/gmailLED.sh
15 * * * * .scripts/gmailLED.sh
20 * * * * .scripts/gmailLED.sh
25 * * * * .scripts/gmailLED.sh
30 * * * * .scripts/gmailLED.sh
35 * * * * .scripts/gmailLED.sh
40 * * * * .scripts/gmailLED.sh
45 * * * * .scripts/gmailLED.sh
50 * * * * .scripts/gmailLED.sh
55 * * * * .scripts/gmailLED.sh

```

**_Credits:_**
- [**Gmail bash script from *dbbolton***]("http://ubuntuforums.org/showpost.php?p=5070961&postcount=950")
- [**Howto: LED-notification by *Pedric***]("http://ubuntuforums.org/showthread.php?t=539425")

---

### Post by K.Mandla on 2008-05-30
Moved to General Help.

---

### Post by pointone on 2008-05-30
Instead of multiple entries in crontab, use the following code to run every 5 minutues:

```
*/5 * * * * .scripts/gmailLED.sh
```

---

### Post by ChameleonDave on 2008-07-03
That script is no good, because it relies on certain hardware.

This should work on any computer.

```

sudo apt-get install blinkd

```

```
#!/bin/bash
gmail_login="**XXXX**"
gmail_password="**XXXX**"
mails="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"
[I]if [ "$mails" -gt "0" ];
then[/I]
blink --scrolllockled --rate=$mails;
[I]else
blink -s --rate=0;
fi[/I]
exit
```

The rate of blinking tells you how many mails are waiting for you.

If you get a lot of mails, you could change the zero in the "if" line to two or three, so that it only bothers you when there are more mails to read.  If you're happy with it alerting you of every e-mail, you could simplify the code by removing all the lines in *italics* in the script.

To "snooze" it (tell it to give you another five minutes to get to gmail, type "*blink -sr 0*".  You could make a launcher for that and stick it on your desktop.

To tell it to stop annoying you for the rest of the session, kill the daemon.  ("*sudo killall blinkd*")

If the flashing doesn't work, make sure that the daemon is running.  ("*sudo blinkd*")

---

### Post by tom957 on 2008-07-04
This is one of the coolest things I've ever seen (computer-related, that is).

---

### Post by Xavier Oddmon on 2008-09-25
This is significantly awesome, but I figured voice would make it better. Here's mine:

```
#!/bin/bash
echo "Checking for new email";
mailsa="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://name1:password1@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

echo $mailsa;

mailsb="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://name2:password2@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

echo $mailsb;

#blink LEDs
if [ "$mailsa" -gt "0" ];
then
	blink -s -r 5;
fi

if [ "$mailsb" -gt "0" ];
then
	blink -c -r 5;
fi

#speak announcements

if [ "$mailsa" -gt "0" ];
then
	espeak "$mailsa new emails in main account.";
fi
if [ "$mailsb" -gt "0" ];
then
	espeak "$mailsb new emails in secondary account.";
fi

sleep 4;
blink;

exit
```

It checks two email accounts. Notice that I did away with the variables containing the name and password and stuck them right in the URL. Don't remember why...

Now, i'd like to know, is there any way to make this code more secure, IE not having my password in plain text?

---

### Post by Götz on 2009-04-19
Thank you very much for the scripts! 

I made a mix with espeak and kdialog, which asks you for you account and password, I think is more secure. 

But I would also like to encrypt the password into the script, maybe using KWallet or GNOME Keyring.

```

#!/bin/bash

echo "Write your email account."
read gmail_login
echo "Write your password."
read gmail_password
# gmail_login="XXXX"
# gmail_password="XXXX"
# echo -n $mail_password | md5sum | awk {'print $1'} > /dev/null
timeout="8"

mails="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"
if [ "$mails" -gt "0" ]; then
  kdialog --passivepopup "($mails) new emails" "$timeout";
  espeak "$mails new emails in main account.";
else
  kdialog --passivepopup "0 new emails" "$timeout";
  espeak "0 new emails in main account.";
fi
exit

```

It is possible to encrypt a text in MD5 (you can also use sha2) 
```
echo -n $mail_password | md5sum | awk {'print $1'} > /dev/null
```  
but I can't use the encrypted password to login into gmail using this url. ```
https://username:password@mail.google.com/mail/feed/atom
```

---

### Post by paradigm2 on 2009-04-19
> **Xavier Oddmon said:**
> This is significantly awesome, but I figured voice would make it better. Here's mine:

```
#!/bin/bash
echo "Checking for new email";
mailsa="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://name1:password1@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

echo $mailsa;

mailsb="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://name2:password2@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

echo $mailsb;

#blink LEDs
if [ "$mailsa" -gt "0" ];
then
	blink -s -r 5;
fi

if [ "$mailsb" -gt "0" ];
then
	blink -c -r 5;
fi

#speak announcements

if [ "$mailsa" -gt "0" ];
then
	espeak "$mailsa new emails in main account.";
fi
if [ "$mailsb" -gt "0" ];
then
	espeak "$mailsb new emails in secondary account.";
fi

sleep 4;
blink;

exit
```

It checks two email accounts. Notice that I did away with the variables containing the name and password and stuck them right in the URL. Don't remember why...

Now, i'd like to know, is there any way to make this code more secure, IE not having my password in plain text?

Very awesome.  Thank you.

I think I am going to try to set it up so it can optionally say the sender's name or otherwise look for certain subjects.

Also, I think I will need to set cron so it does not run late at night while i sleep. :)

---

### Post by paradigm2 on 2009-04-19
> **pointone said:**
> Instead of multiple entries in crontab, use the following code to run every 5 minutues:

```
*/5 * * * * .scripts/gmailLED.sh
```

Just for anyone else kind of new who has their computer in the bedroom :

```
*/5 9-23 * * * .scripts/gmailLED.sh
```

For instance should make it run only from 9am - 11pm local time (I believe local, if not UTC?]

Haven't tested it but it should work.

---

### Post by go_beep_yourself on 2009-06-20
I've been modifying and working on my own version of this script. Here it is. You guys try this out and see what how you like it.

[PHP]chris@ubuntu:~$ crontab -l
# m h  dom mon dow   command
0 * * * * mv /tmp/motion/*.swf /home/chris/Videos/Webcam/
*/5 * * * * /home/chris/bin/mailblinker &> /dev/null
chris@ubuntu:~$ [/PHP]

[PHP]chris@ubuntu:~$ which mailblinker 
/home/chris/bin/mailblinker
chris@ubuntu:~$ cat $(which mailblinker)
#!/bin/bash
gmail_login="xxxxxxx"
gmail_password="xxxxxxxx"
mails="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"
# Use this below to check mail from specific labels or put all to check all mails
# https://mail.google.com/mail/feed/atom/cakes

# blinkd only accepts blink rates of 0-29
if [ "$mails" -gt 29 ];
then
  mails=29
fi

if [ "$mails" -gt 0 ];
then
  blink -c --rate=$mails
  mplayer /home/chris/Downloads/sms-received5.caf &> /dev/null
else
  blink -c --rate=0;
fi
exit
chris@ubuntu:~$ [/PHP]

To make this script work, you are going to have to put in your personal information and paths replacing mine. I've included the sound file I that plays "You've got mail!". And you will need to extract it and put the path and filename to it in the script. You need to chmod +x the script. I also might modify the script to say who the new mail(s) are from. Also having the script in ~/bin is nice because that puts it in my path, and I can type mailblinker from any directory to run the script just like any other command. If you want ~/bin to be in your path, then you need this in your ~/.profile

[PHP] 19 # set PATH so it includes user's private bin if it exists                                                                       
 20 if [ -d "$HOME/bin" ] ; then                                                                                                    
 21     PATH="$HOME/bin:$PATH"                                                                                                      
 22 fi[/PHP]

Don't put the line numbers. Vim puts those line numbers in, and I copied it from there. If my thread helped anyone, push the thanks button.

---

### Post by geo909 on 2009-06-20
Thanks for this thread! This is an amazing idea

---

### Post by go_beep_yourself on 2009-06-20
Don't forget to install blinkd to use this script.

sudo apt-get install blinkd

I use it because it works with the leds on desktop keyboards, not just laptops. The mled software doesn't work for desktops.

---

### Post by vulcanfk on 2013-02-12
Sorry to dig up this old thread, but I just came across this and thought it was a great idea. I had trouble getting this script to work for a domain account though, so I figured I'd share the updated script in case anyone else was trying to do the same thing.

The user/password had to be pulled out of the URL. Since they contained '@', they were confusing wget. Use the following instead. Note: be sure to surround your username/password in quotes.
```

un="user@domain.com"
pw="password"
mails="$(wget --secure-protocol=TLSv1 --http-user=${un} --http-password=${pw} \
--timeout=3 -t 1 -q -O - \
https://mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

<insert chosen flavor of alerting of emails>

```

Also, I've found that the mail/feed/atom/important tag always returns a fullcount of 0, even with unread messages. I'm not sure why this is, but it's annoying. Anyone have ideas about it?

---

### Post by oldos2er on 2013-02-12
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

