---
title: "Browsers cannot submit forms?"
date: 2008-07-01
forum: General Help
---

### Post by eHobayyeb on 2008-07-01
I have Ubuntu 8.04 installed with Fx 3.

And when I tried to submit threads the browser asks me to download the file 'newthread.php' I tride it 1000000 times but nothing happed just download 'newthread.php'.

This problem happend with Opera, Epiphany and Firefox through WINE.

Any help needed

Thanks

---

### Post by y-lee on 2008-07-01
This could be many things, but I would suspect a error on the part of Ubuntu forums. Does this happen to any other sites or is it still happening?

From [Firefox Support Forum]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=fr&forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=0&comments_per_page=20&thread_style=commentStyle_plain")


> The web server tells the web browser what kind of file it is asking for (ContentType). Typically, the server says that an image file is, e.g., "image/jpeg" and an html file is "text/html". If the server instead says that the html file (or for that matter the php file) is an "application/x-unknown" or similar, Firefox will prompt you to download it. This would probably be due to a temporary failure on the server to properly serve the file. Firefox itself does not assume what kind of file is served but trusts that the server is correct.

Occasionally but rarely this happens to me not just with this site but others. In those case sometimes merely restarting firefox fixes the issue. Sometimes clearing cache and cookies and restarting fixes the issue. It also would not hurt to try rebooting Ubuntu.

See the last comment on the [thread mentioned above]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=fr&forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=40&comments_per_page=20&thread_style=commentStyle_plain") for more options on what to do for firefox. Note the advice given is for a windows machine.

If the problem persist and is still happening it might have something to do with your firewall (iptables) or proxie settings. :confused:

---

### Post by eHobayyeb on 2008-07-01
I have the problem in every sites with more than one field in the form.

I clean the cach and every thing.

I Reinstalled Ubuntu it self but nothing happend I only submit to Launchpad Answers!!

I have Wireless LAN works fine with Windows and submit everything but I do not know why Ubuntu cannot??

It is not Only Firefox I tried Opera, Epiphany and Firefox through WINE.

---

### Post by y-lee on 2008-07-01
I honestly don't know then. :confused: So this response serves as a bump. Hopefully somebody can help you.

---

### Post by eHobayyeb on 2008-07-01
I am waiting...

---

### Post by konungursvia on 2008-07-01
I suspect you are running with scripts disabled. Go into your browsers' options, and select "allow scripts" or "allow java". Similarly, you could try and whitelist the sites you want to use forms with, as I do in Noscript for FF, by right-clicking and selecting "Allow whatever.com" and so on. Another thought: Is Java even installed on your linux box? Do a google search on "ubuntu java install" and see what pops up. Also enable or install Adobe flash or a similar product.

---

### Post by y-lee on 2008-07-01
> **konungursvia said:**
> I suspect you are running with scripts disabled. Go into your browsers' options, and select "allow scripts" or "allow java". Similarly, you could try and whitelist the sites you want to use forms with, as I do in Noscript for FF, by right-clicking and selecting "Allow whatever.com" and so on. Another thought: Is Java even installed on your linux box? Do a google search on "ubuntu java install" and see what pops up. Also enable or install Adobe flash or a similar product.

It could very well be scripts disabled but it seems to effect all browsers so that throws me. In Firefox it could have something add ons such as no script. Try a new firefox profile.

---

### Post by eHobayyeb on 2008-07-01
Nothing disabled.
Adobe Flash Player Installed.
Java 6 Installed.

How can I create a new Fx 3 profile.

---

### Post by y-lee on 2008-07-01
> **eHobayyeb said:**
> Nothing disabled.
Adobe Flash Player Installed.
Java 6 Installed.

How can I create a new Fx 3 profile.

In a terminal type
```

firefox -P
```

---

### Post by eHobayyeb on 2008-07-02
I tried it but nothing happend.

You mention somehing about firewall and proxies above.
I do not use any proxy but about firewall how can I check and change?

Please help me I don't wanna go back to the pri$on!!


Strange!!
I can submit through the Quick Reply and in the Launchpad Answers.
But I cannot submit a new thread in UbuntuForums.org or any other site?!

Thanks

---

### Post by eHobayyeb on 2008-07-02
Yes it is strange!!

I went to another WLAN and everything submit successfully!!

Does the problem with my Router??

---

