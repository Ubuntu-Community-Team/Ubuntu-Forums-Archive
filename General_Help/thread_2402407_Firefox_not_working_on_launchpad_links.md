---
title: "Firefox not working on launchpad links"
date: 2018-09-29
forum: General Help
---

### Post by monkeybrain20122 on 2018-09-29
Not sure when it started happening. When try to click some launchpad links on google e.g [https://launchpad.net/~mc3man/%2Barchive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/%2Barchive/ubuntu/mpv-tests), nothing happens. Then when I try open link in new tab I see
> 
[The page you were on is trying to send you to ]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&ved=2ahUKEwjOs_Tk6eDdAhWK5IMKHT8VDuAQFjACegQICBAB&url=https%3A%2F%2Flaunchpad.net%2F~videolan%2F%252Barchive%2Fubuntu%2Fstable-daily&usg=AOvVaw2zRxC7khXwt3jddWr06E72")[https://launchpad.net/~mc3man/%2Barchive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/%2Barchive/ubuntu/mpv-tests).

 If you do not want to visit that page, you can [return to the previous page]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=2ahUKEwjcpYX56uDdAhWS14MKHasPCP0QFjABegQIAxAB&url=https%3A%2F%2Flaunchpad.net%2F~mc3man%2F%252Barchive%2Fubuntu%2Fmpv-tests&usg=AOvVaw0PwtH3QJne5QsTG6iOWMPF#").



If I then click the launchpad link it goes there.

This only happens on Firefox, on Chrome there is no issue. 

I have tried doing this in a new Firefox profile, same thing. Tried on two different machines (Ubuntu 16.04 and Ubuntu 18.04) with clean FF profiles, same. I think it may be some kind of Firefox security feature that blocks my access.  Firefox is fully up to date at version 62.

**Edited**: just to clarify this only happens when trying to access links from google, it doesn't happen to all launchpad links, but to a lot of them. I have not experienced it on other sites yet.

**Edited**: Even more strange, same links work in duckduckgo

---

### Post by &amp;KyT$0P# on 2018-09-29
That is a google page.

---

### Post by Qew on 2018-09-29
Noticed the same. Thought some setting had changed in Firefox 62.0, but it's just really Google that's doing it. Bing and DuckDuckGo work fine. You can go to the link directly, and it's fine. Seems to me that Google are at fault here; probably browser sniffing.

---

### Post by monkeybrain20122 on 2018-09-30
This [extension]("https://addons.mozilla.org/en-US/firefox/addon/google-no-tracking-url/?src=search") apparently fixes it.  "Google uses a redirection link to tracks your clicks, in order to analyze the stats and later optimize their search results. This addon **simply removes that redirection and turns every search result in its original link**, saving your time and giving you more security."

---

