---
title: "How do you reply in claws mail without the greater than sign?"
date: 2008-06-24
forum: General Help
---

### Post by Hooya on 2008-06-24
I like Claws mail (claws-mail) because it's really lightweight and the interface is clean even if it does look a little dated.  It works great in conjunction with my xubuntu install running fluxbox.  Anyway, the only thing about it is that I can't figure out how to reply and forward messages without them getting cluttered with the > greater than symbol.  I hate getting messages replied to with that clutter and I hate sending with that clutter.  How do I make them go away?

---

### Post by x1a4 on 2008-06-24
Hi,

Configuration > Properties > Compose > Writing
At the bottom, where it says: "Treat these characters as quotation marks" remove the chevron.

---

### Post by Hooya on 2008-06-25
That was one of the first things that I tried, but it still leaves them in when I reply.  I also tried removing the > from the "Quotation Marks" field in Compose > Templates > Reply (tab) but that also doesn't seem to change anything.

Is there a setting not sticking somewhere?  Any other ideas?

---

### Post by x1a4 on 2008-06-25
Set the quotation mark to *<space>* in Compose > Writing and Templates.

---

### Post by Hooya on 2008-06-27
Reply still adds chevrons, even with a space for the quote character in that field.  In fact, it adds them in an even more annoying way, with two on a line, then the next line with none, so it looks like this:
> >text
text
> > text

Only on some messages though, others it adds the chevron the usual way.

And sometimes with random extra >>>>> at the end of a message.  So weird.

---

### Post by x1a4 on 2008-06-27
Curious.  I added a space in the quotation mark field in Templates and Writing and I get a space when replying.  Do you have templates enabled for the account you're using? Is the quotation mark set for that account?  

I attached a screenshot of a reply message on my system with space as the quotation mark.

EDIT: when you make the configuration changes, be sure to click the Apply button before you close the dialog.

---

### Post by Hooya on 2008-06-30
I hate to leave this unsolved, but I've just decided that claws-mail isn't the right mail app for me anyway.  It freezes quite a bit on my system, usually if it has any issue at all connecting with my IMAP server.  Add to the fact the formatting issues that I didn't get resolved (I tried what you suggested, same result...).

It'll be more consistent anyway for me to have Evolution as my mail client on my desktop as well on my laptop instead of Evolution on my desktop and claws on the laptop.

I appreciate your help though.

---

### Post by x1a4 on 2008-06-30
> **Hooya said:**
> It freezes quite a bit on my system, usually if it has any issue at all connecting with my IMAP server.  

I've had Claws Mail crash when performing IMAP operations and it turned out that it's the NewMail plugin.  Unload it and it should stop--the crashing I mean. 

> Add to the fact the formatting issues that I didn't get resolved (I tried what you suggested, same result...).

Go over your configuration.  You probably have some setting somewhere adding the chevron to replies. 

> I appreciate your help though.
Not a problem, especially since I haven't helped you solve anything. 

You might want to try Claws Mail in a year or two.  I didn't like it on Edgy and continued using Thunderbird until I discovered Balsa, then a while back I gave Claws a try and made it my default email client.  I don't think I ever used a more powerful email client.

---

### Post by pirateofms on 2010-06-27
I'm just putting this here as a solution in case anyone finds this thread (I know it's 2 years old.)

My claw-mail ignores the settings under Configuration->Templates as it seems was the case with Hooya.  Going to Configuration->Preferences for Current Account->Templates and setting things there worked fine, however.

---

### Post by southpacific on 2011-06-30
I too realise this thread is old but for anyone who has the same problem in the future:

Claws Mail -> Configuration -> Compose -> Templates -> Reply

I changed the %Q to %M which uses the message body (unquoted) in the reply

---

