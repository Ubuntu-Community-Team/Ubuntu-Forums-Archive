---
title: "Send email with a forwarding address (Evolution) ?"
date: 2014-04-09
forum: General Help
---

### Post by obake2 on 2014-04-09
Hi there Ubunteros and Linux users. I have a forwarding email [email]xyz@linux.com[/email] ([See this]("http://www.linuxfoundation.org/about/join") ) and was wondering if there is a way to make it appear as if my messages are coming from [email]xyx@linux.com[/email] when I **send** a message instead of my real email. I know I can do this in web interface of gmail by using email alias, but I wish I could use a email client to do it.

Any guess?


THank you.

---

### Post by SeijiSensei on 2014-04-09
Don't know about Evolution as I don't use it, but you can do this in Thunderbird.  Edit > Account Settings, then click the Manage Identities button.  You can specify various sender addresses and select among them from a drop-down box when composing a message.  The SMTP server to which the messages are sent must be configured to accept mail with that From address.  I control my own servers, so it's not an issue for me, but it might be an issue if your provider's SMTP server only accepts mail from [email]you@yourisp.com[/email] but not from [email]you@example.com[/email].

The other common method to force replies to go to a specific address is to add a "Reply-To" header to the message.  Most email clients can do that.  Thunderbird offers "Reply-To" along with To and CC in the composer.

---

### Post by HermanAB on 2014-04-10
I think it is the 'Reply To' address that you need to set.

---

### Post by SeijiSensei on 2014-04-10
Depends on whether he wants the From address to differ from his default.  For instance, I'm subscribed to a listserver under an account that is different from my usual one.  Unless I select the subscribed sender address, mail to the listserver will be ignored.  So I added that address to my Identities in Thunderbird and select it when I send mail to that list.

---

