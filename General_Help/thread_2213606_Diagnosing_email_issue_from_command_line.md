---
title: "Diagnosing email issue from command line"
date: 2014-03-27
forum: General Help
---

### Post by Dave_L on 2014-03-27
I recently created an email account on a web hosting account. When I try to access the account from thunderbird, using either IMAP or SMTP, I get the error ""Login to server example.com failed." (example.com is not the actual server name; I'm only using it here for privacy.)

If I use the thunderbird addon TBTracer, the error is displayed as "2 NO [AUTHENTICATIONFAILED] Authentication failed."

As far as I can determine, the login credentials (server name, username, port, etc.) are correct.

Is there any documentation on how to diagnose this problem from the command line?

---

### Post by whitesmith on 2014-03-27
I think you'd have better luck with this one by looking/posting on the TBTracer site. Thunderbird also has good support on the Mozillazine forum. On the other hand, by remaining here and being very patient ... Regards.

---

### Post by Dave_L on 2014-03-27
I don't know if it's a problem with thunderbird, or with the email account itself. Thats what I need to isolate.

What I'm trying to do is access the email account "manually", using basic commands, e.g. with telnet or ssh. Do you think either of those sites would help with that?

---

### Post by whitesmith on 2014-03-27
I've thrown out some pretty stick stuff at the Mozillazine forum and received answers that surprised me in their detail. I hope the same works for you!

---

### Post by Dave_L on 2014-03-27
Ok, I'll try that.  Thanks for the tip. :KS

---

### Post by steeldriver on 2014-03-27
You can check the outgoing side at least accepts your mailbox name using telnet / EHLO - here's an actual session transcript (suitably anonymized)

```

$ **telnet smtp.example.com 587**
Trying xxx.xxx.xxx.xxx...
Connected to smtp.example.com.
Escape character is '^]'.
220 mailhost.example.com ESMTP Postfix
** EHLO steeldriver@example.com**
250-mailhost.example.com
250-PIPELINING
250-SIZE 36700160
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250 8BITMIME
** MAIL From:<steeldriver@example.com>**
250 2.1.0 Ok

```

Not sure about the incoming side (POP/LDAP)

---

### Post by Dave_L on 2014-03-27
Thanks.  I tried the corresponding telnet commands, and got the same results that you posted.  Then I tried AUTH LOGIN, and got "535 Incorrect authentication data".

I'll dig into it some more with that approach.

---

### Post by Dave_L on 2014-03-27
Ok, problem fixed. I think the issue was that the username had to include the "@example.com" and that had been omitted. But I kept changing settings, so I'm not sure.

---

### Post by SeijiSensei on 2014-03-28
Most third-party hosting services require the full email address with domain as a login.

---

### Post by Dave_L on 2014-03-28
Yes, I know that, and I thought that I had included the full email address in the relevant places.

---

