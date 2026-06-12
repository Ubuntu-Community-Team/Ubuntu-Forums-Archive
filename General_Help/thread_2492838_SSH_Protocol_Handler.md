---
title: "SSH Protocol Handler"
date: 2023-11-24
forum: General Help
---

### Post by mbd777 on 2023-11-24
I can't seem to find anything within the last decade that enables the protocol handler for SSH. Is there a way to open SSH links directly from the browser? e.g. a link to-> ssh://localuser@hostname.domain.internal/

---

### Post by MAFoElffen on 2023-11-25
Not sure what you are referring to.

Web Browsers work through ports 80, 8080, 443, & 8443... ssh is usually port 22, unless you change it. You are not going to browse an ssh connection through a web browser.

You do an ssh session trough a terminal, or connection manager, which then presents it through a terminal session.

Not if you wanted to save connection details, you could either create a desktop shortcut, or save it in a connection manager such as Remmina.

---

### Post by mbd777 on 2023-11-25
I'm aware how browsers work. A protocol handler is what launches whichever program is associated with the protocol. So when you embed SSH links into a page, and you click on the link, it opens the terminal and launches the SSH connection.

---

### Post by MAFoElffen on 2023-11-25
What you are talking about is trying to get something like this to work from a webpage:
[code=html]
<a href='ssh://user@1.2.3.4'>SSH</a>
[/code]
Which used to work when Browsers used "less locked-down" versions of HTML, which later versions of try to prevent malicious things from happening on users computers from a webpage. This makes a challenge for Businesses, that created web page forms for their employees to use to do their jobs <-- Guilty. As a Contractor, I saw that as a great way to help people do things. 

That used to be covered by this:
[https://github.com/VIRL-Open/](https://github.com/VIRL-Open/)

But that hasn't been maintained in over 6 years, It started to loose momentum circa 2015 to 2016.

I never saw that as truely being a security risk, as it required that you setup your local terminal and other things for that to be able to handle the call. So for a normal user, that was not setup for that, it never did anything.

For "now", "currently"... IDK. I haven't played with that in many years. I could play with it after I finish a few projects, and see if it is still possible, but I have other things more pressing at the moment.

I found an old article at Cisco Academy that said it still works as of 2020, with the old code:
[https://learningnetwork.cisco.com/s/article/how-to-set-up-ssh-handler-on-linux](https://learningnetwork.cisco.com/s/article/how-to-set-up-ssh-handler-on-linux)

Use at your own risk, as I have not tested that.

---

