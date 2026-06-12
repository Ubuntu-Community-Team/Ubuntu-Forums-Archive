---
title: "Single word entries in Address Bar leads to odd redirection"
date: 2007-03-05
forum: General Help
---

### Post by se2131 on 2007-03-05
So I'm not sure if this forum is the right place to ask this question, but I can't figure out where else to put it to.

Recently, I had to do a hard shutdown on my computer (my laptop has been locking up randomly, but that's not the problem I want to tackle right now).  When I rebooted, I tried surfing the internet.  Usually when I enter in a single-word into the address bar and hit enter, it adds the www and .com to it (e.g. google becomes [www.google.com)](www.google.com)).

However, when I do this in Opera, it redirects me to Charter's web search for the term google (which I have never seen before).  Note: Charter is my ISP.  In the options, I still have the "Add www and com" option ticked.

So I tried it in Firefox, and it does the same thing there too.

And then I tried it in Konqueror, and it acted a bit differently.  Now when I enter in a single word, it adds google.xxxxx.edu (where xxxxx is my school's address, like umd,yale,duke, whatever, not putting it here for privacy), and THEN it also goes on to do a Charter search on the google.xxxxx.edu term.

Needless to say, I'd like to figure out if there's something fishy going on here that I do not know about.  First, I'm not connected to my school's network, but I have done so in the past (wirelessly), so why is it trying to put this xxxxx.edu in?  I think this may be an older problem, because when I typed in a term that was unrelated to the school, I got redirected there.  I would like to make sure that I am not somehow connected to the school in any way.  I don't have any proxy servers btw.

And second, charter's thing shouldn't be coming up either, right?  Why am I being directed to their search page.

Any help in removing these problems is greatly appreciated, thanks in advance.

---

### Post by se2131 on 2007-03-06
Also, this isn't happening with either of my roommates (we share a router), so I don't think that it's something that Charter has implemented.

---

### Post by zanglang on 2007-03-06
Just my guesses from what that behaviour looks like, but I think (I probably read it from developer comments somewhere, but I can't remember :p) when you enter an incomplete domain in Firefox it actually uses Google to locate it. Try typing random sentences like 'this is a test' and it actually sends you to a Google search results page.

When you use Opera it might have queried your ISP's DNS servers directly, which redirects it to their search page.

When you use Konquerer it probably interprets it as a network 'URI' (not URL, note difference), and instead looks for the *host* called google on your *domain*. I noticed Ubuntu doesn't reset my domain even when I've left my uni wireless network, so that could explain why you still experience it when you're at home.

---

