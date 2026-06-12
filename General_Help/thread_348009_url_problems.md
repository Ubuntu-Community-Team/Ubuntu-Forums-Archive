---
title: "url problems"
date: 2007-01-28
forum: General Help
---

### Post by Rusty McCrusty on 2007-01-28
I have set up a web server with ubuntu edgy
The problem I am having is that when I type in the url for the web site [www.revclub.net](www.revclub.net)
It goes to the admin page of my router.
I have tested the web page on a friends comp and the page loads up with no problem, but to access it on my home comp I have to type in the static ip of the server.
Anyone have any ideas to fix this?
Cheers
Rick

---

### Post by JamieC on 2007-01-28
You can't view your site if it's on your internal network using an external IP... You can view it by configuring a proxy for your browser.

---

### Post by Rusty McCrusty on 2007-01-28
thanks for the quick reply 
How do I go about doing that?
Cheers
Rick

---

### Post by JamieC on 2007-01-28
Assuming you are using Firefox:

Click the 'Tools' option from the top menu bar, then click 'Preferences' at the bottom of the drop down.

Click the 'Advanced' icon, then the 'Network' tab. There will be a 'Settings' button on the right, click it.

Check 'Manual Proxy Configuration' and fill in the fields for 'HTTP Proxy'. You can find a list of proxies by simply searching Google.

Then click OK, restart Firefox to be sure your changes have been saved, and visit your site once again.

---

### Post by Rusty McCrusty on 2007-01-28
thanks for that

---

### Post by JamieC on 2007-01-28
No problem, is it working now?

---

### Post by Rusty McCrusty on 2007-01-28
no it is still going to the admin page

---

