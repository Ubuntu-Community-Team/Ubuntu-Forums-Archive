---
title: "azureus+java lazy bash-script request"
date: 2007-09-26
forum: General Help
---

### Post by apd on 2007-09-26
Hi,

As we know sometimes when Azureus crashes you have to 
1. update-alternatives --config java and downgrade to a lesser version 
2. start Azureus, check that it start fine
3. close Azureus
4. update-alternatives --config java
5. start Azureus and there you go

Now, I'd like to write a shell script that does this for me, and even better to write a shell script that I can run instead of Azureus that looks if Azureus was cleanly closed and if so start normally and if not first downgrade java, start Azureus after some time send a sig-close (or what's it called), upgrade java and start Azureus for real.

I'm not sure the second part is possible (as I haven't investigated if Azureus leaves a nice report on it's non-clean closings) but at least the first part should be doable.

Any pointers would be much appriciated :)

/tsr

---

