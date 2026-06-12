---
title: "Firefox occasionally &quot;unable to find proxy server&quot; and js issues"
date: 2015-01-25
forum: General Help
---

### Post by sowdust on 2015-01-25
Hello everyone, since a couple of weeks I've been experiencing strange issues with firefox I never had before.Firefox is set up to go through privoxy's proxy, but lately sometimes (roughly 1 in 20) when I request a URL I get the "Unable to find the proxy server" error tab. If I click on "try again" or manually refresh the page, I am immediately brought to the requested URL. Another issue that doesn't seem related but that became to happen at the same time of the just mentioned one, is that sometimes firefox has problems  I think are related to execute javascript. For instance, when I open up the browser and point it on twitter's login page, just to mention a case that can be shared by others, roughly 2 times in 3 I am unable to login: pressing the login button or typing enter does not trigger any activity and I have to restart the browser to make it work.Any suggestion on what might be causing this?Thanks!

---

### Post by flaymond on 2015-01-25
Do you installed any additionals add-on in the browser? It can slow your browser. Thus, it could impact some functionality of the browser.

---

### Post by sowdust on 2015-01-26
Hi, no, I haven't installed any new add-on  in a long time and the most recent ubuntu updates that involved firefox were release only after I started experiencing the problem.

---

### Post by SeijiSensei on 2015-01-26
Is the proxy server designated by hostname or IP address?  If you can choose the latter, give that a try.  It might just be a DNS issue.

Is this a proxy you control?  If not, maybe the proxy is just busy and drops requests.

---

### Post by sowdust on 2015-01-31
Hi, I am sorry for the late replies, but since I have changed email settings the forum seems to have stopped sending me email notifications.Anyway it is an internal proxy that resides on the same OS firefox is running on and is therefore accessed directly through ip:port

---

### Post by SeijiSensei on 2015-01-31
You mean the same machine?  Are you accessing the proxy using localhost (127.0.0.1)?  If so, I can't imagine anything that would cause the symptoms you report.

---

### Post by sowdust on 2015-02-01
Yes, that is what I mean

---

### Post by SeijiSensei on 2015-02-01
And you're using localhost?

---

### Post by sowdust on 2015-02-02
yes, I am using localhost

---

### Post by SeijiSensei on 2015-02-02
Beats me, then.  Have you read the documentation at [http://www.privoxy.org/?](http://www.privoxy.org/?)  Filed a bug report?

---

### Post by sowdust on 2015-02-05
At first I thought I thought it could be a general firefox problem since both javascript and privoxy's issues came up roughly at the same time.Now I am more convinced the problems are separate, and this one has to do with privoxy itself. I will investigate there and post back if I reach any conclusion. Thank you for the support.

---

