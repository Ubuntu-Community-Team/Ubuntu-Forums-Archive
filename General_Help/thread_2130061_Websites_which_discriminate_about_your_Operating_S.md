---
title: "Websites which discriminate about your Operating System"
date: 2013-03-28
forum: General Help
---

### Post by BFG on 2013-03-28
I'm looking for a way to get control over my browsing.  

Prompted by the need to download the windows install of Picasa, using my Ubuntu machine  (actually getting the file was easy, this is just an example).  

Generally I like the principle of using user-agent etc to know about users' browsers to help **enhance** the browsing experience, but using such to discriminate and close doors on sections of the IT community is an unpleasant thing.  

The Picasa website announces "Picasa is not currently available for your operating system".  No other links or help. 
Shame on google for doing this.  But they're not alone.

Is there any way to make my browsing OS agnostic?

---

### Post by coldcritter64 on 2013-03-28
If using firefox you can use the add-on "User Agent Switcher" and have your browser/system appear as another browser/system etc. IIRC a link to the mozilla add-ons page is available in the "Tools" menu of firefox. Cheers

Edit: this may work for simple situations, if picasa requires installation of Windows software, User agent switching likely won't work at all.

---

### Post by BFG on 2013-03-28
Can these be used to completely hide the OS, rather than spoofing to be a different one?  I guess there's a risk the site will think I'm a bot.

---

### Post by hectorgrebbell on 2013-03-28
When your browser sends a request it sends a set of headers followed by the "operation".
So by changing those headers you tell the machine at the other end whatever you like.

The only way it could ever know your lying is if it launches something (say some javascript) that then sent back a confirmation, but I doubt anyone bothers with this.

[User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") simply changes the headers to match a different client.

It allows custom strings, so setting it to blank would completely hide it, but I expect the servers will check for certain strings and give unsupported on everything else. Hence Your better off to spoof.

Hope that helps

---

### Post by coldcritter64 on 2013-03-28
> **BFG said:**
> Can these be used to completely hide the OS, rather than spoofing to be a different one?
As far as I know a site can only tell what your system is from the user-agent; not sure what you mean by "completely hide the OS". I am assuming you are secured, firewalled (if necessary) and are using script blocking etc by the previous line.  

User Agent Switcher can tell a website your browser and system, ie it can say you are on a Windows system and using IE when you are on firefox on Ubuntu, it spoofs system details and browser to the site. This works well when site admins try to "lock" the use of a site to a particular browser when other browsers will still work fine. The problem arises if software is installed by the site, it will be for Windows only usually, Linux fails to work at this point unfortunately.

You can actually imitate a bot, if you want (Google and Yahoo :))

---

### Post by BFG on 2013-03-28
I just tried user agent switcher on Firefox and that does what it says.  A nice workaround, thanks.


Re "completely hide".  Hide is probably the wrong word.  I'm an "opt-in" kind of person in all aspects of life.  

If there were an option to set my browser to "agnostic", i.e. not share anything about what I'm using unless I choose to share (whitelist), I would probably use it. :)

---

### Post by hectorgrebbell on 2013-03-28
As far as I know there is no requirement in HTTP standards to send a user-agent.
But servers that do check it will almost certainly have a list of "approved" clients and just give a standard unsupported error to everything else.

So you'd end up worse off.
Also, be warned, some sites put in their terms of use about only providing correct information. Technically spoofing a user-agent could be considered fraud. Chances of anyone caring is next to 0, but I wouldn't be using a fake string when its not necessary.

---

### Post by BFG on 2013-03-28
True.  I just tried creating a blank user agent and I get the same "Picasa is not currently available for your operating system" message.

---

### Post by BFG on 2013-03-28
I'm new to this, and so I examined the fields given in User Agent Switcher to understand how it's working.

There is a Platform field, which when set to "Win32" doesn't make any difference. So I assume web sites aren't using an explicit field, but just using the user-agent string.
The user-agent string seems, well not unstructured, but certainly not definitive.  Are web designers using pattern matching inside the string?  Seems crude if so.


EDIT. Yep. Seems so.   Idea: To get an agnostic user agent, what if I create a header which has the string for every operating system?
EDIT2:  Well that seemed to work.....

Mozilla/4.0 (X11; Ubuntu; Linux x86_64; compatible; MSIE 8.0; Windows NT 6.1)

I added the string above to a new user agent I called "Agnostic".  It got me to the download page on Picasa.  I just need to try it on other sites.  Any thoughts?

---

### Post by hectorgrebbell on 2013-03-28
See format in [http://en.wikipedia.org/wiki/User_agent](http://en.wikipedia.org/wiki/User_agent)

The site will either be written from scratch, in which case implementation details will depend on who built it.
Or using a framework (for example Django).

This appears to be a fairly reasonable basic tutorial if you are interested
[http://www.garshol.priv.no/download/text/http-tut.html](http://www.garshol.priv.no/download/text/http-tut.html)

---

