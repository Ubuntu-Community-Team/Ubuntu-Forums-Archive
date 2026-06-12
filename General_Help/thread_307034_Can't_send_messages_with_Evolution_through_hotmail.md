---
title: "Can't send messages with Evolution through hotmail..."
date: 2006-11-26
forum: General Help
---

### Post by klokwyze on 2006-11-26
I can't seem to send messages with Evolution through Hotmail though... Evolution just hangs on the "send/receive mail" screen. It completes receiving inbound messages, but just stays @ 0% on outbound messages.

I use a pop3server called Izymail to get around the M$ pop3 webdav problems.

For "server" under server configuration I've tried

127.0.0.1:2500
127.0.0.7:2500
hotmail.com:2500
out.izymail.com:2500

all of them with server type "smtp", "server requires authentication" checked, no security, plain authentication, with my full email as the username.

anyone have any suggestions?

---

### Post by klokwyze on 2006-11-26
I am open to any possible way to send outgoing mail through hotmail via EVolution OR Thunderbird.... I get the same problems with both email clients.

---

### Post by mayonaise15 on 2006-11-26
have you checked [this?]("http://v3.izymail.com/support.aspx#timeout")

---

### Post by vtel57 on 2006-11-26
For Thunderbird, there are two extensions: Webmail and Webmail:Hotmail (you'll need both). I've been using them, plus Webmail:Yahoo, to access my Hotmail and Yahoo mail for a while now. These extensions work excellently for me in T-bird. You can find them [HERE](http://webmail.mozdev.org/).

Luck! :) 

~Eric

---

### Post by klokwyze on 2006-11-26
> **vtel57 said:**
> For Thunderbird, there are two extensions: Webmail and Webmail:Hotmail (you'll need both). I've been using them, plus Webmail:Yahoo, to access my Hotmail and Yahoo mail for a while now. These extensions work excellently for me in T-bird. You can find them [HERE](http://webmail.mozdev.org/).

Luck! :) 

~Eric

Yeah I actually have both those extensions, but the same problem is on both Evolution and Thunderbird.... I just preferred Evolution because it came with Ubuntu. I can receive mail fine through the program, but can't send out. I will mess around and see if port 25 is specifically blocked, but I don't think that is the case.[-(

---

### Post by vtel57 on 2006-11-26
> **klokwyze said:**
> Yeah I actually have both those extensions, but the same problem is on both Evolution and Thunderbird.... I just preferred Evolution because it came with Ubuntu. I can receive mail fine through the program, but can't send out. I will mess around and see if port 25 is specifically blocked, but I don't think that is the case.[-(

Those extensions do NOT use POP3 or SMTP. They are Perl scripts that utilize your local machine and Port 80 to access the webmail services. If you can't send using them, then you most likely have the settings incorrect for the extensions.

---

### Post by AmandaKerik on 2007-02-02
> **vtel57 said:**
> Those extensions do NOT use POP3 or SMTP. They are Perl scripts that utilize your local machine and Port 80 to access the webmail services. If you can't send using them, then you most likely have the settings incorrect for the extensions.

Well, I learn something new every day... :D That's kinda cool.

---

### Post by vtel57 on 2007-02-03
Yes, those extensions are pretty neat... and handy! :)

---

### Post by AmandaKerik on 2007-02-03
I'm a huge fan of Firefox add-ons, but I'm still exploring the Thunderbird ones...

Gotta love open source!

---

### Post by vtel57 on 2007-02-03
I don't use nearly as many with T-Bird as I do with FF. However, I do use a few...

- Mark All As Read Button

- Mozilla Calendar

- Newsworthy

- Preferential

- Time Stamp

- Webmail

- Webmail - Hotmail

- Webmail - Yahoo

---

