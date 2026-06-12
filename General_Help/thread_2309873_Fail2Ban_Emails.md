---
title: "Fail2Ban Emails"
date: 2016-01-14
forum: General Help
---

### Post by jakr2 on 2016-01-14
Im trying to send notifications of IP bans with fail2ban im using sendmail for this but im getting delivery errors, I can send mail via the command line and webmin etc. Just getting these errors for sending notfiactions of banned IPS

```
[COLOR=#393939]   ----- The following addresses had permanent fatal errors -----[/COLOR]<****@gmail.com>
    (reason: 530-5.5.1 Authentication Required. Learn more at)

   ----- Transcript of session follows -----
... while talking to gmail-smtp-msa.l.google.com.:
>>> AUTH dialogue
<<< 534-5.7.14 <[https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbsai](https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbsai)
<<< 534-5.7.14 P7_uE2hEfFDFsNwaVYWjTvZtLY_XbAQo3_GdvedfT35RnRlHfotxGmrCzjn12SNrxpf7g5
<<< 534-5.7.14 6NwwEQvwLL2HDxAeAkJD32MOkyorpxbJkg4WIPnaYWgw_Z4Wt7WIbnGDppUi45bd8BsvrT
<<< 534-5.7.14 aKs-Z0erTmQ96oclu8Jup2GLi5rSnC3UTZ1F_Shi_1kWWv5rkrVYon-_Vgt7uUlOEjPz0B
<<< 534-5.7.14 D2yyIBoG7TDgshr0opYw3TR9mYUw> Please log in via your web browser and
<<< 534-5.7.14 then try again.
<<< 534-5.7.14  Learn more at
<<< 534 5.7.14  [https://support.google.com/mail/answer/78754](https://support.google.com/mail/answer/78754) c190sm2408713qkb.27
- gsmtp
>>> AUTH dialogue
<<< 534-5.7.14 <[https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbuFj](https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbuFj)
<<< 534-5.7.14 ugHHi-i_gzVlKFF1XhHB46zjWOX_oZsc2m6zma0BHLknl6w0Fzumyn7Iz6wp68Q5RxFiJz
<<< 534-5.7.14 TGna0g_V_iB0kBcBXab4NnhKOX15i0u-Gj1o9QkTJjfDdaLH1s8GABtPef6JV3P1mmVW0P
<<< 534-5.7.14 SmOnBH0IyY--xwjXJuClGla0aV4DmMyEzsHAhsnSNbjPa0fjdMiJIyDW1dGw24FRXm9cfB
<<< 534-5.7.14 -csl48FNJyDyECCgBYMNPMooSkCA> Please log in via your web browser and
<<< 534-5.7.14 then try again.
<<< 534-5.7.14  Learn more at
<<< 534 5.7.14  [https://support.google.com/mail/answer/78754](https://support.google.com/mail/answer/78754) c190sm2408713qkb.27
- gsmtp
>>> MAIL From:<fail2ban@[FONT=Verdana]*****.com[/FONT][FONT=Verdana]> SIZE=609[/FONT]
<<< 530-5.5.1 Authentication Required. Learn more at
<<< 530 5.5.1  [https://support.google.com/mail/answer/14257](https://support.google.com/mail/answer/14257) c190sm2408713qkb.27 -
gsmtp
554 5.0.0 Service unavailable
550 5.1.1 <fail2ban@*****.com>... User unknown
```

---

### Post by mastablasta on 2016-01-14
you were provided with links. have you followed instructions in them?
Also :
> Authentication Required.
obviously you didn not setup password or user for sendmail gmail account.

does CLI and webmin use the same service to send mail?

---

### Post by SeijiSensei on 2016-01-14
I don't understand why you're trying to log in at all.

The primary MX for gmail.com isn't the host you're connecting to, it's gmail-smtp-in.l.google.com:
```

$ host -t mx gmail.com
gmail.com mail is handled by 30 alt3.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 40 alt4.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 5 gmail-smtp-in.l.google.com.
gmail.com mail is handled by 10 alt1.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 20 alt2.gmail-smtp-in.l.google.com.

```
By default, sendmail will just consult the DNS and send the message to that server.

My mail server, also using sendmail, sends dozens of messages to gmail.com addresses every day using ordinary SMTP.

---

### Post by jakr2 on 2016-01-14
> **SeijiSensei said:**
> I don't understand why you're trying to log in at all.

The primary MX for gmail.com isn't the host you're connecting to, it's gmail-smtp-in.l.google.com:
```

$ host -t mx gmail.com
gmail.com mail is handled by 30 alt3.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 40 alt4.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 5 gmail-smtp-in.l.google.com.
gmail.com mail is handled by 10 alt1.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 20 alt2.gmail-smtp-in.l.google.com.

```
By default, sendmail will just consult the DNS and send the message to that server.

My mail server, also using sendmail, sends dozens of messages to gmail.com addresses every day using ordinary SMTP.
Im not trying to log in, thats just the delivery message I get from my mail when it attempts to send the email.

---

### Post by SeijiSensei on 2016-01-14
> while talking to gmail-smtp-msa.l.google.com.

Is that the MX server you see with "host -t mx gmail.com" on your server?  As I said, it's not the primary MX reported by my DNS servers, nor by Google's own DNS server at 8.8.8.8.  What nameserver are you using?

---

