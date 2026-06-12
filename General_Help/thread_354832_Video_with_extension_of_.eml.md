---
title: "Video with extension of .eml"
date: 2007-02-06
forum: General Help
---

### Post by jimbob on 2007-02-06
I received an email with an attachment that has an extension of .eml 

Has anyone figured out a way to open this in Linux?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mbeierl on 2007-02-06
.eml is usually the extension of an attached, forwarded email, not video...

---

### Post by Jussi Kukkonen on 2007-02-06
I'd be quite surprised if eml was an extension for video... Are you 100% sure it's not some failed attachment attempt (eml is a weird Outlook export format).

---

### Post by jimbob on 2007-02-06
What it is is a regular text email with an attachment labeled thusly:

1 attachment ATT849.eml (4 KB) (details…)

When I click on this attachment, it opens as a text file with all the embedded html controls junk along with some more text.  If I dig through all the formatting junk I can find the real meat which is a flash video address:  [http://www.flashdemo.net/gallery/wake/index.htm](http://www.flashdemo.net/gallery/wake/index.htm)

Don't know why the attachment doesn't just come out without all the html crud along with it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mbeierl on 2007-02-06
Well, automatically opening unknown attachments and displaying them to you is what got outlook into the trouble it is in today.

Having to make the decision to view the contents of an unknown attachment is part of what makes other email clients so much safer.

Of course there's always a battle between ease of use and security.  Personally, I like having the choice.

---

### Post by jimbob on 2007-02-06
I agree with you but I still would like to have software that gives me the choice as to whether I want to view it or not.

In this case I'm not even given the chance to make a decision.

---

### Post by mbeierl on 2007-02-07
Well, you haven't told us yet what email client you are using :)

Perhaps there is one that would meet your needs better than the one you are currently using.

---

### Post by jimbob on 2007-02-07
gmail

---

### Post by jimbob on 2007-02-27
** bump? **

---

### Post by jimbob on 2007-03-02
Finally found a solution which allows me to read *.eml  files in Thunderbird if anyone is interested but it's not pretty.

Check out this link:  [http://www.broobles.com/eml2mbox/](http://www.broobles.com/eml2mbox/)

Once you have the mbox directory created in T-bird you can use ruby to directly append new .eml's without going through the intermediate steps.

Ruby is available directly on Ubuntu via apt-get.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

