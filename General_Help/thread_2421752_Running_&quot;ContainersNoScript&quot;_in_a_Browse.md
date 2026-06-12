---
title: "Running &quot;Containers/NoScript&quot; in a Browser"
date: 2019-06-26
forum: General Help
---

### Post by cruzer001 on 2019-06-26
I started running containers, FireFox "Temporary Containers" plugin a couple of weeks ago.  Seems to be a good choice when just surfing the internet and wanting to keep the junk (cookies/trackers) out of my browser.

I also run "NoScript", but when running containers, NoScript seems to be unnecessary.  I know it will remove additional crud, but when just surfing the internet, noscript will get in the way a lot.

So the question.  Is there good reason to run NoScript when running inside containers?  From what I see, NoScript is not necessary.

---

### Post by TheFu on 2019-06-26
Not sure I'd trust any internal-to-browser addon for providing a container.  Call it a bias against trust.

```
$ firejail --private firefox

```
this will not allow firefox to write anything to the disk and it will limit access to read based on the profile while allowing sufficient access to run.  There are 9 different profiles shipped with firejail for firefox.

firejail has other options and can be setup as a wrapper around many other tools on the system, like email programs, or other high-risk tools.

It is a general solution, not specific to browsers. There are a few other tools with similar capabilities. I like the idea that this addon provides. However, the implementation as a node.js tool concerns me. I have a bias against trusting javascript.

I use NoScript by default and only allow javascript for very specific websites.

---

### Post by cruzer001 on 2019-06-27
Hi TheFu

Normally I do not give security a lot of thought, but a couple of weeks ago I was surfing the net and got hit with a piece of nicely built malware.  It took over my computer on the spot, didn't matter I was running linux.
The fix wasn't hard, but I then decided it was time to add additional security/containers.

I do block JS and am surprised at how many sites use it.  Now that you pointed out this node.js, my JS bias is coming out.

I totally forgot about firejail #-o Thank you for bringing that up.

---

### Post by TheFu on 2019-06-27
I  appreciate the way that this plug-in tries to segment each window into a separate container, but without having different processes, I just don't believe it.  Plus, browser addons/plugins AND the browsers themselves don't have the best reputation for actually doing what they claim.  
How long were people trusting that "private mode" didn't share data only to find that it did?

With exceptional claims, exceptional proof is required. 

With firejail, I see the impacts of the constraint system almost daily.  It is usually a hassle, because something doesn't work.  Little things like clicking on a URL inside a trusted email opens a new browser instance, not reusing the one running inside a firejail sandbox, is one example.  There are others like trying to read an input file from /tmp/ only to be denied the file exists at all.  Inside firejail, the /tmp/ directory only sees files that program created, nothing created outside.  In short, I **Know** firejail does what it claims. See it daily.

---

### Post by walts48 on 2019-06-27
> **cruzer001 said:**
> I started running containers, FireFox "Temporary Containers" plugin a couple of weeks ago.  Seems to be a good choice when just surfing the internet and wanting to keep the junk (cookies/trackers) out of my browser.

I also run "NoScript", but when running containers, NoScript seems to be unnecessary.  I know it will remove additional crud, but when just surfing the internet, noscript will get in the way a lot.

So the question.  Is there good reason to run NoScript when running inside containers?  From what I see, NoScript is not necessary.

I use [URL="https://support.mozilla.org/en-US/kb/containers"]https://support.mozilla.org/en-US/kb/containers
[/URL]
Just curious here. What version of Firefox are you running and what are your Privacy & Security Content Blocking and Security settings in References?

[URL="https://support.mozilla.org/en-US/products/firefox/privacy-and-security"]https://support.mozilla.org/en-US/products/firefox/privacy-and-security



[/URL]

---

### Post by &amp;KyT$0P# on 2019-06-27
> **cruzer001 said:**
> I also run "NoScript", but when running containers, NoScript seems to be unnecessary.

Unnecessary for what?

> Is there good reason to run NoScript when running inside containers? 

NoScript and containers are completely different.  If you're after security, the good reason is because NoScript is a security tool and containers are more of a privacy tool.

If all you want is "*to keep the junk (cookies/trackers) out of my browser*", NoScript is not designed for keeping out that type of junk.  You might rather use [uBlock Origin]("https://addons.mozilla.org/firefox/addon/ublock-origin/").  And as walts48 pointed out, Firefox has some built-in settings that would also help here.

By the way, I also use firejail and separate browser instances instead of containers (not quite the same way TheFu does, but similar idea).

---

### Post by cruzer001 on 2019-06-27
I have the plan :)

To more fully explain, this malware happen on the Host OS (Gnome Desktop).  That desktop install has been replaced with a minimal install that is now just a virtual server.  My daily driver (Gnome Desktop) is now a virtual machine.  This by its self is a good security measure, but I will take a step further and create a VM just for firefox browsing and not concern myself with added security.  I can just reset it to its vanilla state when necessary.


@TheFu
Going to switch over to firejail on my desktop install with NS and adblock.  VM or not, I still think this is a good move.

This thread is solved

Thanks people :)

---

### Post by TheFu on 2019-07-19
"Incognito mode"  issues: [https://arstechnica.com/tech-policy/2019/07/researchers-investigate-whether-major-advertisers-track-porn-habits-seems-likely/](https://arstechnica.com/tech-policy/2019/07/researchers-investigate-whether-major-advertisers-track-porn-habits-seems-likely/)

---

