---
title: "Sendmail...ergh!!!"
date: 2007-11-01
forum: General Help
---

### Post by mkswanson on 2007-11-01
Hello Everyone,

I am VERY new to the linux world, and am having a serious problem getting a shopping cart solution I have to work with sendmail.

I have installed my webserver using WAMPP/LAMPP.  It wouldn't appear as though sendmail was installed, so I attempted to install it.

When I ran apt-get install sendmail, I got a message that the package didn't exist.  From what I could find, it looks like postfix has replaced sendmail (or includes it).  Is this correct?

Anyway, I installed postfix.  I entered the path to the sendmail program into the php.ini file.

IT STILL DOESN'T WORK.

When I try to end an email from the command line, it just sits and blinks a cursur at me (I think it was trying to tease me).

Can anyone provide some direction to someone that doesn't really have much of an idea about what they are doing...PLEASE?!?

---

### Post by mahousaru on 2007-11-01
postfix is a dropin replacement for sendmail.  Which means other applications should treat it the same.

```
sudo postconf sendmail_path
```

Will give you the binary path

---

### Post by HermanAB on 2007-11-01
Well, postfix has to be configured right else it won't send the mail anywhere.  Go to the postfix web site and read some.

Test with:
$ mail -s whatever [email]yourname@example.com[/email]
.

^-- that is a dot!
and the message should get to you.  If not, then you gotta fixit.

It ain't easy...

Cheers,

Herman

---

### Post by mkswanson on 2007-11-01
Thanks for the replies.

I tried to test it, and it looked like there weren't any errors, but the mail was never delivered.  

Is there a log file somewhere that will point me in the right direction?  I've read losts of posts, and tried to make sense of what I could on the pstfix site...even copied word for word from another config file, but still haven't had any luck.

Any insights/help would be greatly appreciated!

---

### Post by mahousaru on 2007-11-02
Does your ISP allow port 25 or do you need to use a relay?

Check your logs for it unable to send.

System, Administration, System Logs.

If you do need to use a relay host check the file

/etc/postfix/main.cf

you need to have

relayhost = smtp.someisp.com

Receiving email you need
mydestination = yourdnsnames

Hmm i think you might need to also have

inet_interfaces = all

or it won't accept email from external sources

---

