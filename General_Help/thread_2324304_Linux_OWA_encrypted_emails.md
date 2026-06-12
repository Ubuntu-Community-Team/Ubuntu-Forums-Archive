---
title: "Linux OWA encrypted emails"
date: 2016-05-12
forum: General Help
---

### Post by Richard_Romick on 2016-05-12
Greetings forum users,

I regularly use OWA for accessing my Air Force email account at home.  I just recently got OWA w/CAC access to work in Firefox on Ubuntu, a great achievement for me.

My next hurdle is to find a way to access emails encrypted with S/MIME.  From my research, S/MIME is an activeX control that only works on IE.

I know this isn't strictly a Ubuntu issue, but if anyone has any ideas how this could be accomplished, I would be grateful (I am not restricted to using Firefox if the answer requires something else.

Thank you,

---

### Post by QDR06VV9 on 2016-05-12
> **Richard_Romick said:**
> Greetings forum users,

I regularly use OWA for accessing my Air Force email account at home.  I just recently got OWA w/CAC access to work in Firefox on Ubuntu, a great achievement for me.

My next hurdle is to find a way to access emails encrypted with S/MIME.  From my research, S/MIME is an activeX control that only works on IE.

I know this isn't strictly a Ubuntu issue, but if anyone has any ideas how this could be accomplished, I would be grateful (I am not restricted to using Firefox if the answer requires something else.

Thank you,
See if this is of any help.....Down to the green check mark
[http://askubuntu.com/questions/181851/how-to-obtain-a-s-mime-certificate-for-e-mail-encryption](http://askubuntu.com/questions/181851/how-to-obtain-a-s-mime-certificate-for-e-mail-encryption)
Kind Regards

---

### Post by Richard_Romick on 2016-05-12
Good article.  I looked into using S/MIME in Thunderbird, but I couldn't see how to connect it to my Air Force Exchange account.  I haven't been able to find anything by googling it.

---

### Post by mastablasta on 2016-05-13
well probably Google won't have the answer to "how to connect to air force account" :)

check the server settings in TB. what you need to get in there is your server's settings. such as port, server ip or name + uname & pass. then you have to set these up in TB server settings and well then you use certificate to connect. you also need to set up outgoing mail server (SMTP)

exchage has option of  connecting by web browser. do you have this option? in that case you could use certificate on Firefox to connect to webmail. we would get the lin (address) visible in our Outlook account settings at work.

---

### Post by capncooknl on 2017-05-05
The main problem is that there is no password. Logging on to both Outlook and OWA is done through an exchange server and smartcard certificates with a PIN. So Thunderbird isn't an obvious answer, since there's no password.

---

### Post by efflandt on 2017-05-06
OWA is *Outlook "Web" Access* to access mail on an Exchange server with any web browser (https), not POP3 or IMAP or whatever Outlook itself uses. I used Linux Firefox for OWA when not on our company WAN, but never did encrypted e-mails.

The e-mail app on my Android phone had a setting to access Exchange e-mail. But again I never did encrypted e-mail. One link about using S/MIME in Android [https://kb.iu.edu/d/ahof](https://kb.iu.edu/d/ahof) has a note "Email clients not using S/MIME certificates will not be able to view  encrypted email. Clients that cannot use S/MIME certificates include OWA  through Chrome, Firefox, and Safari; recipients who use one of these  clients will be unable to view encrypted email. However, all mail  clients can view digitally signed email." So if you have an Android device you might try web searching "android outlook smime" or for iphone, substitute that for android.

PS: Or better yet web search: linux outlook smime

---

### Post by oldos2er on 2017-05-06
Old thread closed. Anyone still with problems should start a new thread.

---

