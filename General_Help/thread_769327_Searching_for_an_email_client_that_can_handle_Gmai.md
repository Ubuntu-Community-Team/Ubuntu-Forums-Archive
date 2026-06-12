---
title: "Searching for an email client that can handle Gmail and hotmail accounts"
date: 2008-04-26
forum: General Help
---

### Post by ezekielnin on 2008-04-26
Hi,

I'm searching for an equivalent of the Live Mail client I use in windows. I want to access Gmail and hotmail account thru this client. If you have a suggestion please let me know. 

Thank you!

---

### Post by FastZ on 2008-04-26
You can use Mozilla Thunderbird for this while using the webmail extension.

sudo apt-get install thunderbird

and then download the following Thunderbird extensions and install them in Thunderbird:

[http://downloads.mozdev.org/webmail/web-mail-1-3-1.xpi](http://downloads.mozdev.org/webmail/web-mail-1-3-1.xpi)
[http://download.mozdev.org/webmail/hotmail-1-2-15.xpi](http://download.mozdev.org/webmail/hotmail-1-2-15.xpi)
[http://downloads.mozdev.org/webmail/gmail-0-5-14.xpi](http://downloads.mozdev.org/webmail/gmail-0-5-14.xpi)

To install these extensions do the following:

In Mozilla Thunderbird, open the extension manager (Tools Menu/Extensions).
Click the Install button, and locate/select the file you downloaded and click "OK".

---

### Post by ezekielnin on 2008-04-26
I was able to install mozilla thunderbird and the extensions but I don't understand how to setup the accounts .. should I use the option webmail or gmail?

---

### Post by smoker on 2008-04-26
you use webmail to setup your hotmail account, i;m not sure about googlemail, tho there is an option in googlemail, if you go to account, and settings, you can forward mail to thunderbird via pop/imap

best of luck

---

### Post by ludovicc on 2008-04-26
For Hotmail, do the following:
* Edit / Account parameters...
* Add an account...
* Select Web mail, then click Next
* Give you name, then your full email address on hotmail, press Next
* Give again your full email address on Hotmail
* Press Finish, it should work

For Google, it's better to go to Googlemail, activate POP or IMAP and follow the instructions provided by Google.

---

### Post by naylor on 2008-04-26
this might help;-)
for gmail pop settings:
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html)

additional info
server settings:
pop.gmail.com
security settings: ssl
port: 995

outgoing server:
smtp.gmail.com
security settings: ssl
port: 465

note: you must install webmail by itself first! then the other extensions;-).
N

---

### Post by Patsoe on 2008-04-27
> **FastZ said:**
> You can use Mozilla Thunderbird for this while using the webmail extension.

sudo apt-get install thunderbird

and then download the following Thunderbird extensions and install them in Thunderbird:

[http://downloads.mozdev.org/webmail/web-mail-1-3-1.xpi](http://downloads.mozdev.org/webmail/web-mail-1-3-1.xpi)
[http://download.mozdev.org/webmail/hotmail-1-2-15.xpi](http://download.mozdev.org/webmail/hotmail-1-2-15.xpi)
[http://downloads.mozdev.org/webmail/gmail-0-5-14.xpi](http://downloads.mozdev.org/webmail/gmail-0-5-14.xpi)

To install these extensions do the following:

In Mozilla Thunderbird, open the extension manager (Tools Menu/Extensions).
Click the Install button, and locate/select the file you downloaded and click "OK".

Thanks, I didn't know about these extensions. I was browsing the site though (at [http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)) but really couldn't figure out in which way the gmail extension is an improvement over plain pop/imap access. Is it?

---

### Post by ezekielnin on 2008-04-27
It now works with the extensions but not as well as I would like it to work.
For example I can't see the sub-folders in the inbox that I have created (I like to have things organised)

I'll try to emulate the Live mail software from Microsoft with this guide : [run-windows-apps-seamlessly-inside-linux]("http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux").

If it works I will let you know.

---

### Post by elmer_42 on 2008-04-27
GMail supports IMAP, which is way better than POP. I followed [this]("http://lifehacker.com/software/geek-to-live/turn-thunderbird-into-the-ultimate-gmail-imap-client-314574.php") guide to get Thunderbird working with GMail's IMAP.

---

