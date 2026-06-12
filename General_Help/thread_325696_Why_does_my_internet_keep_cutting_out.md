---
title: "Why does my internet keep cutting out?"
date: 2006-12-26
forum: General Help
---

### Post by i_pod25 on 2006-12-26
im very inexperienced with computers....but my Internet lately cuts out and stops working towards either the end of the day or the end of the month...... 

i know i havent given much detail but anyone know maybe why its happening?
im using firefox on unbuntu and its connected directly to the internet....

thanx

---

### Post by flyingbrass on 2006-12-26
You said end of the day or month.  Does your ISP have daily and monthly bandwidth caps?

When it's not working you could pull up a terminal and figure out where the problem is using traceroute (I prefer tcptraceroute -- you'd have to install it), nslookup, etc.  

For example, try:

nslookup google.com

If it resolves to an IP number, DNS is working.

tcptraceroute google.com

That will show where along the line the connection is failing.


Usually the rare times my connection chokes it's because my ISP's DNS servers aren't responding.

---

