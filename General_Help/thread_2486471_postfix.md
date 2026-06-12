---
title: "postfix"
date: 2023-05-01
forum: General Help
---

### Post by fahza on 2023-05-01
is there any smtp relay system I can use to setup postfix to send smtp message from checkmk?
I could use some help I have tried google smtp but I could have set it up wrong, was using the google mail api
I might even be able to use our own smtp hosted server but no matter what I try it never works.
I have checkmk working but if it cannot send emails when shits down its not much good to me.

---

### Post by TheFu on 2023-05-01
What is the architecture?
What is the internet connectivity?
postfix is a typical MTA, like sendmail and exim. Programs that want to send email on any Unix/Linux system would use the normal MTA interface.  This is a server-to-server method.  An email client (or script) can be used too.

The way that google does email from clients isn't normal on a Unix system.

So ... checkmk should have a way to use mail/Mail to send messages through the MTA of your choice.  Then that MTA would scan and forward them to the other server or through your ISP's approved SMTP gateway.  If you have a business connection to the internet, you may need to get them to allow outbound SMTP on port 25/tcp if you don't want to use their gateway.  

If you don't want to accept inbound email, things can be easier.  I've never setup a system like that ... well, not really.  The installation of the postfix package will ask questions. Choose "satellite" in the setup.  

For a more complex gateway, just find a how-to for setting up an email gateway.

None of this addresses whether your ISP allows inbound SMTP traffic nor security considerations nor firewall settings.

In general, it is a really bad idea to set system monitoring messages to outside email systems.  Remember that those messages often contain sensitive data that shouldn't be available outside the organization.

---

