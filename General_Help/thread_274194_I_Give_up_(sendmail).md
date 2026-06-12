---
title: "I Give up (sendmail)"
date: 2006-10-09
forum: General Help
---

### Post by davedekker on 2006-10-09
I know its most likely against the rules, but I have been trying to get sendmail configured on my new LAMP server with no luck... any guru's willing to help?  I have searched and read about everything I could find... from "its the most complicated thing" to "it works right out of the box"... Please Please Please...

thanks

p.s.  trying to get the server so that PHP cripts will send mails for things like signing up on forums I will be hosting


DD

[email]davedekker@gmail.com[/email]

---

### Post by lawina on 2006-10-10
You didn't write what issues you are facing, something like a screenshot or atleast a error message.
This is a desktop forum.
However, try this link for sending emails through php.
[http://www.chauy.com/2005/11/php-sendmail-tutorial/](http://www.chauy.com/2005/11/php-sendmail-tutorial/)

---

### Post by PriceChild on 2006-10-10
Yeah, please also give details of what guides you have been following, how far you've got with them and finally all errors in the terminal :)

Pricey

---

### Post by Coomkeen on 2006-10-11
I had a server and had no problem sending mail from PHP, and that was without sendmail running.
Running or not running sendmail had no effect on mail from PHP.
My website has fascilities writen in PHP to send mail to one of three people, or to send newsletters to a database of subscribers, and it all runs fine without sendmail.

---

### Post by tomBorgia on 2006-10-11
Tried Postfix? It works fine with the mail() function in PHP for me. Think you can install it with apt-get. 
The config file main.cf is not too complicated...

---

