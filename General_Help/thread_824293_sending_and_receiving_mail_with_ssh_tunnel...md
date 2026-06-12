---
title: "sending and receiving mail with ssh tunnel.."
date: 2008-06-09
forum: General Help
---

### Post by Mia_tech on 2008-06-09
is it possible to send and receive email with a ssh tunnel, I know it can be done with your browser, in which you create a dynamic port forwarding to a ssh server and configure your browser with socks to browse using the tunnel, sort of a vpn...is this possible to configure for your mail client, like thunderbird?

any help appreciated

thanks

---

### Post by atoponce on 2008-06-09
Yes.  It depends on the mail server that you are trying to access.  You could use remote forwarding or local forwarding.  I assume you want access to a mail server that is internal to a company intranet?  In that case, SSH remote port forwarding is what you're after:

```
ssh -NR localhost:2525:mail.example.com:25 user@ssh.foo.com
```

The previous code assumes you want access to the mail server under the domain mail.example.com, and that it's running on port 25.  Further, it assumes that you have access to the SSH server ssh.foo.com as "user".  You would run this from work before leaving for the day, then when you get home to your SSH server at ssh.foo.com, you can access the internal corporate mail server.

This has bound port 2525 locally on your box, of which you would tell Thunderbird to connect to connect to a SOCKS proxy on localhost port 2525.  You should then have access to the internal mail server as though you were sitting in the intranet at work.

---

### Post by Mia_tech on 2008-06-10
ok port 25 is to send email, how about receiving?..... pop3 do I have to create another dynamic port forwarding for 110?

thanks

---

### Post by jimv on 2008-06-10
There's no need to forward port 25.  Thunderbird will use a socks5 proxy just like Firefox.  So basically, just set your proxy settings in Thunderbird to the same was waht you have in Firefox.

---

### Post by atoponce on 2008-06-10
> **Mia_tech said:**
> ok port 25 is to send email, how about receiving?..... pop3 do I have to create another dynamic port forwarding for 110?

thanks

I guess I need to understand the context, so I can give you the proper syntax for forwarding your email connection through SSH.  Are you trying to just hide the POP3 connection, or access the POP3 server at work from home, as I previously mentioned?  I'll give you both, how about that?

If you have access to an SSH server and mail server at home with POP3, and you are at work wishing to hide the POP3 protocol through SSH, so your coworkers can't see it, then, assuming your server at home is server.com:

```
ssh -NL 11000:mail.server.com:110 -L 2525:mail.server.com:25 user@ssh.server.com
```

Ports 11000 and 2525 are any arbitrary port you wish to bind so Thunderbird can access.  Of course, make sure those ports are open and available.

If you want access to the company internal mail server that is not available outside of the corporate network, then when you are at work, issue the following command assuming you have an SSH server at home at server.com, and the company mail server is at mail.example.com:

```
ssh -NR 11000:mail.example.com:110 -R 2525:mail.example.com:25 user@ssh.server.com
```

Now, at home, connect your Thunderbird client to ports 11000 for POP3 and 2525 for SMTP, and you're accessing the private intranet server at work through SSH.

That should get you going.  Take a look in the man page at the -L, -R and -D options.  SSH is pretty flexible, and you can do a great deal with it with little effort.

---

