---
title: "Recommended Mail Server"
date: 2008-03-19
forum: General Help
---

### Post by dev@st@tor on 2008-03-19
I am looking to install a simple mail server onto my ubuntu server. I don't need it to have all the features, and I really don't even need it to be able to receive email since I have my DNS set up to forward email sent to my domain name to another email account. I just need to be able to send mail for registration purposes. Any recommendations as to what to install and guides on how to do that would be greatly appreciated. I'm not very experienced with Ubuntu or linux for that matter, so any help I can get is always appreciated.

Thanks!

---

### Post by stalker145 on 2008-03-19
> **dev@st@tor said:**
> I am looking to install a simple mail server onto my ubuntu server. I don't need it to have all the features, and I really don't even need it to be able to receive email since I have my DNS set up to forward email sent to my domain name to another email account. I just need to be able to send mail for registration purposes. Any recommendations as to what to install and guides on how to do that would be greatly appreciated. I'm not very experienced with Ubuntu or linux for that matter, so any help I can get is always appreciated.

Thanks!

I tried setting up mail servers on and off for the last couple of years and finally settled last month on Google Apps. You can run your registered domain's email through them for free :D

And you get all the other cool toys, too.

I don't know if it was my incompetence or my ISP blocking my mail servers that I tried to set up, but I never could get a home brew running.

---

### Post by dev@st@tor on 2008-03-19
> **stalker145 said:**
> I tried setting up mail servers on and off for the last couple of years and finally settled last month on Google Apps. You can run your registered domain's email through them for free :D

And you get all the other cool toys, too.

I don't know if it was my incompetence or my ISP blocking my mail servers that I tried to set up, but I never could get a home brew running.

I know I have been able to send and receive email through my ISP, albeit that the emails I sent out were often filtered as being spam.

I am not sure how it works, but does the Google App you are talking about allow me to send mail from my server? When it comes down to it, I just need this registration script to send an email to the person who registers...

---

### Post by stalker145 on 2008-03-20
> **dev@st@tor said:**
> I know I have been able to send and receive email through my ISP, albeit that the emails I sent out were often filtered as being spam.

I am not sure how it works, but does the Google App you are talking about allow me to send mail from my server? When it comes down to it, I just need this registration script to send an email to the person who registers...

Depending on the server you are using, [Google Apps]("http://www.google.com/a/help/intl/en/index.html") will work. As an example, I am using [Drupal]("http://drupal.org/") for my forum/blog. All I had to do was put the GMail SMTP server and my login information into Drupal and everything worked. 

If you are using a genuine mail server, then it probably won't work. Using Google Apps for your email is, essentially, using GMail. It's just that you get the privilege of using your personally owned domain name instead of @gmail.com. As with using GMail, you can set up your local email client to use IMAP or POP3 and forgo getting on the GMail site.

---

### Post by dev@st@tor on 2008-03-20
> **stalker145 said:**
> Depending on the server you are using, [Google Apps]("http://www.google.com/a/help/intl/en/index.html") will work. As an example, I am using [Drupal]("http://drupal.org/") for my forum/blog. All I had to do was put the GMail SMTP server and my login information into Drupal and everything worked. 

If you are using a genuine mail server, then it probably won't work. Using Google Apps for your email is, essentially, using GMail. It's just that you get the privilege of using your personally owned domain name instead of @gmail.com. As with using GMail, you can set up your local email client to use IMAP or POP3 and forgo getting on the GMail site.

Yeah... google apps isnt what I am looking for. I am looking to be able to send mail from a script on my server and I don't think google apps will be able to do that for me.

If there is something I can install that will just allow me to send mail out from my server, that'd be great. Thats all I need; everything else is just added features.

---

### Post by fjgaude on 2008-03-20
The program sendmail has been the Linux, Unix standard for many years. But I could be behind the times.

---

### Post by dev@st@tor on 2008-03-21
> **fjgaude said:**
> The program sendmail has been the Linux, Unix standard for many years. But I could be behind the times.

Im really busy with other crap right now, but if you could provide a link to said program, that'd be awesome.

---

### Post by dev@st@tor on 2008-03-23
Bump.... looking for some kind of guide to install this "sendmail" program...

---

