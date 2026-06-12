---
title: "Thunderbird and RSS feeds"
date: 2007-05-05
forum: General Help
---

### Post by sam81 on 2007-05-05
I've been unable to use thunderbird to read rss feeds. I've set up a RSS account, but each time I try to add a feed I get a message telling me it's not a valid feed. For example:

# an ubuntu forums feed
[http://ubuntuforums.org/external.php?forumids=169](http://ubuntuforums.org/external.php?forumids=169) is not a valid RSS feed
#BBC front page feed
[http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/front_page/rss.xml](http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/front_page/rss.xml) is not a valid RSS feed

it strikes me that I can't find reports of similar problems on the forums, feel like I'm missing something very basic...

I'm on Feisty now, but had the same problem on Edgy and Fedora Zope.

Thank you in advance for any help!

---

### Post by diskotek on 2007-05-05
so strange, did you checked inputs for feeds, may be you are just typing in the wrong place?
or try a thunderbird tutorial on web for rss howto.

---

### Post by sam81 on 2007-05-07
Solved, apparently was a problem with the internet connection settings, I'm behind a proxy, and had not specified the proxy settings for thunderbird (though I have them as environment variables, and are specified in the GNOME proxy settings). E-mail downloaded fine, but RSS feeds would not download without specifying the proxy settings directly in thunderbird. I feel the error message I got was quite misleading though...

---

