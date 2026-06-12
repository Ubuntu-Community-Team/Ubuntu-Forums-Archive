---
title: "Move toolbars in Firefox"
date: 2006-11-27
forum: General Help
---

### Post by osprey_criminal on 2006-11-27
I was curious to see if anyone knew how to move toolbars (specifically, the tab toolbar) in Swift Fox/Firefox.  I know that in Opera, you could move them to all sorts of places, and I would really like to have my tabs on the bottom of the browser window.

---

### Post by mcduck on 2006-11-27
At least Tab Mix Plus -extension allows you to move tab bar to bottom, as well as many more options to how your tabs work. You could try that.

---

### Post by kohoutec on 2006-11-27
Another option is to add the following to your userChrome.css file (create the file if it doesnt exist, it lives in your firefox profile)

/* Display the tabbar at the bottom */
#content > tabbox { -moz-box-direction: reverse; }

---

