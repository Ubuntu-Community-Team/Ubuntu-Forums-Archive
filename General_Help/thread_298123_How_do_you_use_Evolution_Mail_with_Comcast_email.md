---
title: "How do you use Evolution Mail with Comcast email?"
date: 2006-11-12
forum: General Help
---

### Post by Heyholetsgogrant on 2006-11-12
Does anyone know how to use evolution with with comcast email? or mozilla mail?  My email address is [email]ghardester@comcast.net[/email], I was using outlook express before...

Thanks,

Grant

---

### Post by catlett on 2006-11-12
Just open evolution and go to 'edit' then 'preferences'. Then select 'add' on the right.
When it asks which type of server, select 'pop'.  Next screen enter your real name (or whatever name you want on tyhe account) and your email address, in your case [email]ghardester@comcast.net[/email].
The next screen will ask for a server address. It will have a line under 'configuration' put in>  mail.comcast.net
It will auto fill in your usernam buty make sure it is the correct one. Leave the other things at the default (meaning keep 'password' and 'no encryption'
Next screen will ask about your preferences. You can put what you want. i.e. how many minutes to check,leave messages on server, etc)
The next screen is another server configuration. It is about sending mail through comcast. In the blank line under 'server configuration' enter > smtp.comcast.net 
Next screen is the name you want for the account in evolution. Meaning whatever you want so you can recognize it if you have more than one. I just keep my email address.
Next screen double checks the name. Then hit apply at the next screen. The setup is done.

Now at the regular evolution window, hit 'send/receive'. That brings up a prompt asking for your password. Put in your comcast password. The one you use to login at comcast.net. ( I check off 'remeber password' so it is automatically entered after the first time.)
That is it. Evolution is setup. This site [http://www.comcast.net/help/faq/index.jsp?faq=Emailtop17742](http://www.comcast.net/help/faq/index.jsp?faq=Emailtop17742) isn't about evolution but it has the information you need i.e. the server names and the server type.

---

### Post by Heyholetsgogrant on 2006-11-12
It seems to be working, but whenever i Hit send recieve button at the top it says "Error while performing operation.

RCPT TO <ghadester@comcast.net> failed: User not local; please try <forward-path>"

what does that mean?

Thanks for the help!!!

-Grant

---

### Post by catlett on 2006-11-12
I must admit I never had an error like that. Are you getting emails from your account? Are you able to email out?

P.S. I found out is an smtp reply code. Which means the smtp server is replying about the user not being local.What that means I don't know.Go to 'edit' 'preferences' select the comcast entry and hit 'edit'. Then go to the 'sending mail' tab and make sure the info is correct, just as somewhere to start.


P.S.S Check your spelling of your comcast email. It is coming up with an error. Double check the entry in evolution.

---

### Post by Heyholetsgogrant on 2006-11-12
I think I figured it out!...If theirs no incoming mail then it makes that error prompt.  When I used another account to send mail to my evolution mail account and hit the send receive button, no error came up.  Yes I can send and receive mail, I guess thats all that matters!

Thanks Again!,

Grant

---

### Post by catlett on 2006-11-12
Just make sure you have the correct email address for the account. When I sent it to the name you posted [email]ghardester@comcast.net[/email], I got this error 
> This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    [email]ghadester@comcast.net[/email]

Technical details of permanent failure:
PERM_FAILURE: SMTP Error (state 9): 551 not our customer
Either the address posted in this thread is incorrect or comcast doesn't have it set up yet.
Not being able to connect to the server will cause an error from evolution.
Can you send yourself an email to the comcast account from another email provider?

---

### Post by Heyholetsgogrant on 2006-11-12
you forgot an "R" Its [email]ghardester@comcast.net[/email] not [email]ghadester@comcast.net[/email] :) 

Thanks,

Grant

---

### Post by catlett on 2006-11-12
> **Heyholetsgogrant said:**
> you forgot an "R" Its [email]ghardester@comcast.net[/email] not [email]ghadester@comcast.net[/email] :) 

Thanks,

Grant

I was hoping for something like that. :D  Take care.

---

### Post by Heyholetsgogrant on 2006-11-12
Thanks Again!

-Grant

---

### Post by fragos on 2006-11-12
Remember that Comcast SNMP requires a login as well as POP does.

---

### Post by dcstar on 2006-11-13
> **fragos said:**
> Remember that Comcast SNMP requires a login as well as POP does.

Or you install postfix and run your own SMTP server - little point using an external system when Linux provides one that works just as well.

---

