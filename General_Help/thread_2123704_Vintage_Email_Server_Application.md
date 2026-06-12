---
title: "Vintage Email Server Application"
date: 2013-03-08
forum: General Help
---

### Post by VexingGrey on 2013-03-08
[SIZE=1][COLOR=#696969]Attention: Not sure if this is completely the best place to post this; if not so, then whatever admin or moderator can feel free to move it accordingly (not that you don't already have such power -- I am merely suggesting). Onward to my post.[/COLOR][/SIZE]

    
So, I'm not completely new to Linux. I have office experience with Lucid Puppy and Ubuntu. I, also, have a bit of gaming experience with Ubuntu. I started on windows 98 as a child. I remember 
that there were some applications that could host a virtual email server in XP as I aged. Later, I learned of older versions that were for Unix systems that would export directly to a C terminal. I'm looking for an updated or outdated version of any email server applications that run in the Unix environment that perform as described.  

 Feel free to list any newer email server applications that I can export/manipulate via terminal as well. I like to experience the way that things were long ago, but I'm also a fan of the visual effect 
that it brings. 

    [SIZE=1]
[COLOR=#696969]~Thanks in advance.
Vex\Grey[/COLOR][/SIZE]

---

### Post by tgalati4 on 2013-03-08
*Mail* is a terminal application.  For a mail server, you can install *sendmail*.  There are lots of tutorials on how to set it up.

---

### Post by SeijiSensei on 2013-03-08
My preferred text-mode email client is **alpine**. 

On the server side, you actually need two separate pieces of server software to make things work properly.  First would be an SMTP server program like **Postfix** or **sendmail** that handles the process of exchanging mail with other servers.  After the mail is delivered, typically to a file called /var/mail/username, another program is used to handle mail retrieval by a client like alpine or Thunderbird.  Ubuntu uses a program called **dovecot** for this task.

---

### Post by VexingGrey on 2013-04-12
Thanks for the recommendations. I'll set up a real server at some point and run it on an im/nom domain or externally. This is great!.

---

