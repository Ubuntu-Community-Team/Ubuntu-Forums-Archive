---
title: "[SOLVED] ICA -session doubled up on log in"
date: 2008-05-06
forum: General Help
---

### Post by Jimtuv on 2008-05-06
When I log in I get a window that says:

The ISD - Server could not be started because port 5800 in use

when I go into sessions and look in currant session i find that the 
ica -session is doubled.

I know how it happend. I hit the Remember currantly running applications under the Session Options tab.

the question is how do I get rid of the double entry. I assume this is kept in a file and needs to be edited out.

I am very new to Ubuntu only 5 days. So be patient please.

---

### Post by Jimtuv on 2008-05-08
I have searched high and low and can't find a good explanation of what file holds the local session script when a user logs on. I would bet there is a duplicate entry in there if that is what is going on here.

---

### Post by Jimtuv on 2008-05-08
I solved this myself. What I did is to go:

System > Preferences > Sessions

and then in the Currant Sessions tab I removed all occurrences of

ica -session  117f000101001210253 etc.....

hit apply. made sure nothing else was doubled and then I went to the Sessions Options tab and hit Remember Currently Running Applications.

I hope this will help some one.

---

