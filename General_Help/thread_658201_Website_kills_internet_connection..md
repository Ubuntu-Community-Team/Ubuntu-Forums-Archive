---
title: "Website kills internet connection."
date: 2008-01-04
forum: General Help
---

### Post by keeler1 on 2008-01-04
Whenever I go to newegg.com with firefox (in Ubuntu Gutsy) any page I try to go to after that can not be found.  Firefox says it is looking up the page but can never find it.  Pages like google, yahoo, and everything else can not be found.

Network Manager still says I have a connection to the wireless router.  And other computers connected to the wireless router still have internet access.  If I boot into windows and use firefox the problem dissappears.

Is there anything with Ubuntu that could be causing this or is it a firefox issue (or a web site problem)?

---

### Post by EYEdROP on 2008-01-04
Try this: In Ubuntu, open the command line and type ping [www.newegg.com](www.newegg.com). Tell me what you get.

---

### Post by SyL on 2008-01-04
[http://linux.about.com/library/cmd/blcmdl8_traceroute.htm]("http://linux.about.com/library/cmd/blcmdl8_traceroute.htm")

try to use traceroute

---

### Post by lisati on 2008-01-04
[LIST=1]
[*]Cookies (or similar): if not the specific problem, they might prove to be a useful snack while pondering the problem
[*]Activex? The web page designer might be assuming Windows or IE instead of Firefox
[/LIST]

---

### Post by dannyboy79 on 2008-01-04
it's most likely that your DNS servers are messed up. DO you use a hardware firewall/router in between your modem and computer? when that's the case some routers don't properly forward dns requests so pages won't resolve. does this work?

[http://216.52.208.185/Store/Category.aspx?Category=3&name=Barebones-Accessories](http://216.52.208.185/Store/Category.aspx?Category=3&name=Barebones-Accessories)

if it does, then it's a DNS issue. There are a few ways to solve this that are told within the ubuntuforums.org. Just use the search tool within the forum.

---

### Post by dannyboy79 on 2008-01-04
> **lisati said:**
> [LIST=1]
[*]Cookies (or similar): if not the specific problem, they might prove to be a useful snack while pondering the problem
[*]Activex? The web page designer might be assuming Windows or IE instead of Firefox
[/LIST]

i go to newegg.com all the time with firefox. on gutsy and feisty as well as windows. I don't believe that's the issue but I suppose we can't rule that out until further info is given.

---

