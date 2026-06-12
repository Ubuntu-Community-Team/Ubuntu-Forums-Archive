---
title: "strip out tags from emails (HTML to plain text)"
date: 2013-02-25
forum: General Help
---

### Post by Bagboy23 on 2013-02-25
Hi Guys,
This is my problem; I'm trying to help out at a local charity nursing home. They have emails that come in that they then log or push to the patients account. They have to do this by. These can be medical history etc. The problem is the emails they get are always encased in a tag: **<p> </p>**. So a typical message looks like exactly like this:

**<p>Hi please tell the patient that their son will visit them next week for mother’s day</p>**

The medical system they use is old but it's what they're stuck with, but they have asked me to come up with a method that removes the <p></p> tags from every email, so that it is cleaner. At the moment I'm stuck on how I would go about doing this.

Essentially I have to remove the tags from every email. I’m thinking that I should have a first email account setup, and then somehow parse the message, strip out the tags, and then forward it to the real email, but without the tags.

Any help would be appreciate as I’m doing this just to help being the local computer guy.
Thanks for any help.

---

### Post by SeijiSensei on 2013-02-25
What systems do you have control over in the process?  Is the mail reformatted with the <p> tags and then forwarded to a delivery server that you administer?  If so, **procmail** is your friend.  You can write a "[recipe]("http://linux.die.net/man/5/procmailex")" in /etc/procmailrc that will strip the tags from every message.  You can even limit it to messages coming from the upstream server that adds the tags.  Here's a simple example

```

:0
| sed '/\<p.\>//g'

```

(I'm not certain you need to "escape" the "<>" characters with "\".  You'd have to experiment.)  

/etc/procmailrc is applied to every message, and this recipe would affect every inbound message.  If you only wanted to apply it to messages from the tagging server, let's call it upstream.example.com, you could use:

```

:0
* Received:.*upstream\.example\.com
| sed '/\<p.\>//g'

```

---

### Post by Bagboy23 on 2013-02-25
Thanks for your reply. 

Essentially all messages sent from other people come into this medical system using the [email]case@medical.co.uk[/email] email address. They come in with the tags described. They automatically get inserted to the patients file. So all emails in the patients file have those tags, they essentially mess-up the medical system when they come in like that.

My idea is to have a "catch email" (catch@medical.co.uk)email, that strips out the tags then forwards the resulting mail to [email]case@medial.co.uk[/email]. This way when the mail gets inserted to [email]case@medical.co.uk[/email], the email is in plain text.

I'm not sure how I would go about implementing the procmail. Any help on this would be great.

---

### Post by SeijiSensei on 2013-02-25
> **Bagboy23 said:**
> Essentially all messages sent from other people come into this medical system using the [email]case@medical.co.uk[/email] email address.

Is that the actual destination address, or is "case" a placeholder for something like the patient's ID number or some other identifier?  If that's true, then you would need to preserve the To address to grab the case number.

Does any other mail come to "case@medical.co.uk" or just this stuff?  What about mail for [noparse]someone@medical.co.uk[/noparse]?  If all the messages are addressed to "case", how do you know which patient they should be routed to?

---

### Post by Vaphell on 2013-02-25
not that i have much to say about how to set this thing up, but imo instead of removing tags manually it's better to use some dedicated html-to-text converter like html2text, just in case there is something other than <p>

```
$ echo '<html><p>this is <b>an example</b></html>' | html2text
this is an example
```
if you can plug it in, you are golden

---

### Post by Bagboy23 on 2013-02-25
The email address is just that, the one email address "case@medical.co.uk". No other outside email comes to this email account. The email subject contains the patients ID, the internal medical system uses the subject to identify patients. So for instance this might be an example email:

----
To: [email]case@medical.co.uk[/email]

Subject: PNT:000768/Sam/RHUS

Message:

<p>Please notify the patient that her son will visit her on mothers day</p>
----

The problem I have found is that whatever system is sending the messages, it usually adds the tags which is supposedly formatting the text to HTML. All the existing methods I have tried, actually just end up forwarding a HTML copy anyway. I need a method to read the email from one email address [email]catch@medical.co.uk[/email], re-format, then send to [email]case@medical.co.uk[/email].

I've looked at tools like html2text, but I'm not sure how I would go about implementing that with an email or the approach above.

---

### Post by Vaphell on 2013-02-25
```
:0
| sed '/\<p.\>//g'
```
assuming it means 'pass msg through sed' i'd expect something like *| html2text* to work

---

### Post by SeijiSensei on 2013-02-27
You still haven't told us how the overall system is configured.  Where are you trying these "existing methods?"  What kind of system accepts mail for [email]case@medical.co.uk[/email]?  Is it running Linux?  Is it something you can modify?  Or are you looking to insert another machine between the source of the messages and the server accepting mail for case@medical?  I'm having a hard time seeing what needs to be modified to get this to work for you.

---

