---
title: "How to configure web browser in thunderbird 78.7.1?"
date: 2021-04-12
forum: General Help
---

### Post by lalawawa on 2021-04-12
I have thunderbird 78.7.1 (64-bit) running on Ubuntu.  I would say which version of Ubuntu I'm on but I can't figure out how to find out.

I downloaded "seamonkey", a package derived from mozilla which has several things in it, including a web browser.  It was configured in Chinese and I couldn't figure out how to get it to change to English.  It was generally a disaster.  I didn't get seamonkey through the Ubuntu software system, I just downloaded it from a web page.

The next hyperlink in thunderbird I clicked on loaded the web page in seamonkey, which was not what I wanted.

I blew away the seamonkey directory and binary.  Now when I click on a hyperlink in thunderbird  nothing happens.

There was a thread in these forums about how to configure the web browser in thunderbird, but it was for an older version of thunderbird and you were supposed to go to Edit -> Preferences -> Advanced, and there's no such thing in thunderbird 78.7.1.

So how do I get thunderbird configured to use Firefox to open hyperlinks?

---

### Post by walts48 on 2021-04-13
[LIST=1]
[*] Make Firefox the default browser in Firefox settings.
[*] Make Thunderbird the default email application in Thunderbird. Preferences > General
[*] Make Firefox the default browser and Thunderbird the default email app in the OS Default Applications settings.
[/LIST]

---

### Post by lalawawa on 2021-04-13
Thanks, just step 1 did the trick.

There's a button in Firefox -> Edit -> Preferences -> Startup labelled "Make Firefox your default browser".  Ciicked on that, and right away, clicking on hyperlinks in thunderbird started working again.

---

