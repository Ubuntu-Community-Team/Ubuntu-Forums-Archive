---
title: "Sending SMS Messages via Command-Line"
date: 2007-08-30
forum: General Help
---

### Post by xluryan on 2007-08-30
Just wondering if there are any **command-line** applications or scripts that let you send SMS text messages to mobile phones.

Anyone know of any?

---

### Post by clash on 2007-08-30
[http://www.mackers.com/projects/o2sms/](http://www.mackers.com/projects/o2sms/)

Works with 3 different Irish Mobile Providers by utilising the online "send a text message" from their respective websites facilities from the command line.

---

### Post by xluryan on 2007-08-30
Sweet, thanks! I'm more looking for something for the US though. Any ideas there?

---

### Post by clash on 2007-08-30
I'm not a yank, sorry mate. Never being there.

Maybe you could edit the mackers script ?

---

### Post by EnthropyinAction on 2007-08-30
Alot of the us providers will route email to sms.  You'd have to find out what the domain is though.

For reference, I have verizon and it's <phone number>@vztext.com

---

### Post by niceguy123 on 2007-09-09
> **EnthropyinAction said:**
> Alot of the us providers will route email to sms.  You'd have to find out what the domain is though.

For reference, I have verizon and it's <phone number>@vztext.com

Can Ekiga (or something like it be used to send SMS?

---

### Post by midgemiles on 2007-09-17
I am going to try Gnokii to send SMS from computer via my mobile phone using a bluetooth link.
I found this link telling how to do it.
http://www.developershome.com/sms/smsLinux.asp#1.1.Requirements%20for%20Sending%20and%20Receiving%20SMS%20Messages%20from%20a%20Linux%20PC%20via%20a%20Mobile%20Phone|outline

---

### Post by wieman01 on 2007-09-17
"smssend" is probably what you need:

[http://linux.about.com/cs/linux101/g/smssend.htm]("http://linux.about.com/cs/linux101/g/smssend.htm")

I used it in the past and was quite happy with it. There is also a Kopete plugin if you don't want command line.

---

### Post by xluryan on 2007-11-21
Wow, digging up some old threading here... But I do like to post solutions to my questions once I find them.

EnthropyinAction's answer was probably the closest; because that's what I ended up doing. But it was important that it was from command line. At the time I didn't have any command line email clients. Or anything to send email from the command line, for that matter.

So what I tried before that was using google's little deal to send SMS. I figured I could set it up via wget, so I tried that. But then I found you have to pass it a bunch of POST-DATA, and you can only send 5 texts a day to a certain number. I did write a script to get it all working from strictly the command line, but I didn't want any limitations.

All I'm doing now is using sendEmail. NOT to be confused with sendmail. Google it, it's pretty amazing, and super easy to use. All you have to do is know the number you're sending to, their carrier, and an SMTP server to which you have access to.

Here is the command that will send a text to my T-Mobile phone:
```

sendEmail -f x@x.com -t 6515551234@tmomail.net -m 'You have to much free time!' -s <your smtp server> -xu <your username> -xp <your password>

```

The [email]x@x.com[/email] is just made up. You can use anything as long as the domain is legit. SendEmail is also a great little tool to spoof email addresses and mess with your friends :)

I found this list of carriers email domains. It's not complete, but it covers most of the major ones. [Clicky]("http://www.accutracking.com/sms-email.html")

Also, here is the script to use Google's SMS feature as well, just in case. It's not really complete either, and if you know script then you'll be able to figure it out. An example would be: ```
./send-sms.sh TMOBILE 6515551234 'Dude you are awesome.'
```
```

#!/bin/bash
# args: carrier, 10-digit-phone, "message"

msg="$(echo "$3" | sed 's| |+|g;s|\\n|%0D%0A|g')"
carrier="$(echo "$1" | tr 'a-z' 'A-Z')"
post="gl=US&hl=en&client=navclient-ffsms&text=h4ck3d&from=&c=1&mobile_user_id=$2&carrier=$carrier&ec=on&subject=&text=$msg&send_button=Send"
addr='http://www.google.com/sendtophone'
echo -n 'Sending message...     '
ret="$(wget -qO- --post-data "$post" "$addr")"

if echo "$ret" | grep -q 'Message sent!' ; then
  echo 'OK'
else
  if echo "$ret" | grep -qi 'captcha' ; then
    echo 'FAIL: CAPTCHA AUTH REQUIRED'
  else
    echo 'FAIL: UNKNOWN ERROR'
  fi
fi

exit 0

```

Enjoy!

---

### Post by mld on 2008-03-22
hi
belive me i dont understand the way
 i tried haaaaaaaaaaard  to send sms via command line

i searched all the web
i use every thing i know
but nothing found

more than 40 hours try to fix that problem
nothng found
plz
plz
plz
help  me to send sms via command line
but with a complete way
and i prefer if you send me a batch file to send the sms
thnx

---

### Post by xluryan on 2008-03-22
Ok, here is a quick way to do it:

1) Create a new file. Name is something like texter.sh. Make it executable, like this
```

chmod 755 texter.sh

```

2) Get your ISPs outgoing mail servers, i.e. smtp.comcast.net. You'll also need your username and password, so if you don't know them, get them.

3) Edit the file; put this in it, replacing it with your info where relevent:
```

#!/bin/bash

shopt -s xpg_echo

for i in $(seq 1 $3)
do
        echo -n "sending part $i of $3...  \t"
        if sendEmail -f info@x.com -t "$1@tmomail.net" -m "$2" -s YOURSMTPSERVER -xu YOURUSERNAME -xp YOURPASSWORD | grep -q 'success' ; then
                echo "OK"
        else
                echo "FAIL"
        fi
done

exit 0

```

4) Now before you can run this script,  you'll need to install sendEmail. To install:
```

sudo apt-get update
sudo apt-get install sendemail

```

5) Now, open a terminal and cd to the directory your script is in. Once there, run it like this:
```

./texter.sh PHONENUMBER "message" NUMBEROFTEXTS

```

So for example, it might look like this:
```

./texter.sh 6515551234 "Hey dude, hows it going?" 2

```

That will send 2 text messages to 6515551234, containing the message "Hey dude, hows it going?"

**AN IMPORTANT NOTE**
You'll have to edit the script to send to other carriers if you need to. It's set up right now to send to only TMOBILE numbers. You can see this in the line that contains '@tmomail.net'. You would need to replace tmomail.net with your custom carriers text email domain. So if you wanted to send texts to AT&T people, you would replace tmomail.net with txt.att.net.

Questions?

---

