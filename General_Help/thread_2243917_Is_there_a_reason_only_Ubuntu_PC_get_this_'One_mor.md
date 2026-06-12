---
title: "Is there a reason only Ubuntu PC get this 'One more step required'?"
date: 2014-09-12
forum: General Help
---

### Post by zemega on 2014-09-12
Hi, lately I have been running to web pages showing 'One more step Please complete the security check to access' on PC running Ubuntu in my workplace. **NONE** of the Windows PC has this problem. Both cases Firefox. Please refer to the attachment for example. I have to put in some Captcha but in the attachment scrrenshot did not show the captha, because sometimes it doesnt appear.

---

### Post by lisati on 2014-09-12
It's possible that the website is examining the user-agent information provided by your browser, and is failing to recognize your linux machine as something safe.

---

### Post by zemega on 2014-09-12
A website? That's a bit wrong, its multiple website. There are multiple websites. All Wordpress blog will show this.

---

### Post by yancek on 2014-09-12
There are literally thousands of sites which only recognize a windows browser so try changing the User Agent extension in your Linux firefox to a windows user agent.
Firefox, Toots, Add-ons, then type:  User Agent Switcher in the search box, hit enter and pick one.

---

### Post by zemega on 2014-09-12
> **yancek said:**
> There are literally thousands of sites which only recognize a windows browser so try changing the User Agent extension in your Linux firefox to a windows user agent.
Firefox, Toots, Add-ons, then type:  User Agent Switcher in the search box, hit enter and pick one.

Surprisingly, that include website that talks about Linux and not Windows? I don't think so, I think its one of the Internet route around here, to be exact Cloudfare Singapore that's giving this problem. Which is beyond my control.
Yes changing user agent does work, but it does not solve the fundamental problem, an ISP doesn't like Linux or Ubuntu specifially (Mac OS X don't have problems as well).

---

