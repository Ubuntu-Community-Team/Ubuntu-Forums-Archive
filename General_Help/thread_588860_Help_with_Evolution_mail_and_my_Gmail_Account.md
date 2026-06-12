---
title: "Help with Evolution mail and my Gmail Account"
date: 2007-10-23
forum: General Help
---

### Post by AndyCat on 2007-10-23
hello there all. I was wondering how to set up my gmail account so i can use it with evolution but i havent been able to get it to work. Can anyone explain me how to do this?? I know i have to setup some ports for both out and incoming server but I cant find where to change them on evolution.
Any help  will be appreciate it.

Id like to use evolution coz all the features it has.. Currently runnin thunderbird which is great but it lacks things like contacts, to do list and that stuff.


Thanks in advance:confused:

---

### Post by stixguy on 2007-10-23
> **AndyCat said:**
> hello there all. I was wondering how to set up my gmail account so i can use it with evolution but i havent been able to get it to work. Can anyone explain me how to do this?? I know i have to setup some ports for both out and incoming server but I cant find where to change them on evolution.
Any help  will be appreciate it.

Id like to use evolution coz all the features it has.. Currently runnin thunderbird which is great but it lacks things like contacts, to do list and that stuff.


Thanks in advance:confused:

First step, you have to let Gmail know you're going to access it via POP. 

See this FAQ from Gmail: [URL="http://mail.google.com/support/bin/answer.py?hl=en&answer=13273"]

Once you've enabled POP access in Gmail, you can set up an account by selecting "Edit", then "Preferences", Under mail accounts, click add.

This will run you through the account set-up wizard. Click Forward to begin.

The Identity page is where you enter your name and e-mail address.

On the receiving email page, select "POP" for server type. 

Under Server, enter:

```
pop.gmail.com:995
```

In the Security drop down, select SSL.

Click Forward to continue to Receiving Options, The defaults here work for most folks.

Click Forward to go to Sending Mail. For server type, select "SMTP". For server, enter:

```
smtp.gmail.com:465
```

Make sure the server requires authentication checkbox is checked.

Under Use Secure Connection, select SSL Encryption.

Hit Forward until you're done!

HTH

---

### Post by jugs on 2007-10-23
Or you can use IMAP instead.

:popcorn:

[http://www.downloadsquad.com/2007/10/23/gmail-gets-imap/](http://www.downloadsquad.com/2007/10/23/gmail-gets-imap/)

:)

---

### Post by chronusdark on 2007-10-25
has anyone managed to get gmail IMAP to work correctly in evolution i keep getting various errors

---

### Post by jayson.rowe on 2007-10-25
Using IMAP and Evolution - worked first try - no errors/problems at all...best thing since sliced bread :)

---

### Post by chronusdark on 2007-10-25
hmmm i wonder what i am doing to make it buggy

---

### Post by C00P88 on 2007-10-27
> hmmm i wonder what i am doing to make it buggy

I am unable to use IMAP with Evolution as well. Looks like it's POP only for me.

---

### Post by AndyCat on 2007-10-28
same thing happens to me. I Havent been able to use Imap and Evolution... so in the meantime im using pop... anyone has any idea o way to make it work?

---

### Post by dewey on 2007-10-28
I have not tried using evolution with gmail, however, I can report that thunderbird handles gmail very well through the new addition of IMAP.

I know it's not the answer you were looking for, as you wanted to use evolution, but it's an alternative if you can't get evolution to work.

Edit:  I somehow missed where the OP said he tried thunderbird, but it didn't suit his needs.  Disregard this post, sorry.

Editx2:
I just got evolution to log in to my gmail account, I haven't explored much, but I am able to use evolution at the very least.  I followed the steps here:
[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)
and just tried to apply them as best I could to evolution.  (The instructions are for thunderbird, but worked well enough for me.)

---

### Post by seditiousmonkey on 2007-10-29
This [blog post]("http://wazem.blogspot.com/2007/10/hot-to-configure-imap-on-evolution-and.html") helped me configure imap with gmail in evolution


where i was going wrong was specifying which ports i wanted evolution to access.  and apparently you need to restart evolution to get it working.

---

### Post by AverySimonsen on 2007-10-31
Thanks for the link. It works beautifully! The only problem was it took me a few minutes to spot the new folder hierarchy in evolution. :) Imap rocks!

---

### Post by uglowp on 2007-11-03
Thanks!

That blog got me set up ok with IMAP.

I found two mistakes in my previous setup.

1./  I forgot to add "@gmail.com" in one of the email address fields and

2./  I used "Plain" instead of "Login" in the "Authentication Type" field.

Thanks again.

---

### Post by anliveyak on 2007-11-03
theese instructions are for pop gmail accounts

in the reciving options
server type : pop
server : pop.gmail.com
username : [email]name@gmail.com[/email]
secure connection: ssl
authentication: password

in the sending potions
server type: SMTP
server:smtp.gmail.com
username : [email]name@gmail.com[/email]
secure connection: ssl
authentication: password

---

### Post by Denny Johnson on 2007-11-18
Thanks seditiousmonkey............great link for a newbie.

---

