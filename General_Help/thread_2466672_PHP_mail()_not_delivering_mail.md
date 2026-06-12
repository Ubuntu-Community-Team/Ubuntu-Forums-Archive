---
title: "PHP mail() not delivering mail"
date: 2021-09-02
forum: General Help
---

### Post by ainulindale127 on 2021-09-02
Hi, I'm new to web development/php, so this may be a simple mistake. I am using Apache2 on Ubuntu. Added: '/usr/lib/sendmail -t -i' to sendmail_path in php.ini. The attachment includes the basic mail() function call I used, and it always returns 'true' indicating that the message was accepted for delivery and the logs confirm. However, the email is never sent. How do I get it to actually deliver the mail? Thanks for any help in advance.

---

### Post by norobro on 2021-09-02
From here: [https://www.php.net/manual/en/function.mail.php](https://www.php.net/manual/en/function.mail.php)> [COLOR=#333333][FONT=&amp]Returns [/FONT][/COLOR][COLOR=#333333][FONT=&amp]true[/FONT][/COLOR][COLOR=#333333][FONT=&amp] if the mail was successfully accepted for delivery, [/FONT][/COLOR][COLOR=#333333][FONT=&amp]false[/FONT][/COLOR][COLOR=#333333][FONT=&amp] otherwise.

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]It is important to note that just because the mail was accepted for delivery, it does NOT mean the mail will actually reach the intended destination.[/FONT][/COLOR]Have you checked your MTA logs?

---

### Post by HermanAB on 2021-09-03
Divide and conquer: Try debugging the problem using the mail command in a terminal.  That may give you more meaningful error messages.

---

