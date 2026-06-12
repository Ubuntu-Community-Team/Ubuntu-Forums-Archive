---
title: "firefox under ubuntu cannot handle WML(?) links..."
date: 2008-06-05
forum: General Help
---

### Post by A$h X on 2008-06-05
Here's a link from a page I regularly visit. It works under windows+firefox:

[http://gallery.breakbeat.co.uk/view.aspx?gallery=data%2fdrumandbassarena%2fusercontent%2f,mode=1](http://gallery.breakbeat.co.uk/view.aspx?gallery=data%2fdrumandbassarena%2fusercontent%2f,mode=1)

Now if I use the SAME firefox version under ubuntu hardy it refuses to load. I get a dialog asking if I want to save the file "view.aspx" or open it with another program. 
Is this fault common or is there something wrong with my setup?

I actually asked an admin of the site what's the problem, and he replied that it was because the site doesn't recognize the browser. Firefox 2 is pretty much standard nowadays isn't it?

---

### Post by BUSHYBOB on 2008-06-05
The site's browser detection is flawed
Change your userAgent string with this

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

to IE 7 and vista and that site works.

---

