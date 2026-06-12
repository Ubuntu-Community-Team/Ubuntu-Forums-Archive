---
title: "Apturl working in other browsers besides the default Firefox installation."
date: 2007-10-24
forum: General Help
---

### Post by n0yd on 2007-10-24
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/apturl/+question/16074](https://answers.launchpad.net/ubuntu/+source/apturl/+question/16074) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Can someone explain how I can get Apturl to work in other browsers (Gecko based, as it only supports gecko based browsers at this point in time), I use Swiftweasel which is basically the Swiftfox version of Iceweasel, and I've spent all day fiddling with trying to get Apturl going in Swiftweasel to no avail.  It works fine in the default Firefox installation, and some people have said it also works out of the box using Epiphany also.  So anyone know the trick?  I sure hope so. :)

---

### Post by n0yd on 2007-10-25
I found a solution to my problem.:guitar:


All you have to do is open about:config in your browser, right click in the window and choose add new string.

Then for the name make it:
network.protocol-handler.app.apt 
Then make the strings value "/usr/bin/apturl" without the quotes.

And to make it work for http hosts make another string:

Name = network.protocol-handler.app.apt+http
And for the strings value make it the same as above. :biggrin:

---

